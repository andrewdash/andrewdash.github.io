---
layout: post
title: Setting up a blog using Jekyll
date: 2019-01-09
categories: blog
---


Jekyll is a popular way to generate a blog site. My first attempt at the site had been through it's vanilla version, as [found here](https://github.com/barryclark/jekyll-now). This link isn't to the Jekyll website, but rather by someone who had created an easily generatable version of it on Github. Simply following the instructions will get the blog up and running!

I decided it was too plain, so I wanted to get some sort of designs going. Without HTML/CSS experience, this challenging (hence using Jekyll in the first place), but after a lot of research, picking up small  bits of syntax, and tons of trial and error, here's the process I found to get my site up and running. I hope to eventually fully re-design the website to my liking, but this will have to do for now.

I used a Jekyll theme called [Tactile](https://github.com/pages-themes/tactile), but made certain modifications in order to get a couple things up that I wanted to have. Making these modifications took a large bulk of this research process (would've been helpful to know HTML/CSS here).

I used GitHub Pages to host my website, which has some restrictions on the pre-made themes available. This guide is intended as notes for myself, and for the HTML-illiterate (no shame-- we're here to learn!). If you're able to host your site independently, this guide isn't probably of much use to you anyways.

**Phase 1: downloading & installing stuff to prep**
  - [Ruby+Devkit installation](Ruby+Devkit installation)
  - clone the git repository so that you have it locally
  - upload it to your Github so that you can host it on Github pages
    - use `git push remote origin`
    - in CMD, inside your local repository, run `git remote -v` to make sure you're uploading to the right Github repository
  - depending on your theme, you'll need to upload a bunch of random rubygems.org stuff. For Tactile, I had to download `rubocop`, `html-proofer`, `w3c-validators`

**Phase 2: getting the site to run locally and connecting it to GitHub Pages**
  - to have the theme run, you need to have a functional Gemfile within your repository. To do so, run `bundle init` within your website's parent directory
  - download the entire Github repository and follow the instructions to get it up and running. Once you do, you'll have a blank site
  - running the website locally, you want to be in the base folder, which has your Gemfile, config.yml file, and the others. You run `bundle exec jekyll serve` here and your website will run locally.


**Phase 3: figuring out what sort of new adjustments you want to the themes**
- I put in `<a href="{{ site.baseurl }}/about">About</a>` within my `default.html's` <body> / div / div / header / nav. Doing this let all pages in my website populate the word Home in a specific spot. It also take me, when I clicked on that word About, to the About webpage. The About webpage is defined within the base folder (with the config.yml file and stuff) as an html file called about.md. The code posted here routes to that about.md.
-

**Phase 4: solving for those adjustments!**


Congratulations! You have a themed Jekyll site up and running. After writing a few short pieces and taking a stab at that Phase 4, it's cool to see that effort  become realized into a visual piece of work. Best of luck as you keep at it!

Useful links:

[jekyll video walkthrough](https://jekyllrb.com/tutorials/video-walkthroughs/)

[how categories work in jekyll](https://blog.webjeda.com/jekyll-categories/)
