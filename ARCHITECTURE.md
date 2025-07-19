# 🏗️ Архитектура Telegram Mini App MVP

## � Обзор проекта

Telegram Mini App представляет собой современное веб-приложение, интегрированное в экосистему Telegram через WebApp API. Проект реализует MVP с двумя основными функциональными блоками: новостной агрегатор и мультиплеерные мини-игры.

## 🎯 Техническое задание MVP

### 📰 Новостной агрегатор
- RSS парсинг проверенных источников
- Категоризация: Технологии, Спорт, Политика, Развлечения, Наука
- Фильтрация и поиск по контенту
- Кэширование для оффлайн доступа

### � Мини-игры (3 шт.)

#### 1. Кубики
- **Тип**: Одновременная игра
- **Игроки**: 2-4
- **Механика**: Бросок 2 кубиков, максимальная сумма побеждает
- **Ставка**: 100 очков

#### 2. Карты 21
- **Тип**: Пошаговая игра
- **Игроки**: 2-4
- **Механика**: Blackjack с таймером 15 сек на ход
- **Ставка**: 100 очков

#### 3. Камень-Ножницы-Бумага
- **Тип**: Одновременная игра
- **Игроки**: 2-4
- **Механика**: Классические правила + обработка множественных ничьих
- **Ставка**: 100 очков
T-MiniGames/
├── server/                     # 🐍 Backend (Python FastAPI)
│   ├── main.py                # Основной сервер
│   └── requirements.txt       # Python зависимости
│
├── client/news-aggregator/    # ⚛️ Frontend (React)
│   ├── src/
│   │   ├── types/            # 📝 TypeScript типы
│   │   │   └── news.ts       # Интерфейсы данных
│   │   ├── services/         # 🔌 API сервисы
│   │   │   └── newsService.ts # HTTP клиент
│   │   ├── hooks/            # 🔄 React хуки
│   │   │   └── useNews.ts    # Логика состояния
│   │   ├── components/       # 🎨 UI компоненты
│   │   │   ├── NewsCard.tsx  # Карточка новости
│   │   │   ├── LoadingSpinner.tsx # Загрузка
│   │   │   └── ErrorDisplay.tsx   # Ошибки
│   │   └── App.tsx           # Главный компонент
│   ├── package.json          # Node.js зависимости
│   └── test.html            # 🎨 Демо версия
└── README.md                # Общая документация
```

## 🔧 Как работает каждый файл

### Backend (FastAPI)

#### `server/main.py` - Сердце API сервера
```python
# 🌐 Настройка FastAPI приложения
app = FastAPI(title="News Aggregator API", version="1.0.0")

# 🔄 CORS для взаимодействия с фронтендом
app.add_middleware(CORSMiddleware, ...)

# 📰 Структура данных новости
@dataclass
class NewsItem:
    title: str      # Заголовок
    link: str       # Ссылка на статью
    source: str     # Источник (URL RSS)
    date: str       # Дата публикации
    description: Optional[str]  # Описание
    author: Optional[str]       # Автор
```

**Основные функции:**
- 🔄 `fetch_rss_feed()` - Асинхронная загрузка RSS каналов
- 📊 `get_news()` - API эндпоинт с пагинацией
- 🔍 `search_news()` - Поиск по новостям
- ❤️ `health_check()` - Проверка состояния сервера

**RSS источники:**
- 🌍 BBC News - международные новости
- 🔴 Reddit - популярные посты
- 💻 Habr - IT новости

### Frontend (React)

#### `src/types/news.ts` - TypeScript контракты
```typescript
// 📄 Структура одной новости
interface NewsItem {
    title: string;
    link: string;
    source: string;
    date: string;
    description?: string;
    author?: string;
}

// 📦 Ответ API с метаданными
interface NewsResponse {
    news: NewsItem[];
    total: number;
    page: number;
    hasMore: boolean;
}
```

#### `src/services/newsService.ts` - API клиент
```typescript
class NewsService {
    // 🔄 Singleton паттерн для единого экземпляра
    static getInstance(): NewsService
    
    // 📊 Загрузка новостей с пагинацией
    async getNews(page: number, limit: number): Promise<NewsResponse>
    
