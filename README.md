# 🎮 Telegram Mini Games

Современное Telegram мини-приложение с мультиплеерными играми и новостным агрегатором.

## � Структура проекта

```
📦 T-MiniGames/
├── 📱 client/telegram-mini-games/     # React фронтенд
│   ├── src/
│   │   ├── components/               # UI компоненты
│   │   │   ├── LiveGameSelection.tsx # Выбор онлайн игр
│   │   │   ├── GameLobbyEnhanced.tsx # Игровое лобби
│   │   │   └── NewsAggregator.tsx    # Агрегатор новостей
│   │   ├── games/                   # Игровые компоненты
│   │   │   ├── dice/DiceGame.tsx    # Игра в кубики
│   │   │   ├── cards/CardsGame.tsx  # Карты 21
│   │   │   └── rps/RockPaperScissors.tsx # Камень-ножницы-бумага
│   │   ├── services/                # API сервисы
│   │   │   ├── gameAPI.ts          # REST API для игр
│   │   │   ├── gameWebSocket.ts    # WebSocket подключение
│   │   │   └── telegramService.ts  # Telegram WebApp API
│   │   ├── App.tsx                 # Главный компонент
│   │   ├── main.tsx               # Точка входа
│   │   └── index.css              # Стили (Tailwind)
│   ├── package.json               # Зависимости Node.js
│   └── vite.config.ts            # Конфигурация сборки
├── 🖥️ server/                      # Python бэкенд
│   ├── games/
│   │   └── dice_game.py          # Логика игры в кубики
│   ├── main.py                   # FastAPI сервер
│   ├── models.py                 # Модели данных
│   ├── room_manager.py           # Управление игровыми комнатами
│   └── telegram_news_service.py  # Сервис новостей
├── 🤖 telegram_bot/              # Telegram бот (опционально)
│   ├── bot.py                    # Логика бота
│   └── requirements.txt          # Зависимости бота
├── ⚙️ Конфигурация деплоя
│   ├── requirements.txt          # Python зависимости
│   ├── runtime.txt              # Версия Python
│   ├── Procfile                 # Команда запуска для Render
│   └── vercel.json              # Конфигурация для Vercel
└── 📖 README.md                  # Документация
```

## �🚀 Быстрый деплой

### 🟦 Backend на Render.com
1. Подключите репозиторий к Render
2. **Build Command:** `pip install -r requirements.txt`
3. **Start Command:** `cd server && uvicorn main:app --host 0.0.0.0 --port $PORT`
4. **Python Version:** 3.12.7

### 🟩 Frontend на Vercel.com
1. Подключите репозиторий к Vercel
2. **Root Directory:** `client/telegram-mini-games`
3. **Build Command:** `npm run build`
4. **Output Directory:** `dist`

## 🎯 Возможности

### 🎲 Игры
- **Кубики** - Бросайте кубики и набирайте очки
- **Карты 21** - Наберите 21 очко не превышая лимит  
- **Камень-Ножницы-Бумага** - Классическая игра

### 📰 Новости
- Агрегация из 16+ Telegram каналов
- Категории: Подарки, Криптовалюта, NFT, Технологии
- Обновление каждые 30 минут

### 🔗 Live игры
- Мультиплеер через WebSocket
- Создание и присоединение к комнатам
- Реальное время

## 🛠️ Техническое описание

### Backend
- **FastAPI** - современный Python web framework
- **WebSocket** - для real-time игр
- **aiohttp** - для асинхронных HTTP запросов
- **feedparser** - для RSS новостей

### Frontend  
- **React 19** + **TypeScript** - современный UI
- **Framer Motion** - плавные анимации
- **Tailwind CSS** - стильный дизайн
- **Vite** - быстрая сборка

## 📱 Настройка Telegram Bot

1. Создайте бота через @BotFather
2. Создайте Mini App командой `/newapp`
3. Укажите URL вашего деплоя на Vercel
4. Готово! Бот доступен в Telegram

## 🔧 Локальная разработка

