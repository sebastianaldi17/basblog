---
title: "Creating another personal site and buying a domain"
date: 2025-01-25T12:00:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Creating yet another personal site, but I bought a domain to be more professional."
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "/Images/PortfolioSiteAndDomain/personal-site.png" # image path/url
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Background
In an effort to become more professional, I decided that I want to have a personal portfolio site, and buy a domain that uses my name. I also want to relearn React and Tailwind, so this is a good opportunity for me.

# Creating a portfolio site
Since my portfolio site has no interactive experience, a static site is my end goal. Since the static site is going to be built into HTML by Vite, I could have just made a vanilla site, purely using HTML and CSS. In the end I still chose to use React and Tailwind for learning purposes.

The process is relatively simple, I ran `npm create vite@latest` to generate boilerplate react + typescript code, installed tailwind according to [their instructions](https://tailwindcss.com/docs/installation/using-vite), and started coding.

# Hosting the site
![netlify](/Images/PortfolioSiteAndDomain/netlify.png)
Since this blog is already using Netlify, might as well use my existing netlify account for hosting my portfolio site.

Fun fact, my blog site is considered a single site, so a site with multiple pages is still just a single site. Good to know, especially since their free plan is good enough for me (500 sites, 100 GB monthly bandwidth, 300 build minutes).

Why didn't I use vercel? I forgot the reason why I decided to host my blog using netlify, and I don't feel the need to create a new account on a separate service.

# Picking a domain registrar
Up next is picking from which vendor do I want to buy my domain. There are a few choices that I considered:

## Local registrars (niagahoster, domainesia)
I thought that they might be cheaper due to regional pricing, but that is not the case. Registering a new domain costs ~$7-$8.5, but the renewal costs ~$12. They also didn't offer WHOIS privacy protection, which is something to consider.

## Namecheap
Registering costs $6.49, but renewal costs $16.98. My friend uses this because they wanted to use a .dev domain, but after a lot of thought I decided I wanted a .com domain, and namecheap is not very cheap.

## Porkbun
Many people online recommended porkbun, to the point that I suspected it could have been astroturfed. Registering and renewal costs $11.06, so I tried to make an account. After inputting my details, they wanted to take a picture of my government ID, which made me hesitate, and ended up going with another domain registrar.

## Cloudflare
Cloudflare is actually the cheapest of the bunch, coming in at $10.44 for registering and renewal. The few reasons people don't like to use Cloudflare is that Cloudflare does not allow you to change the name servers used.

# Setting up custom domain & subdomains in Netlify
![netlify-custom](/Images/PortfolioSiteAndDomain/netlify-custom-domain.png)
Setting up custom domain and subdomains is quite simple in Netlify. Go to your site's overview -> Domain management, and then press "Add domain alias".

![cloudflare](/Images/PortfolioSiteAndDomain/cloudflare.png)
Then, add a CNAME record that points to the netlify link that contains the site.

# Closing thoughts
I hope my experience with Netlify and Cloudflare domains may be of help to someone reading this article. Since I'm already paying for my custom domain, I want to start making projects that use my domain. Cheers!
