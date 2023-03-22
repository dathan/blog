---
title: "Openai Fine Tuning Notes"
date: 2022-11-21T10:06:01-04:00
draft: false
---

## OpenAI fine-tuning with a notebook in VSCode


AI is the future. Co-pilot is the future. Building a finetuned layer for GPT-X will enable products to produce results faster, with less upfront effort for a fraction of the cost.


###  Setting up a training set

Let's assume for this post, is based on some structured data. That structured data has been tagged by a human, and there is a lot of it. Roughly 3 MB of data.

The question now is `how `does one `fine-tune` gpt-3 with` this data`?


### Jump Right in

### Generate the data.

```
import pandas as pd # data analysis package
# Two-dimensional, size-mutable, potentially heterogeneous tabular data.
df = pd.DataFrame(dataset, columns = ['prompt','completion'])
print(df.nunique())
df.head()
```

```
prompt        5065
completion      87
```


Notice the completions. This is directly corresponding to a field in the openai client `classification_n_classes`.  Note: *if the train and _valid set _does_ not have_ the completion you'll receive an error described below*

### Dump the data 
```
df.to_json("tags_completion.jsonl", orient='records', lines=True)

```

This command turns the data frames of prompt and completion to a file called tags_completion, which we will use openai to generate a valid and train set.


### Generate the valid trainset for the classification

```
model = 'ada'  # can be ada, babbage or curie
n_epochs = 4
batch_size = 4
learning_rate_multiplier = 0.1
prompt_loss_weight = 0.1
classification_n_classes = 87
```

```
!openai api fine_tunes.create -t "tags_completion_prepared_train.jsonl" -v "tags_completion_prepared_valid.jsonl" --compute_classification_metrics --classification_n_classes $classification_n_classes --no_check_if_files_exist -m $model --n_epochs $n_epochs --batch_size $batch_size --learning_rate_multiplier $learning_rate_multiplier --prompt_loss_weight $prompt_loss_weight`
```

### Meaning of the inputs
* *model* - The name of the base model to fine-tune. You can select one of "ada", "babbage", "curie", or "davinci". To learn more about these models, see the Models documentation.
* *n_epochs* - defaults to 4. The number of epochs to train the model for. An epoch refers to one full cycle through the training dataset.
* *batch_size* - defaults to ~0.2% of the number of examples in the training set, capped at 256. The batch size is the number of training examples used to train a single forward and backward pass. In general, we've found that larger batch sizes tend to work better for larger datasets.
* *learning_rate_multiplier* - defaults to 0.05, 0.1, or 0.2 depending on final batch_size. The fine-tuning learning rate is the original learning rate used for pretraining multiplied by this multiplier. We recommend experimenting with values in the range 0.02 to 0.2 to see what produces the best results. Empirically, we've found that larger learning rates often perform better with larger batch sizes.
* *compute_classification_metrics* - defaults to False. If True, for fine-tuning for classification tasks, computes classification-specific metrics (accuracy, F-1 score, etc) on the validation set at the end of every epoch.



### Encountered Problems and Resolutions


### Problem: The number of classes in file-njsdeo0sSlPVGFsK2an0iinJ does not match the number of classes specified in the hyperparameters

What this means is that the train or valid file does not have enough data for each class in the neural network. There are recommendations to make this work.

#### Recommendations

* The `completion` SHOULD have a 100 entries per class
* The `completion` tokens MUST be distinct enough for the GPT-2 tokenizer. Basically, 3/4 of the word must be distinct enough in the completion of classes.
* The length of `prompt` and `completion` MUST not be larger than 2048 characters.


### Problem: If `compute_classification_metrics` is `True`, each of the classes must start with a different token

* The completion is not distinct enough based on GPT-2 tokenize specifications.
* https://beta.openai.com/tokenizer?view=bpe to see the token overlap


#### Recommendations
```
# cat tags_completion.jsonl |jq .completion |sort -u |awk '{ print $2}'|
```

* This command allows you to view the classes and the 1st token - this helps determine if your tokens are ok.
* Since the documentation alludes that tokenization starts from left to right and is approx 3/4 of the word. The common words need to be worked out.

```
#keep a map
checkDict = {}
distinct = 0
for index, row in df.iterrows():
    # if the completion exists in the dict use that value
    if row['completion'] in checkDict:
       df.at[index,'completion'] = " {}".format(checkDict[row['completion']])
    else:
        distinct += 1
        checkDict[row['completion']] = distinct
        df.at[index, 'completion'] = " {}".format(checkDict[row['completion']])

# Save the data as jsonl file\n",
df.to_json("tags_completion.jsonl", orient='records', lines=True)
```


## Progress

~~Most of my time is massaging the data to fine-tune gpt-3. I am very close and will update this post once I get past my last error.~Conclusion

* prompt and completion length must not be longer than 2048 characters
* each completion is a classification class and must be token unique, thus switching the completion to a number is ideal (1-100)
* there *SHOULD* be 100 data points for each completion
* both train and valid files need ALL completions present ideally at least 100 in each file.


### Helpful links

* [https://github.com/openai/openai-cookbook](OpenAI Cookbook)