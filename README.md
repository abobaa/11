#API Token
API_TOKEN = ‘1130048599:AAFoH93Gccxp9Y_1tQTAXEn-2tr9mn8oWQU’ 

#Admin ID
admin_id = 155752773

# Import library
from main import bot, dp
from aiogram import types
from aiogram.types import Message

# Send message to admin
async def send_to_admin(dp):
        await bot.send_message(chat_id=admin_id, text="Bot start")
# Start bot using func
@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
	text = f'''Привет! {message.from_user.full_name}
Получается это бот 🤖 
🙌 Для работы бота в группе необходимо дать ему права администратора и включить все разрешения .'''
await message.answer(text=text)


import asyncio
from aiogram import Bot, Dispatcher, executor
from config import API_TOKEN

loop = asyncio.get_event_loop()
bot = Bot(API_TOKEN, parse_mode="HTML")
dp = Dispatcher(bot, loop=loop)

if __name__ == "__main__":
    from handlers import dp, send_to_admin
    executor.start_polling(dp, on_startup=send_to_admin)