```bash
# Backend
cd server
pip install -r ../requirements.txt
python main.py

# Frontend
cd client/telegram-mini-games
npm install
npm run dev
```

## ✨ Что удалено (беспорядок убран!)

❌ **Дублирующиеся файлы:**
- `App_new.tsx` → оставлен `App.tsx`
- `styles.css`, `App.css` → оставлен `index.css`
- `GameCard.tsx`, `GameSelection.tsx` → ненужные компоненты
- `main_new.py` → оставлен `main.py`
- `test.html`, лишние конфиги

✅ **Чистая структура:**
- Один файл на компонент
- Логичная организация папок
- Минимум конфигурационных файлов
- Понятная документация

## 🎉 Готово к деплою!

Теперь проект организован правильно и готов к мгновенному деплою на Render + Vercel без лишних файлов!

### 📰 Новостной агрегатор
- **RSS источники**: Агрегация из проверенных новостных лент
- **Категории**: Технологии, Спорт, Политика, Развлечения, Наука
- **Фильтрация**: Сортировка новостей по категориям и времени
- **Обновление**: Ручное и автоматическое обновление ленты

### � Мини-игры

#### 1. 🎲 Кубики (Dice Game)
- **Игроки**: 2-4 человека
- **Механика**: Одновременный бросок 2 кубиков
- **Правила**: Побеждает игрок с максимальной суммой
- **Ставка**: Фиксированная 100 очков

#### 2. 🃏 Карты 21 (Blackjack)
- **Игроки**: 2-4 человека  
- **Механика**: Пошаговая игра с таймером 15 сек
- **Правила**: Набрать 21 очко, не превышая лимит
- **Ставка**: Фиксированная 100 очков

#### 3. ✂️ Камень-Ножницы-Бумага
- **Игроки**: 2-4 человека
- **Механика**: Одновременный выбор
- **Правила**: Классические + обработка множественных ничьих
- **Ставка**: Фиксированная 100 очков

## 🛠 Технологии

**Frontend:**
- React 19 с TypeScript
- Vite для быстрой разработки
- Tailwind CSS для стилизации
- Telegram Web App API
- React Icons для иконок

**Backend:**
- FastAPI (Python)
- SQLite/PostgreSQL для хранения рекордов
- WebSocket для мультиплеера
- JWT аутентификация через Telegram

## ✨ Возможности

- 🎮 Множество классических игр
- 🏆 Система рекордов и достижений
- 👥 Мультиплеер режимы  
- 🎨 Красивый современный дизайн
- � Полная адаптация под мобильные устройства
- ⚡ Молниеносная загрузка
- 🔄 Offline режим для некоторых игр

## 🚀 Запуск проекта

### Backend

```bash
cd server
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### Frontend

```bash
cd client/news-aggregator
npm install
npm run dev
```

Приложение будет доступно по адресу: http://localhost:5173

## Структура проекта

```
├── client/
│   └── news-aggregator/         # React приложение
│       ├── src/
│       │   ├── components/      # Компоненты UI
│       │   ├── hooks/          # Кастомные хуки
│       │   ├── services/       # API сервисы
│       │   └── types/          # TypeScript типы
│       └── package.json
└── server/
    ├── main.py                 # FastAPI сервер
    └── requirements.txt        # Python зависимости
```

## API Endpoints

- `GET /news` - Получить новости с пагинацией
- `GET /news/search?q={query}` - Поиск новостей
- `GET /health` - Проверка состояния сервера

## Параметры API

**Пагинация:**
- `page` - номер страницы (по умолчанию: 1)
- `limit` - количество элементов на странице (по умолчанию: 20, максимум: 100)

**Поиск:**
- `q` - поисковый запрос (обязательный)

## Конфигурация

RSS источники настраиваются в файле `server/main.py` в переменной `RSS_SOURCES`.

По умолчанию используются:
- TengriNews (https://tengrinews.kz/rss/all.xml)
- Zakon.kz (https://www.zakon.kz/rss/)

## Разработка

Для разработки рекомендуется запускать backend и frontend в отдельных терминалах.

Backend будет доступен на порту 8000, frontend на порту 5173.
