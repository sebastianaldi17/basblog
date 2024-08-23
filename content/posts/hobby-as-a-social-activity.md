---
title: "HaaSA: Hobby as a Social Activity"
date: 2022-07-02T20:30:00+07:00
tags: ["life", "keyboard", "tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "A two part story, that consists of a failed mechanical keyboard mod and a laptop cleaning"
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1527097779402-4a4b213307fc?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1196&q=80" # image path/url
    alt: "internals" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Preface
It was my birthday yesterday! But it was a workday, so I couldn't hung out with my friends. Instead I met up with my friends today. The agenda was simple:
- Attempt tempest tape mod on an one year old [Rexus Legionnaire MX9](https://tokopedia.link/r28IQQ9Tkrb) that I had laying around.
- Open up my laptop to do some deep cleaning
- Have dinner (this part is not interesting so I won't say anything about this)

# Part 1: Tempest tape mod epic failure
For those who are not in the know about what tempest tape mod is, it is applying masking / non sticky tape to the back part of your keyboard's PCB to dampen the sound. I wanted to try this on my main board, but I am a bit afraid of breaking my (pretty expensive) board...
![Poor lad](/Images/HaaSA/MomentBeforeDisaster.jpg#center)
I had an old keyboard laying around that has removable outemu switches, but they are not compatible with gateron switches. Since the switches are removable, it means I can get to the PCB without desoldering. Sadly I didn't document the keyboard teardown, but it was very stressful due to the sole fact that ***it is really hard to remove the switches from the socket***. I don't know if this is because it's my first time removing the switch from the keyboard (not loose at all), or simply because the keyboard was cheap, therefore making it hard to remove the switches. With some force, I managed to remove all of the switches (not without breaking some parts of the clear plastic, rest in peace 2 outemu reds :pray:). After loosening 13 screws on the board, I finally got to the PCB. All that is left is to apply the masking tape to the back of the PCB and reassemble the keyboard. Except I was really stupid and didn't make holes in the parts where I needed to make a hole, which are the screw holes of the keyboard (if I could take a picture I would, but I really don't want to remove ~80 switches again just to take a picture of the case). While making holes for where the screw holes should go, I might have bent the PCB too hard. Why did I say that? Because after reassembling, some keys are messed up. It is not a case of bent pins, because:
- When the f3 column (f3, 3, e, d, c) is pressed, ***all keys on the same rows are pressed simultaneously***, This happened on the f10 row, and the left arrow row as well.
- The columns with the broken functionality has a white light, instead of rainbow (following the lighting scheme of the rest).

![me say alone ramp](https://c.tenor.com/pPagLcCVYwIAAAAd/keyboard-computer.gif#center)

Welp. Goodbye board, it was nice knowing you. What I learned from this story is that:
- Make holes for the screwdriver holes (standoff?), because the PCB might have holes in certain places for that exact reason, and applying the tape will cause the board to not fit properly
- Why even bother with sound if I use head/earphones when playing games anyawy? I won't even hear my keyboard if I listen to music while typing this blog post
- Cheap keyboards with removable outemu switches are moddable, but very hard to remove, especially for the first time. No such hassle on the Rover84.

# Part 2: Laptop deep cleaning
I only brought one switch puller, so my friends couldn't help with the disassembly of the keyboard. Instead, they opened up my laptop because I was too much of a pussy to do it myself (also, they are more experienced in disassembling electronics that aren't mechanical keyboards). My laptop was four years old, and it started to have pretty high thermals, which may (or may not) cause BSOD `whea_uncorrectable_error` on Windows 10. I suspected thermals because `HWMonitor` reported this (on idle):
![preclean](/Images/HaaSA/BeforeCleaning.png#center)
Almost 60 degrees celcius on idle is pretty scary, so I had my friends open up the laptop. The fans were relatively clean, but inside the heatsink is a pretty massive dust / lint speck covering the heatsink. After removing said speck, the thermals seem to be pretty OK (on idle but with wallpaper engine and discord running in the background):
![afterclean](/Images/HaaSA/AfterCleaning.PNG#center)
Kind of high, but this is weird because `CoreTemp` said my temperatures are below 50. My point is, open up your laptop for cleaning, especially if you haven't opened it up for years. In my case the thermal paste is still kind of viscous (not dry), so it didn't needed replacing. However, the heatsink needed cleaning, and after cleaning it went pretty smoothly. I will update you guys if it does bluescreen again though.

## Special thanks to
- https://www.instagram.com/robertoevans26/
- https://www.instagram.com/albert_ahi/