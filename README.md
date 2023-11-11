import typing
import g4f
import discord
from discord.ext import commands
from discord import app_commands
import traceback
import openai

intents = discord.Intents.default()
intents.message_content = True
client = discord.Client(intents=intents)
bot = commands.Bot(command_prefix='!', description="Nothing to see here!", intents=intents)
TEST_GUILD = discord.Object(0)

@client.event
async def on_ready():
    print(f'We have logged in as {client.user}')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    elif message.content.startswith('!start'):
        await message.channel.send("Hi!")
    elif message.content.startswith('!finish'):
        await message.channel.send("Ну ок!")
    elif message.content.startswith('!secret_rol'):
        await message.channel.send('')
    if message.content.startswith('!secret_way'):
        await message.channel.send('1000-7=?')
    elif message.content.startswith('replay=-1'):
        await message.channel.send('Oshiete, oshiete yo, sono shikumi wo')
        await message.channel.send('Boku no naka ni, dare ka iru no?')
        await message.channel.send('Kowareta kowareta yo, kono sekai de')
        await message.channel.send('Kimi ga warau, nani mo miezu ni')
        await message.channel.send('Введите:1000-7-1gul')
    if message.content.startswith('1000-7-1gul'):
        await message.channel.send('Скоро вы получите секретную роль')

@bot.command()
async def mem(ctx):
    with open('images/mem1.jpg', 'rb') as f:
        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!
        picture = discord.File(f)
   # Можем передавать файл как параметр!
    await ctx.send(file=picture)


client.run
