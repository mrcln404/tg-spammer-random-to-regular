# tg-spammer-random-to-regular
from telethon import TelegramClient, sync, events
from time import sleep
import random

from telethon.errors import PeerFloodError
from telethon.tl.functions.messages import SendMessageRequest


api_id = xxxxxx
api_hash = 'xxxx'
phone = "+00000000"

client = TelegramClient('Spam-session', api_id, api_hash)
client.start()
client.connect()
if not client.is_user_authorized():
    client.send_code_request(phone)
    client.sign_in(phone, input('Р’РІРµРґРёС‚Рµ РїРѕР»СѓС‡РµРЅРЅС‹Р№ РєРѕРґ: '))

usernames = open('tg-usernames.txt', 'r')


def spam():
    for username in usernames:
        try:
            client(SendMessageRequest(username, random.choice(open('input-text.txt', encoding='utf8').readlines())))
            sleep(30)
