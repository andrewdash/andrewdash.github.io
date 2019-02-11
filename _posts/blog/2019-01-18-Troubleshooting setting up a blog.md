---
layout: post
title: Troubleshooting setting up a blog
date: 2019-01-18
categories: blog
---

There are a lot of small things that can go wrong when setting up the blog. Here are a few that I've run into:

**0. Things to make sure you've done**
- anything that is uploaded as a post (blog, essays, projects) should be within the `_posts` folder. Within posts, I have `blog`, `projects` as my subfolders, and those folders contain the postings for each
- any file that is an image, pdf, or whatever should be within `assets`, organized into folders as well
- Things that you want to show up all the time will be located in your `_layouts` default.html file

**1. Uploading files via `git push origin master` only uploads some of the files but not all?**
<br>
Try `git rm -r --cached .` will clear the github cache. Then, you can `git push origin master` your files properly

**2. How do you upload a photo that is clickable to some URL, but also changeable by size?**
```python
[![](/assets/images/yelp_og_image_small.png){:height="160px" width="400px"}]({{ site.baseurl }}{% post_url 2019-01-17-Yelp-Connections %})
```
