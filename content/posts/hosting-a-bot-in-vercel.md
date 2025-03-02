---
title: "Hosting a Discord Bot in Vercel"
date: 2025-03-02T15:50:00+07:00 # change this, format is yyyy-mm-ddThh:mm:ssZhh:hh
tags: ["tech"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "This is most definitely not me stalling part 2 of my maisocial project"
disableShare: false
disableHLJS: false # highlight.js syntax highlighter
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "/Images/VercelDiscordBot/thumbnail.png" # image path/url
    alt: "Sample reply" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
Did you know that you could host a Discord bot in Vercel for free? I didn't knew until I googled around. If you're curious on how you could host your own bot in Vercel, follow along

# The theory
I had made bots before, but they were like servers that are always on, so that the bot has an online status. But that was a long time ago. Discord supports webhooks for their slash commands, so when a user sends a command to your Discord bot, Discord will send a POST request. Vercel supports serverless functions, so it is perfect for this use case (despite them [not recommending it](https://vercel.com/guides/can-i-deploy-discord-bots-to-vercel)).

# Setting up your bot
![](/Images/VercelDiscordBot/application.png#center)
You can create an application in Discord through their developer portal [here](https://discord.com/developers/applications). After creating your application, you will get an application ID and public key. The application ID will be used for registering/updating/deleting your commands, while the public key is for verifying if incoming requests come from Discord or not.

![](/Images/VercelDiscordBot/bot.png#center)
After that, head to the bot section and generate a token. Save it somewhere safe, because it is also used to register your slash commands.

# Registering your slash command(s)
Registering your slash command can be done by sending a POST request to `https://discord.com/api/v${versionNumber}/applications/${applicationId}/commands`.

A sample python script is provided by Discord [here](https://discord.com/developers/docs/interactions/application-commands#making-a-global-command), but you probably could just use Postman or even cURL. Just make sure to **use `Bot ${yourBotToken}` for the `Authorization` header** & follow their sample request body, the important sections are:

- `name`: the name of your slash command (please make sure it is all lowercase, I had problems related to this before)
- `type`: application command type, read [this documentation](https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-types) for more info, but usually we would use 1
- `description`: description of your slash command:
- `options`: array of parameters, which consist of:
  - `name`: name of your param
  - `description`: description of your param
  - `type`: param type, read [this documentation](https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-type) for more info
  - `required`: boolean, true if required, false if not, please make sure required params are first

Here is an example of my slash command:
![](/Images/VercelDiscordBot/sample-command.png#center)
- get-random is the root `name`
- the description is your root `description`

And here is an example of the option:
![](/Images/VercelDiscordBot/sample-option.png#center)
- min-level/max-level/song-count is the `name` of the option
- description of selected param is the `description`
- Discord will validate the type, so if the user tries to enter text on an integer option, Discord will not send it

# Creating the serverless bot
Vercel's project structure looks like this:
```
api
└─index.js/ts
```

And their serverless function is pretty straightforward, something like this:
```typescript
export default async function main(request, response) {
    // your code here
}
```

You will need to put a few things on the bot as the foundation:

## Verify if incoming requests are from Discord or not
In order to validate if a request comes from Discord or not, the [documentation here](https://discord.com/developers/docs/interactions/overview#setting-up-an-endpoint-validating-security-request-headers) requires you to:

- Make sure that `X-Signature-Ed25519` exists on the request header
- Make sure that `X-Signature-Timestamp` exists on the request header
- Validate both values & the request body & your public key

Discord provides an example using `tweetnacl`, but I prefer `discord-interactions` (this [npm package](https://www.npmjs.com/package/discord-interactions)) because it has type definitions to help make my code tidier.

The validation would look something like this:
```javascript
const signature = req.get('X-Signature-Ed25519');
const timestamp = req.get('X-Signature-Timestamp');
const isValidRequest = await verifyKey(req.rawBody, signature, timestamp, 'MY_CLIENT_PUBLIC_KEY');
if (!isValidRequest) {
    return res.status(401).end('Bad request signature');
}
```

## Respond to pings
According to this [documentation](https://discord.com/developers/docs/interactions/overview#setting-up-an-endpoint-acknowledging-ping-requests), the way Discord verifies if your endpoint works or not is by sending a PING request, so you have to respond with a PONG. It should look something like this:
```javascript
if (message.type === InteractionType.PING) {
    const pingResponse: InteractionResponse = {
        type: InteractionResponseType.PONG,
    };
    response.send(pingResponse); // Basically send a {"type": 1}
}
```

Once you have both pieces of code in your function, you are ready to develop

## Respond to slash commands
The full request send by Discord can be seen in this [documentation](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object). I will provide an example below:
```javascript
if (message.type === InteractionType.APPLICATION_COMMAND) {
    switch (message.data.name.toLowerCase()) {
        case "get-song": // change with your command name
            const title = message.data.options[0].value; // access params
            const songs = await fetch(`some-api-url?title=${title}`);

            response.status(200).send({
              type: 4, // see https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type
              data: {
                content: `This is the message`,
                embeds: songs.map((song) => ({ // embed is optional, just send content only if you want to
                  title: `This is top text of the embed`,
                  description: `This is directly below\nAnd it can be multiline`,
                  fields: song.difficulties.map((difficulty) => ({
                    name: "This will be bold",
                    value: `This is below the bold text`,
                  })),
                  image: {
                    url: "image url here",
                  },
                  url: `Hyperlink for the title of your embed`,
                })),
              },
            })
        default:
            response.status(400).end("Unknown command");
    }
}
```

## Deploy to Vercel
Nothing special here, just do these steps:
- Make sure your code is on GitHub, **PLEASE MAKE SURE YOU DON'T PUSH YOUR CREDENTIALS**
- Create a new project in Vercel
- Set up environment variables for your bot

## Make sure Discord hits your Vercel project
If you go to your Discord applications detail, there should be a `Interactions Endpoint URL` on the `General Information` section. Put your vercel project URL there but append `/api` to it. If everything is set up properly, it should be good to go.

# Conclusion
Now you too can create your own serverless Discord bot in Vercel. You can go as crazy as you want, as long as it is using Node.js (or Go or Python or Ruby if you want to still use Vercel's [runtime](https://vercel.com/docs/functions/runtimes)).

- Render can host your API for free
- Supabase has a free PostgreSQL instance
- MongoDB has its own cloud provider, called MongoDB Atlas
- Firebase can also store data, in theory it should work
- I recommend looking around this [resource](https://github.com/255kb/stack-on-a-budget) for free tier services
