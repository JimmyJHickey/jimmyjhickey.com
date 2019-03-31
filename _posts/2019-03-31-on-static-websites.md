---
layout: post
comments: true
title: On Static Websites
description: An overview on static websites, their advantages, and an introduction on how to use them.
---

* Do not remove this line (it will not be displayed)
{:toc}

### What is a static site?

A *static website* has all of its files stored on a computer/server. When you go to that site, the files are presented to you exactly as they are saved. 

In contrast, there are *dynamic sites* which have the ability to change based on factors such as who is accessing the website, the time of day it is accessed, and more. These sites have the ability to do things that statics sites cannot like access databases, store log in information, and save forum posts.

Static sites are particularly useful when the site only changes if the author uploads new content. Some uses may be a blog, landing page, online portfolio, and information site.

### Advantages to using static sites

Though they may initially seem limited in functionality, static sites have many advantages over dynamic sites. First, they are fast. By not having to access any databases or run any scripts on the server prior to loading the page for the user, static pages are delivered very quickly. This has the benefit of keeping users engaged and gaining you more views as search engines prefer pages with quick load times. 

The absence of server-side code and databases also increases security. Dynamic sites needs to be built before they are served to a user. This saves on hosting costs making static sites very affordable.

Also, this build process offers a large area of attack. In 2014, Drupal, a popular content management system used for creating dynamic websites, was the victim of <a href="https://www.drupal.org/forum/newsletters/security-public-service-announcements/2014-10-29/drupal-core-highly-critical" target="_blank">an attack</a>. The report states that if a site was not updated within 7 hours of the patch, that it should be assumed to be compromised. Static sites have very few dependencies to keep up to date.

### How to use static sites

You could write all the HTML by hand; however, there are many static site generators that will help you. For a list of options, you can refer to <a href ="https://www.staticgen.com/" target="_blank">staticgen.com</a>. More popular generators have large communities behind them developing plug-ins and themes that can often be used for free. Many also support Markdown syntax for pages, making writing a page simpler than writing the HTML from scratch.

I chose to use Jekyll for this blog due to its popularity and its integration with GitHub Pages. If you also wish to set up a Jekyll site, I recommend looking at some of the <a href="https://blog.webjeda.com/create-jekyll-blog/" target="_blank">Webjeda tutorials</a>.

### Sources

Much of this post comes from my experience and research using Jekyll to create this website over the past few weeks. I also pulled information from Part one of <a href="https://www.lynda.com/GitHub-tutorials/Learning-Static-Site-Building-Jekyll/761964-2.html" target="_blank">*Learning Static Site Building with Jekyll*</a>, a course by Nate Barbettini on Lynda.com.
