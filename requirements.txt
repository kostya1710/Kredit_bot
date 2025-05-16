from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import ApplicationBuilder, CommandHandler, ContextTypes

# ВСТАВ СЮДИ СВІЙ ТОКЕН
TOKEN = "7498932756:AAEgEn_7apITPxdi8FPkSEnccO_2ab8xvE0"

# Партнерські посилання
credit_links = [
    ("CreditPlus", "https://rdr.fmcgsd.net/in/offer/2681?aid=110415"),
    ("Moneyveo", "https://rdr.fmcgsd.net/in/offer/1921?aid=110415"),
    ("ШвидкоГроші", "https://rdr.sdpdl.com.ua/in/offer/3349?aid=110415")
]

# Команда /start
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    keyboard = [[InlineKeyboardButton(name, url=link)] for name, link in credit_links]
    reply_markup = InlineKeyboardMarkup(keyboard)
    await update.message.reply_text(
        "Привіт! Обери сервіс, де хочеш отримати кредит онлайн:",
        reply_markup=reply_markup
    )

# Ініціалізація бота
app = ApplicationBuilder().token(TOKEN).build()
app.add_handler(CommandHandler("start", start))

print("Бот запущено...")
app.run_polling()
