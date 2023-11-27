# Телеграм Бот для Тестирования

<p align="center">
  <a href="#введение">Введение</a> &nbsp;&bull;&nbsp;
  <a href="#установка">Установка</a> &nbsp;&bull;&nbsp;
  <a href="#использование">Использование</a> &nbsp;&bull;&nbsp;
  <a href="#разработка">Разработка</a>
</p>

## Введение

Этот репозиторий содержит Telegram бота, написанного на Python с использованием библиотеки aiogram версии 3. Бот является частью системы тестирования и отвечает за организацию процесса тестирования, получение тестов из внешних источников, таких как сервер, и использование опросов Telegram для проведения тестирования.

- **Паттерн программирования "Адаптер"**: Реализация адаптера позволяет подключаться к различным удаленным источникам без внесения изменений в код бота. Это обеспечивает удобство поддержки и не зависит от конкретной реализации источника.

- **Использование aiogram**: Асинхронная структура библиотеки aiogram обеспечивает быстрый ответ бота. Библиотека также мгновенно внедряет новые возможности, предоставленные API Telegram BOT, что обеспечивает возможность использования новых функций без длительного ожидания обновления библиотеки.

## Установка

### Стандартная

1. Клонируйте репозиторий:
   ```
   git clone https://github.com/adunyt/testing_bot/
   cd testing_bot
   ```
2. Создайте файл `.env` в корневой директории и добавьте в него:
   ```
   BOT_TOKEN=ваш_токен_бота
   ```
   Замените `ваш_токен_бота` на токен вашего Telegram бота.
3. Установите зависимости:
   ```
   pip install -r requirements.txt
   ```
4. Запустите бота:
   ```
   python main.py
   ```

### Docker

#### Скачивание образа Docker
```
docker pull adunyt/testing_bot:latest
```

#### Запуск контейнера с передачей переменной окружения
```
docker run -d -e BOT_TOKEN=ваш_токен_бота adunyt/testing_bot:latest
```

Замените `ваш_токен_бота` на токен вашего Telegram бота.

## Использование

Бот организует тестирование пользователя через deep-link ссылку. Пользователь переходит по ссылке, сформированной в следующем формате:
```
https://t.me/{BOT_USERNAME}?start={DEEPLINK_DATA}
```
- **BOT_USERNAME**: Юзернейм вашего Telegram бота.
- **DEEPLINK_DATA**: ID теста, который пользователь хочет пройти.

После перехода по ссылке бот проверяет существование теста и наличие аккаунта пользователя в удаленном источнике. Если аккаунт отсутствует, бот проводит процесс регистрации, отправляет данные в источник и переходит к тестированию пользователя.

## Разработка

Для внесения своего вклада в разработку бота:

1. Клонируйте репозиторий:
   ```
   git clone https://github.com/adunyt/testing_bot/
   cd testing_bot
   ```
2. Настройте файл `.env`, как описано в разделе Установка.
3. Установите зависимости:
   ```
   pip install -r requirements.txt
   ```
4. Начните разработку!
