# 👾 DeviousDiscord

[Discord.py](https://github.com/Rapptz/discord.py) Fork with experimental features and super hacky for [LuaBot](https://theluabot.squareweb.app/).

I've never worked with API wrapper code, especially not discord.py! And since I want to implement "simple" functions, I need to understand how the library works and understand every little detail :3

I made this fork because I wanted to "simplify" the discord.py library, but then I thought: "What if I put my own functionalities in the library?", and here I am.

## 💁 Some Examples

### Quick Example

```python
import discord

class MyClient(discord.Client):
    async def on_ready(self):
        print('Logged on as', self.user)

    async def on_message(self, message):
        # don't respond to ourselves
        if message.author == self.user:
            return

        if message.content == 'ping':
            await message.channel.send('pong')

intents = discord.Intents.default()
intents.message_content = True
client = MyClient(intents=intents)
client.run('token')
```

### Bot Example

```python
# I Use this in LuaBot!
import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='+', intents=intents)

@bot.command()
async def ping(ctx):
    await ctx.send('pong')

bot.run('token')
```
