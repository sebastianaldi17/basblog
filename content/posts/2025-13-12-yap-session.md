---
title: "2025-13-12 Yap session"
date: 2025-12-13T22:30:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["life", "tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Just writing to get some negative feelings off my chest"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1661160094555-a798a7df499f?q=80&w=1632&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

Some of my pent up negative feelings have been building up in the background lately, so I needed to get them out for my own sanity.

# Enshittification
It feels like everything is going on a decline lately. I would have loved things to stay the way they are, but companies like to change up stuff for no reason (お金).

## Browser
Google dropped support of Manifest V2 on [July 24th, 2025](https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline). Unfortunately, uBlock Origin and other adblockers stopped working because of this. Using a browser without an adblock is insanity, so I tried 2 different things:

- Move to Firefox & use uBlock Origin there
- Move to Brave with their built in adblock

I used Firefox on my PC and Brave on my laptop. After using both for some time, I decided to move on with Firefox for personal use, but I'm still using Brave for work laptops.

Migrating my bookmarks, history, etc is a little painful since I decided to move to Firefox on my phone as well, but I deem it an investment for the future.

## OS 
My personal PC uses Windows 10, and I am hesitant to upgrade to Windows 11. I asked my friends who upgraded to Windows 11 about their experience, and they don't really have nice things to say about it. It's very worrying that they keep making Windows worse (at least in the UX side) and that people are forced to upgrade anyway. Windows 10 support has ended on [October 14th, 2025](https://support.microsoft.com/en-us/windows/windows-10-support-has-ended-on-october-14-2025-2ca8b313-1946-43d3-b55c-2b95b107f281), so sooner or later the security updates will stop.

I really want to move to Ubuntu, but some of the things I use require Windows (peripheral firmware, any games that use DirectX, or kernel level anticheat such as Valorant).

It's such a shame because I genuinely enjoy coding more using my Macbook (brew, zsh, forward slashes for path).

- Windows has chocolatey, but I don't think it's that widely adopted yet because I rarely see instructions asking for chocolatey
- Powershell's `history` does not show the old commands if your command prompt is closed.
    - Why do I have to `cat (Get-PSReadlineOption).HistorySavePath` if I want to see the history?
    - The commands I am used to (`grep`) may have some Windows equivalent (`findstr`) but I have to look it up everytime I forget
- What's with Windows using backwards slash for path? Just let it be for escape characters...
- Some stuff just don't work on windows unless you use WSL (e.g. node version manager, a.k.a `nvm`)
    - Why do I have to set up WSL and configure Docker to use it? I genuinely hate the process because the last time I tried using it, my hot reload didn't work (IT WORKS ON MY MACBOOK THOUGH?)

There may be a lot more grievances, but I must have forgotten them because I haven't coded in Windows for a long time. I only wrote my blog posts which involves writing to a markdown file.

One of the solutions a friend recommended is to dual boot, but that takes some time to set up so I might do that on the holidays (maybe christmas or new year)

## Android
There is a new system of developer verification going in effect later next year, on [September 2026](https://android-developers.googleblog.com/2025/08/elevating-android-security.html) in Indonesia and other countries, 2027 globally. 

> Starting next year, Android will require all apps to be registered by verified developers in order to be installed by users on certified Android devices. This creates crucial accountability, making it much harder for malicious actors to quickly distribute another harmful app after we take the first one down.

I understand that scammers tricking people to install malicious .apk files are bad, but this change makes it harder/impossible for people to install apps that are not verified by Google. I thought the core principle of Android is open, unlike Apple?

I concede that I use sideloading for installing Vanced because I don't want to pay for YouTube Premium (which is funny considering I paid for Discord Nitro) despite the somewhat cheap regional pricing (as of writing, IDR 69,000 / month, equivalent to around 4 US dollars). It's just that I don't want to give money to a product that keeps getting worse (constant UI changes, hiding dislikes, **AUTOMATIC AI dubs** for foreign languages) and avoids user feedback.

# Closing thoughts
Not much else to say, I hate this downwards trend of making services worse for no reason (お金). Google is trying to make me pay for YouTube Premium but I am going to resist until YouTube actually deserves my money. Windows 11 can also go piss off until they understand that users don't want to have an online account just to use the OS, or that they don't like AI features baked into the OS.
