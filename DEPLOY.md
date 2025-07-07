# 🚀 Деплой на Railway

## Быстрый деплой (5 минут)

### 1. Подготовка GitHub репозитория

1. Создайте репозиторий на GitHub
2. Загрузите все файлы проекта
3. Убедитесь, что есть файлы:
   - `main.py`
   - `requirements.txt`
   - `Procfile`
   - `runtime.txt`
   - `railway.json`

### 2. Настройка Railway

1. **Перейдите на [Railway.app](https://railway.app)**
2. **Войдите через GitHub**
3. **Нажмите "New Project"**
4. **Выберите "Deploy from GitHub repo"**
5. **Выберите ваш репозиторий**
6. **Нажмите "Deploy Now"**

### 3. Настройка переменных окружения

После деплоя:

1. **Перейдите в настройки проекта**
2. **Выберите "Variables"**
3. **Добавьте переменную:**
   ```
   API_TOKEN = ваш_токен_бота
   ```

### 4. Получение URL

1. **В настройках проекта найдите "Domains"**
2. **Скопируйте URL** (например: `https://your-bot.railway.app`)

## 🔧 Альтернативный способ через CLI

### Установка Railway CLI

```bash
# Windows (PowerShell)
iwr https://railway.app/install.ps1 -useb | iex

# macOS/Linux
curl -fsSL https://railway.app/install.sh | sh
```

### Деплой через CLI

```bash
# Логин в Railway
railway login

# Инициализация проекта
railway init

# Линк с существующим проектом
railway link

# Установка переменных
railway variables set API_TOKEN=ваш_токен_бота

# Деплой
railway up

# Просмотр логов
railway logs
```

## 📊 Мониторинг

### Просмотр логов
- В веб-интерфейсе Railway
- Через CLI: `railway logs`

### Статус приложения
- В веб-интерфейсе Railway
- Через CLI: `railway status`

### Перезапуск
- В веб-интерфейсе: кнопка "Redeploy"
- Через CLI: `railway up`

## 🔒 Безопасность

### Переменные окружения
- Никогда не коммитьте токены в код
- Используйте Railway Variables
- Токены автоматически шифруются

### SSL сертификат
- Railway автоматически предоставляет SSL
- Все соединения защищены

## 💰 Стоимость

### Бесплатный план
- ✅ 500 часов в месяц
- ✅ 1 проект
- ✅ 512 MB RAM
- ✅ 1 GB storage

### Платные планы
- $5/месяц: 1000 часов, 2 GB RAM
- $10/месяц: неограниченно, 4 GB RAM

## 🐛 Устранение неполадок

### Бот не запускается
1. Проверьте логи в Railway
2. Убедитесь, что API_TOKEN установлен
3. Проверьте requirements.txt

### Ошибки деплоя
1. Проверьте Procfile
2. Убедитесь в правильности runtime.txt
3. Проверьте синтаксис Python

### Проблемы с базой данных
1. Railway использует временную файловую систему
2. База данных сбрасывается при перезапуске
3. Для постоянного хранения используйте Railway PostgreSQL

## 📞 Поддержка

- [Railway Docs](https://docs.railway.app)
- [Railway Discord](https://discord.gg/railway)
- [GitHub Issues](https://github.com/railwayapp/railway/issues) 