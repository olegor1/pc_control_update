<div align="center">

# 🖥️ PC Control Bot

**Управляй своим компьютером удалённо через Telegram**

[![Electron](https://img.shields.io/badge/Electron-27.0.0-47848F?style=flat-square&logo=electron&logoColor=white)](https://www.electronjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-16%2B-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Telegram Bot API](https://img.shields.io/badge/Telegram%20Bot%20API-0.61.0-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://core.telegram.org/bots/api)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6?style=flat-square&logo=windows&logoColor=white)]()
[![License](https://img.shields.io/badge/License-ISC-blue?style=flat-square)]()

</div>

---

## О проекте

**PC Control Bot** — это настольное приложение на базе Electron, которое позволяет удалённо управлять вашим компьютером через Telegram-бота. Планируйте выключение с точностью до минуты, следите за состоянием системы и управляйте таймером прямо из мессенджера — не вставая с дивана.

### Ключевые возможности

- **Таймер выключения** — быстрые пресеты и ручной ввод времени
- **Telegram-управление** — полный контроль через бота с кнопками и командами
- **Мониторинг системы** — CPU, RAM, диск, время работы
- **Авторизация** — доступ только для доверенных пользователей по Telegram ID
- **Трей и автозапуск** — работает тихо в фоне

---

## Скриншоты

> *Интерфейс приложения с круговым прогрессом таймера, настройками бота и управлением через Telegram*

---

## Установка и запуск

### Требования

- Windows 10 / 11
- Подключение к интернету (для работы Telegram-бота)

### Шаги

1. Скачайте последнюю версию `.exe` из раздела [Releases](https://github.com/olegor1/pc_control_update/releases)
2. Запустите установщик и следуйте инструкциям **или** запустите portable-версию напрямую
3. Настройте бота в приложении (см. раздел ниже)

---

## Настройка Telegram-бота

### 1. Создайте бота

1. Откройте [@BotFather](https://t.me/BotFather) в Telegram
2. Отправьте `/newbot` и следуйте инструкциям
3. Скопируйте полученный **API Token**

### 2. Узнайте свой Telegram ID

Откройте [@userinfobot](https://t.me/userinfobot) — он пришлёт ваш числовой ID.

### 3. Введите данные в приложение

Откройте вкладку **Настройки** в PC Control Bot:
- Вставьте токен бота
- Добавьте ваш Telegram ID в список разрешённых
- Нажмите **Сохранить и запустить бота**

---

## Команды бота

| Команда / Кнопка | Описание |
|------------------|----------|
| `/start` | Главное меню с кнопками управления |
| `⏱ Таймер выключения` | Выбор времени до выключения |
| `🔴 Выключить сейчас` | Немедленное завершение работы |
| `❌ Отменить выключение` | Отмена запланированного таймера |
| `📊 Статус системы` | CPU, RAM, диск, аптайм |

> Бот поддерживает несколько авторизованных пользователей, но работает только один таймер одновременно.

---

## Конфигурация

Настройки хранятся через `electron-store` и автоматически сохраняются между сессиями:

```json
{
  "telegramToken": "ВАШ_ТОКЕН",
  "authorizedUsers": [123456789],
  "startMinimized": false,
  "autoStart": false,
  "theme": "auto"
}
```

| Параметр          | Тип       | Описание                              |
|-------------------|-----------|---------------------------------------|
| `telegramToken`   | `string`  | Токен бота от @BotFather              |
| `authorizedUsers` | `number[]`| Whitelist Telegram ID                 |
| `startMinimized`  | `boolean` | Запуск сразу в трей                   |
| `autoStart`       | `boolean` | Автозапуск при старте Windows         |
| `theme`           | `string`  | `"light"` / `"dark"` / `"auto"`       |

---

## Безопасность

- Доступ к боту — только для пользователей из whitelist по Telegram ID
- `nodeIntegration: false` — рендерер изолирован от Node.js
- `contextIsolation: true` — безопасный preload-мост через `contextBridge`
- Токен бота маскируется в интерфейсе (поле `password`)

---

## Технологии

| Технология | Назначение |
|------------|------------|
| [Electron](https://www.electronjs.org/) 27 | Desktop-фреймворк |
| [node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api) | Telegram Bot API |
| [electron-store](https://github.com/sindresorhus/electron-store) | Хранение конфигурации |
| [node-os-utils](https://github.com/nicedoc/node-os-utils) | Информация о системе |
| [electron-builder](https://www.electron.build/) | Сборка и дистрибуция |

---

<div align="center">

Сделано на Electron + Node.js

</div>
