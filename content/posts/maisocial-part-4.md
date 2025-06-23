---
title: "MaiSocial - Part 4"
date: 2025-06-23T13:15:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Circular dependency, Event emitters, GitHub Copilot"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "/Images/MaiSocial/thumbnail-part-4.png" # image path/url
    alt: "thumbnail" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

# Background
This is another update of my current hobby project. You can read the previous parts here:

- [MaiSocial - Part 1 (Backend & Frontend initialization)](/posts/maisocial-part-1)
- [MaiSocial - Part 2 (Comment section, Google SSO)](/posts/maisocial-part-2)
- [MaiSocial - Part 3 (WebP, romaji search)](/posts/maisocial-part-3)

I had some spare time during a sprint, so I decided to work on my personal project a bit. The feature I wanted to make is a playlist feature, where users can create playlists & can share them publicly. In this post I will be talking about a few things:

- Circular dependency
- Event emitters
- My GitHub copilot experience

# Circular dependency
NestJS is an opinionated framework, where you have modules that handle different parts of your application. In my case, I have a module for comments, songs, playlists, and users.

Sometimes modules may require features that belong to other modules, and that is fine. For example, I need to load the song's metadata when displaying a playlist, and I only stored the song IDs on my playlist schema, so I need to fetch the song metadata whenever a playlist is requested.

The problem arises when modules depend on each other. In my case, when a user deletes their playlist, I want to delete all comments related to the playlist, in order to prevent dangling/orphaned comments that won't show up in the frontend. At the same time, I need to load the playlist's metadata when I want to show a user a list of their own comments.

- Playlist module depends on comment module to erase comments
- Comments module depends on playlist module to load playlist metadata

A circular dependency arises because they depend on each other. In order to solve this, there are a few ways that I could think of:

- [Use `forwardRef()`](https://docs.nestjs.com/fundamentals/circular-dependency), but for some reason I could not get this to work
- Use a message queue, but this is a bit overkill & I want to try to keep my project running for free
- [Use events](https://docs.nestjs.com/techniques/events)

# Event emitters
Event emitters are like mini message queues that run in your backend service:

- They listen to your events & perform tasks asynchronously
- It can be listened by more than one listener

The only downside I can see is probably that they're not durable (messages/events not saved to disk), and other backend services cannot listen to the event.

I think event listeners are ideal for me, because deleting comments / updating user metadata on playlists & comments might take a long time if there are a lot of them.

# GitHub copilot
My workplace gave me a GitHub copilot subscription, so I have been using it lately. It really helped me during my daily work & this project, but I also felt like it stunted my growth / thinking ability.

## The good
I wouldn't call myself a good frontend engineer. Far from it. As someone who is primarily a backend programmer, frontend is just a means to showcase my project.

For this current project, I decided to use tailwind, while my previous experience was using Material UI. The nice part about tailwind is how it is just a CSS framework with tons of utility classes. The not so nice part is that you have to make your own components, while Material UI has some predefined components that you can use.

An example would be an combobox/autocomplete component, where [Material UI](https://mui.com/material-ui/react-autocomplete/) has it out of the box, while you have to make your own in tailwind.

I used copilot's agent mode to create me a "create playlist" page from scratch. For me, the results are good enough.

![](/Images/MaiSocial/create-playlist.png#center)

## The bad
The problem with generating code using AI is that I learned nothing in the process. If you ask me how to make a combobox using tailwind classes only, I would still blank out or not remember.

I'm more of a learning by experience person, so reading generated code would not help me at all. I could tinker with the code to see what happens, but I chose not to, and that is a problem in itself.

I think being dependant on AI to do my job is scary, because then I would not need to think in order to accomplish my job. I feel like if I stop thinking, my brain would atrophy and I would end up being a bad programmer.

## The ugly
Another problem with using AI is that it might need multiple prompts to finish something, and if the AI decides to go off the rails, the good parts become unsalvageable as well. This is where a wonderful tool called `git` comes in handy :laughing:

# What's next
Before moving on to other features, I think I want to look over my codebase again, and tidy up any inconsistencies that arose during my AI-assisted coding binge. I think that I am more of a move fast tidy up later person, so if I keep moving on to new features, the technical debt would eventually pile up. I try to reduce the amount of technical debt that I accrue, but I'm not good enough to guarantee zero technical debt.

The JLPT is in 14 days, so I don't think I will be touching my personal project again until then. Wish me luck!
![](https://media1.tenor.com/m/IQHDe-cXPBkAAAAd/not-prepared-for-exam-patrick-bateman-meme.gif#center)