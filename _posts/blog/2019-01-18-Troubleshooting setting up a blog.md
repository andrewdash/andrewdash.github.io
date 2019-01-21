---
layout: post
title: Troubleshooting setting up a blog
date: 2019-01-18
categories: blog
---

There are a lot of small things that can go wrong when setting up the blog. Here are a few that I've run into:

**1. Uploading files via git push origin master only uploads some of the files but not all?**
<br> Try `git rm -r --cached .` will clear the github cache. Then, you can `git push origin master` your files properly

**2. How do you upload a photo that is clickable to some URL, but also changable by size?**
```markdown
[![](/assets/images/yelp_og_image_small.png){:height="160px" width="400px"}]({{ site.baseurl }}{%post_url 2019-01-17-Yelp Connections %})
```