    // 🔍 Поиск новостей
    async searchNews(query: string, page: number): Promise<NewsResponse>
}
```

**Особенности:**
- ⏱️ Таймаут 10 секунд
- ❌ Детальная обработка ошибок
- 🔄 Автоматическая типизация ответов

#### `src/hooks/useNews.ts` - Управление состоянием
```typescript
export const useNews = (initialPage: number = 1) => {
    const [news, setNews] = useState<NewsItem[]>([]);     // 📰 Список новостей
    const [loading, setLoading] = useState<boolean>(true); // ⏳ Состояние загрузки
    const [error, setError] = useState<ErrorState>(...);   // ❌ Ошибки
    const [hasMore, setHasMore] = useState<boolean>(true); // 📄 Есть ли еще страницы
    
    // 🔄 Функции
    const loadNews = useCallback(...);    // Загрузка страницы
    const loadMore = useCallback(...);    // Загрузка следующей страницы
    const refresh = useCallback(...);     // Обновление
}
```

#### `src/components/` - UI компоненты

**NewsCard.tsx** - Карточка новости
- 🎨 Стильное отображение новости
- 📅 Форматирование даты
- 🏷️ Бейджи источников
- 🔗 Ссылка на оригинал

**LoadingSpinner.tsx** - Индикатор загрузки
- ⚡ Разные размеры (sm, md, lg)
- 💫 CSS анимации
- 📝 Настраиваемый текст

**ErrorDisplay.tsx** - Отображение ошибок
- ❌ Красивые уведомления об ошибках
- 🔄 Кнопка повторной попытки
- 📱 Адаптивный дизайн

## 🎨 Дизайн система

### Цветовая палитра
- 🟣 **Основной**: Градиент Purple-Blue (#667eea → #764ba2)
- ⚪ **Фон**: Светло-серый (#f9fafb)
- 🔘 **Карточки**: Белый с тенями
- 🟡 **Акценты**: Цветные бейджи по источникам

### Типографика
- 📖 **Шрифт**: Inter (современный, читаемый)
- 📏 **Размеры**: 
  - Заголовки: 2xl-4xl
  - Основной текст: base-lg
  - Мелкий текст: sm-xs

### Анимации
- ✨ **Fade In**: Плавное появление карточек
- 🔄 **Hover**: Поднятие карточек при наведении
- ⚡ **Spinner**: Вращение индикаторов загрузки
- 📱 **Responsive**: Адаптация под все экраны

## 🚀 Поток данных

1. **Пользователь открывает страницу**
2. **useNews хук** автоматически вызывает `loadNews()`
3. **NewsService** отправляет HTTP запрос к API
4. **FastAPI сервер** параллельно загружает RSS каналы
5. **feedparser** парсит XML данные
6. **Сервер** возвращает JSON с новостями и метаданными
7. **React** обновляет состояние и рендерит компоненты
8. **Пользователь** видит красивые карточки новостей

## 🔄 Жизненный цикл новости

```
RSS источник → feedparser → NewsItem → API Response → 
React State → NewsCard → HTML → Пользователь
```

## 📊 API Endpoints

### `GET /news`
**Параметры:**
- `page` (int): Номер страницы (по умолчанию: 1)
- `limit` (int): Количество на странице (по умолчанию: 20, максимум: 100)

**Ответ:**
```json
{
    "news": [...],
    "total": 45,
    "page": 1,
    "hasMore": true
}
```

### `GET /news/search`
**Параметры:**
- `q` (string): Поисковый запрос
- `page` (int): Номер страницы
- `limit` (int): Количество на странице

### `GET /health`
**Ответ:**
```json
{
    "status": "healthy",
    "timestamp": "2025-07-18T16:50:32"
}
```

## 🛠️ Технологический стек

### Backend
- **FastAPI** - Современный Python веб-фреймворк
- **feedparser** - Парсинг RSS/Atom каналов
- **asyncio** - Асинхронное программирование
- **uvicorn** - ASGI сервер

### Frontend
- **React 19** - Библиотека UI
- **TypeScript** - Типизированный JavaScript
- **Tailwind CSS** - Utility-first CSS фреймворк
- **Axios** - HTTP клиент
- **Vite** - Сборщик проектов

### Дизайн
- **Font Awesome** - Иконки
- **Google Fonts** - Шрифт Inter
- **CSS Grid/Flexbox** - Адаптивная верстка
- **CSS анимации** - Плавные переходы

Это полноценное, масштабируемое приложение с современной архитектурой! 🎉
