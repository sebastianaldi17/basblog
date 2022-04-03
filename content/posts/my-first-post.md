---
title: "First post, new website"
date: 2022-04-03T11:30:03+07:00
# weight: 1
# aliases: ["/first"]
tags: ["life"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Returning to making a personal website for the third time"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1555066931-4365d14bab8c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80" # image path/url
    alt: "Generic coding picture" # alt text
    caption: "Looks like I am back making a personal website, for the third time" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Third time?
Yes, this is my third time making a personal website. The first time was using plain HTML, CSS, and Javascript, then publishing it to github pages. The second time was using React.js with Material-UI, which can be seen [here](https://github.com/sebastianaldi17/React-Personal-Site). It used netlify to host static pages, and it worked pretty well until I decided to take down the website for several reasons:

- I got a job as a software engineer, so I felt that I didn't need to advertise myself that much.
- I wanted to make a blog, but at the time I didn't know how because I wanted to keep a folder full of markdown files that serve as blog content, but I can't get it to work without a backend iterating through the folder containing multiple markdown files.

After a coworker decided to leave his current job, I decided that I need to be open to other options instead of just being satisfied in one place, so I wanted to remake a personal website, for the third time. The solution I decided to use was to use [hugo](https://gohugo.io/) to create static HTML files from markdown files. I used hugo because hugo used Go, which was already installed on my laptop (compared to using jekyll needing Ruby installed, but in retrospect this might have been way easier because github pages endorsed it).
