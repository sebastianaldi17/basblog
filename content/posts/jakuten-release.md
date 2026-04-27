---
title: "Jakuten release"
date: 2026-04-27T20:00:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "And for a bonus no one asked for, my thoughts about AI, 2026 edition"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "Images/Jakuten/landingpage.png" # image path/url
    alt: "Landing page" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

# Background
I actually have a Japanese cheatsheet that contains my weak points spread between notion and google sheets, but they're not really :sparkles:**a e s t h e t i c**:sparkles: compared to a static site that is responsive and has furigana, you know?

So in my weekend's to do list, one of it was to turn my cheatsheet into a static site that anyone can see, hopefully it will be helpful for you guys as well

Except that I suck at frontend now since I never coded frontend stuff ever since I moved jobs :laughing:

I ended up using AI for the frontend stuff, as well as generating example sentences for each point. No money to Anthropic though (site fully generated using chat, so no subscription at all), just my cheatsheet data (that I made public here anyways with the release of this site) :thumbsup:

THe site can be accessed [here](https://jakuten.sebastianaldi.com/).

# Thoughts on AI, 2026 edition
![](https://media1.tenor.com/m/-VOaW6RJJwMAAAAd/kamen-rider-wizard-washing-machine.gif#center)

Back in [2025](/posts/maisocial-part-4) I said this:

> Another problem with using AI is that it might need multiple prompts to finish something, and if the AI decides to go off the rails, the good parts become unsalvageable as well.

My experience one year ago was very negative, but that was when I used ChatGPT 4 I think? It is scary how good these models become.

I also said this:

> I think being dependant on AI to do my job is scary, because then I would not need to think in order to accomplish my job. I feel like if I stop thinking, my brain would atrophy and I would end up being a bad programmer.

Fast forward to today and now my job relies on a Claude subscription to meet what was once considered unrealistic deadlines.

There is still a nagging fear on the back of my mind regarding bugs that I couldn't catch due to not coding myself (it's not like my pre-AI code is bug free), so I just hope my personal local testing & the test engineer's end to end testing can catch any issues before the go up in production :sweat_smile:

I do feel myself getting lazier though, because I feel like reading 200 pages of documentation (not sure if this one vendor is inflating it too much, or there are just that many endpoints) is a massive time sink, while if I feed it to the AI and ask for relevant sections, it can easily bring up things that I ask for.

For my unbiased thoughts on AI regardless of my current job & my mindset, what people call AI are actually LLMs (Large Language Models) right? **Since they train based on existing data, I feel like it is a "better" version of search engines**. Many problems are already "solved" to the point that questions asked in forums such as Stack Overflow or Reddit are most likely duplicates of things that are already asked previously.

**It feels like the future of Software Engineering jobs is to translate requirements from the product team to an actionable system design (endpoints, cronjobs, message queues, etc) that the AI implements**. Corporate coding is repetitive as hell (make an endpoint, and if your codebase uses DDD / clean architecture, it's always the same "make a controller, make a service, make a repository if needed") so this change is somewhat welcome for me.

Some places might even remove product managers & have engineers become product managers as well, calling them "product engineers". It's scary how the amount of responsibilities will keep growing. Or maybe my place is just understaffed, who knows.

**I definitely fear for the time when everyone gets too comfortable with AI, then AI companies could raise the price to whatever they want** & people will have to pay them since the coding skills have atrophied. Hopefully before then local models could be strong enough to meet my needs.

**I also fear that if everyone becomes too reliant on AI, there could come a time where an unsolved problem does pop up**, and no one could innovate enough to solve that issue due to not thinking much (or not wanting to think too much). If everyone relies on AI for everything, then newer problems that the AI can't solve will remain unsolved since no one can think of a creative approach. 

After all, newer algorithms are discovered because people don't stick to existing solutions, right?

# TLDR
Sorry I rambled a bit too much, honestly there has been a lot in my mind. In short, here are my main points:

1. LLMs are trained based on existing data
2. Currently most problems are just old problems in different flavors
3. But if everyone relies on AI, then there will be no more new "data" for the AI to train on
4. No more innovation, so if there is a problem never seen before, AI can't do it, people will think it's impossible

Not sure if I got my point across, but I don't want to use AI to write my blog posts. It would feel inhuman.
