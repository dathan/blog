---
title: "Some Thoughts on Github Hugo"
date: 2021-10-12T18:11:46-07:00
draft: false
---

Unless one uses GitHub pages you may not be aware that the contents of GitHub pages site can happen on branches and path combos. Using the GitHub action and reading the documentation, the action to build is on main. `Main` is the default branch, but the git hub action that is activated on pushes to main executes hugo and publishes the hugo generated site to the root of the `gh-pages` branch. As a result, a silent step was needed to automated the blog post. Changing the pages setting.

Thus to recap. Goto

```
Settings > Pages > Source pick gh-pages and root and click save
```
