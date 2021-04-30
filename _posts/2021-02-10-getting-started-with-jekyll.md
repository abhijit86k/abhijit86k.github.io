---
title: Jekyll Webpages
author: Abhijit
layout: post
tags: Jekyll
---

A few months ago I was faced with the task of developing a bunch of websites / webpages for a variety of requirements (one of which was the new Opelex website). This post is a brief log of how I set it up using Jekyll and github pages. [Test](google.com).

<!--more-->

### Requirements
Most of the requirements were fairly straightforward:
 - A "content-first" approach - once the site is set up, adding content should be as simple as possible
 - Appearance should be simple and aesthetic - nothing fancy needed
 - Good responsive design - should be usable on any screen size / device.
 - Must support a mix of blog-type content, simple pages, images, and embedded content.

I had [worked with bootstrap earlier](https://github.com/abhijit86k/BootstrapHomepageTemplate) to develop my [university homepage](https://iitdh.ac.in/~kabhijit/), but I knew that it was not a scable solution beyond a few simple pages with largely unchanging text. Based on the requirements, Jekyll seemed like the obvious choice, especially given the great support from Github pages.

Other than the official documentation, here are some notes that I would have found useful, in hindsight.

1. The Official Jekyll documentation is good for creating a very plain website. Definitely go through the example once so you know what a working system should look and behave like. 
2. Themes
 - Choosing a base theme is critical. Do not waste time on a theme that does not look 90% of what you finally want. Changing colors and fonts in the theme is realatively easy - changing layouts is not. Spend some time looking through the demo site - usually the demo site will show off all the features of the theme/template.
 - Not all themes work with github pages. As far as possible use a theme that explicitly states compatibility with github pages. 
 - Tags and Categories are baked into Jekyll. Even if you don't see categories/tags in a theme, these can be added.
 
3. To "live preview the site / code as you write it, you can use a markdown editor like brackets, or you can locally serve the site using this command
```
bundle exec jekyll clean; bundle exec jekyll serve --livereload --watch
```
The first command "cleans" up all generated files; the second one force-regenerates everything and serves it up to be viewes in a browser. Note that the  `--watch` option causes re-compilation whenever any file changes, and `--livereload` causes the browser to refresh / reload when this happens. This only works when you edit the layouts/markdown content. If you edit `_config.yml` or other files you need to run the clean and serve commands again.
