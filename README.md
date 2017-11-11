# Eve of Darkness Blog

This is the source for the blog that is hosted at `www.eveofdarkness.org`.  Any
pushes to master with a successful build will update the site.


## Adding A Post

If you know Ruby and want to take the time to learn Jekyll / Octopress you can
create a new post with `octopress new post "post name"`; however, it's as easy
as making a new file with the following formatted name in `_posts/`

```
YYYY-MM-DD-some-catchy-title.markdown
```

The very top of the post file should be formatted like this:
``` yaml
---
layout: post
title: "Some Catchy Title"
date: YYYY-MM-DD
author: "Your Name"
category: "optional category"
---
```
