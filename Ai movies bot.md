from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

# Replace 'YOUR_BOT_TOKEN' with the actual token obtained from BotFather
TOKEN = 'df405dd77304e8a46bb2a970f49d9668a3124e8c'

def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text('Hello! I am your echo bot. Send me a message, and I will echo it back.')

def echo(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(update.message.text)

def main() -> None:
    updater = Updater(TOKEN)

    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(MessageHandler(Filters.text & ~Filters.command, echo))

    updater.start_polling()

    updater.idle()

if __name__ == '__main__':
    main()
