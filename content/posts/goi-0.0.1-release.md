---
title: "Goi v0.0.1 release"
date: 2026-04-05T19:45:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "I managed to procrastinate my procrastination"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "Images/Goi001/landingpage.png" # image path/url
    alt: "Landing page" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

# Background
Thanks to Good Friday & Easter, I managed to get a long holiday from work. Normally I would just be lazy & enjoy myself, but the JLPT registration opens on the 8th of April for my city. I was considering skipping July's test, but my friends sent me a link to a [news article](https://english.kyodonews.net/articles/-/73562) about engineers and visa status:

> According to the source, the revised policy will require applicants to submit documentation proving Japanese proficiency at the B2 level of the Common European Framework of Reference for Languages, equivalent to N2 of the Japanese-Language Proficiency Test.

Better start grinding then...

You can access Goi [here](https://goi.sebastianaldi.com/).

# Code base
The code base can be seen [here](https://github.com/sebastianaldi17/goi/). It is split into 4 main folders which are:

## sql
Not much to talk about here. I use PostgreSQL because I'm more familiar with it.

Currently I divide my tables into 4 tables: `vocabs` (the word itself), `tags` (any special tag/note to attach to the vocab if needed), `definitions` (the part of speech, meanings, and tags from jisho), and `examples` (JP example + English translation, sourced from jisho).

## scripts
![](/Images/Goi001/sheet.png#center)
The initial population of the database is done through a Google Sheet spreadsheet that I made & fill. It consists of 4 columns: Kanji, Kana (acts as a fallback & safeguard since Japanese do be like that sometimes), Level (N5-N1), Tag (not shown in the image).

The script requires a service account, which requires a Google Cloud project (it's free). The service account credentials is used by the script to login as the service account & read the contents of my spreadsheet, then hit jisho to fetch the definition & examples.

## goiweb
I'm a bit ashamed to admit this, but the frontend part is mostly coded by Claude. I have some frontend knowledge & have written the code myself for my past projects, but initializing a new frontend project is very rough for me (at least compared starting a new backend project). I didn't subscribe to Anthropic's paid plans, so it is a lot of back and forth in the chat (Claude Code requires an active subscription).

I have no preference on Vue vs React, regular React vs Next.js, etc. If I were to do vanila Vue or React then I would have to deal with setting up client side routing (CSR), so I ended up using Next.js because their folder based routing makes everything a breeze.

Of course everything can actually be done with vanilla HTML + CSS + JS but I'm too used to React.

## goibackend
The only reason I used Java + Spring Boot is so that my Java skills don't decay as much, despite me being much more proficient in go. This decision kind of backfiring at me because Render (see the section about Render below) doesn't support Java, so I had to tinker a bit with Docker to get it working.

# Free service stack
When starting a project ideally want to create a prototype that doesn't cost me anything. Here are what I used to make everything free:

## Supabase
[Supabase](https://supabase.com/) actually has a ton of free features such as authentication & a free S3-like object storage (after all it was meant to be an alternative to Firebase), but I only utilized their free 500MB PostgreSQL DB.

Their DB is very slow though since it is a shared resource, but I don't get to complain when I don't even pay them :laughing:

## Render
[Render](https://render.com/) has a free plan to host my API. It supports Node.js, python, ruby, go, rust, elixir. Sadly it doesn't support java, but they accept docker images. All I need to do is to have a Dockerfile on the root my my API (goibackend).

Their free plan spins down with inactivity though, so there might be times where my website will be extremely slow :sweat_smile:

To mitigate potential slow starts I have [FastCron](https://www.fastcron.com/) hit my API every 5 minutes.

## Vercel
Since my frontend project uses Next.js, might as well use [Vercel](https://vercel.com) since Vercel maintains Next.js. They have a free plan that I used for MaiSocial & Maibot without complaints.

# What's next
Since this is a personal curated list of mine, the list will grow slowly based on when I decide to expand them. Based on the levels, these are my plans for the future:

- N5: Thirdy priority
- N4: Second priority
- N3: Alongside N2, will be main priority
- N2: Alongside N3, will be main priority
- N1: Definitely not anytime soon

Feature-wise I don't have any plans to expand the capabilities of my website. I will probably only do bugfixes.

If I enjoy this project & get annoyed by the latency & late starts then I will invest in a VPS for the DB + API.
