# NothingBot
#Discord Bot

import discord
from discord.ext import commands 
import logging
import calendar


import asyncio

from discord import permissions
from discord.colour import Color
from discord.ext import commands, tasks
from discord.utils import get
from discord import Activity, ActivityType







intents = discord.Intents().all()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.listen
async def on_message(message):
    if message.author == bot.user:
        return

        
@bot.command()
async def ping(ctx):
    await ctx.channel.send('Ping is 40ms')
    
    
@bot.command()
async def latency(ctx):
    #show latency in an embed
    await ctx.send(embed=discord.Embed(title="Latency", description=f"{round(bot.latency * 1000)}ms", color=Color.blue()))


@bot.command()
async def hello(ctx):
    await ctx.send(f'Hello! {ctx.author.mention}')
    

@bot.command()
async def clear(ctx, amount=0):
    await ctx.channel.purge(limit=amount)
    await ctx.send(f'Cleared {amount}  messages')
    

@bot.command()
async def who_are_you(ctx):
    await ctx.send(f'I am NothingBot! How can I help you today?')
    
    
@bot.command()
async def Which_day_it_is(ctx):
    await ctx.send(f'Today is {calendar.day_name[calendar.weekday(year=0000, month=0, day=0)]}')
    

    


@bot.command()
async def dog(ctx):
    await ctx.send("https://images.unsplash.com/photo-1552053831-71594a27632d?q=80&w=1924&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D")
    


handler = logging.FileHandler(filename='discord.log', encoding='utf-8', mode='w')
bot.run('MTI1MDY5MzI4OTYxOTc1NTAwOA\.G9SZxH\.fFDnmvD3NfewAeUUi5zgydyCagdet2lawn3vGg', log_handler=handler)
