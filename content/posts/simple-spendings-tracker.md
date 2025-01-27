---
title: "Creating a simple spendings tracker app using Expo.dev"
date: 2025-01-27T18:00:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "I just want a simple spendings tracker without ads, so why not make one myself?"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1628348068343-c6a848d2b6dd" # image path/url
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---

# Background
Currently my family depends on me to count the monthly spendings. Their reasoning is that so I know the cost of living. The way this works is that my mother will write out the spendings on a book everyday, and on the start of the month I will read her handwriting, add the items to a google sheet, make sure there are no items missed, and report the monthly spending of that month to my parents. After 7 years of doing it, I had enough because:

- My mother's handwriting is sometimes illegible, resulting in confusing description or wrong amount
- The number of expenses is quite a lot (150-200 per month), it took me 30 minutes to an hour of typing and reading just to finish the report

Things would be much easier if I can get my mother to use an existing spendings tracker app, but there are a few reasons why I want to make my own app:

- Mobile development learning experience
- Ad-free result
- The requirement to mark some spendings as "split"
- Don't need features such as payment method, expense category, etc
  - Any additional feature ends up as confusing user experience for my mother, she can't even order Grab/Gojek by herself

# What should I build the app with?
My mother uses an Android phone, so these are probably the options available:

## Kotlin
Ol' reliable Android Studio. Except that I have bad memories with this. Especially regarding switching between "screens" (activities).

If a certain assistant lecturer responsible for teaching mobile programming is reading this, please know that I don't blame you for me not understanding intent, context, activities, etc.

## Flutter
I actually have experience with [Flutter](https://github.com/sebastianaldi17/FlutterFoodJournal), but that was in 2021. I could relearn Flutter, but I have a soft deadline for myself (Feb 1, because I want my mother to start using it next month).

## Expo (React Native)
A coworker recommended Expo, a React Native framework for making apps quickly. I ended up choosing this approach because:

- I have experience with Typescript and React, while on Flutter I have to relearn Dart
- I can ask my coworker directly if I have any questions
- Switching screens is simple due to their Expo router, where each file is a page, and all I have to do is to call `router.push({page})`

# Choosing a datastore
Next up is picking how to store the data. These are the options that I considered:

## SQLite
I don't really need complex SQL features, so SQLite is actually viable. The problem is, the moment the app is uninstalled or the data is cleared, it will all be gone. I could mitigate this by implementing a backup feature, but that feels kind of overkill.

## PostgreSQL / MongoDB
Supabase offers free PostgreSQL hosting, and MongoDB Atlas has a free tier as well. The problem is that I would have to make a CRUD backend on top of it, and again, it feels kind of overkill.

## Firestore
I ended up choosing Firebase, because it has Firestore (document store) & I don't have to write any backend code. Firestore has a limit of 50K reads and 20K writes, but I only plan on having a user count of 1.

# Building the app
Since I don't need any fancy features like spending category and payment method, my `Spending` class looks like this:
```typescript
export class Spending {
  id: string = ""; // filled by Firebase on insert
  amount: number = 0;
  description: string = "";
  date: string = ""; // YYYY-MM-DD format
  timestamp: number = 0; // UNIX timestamp of when the spending is created
  shared: boolean = false;
}
```
The best thing about having a date format of `YYYY-MM-DD` is that the date is in lexicographic order, so you can sort it & filter spendings by month just by doing `YYYY-MM-01 <= date <= YYYY-MM-31` without worrying about `DD` being correct or not.

The user can input a spendings for a different date, but the timestamp still uses `new Date()` to maintain some sort of order when creating multiple spendings for a single day.

The fetch logic looks something like this:
1. Fetch all dates from the collection, where `date` is between `YYYY-MM-01` and `YYYY-MM-31` for a certain month (by default current month), sorted by `date` in descending order
2. Group spendings by `date` (e.g. spendings of 2025-01-25 should all be a single section)
3. Sort each section by `timestamp` in descending order

# Closing thoughts
The repo can be seen [here](https://github.com/sebastianaldi17/simple-spendings-tracker). There are a lot of things that I can implement to improve my app (e.g. infinite scroll to reduce read queries to Firebase). I might have also done some things that are not best practice. But for now, I will wait for results since she will start using it next month.

Hopefully this writeup may be helpful for someone out there reading this. See you next time!
