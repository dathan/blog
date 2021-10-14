---
title: "Some Thoughts on Github Hugo"
date: 2021-10-12T18:11:46-07:00
draft: false
---

GitHub pages is new for me and I was not aware that the contents of GitHub pages site can be based on branches and path combos. Using the GitHub action and reading the documentation, the action to build is on main. `Main` is the default branch. The action also executes hugo and publishes the hugo generated site to the root of the `gh-pages` branch. As a result, a silent step that was needed to automated this blog post. Changing the pages setting to set the doc root of this [repo](https://github.com/dathan/blog) to the `gh-pages` branch.


Thus to recap. Goto

```
Settings > Pages > Source pick gh-pages branch and root path then click save
```
