---
title: "Hosting A Starbound Server"
date: 2022-04-30T21:00:00+07:00
tags: ["tech"]
showToc: false
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Dealing with a server with memory leaks"
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://hb.imgix.net/706c69fa24708ff0343da6845955d01a5f5632d3.jpeg?auto=compress,format&fit=crop&h=353&w=616&s=570be69ff14c80292c8ee96e00933e57" # image path/url
    alt: "Starbound" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Multiplayer
So me and a couple of my friends wanted to play Starbound together. Hosting a server using your own machine or simply joining via steam is a viable option, but none of our connections were stable enough. If I hosted, sometimes packet loss would cause **everyone** to disconnect from the server (including myself, even though I was hosting the server). With that in mind, we decided to find a dedicated VPS to run the starbound server. We eventually setteled for [ID Cloud Host](https://idcloudhost.com/) because it is hosted in our country (Indonesia).

# Setting up the server
We used a prepaid method because none of us were comfortable on putting our debit/credit card details. After topping up some credit, I was tasked to set up and manage the server. For the server, I went with Ubuntu 20.04 LTS, 1 vCore, 4GB RAM and 20GB storage. For the most part, setting up the starbound server is pretty straightforward, just follow [this guide](https://starbounder.org/Guide:LinuxServerSetup). The TL;DR is logging in to SteamCMD and download the Starbound files for Linux (my main machine is Windows, so it does not have the game files for it. If you use a linux machine, maybe you could FTP the game files directly into the VPS). After all that is done, run `./starbound_server` on the linux folder to generate the storage folder (containing the config files and saves).

# FTP
SteamCMD would try to download the workshop files (mods for Starbound), but I think it is easier for me to just FTP the mod files. If there is anyone interested on how to FTP to ID Cloud Host, [here](https://idcloudhost.com/panduan/cara-upload-file-vps-melalui-filezilla/) is the guide I used, but I used WinSCP instead of Filezilla. The mod files are on your local machine are at `/steamapps/workshop/content/211820`. There should be a bunch of folders that are just numbers, and inside them should be a single `contents.pak` file. Rename all the `contents.pak` files to whatever you want and then move all of them to the mods folder in the server. If the mods you are planning on using include custom world types, delete the universe file that was generated.

# Configuring the server
The config file for the server should be located at the storage folder. The config file should be named `starbound_server.config`. Since we are planning on running mods, the server and the clients should both allow asset mismatch (just in case). For the client side, it can be enabled on the options menu. For the server, edit the `allowAssetsMismatch` property to true.

If you are paranoid just like me, you would be afraid of random strangers breaking into your server. For that, you would want a password for entering the server. For that, change `allowAnonymousConnections` to false, and then add a single object to the `serverUsers` property. The syntax can be found in this [article](https://playstarbound.com/february-17-server-configuration-changes/).

# Problems arise
You would assume that you could just run the server and leave it be. While this is true, Starbound is a bit... unique. Observe this screenshot below:
![Killed by OOM Killer](/Images/StarboundHosting/oom.png#center)
From the screenshot above, there are some things that can be noticed:
- The server is killed by [Out of Memory Killer](https://www.digitalocean.com/community/questions/getting-regular-out-of-memory-kill-process-how-to-resolve-this-isse). 
- There is no swap memory.
- The memory usage is 5 Gigs of RAM.

Apparently, the VPS does not have any dedicated swap memory (I guess this is for clients to decide how much storage they want to allocate as swap). To allocate some of my storage as swap, I followed [this guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04).

For the other issue (being killed by the Out of Memory Killer), I changed the memory overcommit to `2` instead of `0`. The method and explanation can be seen [here](https://serverfault.com/a/142003). I didn't disable the Out of Memory Killer because I was afraid of breaking something.

For the last issue (the memory usage of the server), I can't exactly do anything about it. From what I've read, Starbound dedicated server has a memory leak issue, and I haven't seen any signs of it being fixed. The only real solution is just to allocate more RAM, or occasionally restart the server.

After changing the memory overcommit setting and allocating the swap file, the server no longer dies after 5 minutes, progress! Instead, the server would die if there are too many worlds being explored at the same time! Here are some screenshots.

![Segfault](/Images/StarboundHosting/segfault.jpg#center)
![malloc](/Images/StarboundHosting/coredump.png#center)

# What have we learned
- How to set up a Starbound server
- Starbound is an abandoned game, no more updates since June 2019 (last patch note in blog)
- Starbound has a memory leak for dedicated servers
- Swap memory is not allocated on creating a VPS instance of Ubuntu

Just stay away from this game, the devs do not care, why should I?