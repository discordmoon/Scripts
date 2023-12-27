import discord
from discord.ext import commands 
import asyncio
from concurrent.futures import ThreadPoolExecutor
import concurrent.futures

bot = commands.Bot(command_prefix='.', intents=discord.Intents.all(), help_command=None)

@bot.command()
async def fast(ctx):
    num_channels = 25
    
    with concurrent.futures.ThreadPoolExecutor() as executor:
        loop = asyncio.get_event_loop()
        tasks = [loop.create_task(create_channel(ctx.guild, f'fast')) for i in range(num_channels)]

        await asyncio.gather(*tasks)

async def create_channel(guild, channel_name):
    await guild.create_text_channel(channel_name)

bot.run('Token') 
