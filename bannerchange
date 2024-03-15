import discord, requests, aiohttp

intents = discord.Intents.default()
intents.guilds = True
intents.messages = True
intents.guild_messages = True
intents.members = True

client = discord.Client(intents=intents)

async def change_banner():
    url = 'URL_HERE' # Replace URL_HERE with the banner url you want your bot to have
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            image_data = await response.read()
            image_base64 = discord.utils._bytes_to_base64_data(image_data)
            payload = {'banner': image_base64}

            async with session.patch('https://discord.com/api/v9/users/@me', headers={'Authorization': f'Bot {TOKEN}'}, json=payload) as response:
                if response.status == 200:
                    print('**Bot banner was updated successfully!**')
                else:
                    print(f'Error updating banner image: {response.status}')

@client.event
async def on_ready():
    print('Bot is focoused')
    await change_banner()
    
TOKEN = 'TOKEN_HERE' # Replace TOKEN_HERE with your bots token
client.run(TOKEN)
