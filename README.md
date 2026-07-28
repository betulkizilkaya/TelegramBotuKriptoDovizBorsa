# Telegram Crypto, Forex and Stock Market Bot

This project is a Python-based Telegram bot that provides cryptocurrency, foreign exchange, and market-related information through simple Telegram commands.

The bot can retrieve current prices, display price charts, fetch financial news, perform currency and cryptocurrency conversions, and create target-price alerts.

## Features

- Retrieve cryptocurrency prices through Binance
- Retrieve foreign exchange data through Yahoo Finance
- Display historical price charts
- Fetch Turkish financial news by keyword
- Convert currencies and cryptocurrencies
- Create user-specific target-price alerts
- List supported symbols
- Support private chats and group mentions
- Register Telegram bot commands automatically
- Perform basic news sentiment analysis
- Log application activity and errors

## Available Commands

| Command | Description | Example |
|---|---|---|
| `/start` | Starts the bot | `/start` |
| `/help` | Displays the command list | `/help` |
| `/stock` | Retrieves a cryptocurrency or exchange-rate price | `/stock BTCUSDT` |
| `/news` | Retrieves market news for a keyword | `/news Bitcoin` |
| `/symbols` | Lists supported symbols | `/symbols` |
| `/set_alert` | Creates a target-price alert | `/set_alert BTCUSDT 50000` |
| `/plot_stock` | Sends a historical price chart | `/plot_stock BTCUSDT` |
| `/convert_currency` | Converts a currency or cryptocurrency amount | `/convert_currency 40 USDTRY` |

## Technologies and Services

- Python 3
- `python-telegram-bot`
- Binance API
- Yahoo Finance through `yfinance`
- NewsAPI
- `matplotlib`
- NumPy
- Requests
- Python Dotenv
- TextBlob
- VADER Sentiment

## Current Project Structure

```text
TelegramBotuKriptoDovizBorsa/
├── .venv/
│   └── Scripts/
│       └── TelegramBotu.py   # Main Telegram bot application
├── .env                      # Environment variables
├── .gitignore
└── .idea/                    # IDE configuration files
```

> The main source file is currently stored inside `.venv/Scripts/`. For a cleaner project structure, move it to the repository root or a dedicated `src/` directory and avoid committing virtual-environment files.

A recommended structure is:

```text
TelegramBotuKriptoDovizBorsa/
├── src/
│   └── telegram_bot.py
├── .env.example
├── .gitignore
├── requirements.txt
├── README.md
└── LICENSE
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/betulkizilkaya/TelegramBotuKriptoDovizBorsa.git
cd TelegramBotuKriptoDovizBorsa
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install the dependencies

```bash
pip install python-telegram-bot python-dotenv python-binance yfinance requests matplotlib numpy textblob vaderSentiment
```

## Environment Variables

Create a `.env` file in the project root:

```env
TOKEN=your_telegram_bot_token
API_KEY=your_newsapi_key
BINANCE_API_KEY=your_binance_api_key
BOT_USERNAME=@your_bot_username
```

The current source code reads the following values:

- `TOKEN`: Telegram bot token
- `API_KEY`: NewsAPI key
- `BINANCE_API_KEY`: Binance API key

Update `BOT_USERNAME` in the source code if the bot will also respond to mentions in Telegram groups.

## Running the Bot

Run the main Python file:

```bash
python .venv/Scripts/TelegramBotu.py
```

After moving the source file to a cleaner location, the command could instead be:

```bash
python src/telegram_bot.py
```

## How It Works

The application uses `python-telegram-bot` to register asynchronous command handlers.

- Cryptocurrency prices are retrieved through the Binance client.
- Foreign exchange prices and historical data are retrieved through Yahoo Finance.
- Market news is requested from NewsAPI and filtered by relevant Turkish financial keywords.
- Matplotlib is used to generate charts that are sent to Telegram users.
- Price alerts are stored temporarily in memory and checked by a scheduled background job.

## Important Security Notice

Never commit real API keys or Telegram bot tokens to a public repository.

This repository currently contains a tracked `.env` file. Any real credentials that were previously stored there should be considered exposed and must be revoked or regenerated from the relevant service dashboards.

Recommended actions:

1. Regenerate the Telegram bot token through BotFather.
2. Regenerate the NewsAPI key.
3. Regenerate the Binance API key.
4. Remove `.env` from Git tracking.
5. Keep `.env` listed in `.gitignore`.
6. Add a placeholder-only `.env.example` file instead.

To remove the tracked `.env` file while keeping it locally:

```bash
git rm --cached .env
git commit -m "Stop tracking environment variables"
git push
```

Also avoid committing the `.venv/` directory because it may contain machine-specific files and unnecessary dependencies.

## Limitations

- Price alerts are stored only in memory and are lost when the bot restarts.
- API availability and rate limits may affect responses.
- Financial data may be delayed or unavailable for some symbols.
- The project is educational and should not be treated as financial advice.

## Possible Improvements

- Store alerts in SQLite or PostgreSQL
- Add multiple alerts per user
- Add Docker support
- Add automated tests
- Create a `requirements.txt` file
- Move the source code outside `.venv`
- Add structured configuration validation
- Improve symbol normalization between Binance and Yahoo Finance
- Add deployment instructions for a cloud server

## Disclaimer

This project is intended for educational purposes only. The information provided by the bot does not constitute financial or investment advice.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

© 2025 [Betül Kızılkaya](https://github.com/betulkizilkaya)
