# News Aggregator (MVP)

Простой MVP: агрегатор RSS → суммаризация → публикация в Telegram. Разворачивается на VPS.

Структура:
- fetcher.py
- db.py
- summarizer.py
- publisher.py
- cron_runner.py
- utils.py
- config.json.example
- requirements.txt
- deploy/setup.sh
- deploy/systemd/news-aggregator.service
- LICENSE, .gitignore, README.md

Быстрый старт:
1. Клонируйте репо:
   git clone https://github.com/lli2412/news-aggregator.git
2. На VPS:
   sudo apt update && sudo apt install -y python3-venv python3-pip git
   cd news-aggregator
   ./deploy/setup.sh
3. Скопируйте config.json.example → config.json и отредактируйте (TG_BOT_TOKEN, CHAT_ID, RSS фиды).
4. Запустите тестовый прогон:
   source .venv/bin/activate
   python3 cron_runner.py
5. (Опционально) Установите systemd unit:
   sudo cp deploy/systemd/news-aggregator.service /etc/systemd/system/
   sudo systemctl daemon-reload
   sudo systemctl enable --now news-aggregator

Получение Telegram токена:
- @BotFather → /newbot → сохраните BOT_TOKEN. CHAT_ID можно получить через @userinfobot или отправив сообщение боту и проверив recent updates.

Лицензия: MIT
