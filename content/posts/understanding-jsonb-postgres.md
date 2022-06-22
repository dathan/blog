---
title: "Understanding Jsonb Postgres"
date: 2022-06-21T18:17:27-07:00
draft: false
---



I am running across how to debug data in PostgreSQL, a platform I am not familiar with. Specifically using [JSONB_SET](https://www.postgresql.org/docs/13/functions-json.html). JSONB_SET documentation is the following

*jsonb_set ( target jsonb, path text[], new_value jsonb [, create_if_missing boolean ] ) → jsonb*

```

Returns target with the item designated by path replaced by new_value, or with new_value added if create_if_missing is true (which is the default) and the item designated by path does not exist. All earlier steps in the path must exist, or the target is returned unchanged. As with the path oriented operators, negative integers that appear in the path count from the end of JSON arrays. If the last path step is an array index that is out of range, and create_if_missing is true, the new value is added at the beginning of the array if the index is negative, or at the end of the array if it is positive.

jsonb_set('[{"f1":1,"f2":null},2,null,3]', '{0,f1}', '[2,3,4]', false) → [{"f1": [2, 3, 4], "f2": null}, 2, null, 3]

jsonb_set('[{"f1":1,"f2":null},2]', '{0,f3}', '[2,3,4]') → [{"f1": 1, "f2": null, "f3": [2, 3, 4]}, 2]
```

## The operators 

| Operator | Right Operand Type | Description                                                                                                                                   | Example                                             |
| -------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| @>       | jsonb              | Does the left JSON value contain the right JSON path/value entries at the top level?                                                          | '{"a":1, "b":2}'::jsonb @> '{"b":2}'::jsonb         |
| <@       | jsonb              | Are the left JSON path/value entries contained at the top level within the right JSON value?                                                  | '{"b":2}'::jsonb <@ '{"a":1, "b":2}'::jsonb         |
| ?        | text               | Does the string exist as a top-level key within the JSON value?                                                                               | '{"a":1, "b":2}'::jsonb ? 'b'                       |
| ?|       | text\[\]           | Do any of these array strings exist as top-level keys?                                                                                        | '{"a":1, "b":2, "c":3}'::jsonb ?| array\['b', 'c'\] |
| ?&       | text\[\]           | Do all of these array strings exist as top-level keys?                                                                                        | '\["a", "b"\]'::jsonb ?& array\['a', 'b'\]          |
| ||       | jsonb              | Concatenate two jsonb values into a new jsonb value                                                                                           | '\["a", "b"\]'::jsonb || '\["c", "d"\]'::jsonb      |
| \-       | text               | Delete key/value pair or string element from left operand. Key/value pairs are matched based on their key value.                              | '{"a": "b"}'::jsonb - 'a'                           |
| \-       | integer            | Delete the array element with specified index (Negative integers count from the end). Throws an error if top level container is not an array. | '\["a", "b"\]'::jsonb - 1                           |
| #-       | text\[\]           | Delete the field or element with specified path (for JSON arrays, negative integers count from the end)                                       | '\["a", {"b":1}\]'::jsonb #- '{1,b}'                |


## Some examples

[https://popsql.com/learn-sql/postgresql/how-to-query-a-json-column-in-postgresql](https://popsql.com/learn-sql/postgresql/how-to-query-a-json-column-in-postgresql)

[https://www.postgresql.org/docs/13/functions-json.html](https://www.postgresql.org/docs/13/functions-json.html)

[https://www.haselt.com/blog/working-with-postgresql-jsonb](https://www.haselt.com/blog/working-with-postgresql-jsonb)
