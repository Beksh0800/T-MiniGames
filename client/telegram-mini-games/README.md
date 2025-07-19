# Telegram Mini App - Игры и Новости

## Описание проекта

Телеграм мини-приложение, объединяющее в себе новостной агрегатор и мультиплеерные мини-игры. Проект создан по техническому заданию MVP с полным функционалом для интеграции в Telegram Bot API.

## 🎮 Функционал MVP

### 📰 Новостной агрегатор
- **Источники**: Агрегация новостей из проверенных RSS источников
- **Категории**: Технологии, Спорт, Политика, Развлечения, Наука
- **Интерфейс**: Современный дизайн с фильтрацией по категориям
- **Обновление**: Автоматическое и ручное обновление ленты

### 🎲 Мини-игры

#### 1. Кубики (Dice Game)
- **Игроки**: 2-4 человека
- **Правила**: Каждый игрок бросает 2 кубика, выигрывает тот, у кого больше сумма
- **Ставки**: Фиксированная ставка 100 очков
- **Механика**: Одновременный бросок всех игроков

#### 2. Карты 21 (Blackjack)
- **Игроки**: 2-4 человека
- **Правила**: Набрать 21 очко, не превышая лимит
- **Ставки**: Фиксированная ставка 100 очков
- **Механика**: Пошаговая игра с 15-секундным таймером

#### 3. Камень-Ножницы-Бумага
- **Игроки**: 2-4 человека
- **Правила**: Классические правила РПС
- **Ставки**: Фиксированная ставка 100 очков
- **Механика**: Одновременный выбор с обработкой ничьих

## 🎨 Дизайн

### Glass Morphism UI
- **Стиль**: Современный стеклянный дизайн с размытием
- **Анимации**: Плавные переходы и hover-эффекты
- **Градиенты**: Фиолетово-синие градиенты
- **Адаптивность**: Полная поддержка мобильных устройств

### Компоненты
- Карточки игр с иконками и описанием
- Анимированные кнопки и переходы
- Информационные панели с прозрачностью
- Responsive grid layout

## 🚀 Технологии

### Frontend
- **React 19**: Последняя версия с новыми возможностями
- **TypeScript**: Типизированный JavaScript
- **Tailwind CSS 4.1.11**: Современные стили
- **Vite 7.0.5**: Быстрая сборка
- **React Icons**: Иконки Font Awesome

### Backend (планируется)
- **FastAPI**: Высокопроизводительный Python API
- **WebSocket**: Реалтайм мультиплеер
- **SQLite/PostgreSQL**: База данных
- **RSS Parser**: Агрегация новостей

## 🛠️ Установка и запуск

### Frontend
```bash
cd client/telegram-mini-games
npm install
npm run dev
```

### Backend
```bash
cd server
pip install -r requirements.txt
python main.py
```

## 🎮 Игровая механика

### Система очков
- Стартовый баланс: 1000 очков
- Ставка за игру: 100 очков
- Победитель забирает весь банк
- При ничьей ставки возвращаются

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
