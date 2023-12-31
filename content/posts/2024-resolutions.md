---
title: "2024 Resolutions" # change this
date: 2024-01-01T00:00:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
# weight: 1
# aliases: ["/first"]
tags: ["life", "resolutions"] # change this
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Living life one year at a time" # change this
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1700700743542-0cd69d4d52b2?q=80&w=2128&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" # image path/url
    alt: "<alt text>" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

# Intro
I'll be honest, my only happy memory of 2023 that stuck with me was the fact I bought a PC in August. Let's not dwell on that and reflect on my past resolutions that can be seen in this post, or my [older post](/posts/2023-resolutions/).

## Reflection time
I had 4 resolutions, let's take a look at each one:

### Fix my GERD
People who meet me daily would know that I still have problems with this. My main problem is my lack of discipline. If I eat too much or drink while eating, I would feel bloated. Knowing that, I still keep overeating, or drinking because my brain wants to. The constant stress from my daily life also does not help, but I don't think I can do anything about this for the time being. I'll try to be more strict with myself, but these are probably meaningless words that I will ignore during 1 2024.

### Set up an exercise routine
If you consider playing maimai or Pump It Up weekly as exercise, then yes. Else, I didn't have an exercise routine.

### Finish Tae Kim's complete guide to Japanese
Did I finish it? Yes. Did I forget most of the comments inside of it? Also yes. I think this is unrealistic because he also has obscure grammar from N1 and N2, while I am striving for N3, or at least N4.

### PIU: Clear 50 S17 with break on
I did get 50 different stage clears, but the arrival of Phoenix wiped all of my scores, due to their new scoring system (1 million points max, different rank system, etc). It's ok because at least I improved compared to the beginning of the year. I still struggle with footspeed charts though, or any charts above 160 BPM.

## New resolutions time
Ok, so here are my new resolutions which are hopefully more achievable. I probably might not complete all of it though, it depends on how disciplined I am (Which I'm not)

### maimai: Achieve 15500 rating
![Rating](/Images/2024Resolutions/maimai.PNG)
So people might be confused about what is maimai, and what is their rating system. So, maimai is an arcade rhythm game by SEGA. The full list of arcades that have maimai can be seen in this [site](https://location.am-all.net/alm/location?gm=98&lang=en&ct=1007).

The way their rating system works is like this:
- maimai uses 50 charts (song-difficulty combo, for example, FFT Master, Hagakiri Expert, etc.) to calculate your rating. This is broken down into 35 old songs (oldest version until previous version), and 15 new songs (current version). The top 35 and top 15 are then summed to get your rating.
![138.PNG](/Images/2024Resolutions/138.PNG)
- The value of each chart is then calculated this way: `rank_factor * internal_difficulty * accuracy / 100`
    - `rank_factor` is the rank you got (100.5% - 101% is SSS+, 100% - 100.4999% is SSS, etc.), turned into a number (SSS+ is 22.4, SSS is 21.6, etc.). The value of each rank factor can be seen [here](https://github.com/sebastianaldi17/maifavorite/blob/d6bacf25dc2555fe814d7196784837f8eb5f7208/supabase-frontend/src/components/ChartModal.vue#L53).
    - `internal_difficulty` is the internal constant value of the chart. SEGA hides this from the general public, but people have calculated the internal difficulty based on research by [@maiLv_Chihooooo on Twitter (yes I am still calling it Twitter, Elon can cry if he wants)](https://twitter.com/maiLv_Chihooooo).
    - `accuracy` is your accuracy (max 101%, not 100%). That is your score after playing said chart.
    - Let's take the above example: MAGENTA POTION has an `internal_difficulty` of 13.8, and my accuracy is `100.6171%`, which results in a rank of SSS+ (`rank_factor` will be 22.4). 13.8 times 100.6171 times 22.4 divided by 100 is `311.02758`, rounded down to `311`. Not sure why [MaiChart](https://maichart-en.nuko.cat/) shows it as 310, it could be an error on my calculations, it could be an error on their calculations. The values we show are NOT officially from SEGA, it is researched but not confirmed 100%.
    - I created a rating calculator for each chart, you can find it on my [GitHub page](https://sebastianaldi17.github.io/).
![current rating](/Images/2024Resolutions/maimairating.png)
My current rating as of writing is 15258. To get a rating of 15500, I would need 15500 / 50 = 310 rating for ALL charts. It is still pretty far off, and I would need to go to a different arcade to get a good score (the arcade nearest to my location has crappy sensors). But I am pretty confident I can reach 15500 before the end of next year. Or at least I hope...

### PIU: Get Intermediate Lv.9
![pump](/Images/2024Resolutions/pumpitup.PNG)
Currently, I have Intermediate Lv.8, which is from playing many level 17 songs. I need to play level 18 songs, which I only have a few clear: ENERGY SYNERGY MATRIX S18, After Like S18, Amor Fati S18, MURDOCH S18 (this one is very lucky), and iRELLiA S18 (this was lucky and surprising, considering it is 204 BPM). I still need 15 more clears (possibly less if I get a good score, but this is unlikely), which means about 1-2 level 18 songs clear per month. Wish me luck!

To calculate how to achieve a certain title, someone made a calculator [here](https://docs.google.com/spreadsheets/d/1O3xmKyy3kZlB87YcUIQvnQkA0FMCfhCoPXz2V-o7Lwk/edit#gid=0), just duplicate it and replace the numbers on the sheet with the number of actual clears you got.

### Get JLPT N4 certification
![JLPT](https://upload.wikimedia.org/wikipedia/commons/e/e3/Japanese-Language_Proficiency_Test_logo.jpg)
It might be surprising to people that I decided to skip N5, but N5 basically means that you are a weeb who barely speaks Japanese. Just kidding. Jokes aside, N5 and N4 is not really useful. Employers are going to look for people with N2 or N1 certification. Knowing this, why do I want to get N4 anyway?

- The JLPT test is conducted once or twice per year. More research on my side is required, but I don't really want to clear N5 and then waste another 6 months - 1 year for N4.
- The amount of knowledge I currently have is not enough to clear anything higher than N4. I'm not even sure if I can clear N4, which is why striving for N4 is somewhat a safe bet, at least safer than N3, and more useful than N5.

### Learn Spring Boot
![code](https://images.unsplash.com/photo-1555952494-efd681c7e3f9?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
I wanted to learn this since last year, but I kept postponing it due to IRL stuff & just being lazy. I do programming for a living, so I didn't really wanted to code during my free time. This resolution is to give some pressure to myself, so that I can start learning and hopefully make a project using it.

I also wanted to learn other stuff, but I think this is a good place to start since this framework is quite used worldwide.

# Epilogue
I think that's about it. The beginning of 2024 will be very spicy, starting off with a septoplasty on the 9th of January. There is also going to be an election, because it has been 5 years since the last one. Lastly, there is quite a high chance of me changing jobs, whether I like it or not. We will see.

Thank you for reading this far. Let's face 2024 with a fresh start.