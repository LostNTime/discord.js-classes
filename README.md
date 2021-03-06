# discord.js-classes

## Installation & Setup
1. Run `npm i --save discord.js-classes`
2. Follow the example bot file in the [examples](https://github.com/memework/discord.js-classes/tree/master/examples) directory

### Client Options
- ownerID - UserID (string)
- token - Bot token (string)
- commandPath - Path to load commands from (string, i.e: path.join(__dirname, "eventpath"))
- eventPath - Path to load events from (string, i.e: path.join(__dirname, "commandpath"))
- prefix - Command prefix (string)
- selfbot - Whether the client should be a selfbot or not (boolean)

### Command Options
- name - Name of the command (string)
- usage - Command usage (string)
- group - Command group (string)
- ownerOnly - Whether the command is usable only by the owner or not (boolean)
- disabled - Whether the command is active (boolean)

### Creating Commands - Simple Ping Command
> This ping command uses async/await - Node 7+ is required!
```js
const { Command } = require("discord.js-classes");

module.exports = class Ping extends Command {
  constructor(client) {
    super(client, {
      name: "ping"
    });
  }

  async run(message, params) {
    const msg = await message.channel.send("Ping?");
    msg.edit(`Pong! \`${msg.createdTimestamp - message.createdTimestamp}\`ms`);
  }
}
```