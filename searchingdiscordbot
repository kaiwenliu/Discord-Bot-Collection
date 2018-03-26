import discord
import asyncio
from googlesearch import search

client = discord.Client()

error = '[ ERROR ] - '
warn = '[ WARN ] - '
info = '[ INFO ] - '

@client.event
async def on_ready():
    print(info + "Logged In!")
    print("Username: " + client.user.name)
    print("User ID: " + client.user.id)
    print("=====================")

@client.event
async def on_message(message):
    if message.content.lower().startswith("?ping"):
        print(info + message.content + " was executed by " + str(message.author))
        await client.send_message(message.channel, "<@%s> ping pong masterrace!!!" % message.author.id)
    if message.content.lower().startswith("?google"):
        print(info + "?ping was executed by " + str(message.author))
        searchtermlist = str(message.content).split(" ")
        try:
            resultamount = int(searchtermlist[1])
            if resultamount > 5:
                await client.send_message(message.channel, "<@%s> you can only get 5 or less results in order to prevent spam." % message.author.id)
                resultamount = 0
            searchterms = " ".join(searchtermlist[1:])
            for url in search(searchterms, num=resultamount, stop=1, pause=2):
                await client.send_message(message.channel, url)
        except ValueError:
            await client.send_message(message.channel, "you need to type **?google [amount of results] [search terms]**")


client.run("INSERT YOUR BOT ACCOUNT TOKEN HERE")
