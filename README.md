# hubs-discord-bot (Beta)

A Discord bot that interacts with [Mozilla Hubs](https://hubs.mozilla.com). Mostly bridges information (chat, media links, joins/leaves), lets you see who is currently in Hubs from Discord and sets Hubs permissions and abilities based on Discord roles. Check out the bot in action on our own [Hubs community Discord][hubs-discord]!

[Request an invitation link to add the Discord Bot to a server you own][bot-invite] by emailing hubs@mozilla.com.

* [Usage](#usage)
    * [Running the bot](#great-i-want-to-run-this-on-my-discord-server)
    * [Permissions](#permissions)
* [Hacking on it](#hacking-on-it)

## Usage

The primary function of the bot is to establish a 1:1 linkage between a Discord text channel and a Hubs room. Once rooms are linked, then the bot will do the following:

- Bridge text chat from the Discord channel into the Hubs room.
- Bridge text chat from the Hubs room into the Discord channel.
- Post links in Discord to media (images, videos, models) which are pinned in the Hubs room.
- Post in the Discord channel when someone joins or leaves the Hubs room, or if administrative stuff happens in the Hubs room.

When a Hubs room is associated with a Discord channel, users will be assigned abilities in the Hubs room based on their Discord roles. For example, Discord owners and moderators will be able to change settings on a Hubs room and be able to moderate users in the room.

### Great. I want to run this on my Discord server.

1. Request an [invite link][bot-invite] to invite the bot to your guild by emailing hubs@mozilla.com.

2. Give the bot [appropriate permissions](#permissions) on the channels you want it to run in.

3. Create a webhook named "Hubs" in the channels you want it to run in. It will use this webhook to bridge chat and
   send Hubs status updates.

4. Try out the bot! Type `!hubs` in a channel the bot is in to see some things you can do. The bot will bridge a Discord channel and a room if it sees the room URL in the topic of the channel.

### Permissions

The bot requires several permissions in order to work:

- "Send messages," "Read messages," and "Embed links" are necessary in order to bridge between the Hubs room that is linked to a channel and the messages that are sent within the channel on Discord.
- "Manage webhooks" is necessary in order for the bot to find and use a webhook for bridging chat.
- "Manage channels" is necessary in order for the bot to set the channel topic and bridge chat. **Note:** We do not ask for this permission globally when you add the bot to your server, instead we recommend you grant this permission to the bot in specific groups or channels.

You can and should assign these on a channel-by-channel basis to the bot role after adding the bot to your guild.

## Hacking on it
If you just add the bot to your Discord guild, it will run on the Hubs servers and you don't need to do anything.
But if you want to hack it, run it yourself, or point it at your own deployment of Hubs, read on. Please note that there may be some differences between a self-hosted version of the Hubs Discord bot and the one provided by Mozilla.

1. Clone this repository.

2. Install Node and `npm`. The instructions [at the NPM website][npm] should suffice.

3. Install Javascript dependencies by running `npm ci`.

4. [Create a Discord bot on the Discord website.][discord-docs]

5. Create an `.env` file with your bot's API token. If you want it to work with rooms on hubs.mozilla.com, also include `RETICULUM_HOST=hubs.mozilla.com` and `HUBS_HOSTS=hubs.mozilla.com`. You can see the different configuration bits you can override in [`.env.defaults`](./.env.defaults). You can also pass these values as environment variables when you run `npm start`.

6. Run `npm start` to start the server, connect to Discord and Reticulum, and operate indefinitely.

7. [Follow the instructions above](#usage) to set up and use the bot on your Discord guild.

[npm]: https://nodejs.org/en/
[discord-docs]: https://discordapp.com/developers/docs/intro
[hubs-discord]: https://discord.gg/wHmY4nd
[bot-invite]: mailto:hubs@mozilla.com
