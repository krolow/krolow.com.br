+++
categories = ["git"]
date = "2016-02-23T23:47:56-03:00"
title = "How clean old remote branches locally"
+++

I use git-flow, so we use a lot of branches often, and those branches got stuck in our local repository,
to cleanup old remote branches we can use:

```bash
git fetch origin --prune
```
