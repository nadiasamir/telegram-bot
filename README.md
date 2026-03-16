import os
from telegram import Update
from telegram.ext import Application, CommandHandler, MessageHandler, filters, ContextTypes

BOT_TOKEN = os.getenv("BOT_TOKEN")

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "🛡️ SpyTV APK Download Bot\n\n"
        "Send any link and get safe APK files directly!\n"
        "ربات دانلود SpyTV 🔐 | ساده و سریع\n\n"
        "لنک بھیجیں، APK فوراً مل جائے گا!"
    )

async def handle_message(update: Update, context: ContextTypes.DEFAULT_TYPE):
    link = update.message.text
    await update.message.reply_text(
        f"🔍 Link مل گیا: {link}\n"
        "⏳ APK تیار ہو رہا ہے...\n"
        "ربات دانلود SpyTV | در حال دانلود"
    )

def main():
    app = Application.builder().token(BOT_TOKEN).build()
    
    app.add_handler(CommandHandler("start", start))
    app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, handle_message))
    
    print("🤖 Bot شروع ہو گیا!")
    app.run_polling()

if __name__ == "__main__":
    main()
    
