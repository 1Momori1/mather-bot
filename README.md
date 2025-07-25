# 🤖 Mather Bot - Менеджер Telegram ботов

Мощный Telegram бот для управления другими ботами на вашем сервере/компьютере.

## ✨ Возможности

### 🎛️ Управление ботами
- ✅ **Добавление ботов** - простой диалог для добавления новых ботов
- ▶️ **Запуск/Остановка** - управление процессами ботов
- 🔄 **Перезапуск** - быстрый перезапуск ботов
- 🗑️ **Удаление** - удаление ботов с подтверждением
- 📈 **Информация** - детальная информация о каждом боте

### 📊 Мониторинг и статистика
- 📈 **Статистика** - общая статистика по всем ботам
- 🖥️ **Системная информация** - CPU, память, диск, время работы
- 📅 **История запусков** - количество запусков и последний запуск
- 🏆 **Самый активный бот** - статистика активности

### 🔒 Безопасность и надежность
- 💾 **Резервное копирование** - автоматическое создание резервных копий БД
- 📝 **Логирование** - подробные логи всех действий
- ⚠️ **Подтверждения** - подтверждение опасных действий
- 🔍 **Валидация** - проверка путей к файлам и данных

### 🎨 Удобный интерфейс
- 🎛️ **Кнопочное управление** - все действия через кнопки
- 🎨 **Красивый дизайн** - эмодзи и форматирование
- 📱 **Адаптивный интерфейс** - удобно на любых устройствах

## 🚀 Установка

### 1. Клонирование и настройка
```bash
git clone <repository>
cd Mather_bot
```

### 2. Установка зависимостей
```bash
pip install -r requirements.txt
```

### 3. Настройка токена
Отредактируйте файл `config.py`:
```python
API_TOKEN = 'ваш_токен_бота'
```

### 4. Запуск
```bash
python main.py
```

## 📁 Структура проекта

```
Mather_bot/
├── main.py              # Основной файл бота
├── config.py            # Конфигурация (токен, настройки)
├── db.py                # Работа с базой данных
├── process_manager.py   # Управление процессами ботов
├── logger.py            # Система логирования
├── system_info.py       # Системная информация
├── requirements.txt     # Зависимости
├── bots.db             # База данных (создается автоматически)
├── logs/               # Папка с логами
└── backups/            # Папка с резервными копиями
```

## 🎯 Использование

### Основные команды
- `/start` - запуск бота и показ главного меню

### Главное меню
- 🤖 **Добавить бота** - добавление нового бота
- 📊 **Статистика** - общая статистика
- 🖥️ **Система** - информация о системе
- 📋 **Список ботов** - список всех ботов
- 💾 **Резервная копия** - создание резервной копии

### Управление ботом
- ▶️ **Запустить** - запуск бота
- ⏹️ **Остановить** - остановка бота
- 🔄 **Перезапустить** - перезапуск бота
- 🗑️ **Удалить** - удаление бота
- 📈 **Информация** - детальная информация

## 🔧 Технические детали

### Технологии
- **Python 3.x** - основной язык
- **aiogram 3.x** - Telegram Bot API
- **aiosqlite** - асинхронная работа с SQLite
- **psutil** - системная информация
- **asyncio** - асинхронное программирование

### База данных
SQLite база с таблицей `bots`:
- `id` - уникальный идентификатор
- `name` - имя бота
- `script_path` - путь к скрипту
- `token` - токен бота (опционально)
- `status` - статус (running/stopped)
- `created_at` - дата создания
- `last_started` - последний запуск
- `start_count` - количество запусков

### Логирование
Все действия записываются в файлы:
- `logs/bot_manager_YYYYMMDD.log` - ежедневные логи
- Уровни: INFO, ERROR
- Формат: время - уровень - сообщение

## 🛠️ Разработка

### Добавление новых функций
1. Создайте новый модуль в отдельном файле
2. Добавьте импорт в `main.py`
3. Создайте обработчики и клавиатуры
4. Добавьте логирование

### Структура обработчиков
```python
@dp.callback_query()
async def process_callback(callback_query: types.CallbackQuery, state: FSMContext):
    # Обработка callback_query.data
    pass

@dp.message(StateClass.state_name)
async def process_state(message: types.Message, state: FSMContext):
    # Обработка состояний FSM
    pass
```

## 📝 Логи

Логи содержат:
- Действия пользователей
- Статусы ботов
- Системные сообщения
- Ошибки и исключения

Пример лога:
```
2024-01-15 10:30:15 - INFO - ACTION: start - User 123456789 started bot
2024-01-15 10:30:20 - INFO - BOT: TestBot - start_attempt User 123456789
2024-01-15 10:30:21 - INFO - BOT: TestBot - started success
```

## 🔒 Безопасность

- Проверка путей к файлам
- Валидация входных данных
- Подтверждение опасных действий
- Логирование всех операций
- Резервное копирование данных

## 🐛 Устранение неполадок

### Бот не запускается
1. Проверьте токен в `config.py`
2. Убедитесь, что все зависимости установлены
3. Проверьте логи в папке `logs/`

### Ошибки при управлении ботами
1. Проверьте пути к скриптам ботов
2. Убедитесь, что скрипты имеют права на выполнение
3. Проверьте логи для деталей ошибок

### Проблемы с базой данных
1. Проверьте права доступа к папке
2. Восстановите из резервной копии
3. Пересоздайте базу данных

## 📞 Поддержка

При возникновении проблем:
1. Проверьте логи в папке `logs/`
2. Убедитесь в корректности настроек
3. Проверьте системные требования

## 📄 Лицензия

MIT License - свободное использование и модификация.

---

**Создано с ❤️ для управления Telegram ботами** 