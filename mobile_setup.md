# 📱 Мобильная версия Mather Bot

## 🎯 Установка на Android через Termux

### Шаг 1: Установка Termux

1. **Скачайте Termux** из [F-Droid](https://f-droid.org/packages/com.termux/) (НЕ из Google Play!)
2. **Установите и откройте Termux**

### Шаг 2: Обновление системы

```bash
# Обновляем пакеты
pkg update && pkg upgrade -y

# Устанавливаем необходимые пакеты
pkg install python git wget curl -y
```

### Шаг 3: Клонирование проекта

```bash
# Клонируем репозиторий
git clone https://github.com/1Momori1/mather-bot.git
cd mather-bot

# Устанавливаем зависимости
pip install -r requirements.txt
```

### Шаг 4: Настройка автозапуска

```bash
# Создаем скрипт автозапуска
cat > ~/start_bot.sh << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash

# Переходим в папку бота
cd ~/mather-bot

# Проверяем, не запущен ли уже бот
if ! pgrep -f "python main.py" > /dev/null; then
    echo "$(date): Starting Mather Bot..."
    python main.py
else
    echo "$(date): Bot is already running"
fi
EOF

# Делаем скрипт исполняемым
chmod +x ~/start_bot.sh
```

### Шаг 5: Настройка автозапуска при старте Termux

```bash
# Создаем файл автозапуска
mkdir -p ~/.termux/boot
cat > ~/.termux/boot/start_mather_bot.sh << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
cd ~/mather-bot
python main.py > ~/bot.log 2>&1 &
EOF

chmod +x ~/.termux/boot/start_mather_bot.sh
```

### Шаг 6: Установка Termux:Boot (для автозапуска)

```bash
# Устанавливаем Termux:Boot
pkg install termux-boot

# Включаем автозапуск
termux-boot enable
```

## 🎛️ Управление ботом

### Запуск вручную:
```bash
cd ~/mather-bot
python main.py
```

### Проверка статуса:
```bash
# Проверить, запущен ли бот
ps aux | grep "python main.py"

# Посмотреть логи
tail -f ~/bot.log
```

### Остановка бота:
```bash
pkill -f "python main.py"
```

### Перезапуск:
```bash
pkill -f "python main.py"
sleep 2
cd ~/mather-bot
python main.py
```

## 🔧 Дополнительные настройки

### Настройка уведомлений:
```bash
# Установка termux-api для уведомлений
pkg install termux-api

# Тестовое уведомление
termux-notification --title "Mather Bot" --content "Bot is running!"
```

### Создание алиасов для удобства:
```bash
# Добавляем алиасы в ~/.bashrc
echo 'alias bot-start="cd ~/mather-bot && python main.py"' >> ~/.bashrc
echo 'alias bot-stop="pkill -f \"python main.py\"'" >> ~/.bashrc
echo 'alias bot-status="ps aux | grep \"python main.py\"'" >> ~/.bashrc
echo 'alias bot-logs="tail -f ~/bot.log"' >> ~/.bashrc

# Перезагружаем bashrc
source ~/.bashrc
```

## 📱 Альтернативные варианты

### 1. Pydroid 3 (Python IDE для Android)
- Скачайте из Google Play
- Откройте проект
- Запустите main.py
- Настройте автозапуск

### 2. Flutter приложение
- Создаем красивое приложение
- Управление через кнопки
- Уведомления о статусе
- Автозапуск при старте телефона

### 3. React Native
- Кроссплатформенное решение
- Работает на iOS и Android
- Веб-интерфейс для управления

## 🔒 Безопасность

### Настройка пароля для Termux:
```bash
# Установка пароля
passwd
```

### Ограничение доступа:
```bash
# Создание отдельного пользователя (если нужно)
# (Требует root права)
```

## 📊 Мониторинг

### Просмотр логов:
```bash
# Реальные логи
tail -f ~/mather-bot/logs/bot_manager_*.log

# Логи запуска
tail -f ~/bot.log
```

### Проверка ресурсов:
```bash
# Использование памяти
free -h

# Использование CPU
top

# Сетевые соединения
netstat -tulpn
```

## 🚀 Автоматизация

### Создание скрипта мониторинга:
```bash
cat > ~/monitor_bot.sh << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash

while true; do
    if ! pgrep -f "python main.py" > /dev/null; then
        echo "$(date): Bot crashed, restarting..."
        cd ~/mather-bot
        python main.py > ~/bot.log 2>&1 &
        termux-notification --title "Mather Bot" --content "Bot restarted automatically"
    fi
    sleep 60
done
EOF

chmod +x ~/monitor_bot.sh
```

### Запуск мониторинга:
```bash
nohup ~/monitor_bot.sh > ~/monitor.log 2>&1 &
```

## 💡 Советы

1. **Используйте Termux из F-Droid** - версия из Google Play устарела
2. **Включите автозапуск** - бот будет работать после перезагрузки
3. **Настройте уведомления** - получайте уведомления о статусе
4. **Используйте алиасы** - для быстрого управления
5. **Мониторьте ресурсы** - следите за использованием памяти

## 🎯 Результат

После настройки ваш бот будет:
- ✅ Автоматически запускаться при старте Termux
- ✅ Работать в фоне
- ✅ Автоматически перезапускаться при сбоях
- ✅ Отправлять уведомления о статусе
- ✅ Управляться через Telegram
- ✅ Логировать все действия 