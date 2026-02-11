# Шаблон конфигурации API ключей

Заполните все ключи и ID, затем подставьте в workflow.

## 🔑 API Ключи

### Claude API
```
YOUR_ANTHROPIC_API_KEY = sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
**Где взять:** https://console.anthropic.com/settings/keys

**Важно:** У тебя уже есть! Используй тот же что для Claude Code.

---

### OpenAI API
```
YOUR_OPENAI_API_KEY = sk-proj-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
**Где взять:** https://platform.openai.com/api-keys

**Важно:** У тебя $20 закинуто, просто создай ключ.

---

### Telegram Bot Token
```
YOUR_TELEGRAM_BOT_TOKEN = 1234567890:ABCdefGHIjklMNOpqrsTUVwxyz
YOUR_TELEGRAM_CHANNEL_ID = @apartguru   или   -1001234567890
```

**Где взять:**
1. Найди @BotFather в Telegram
2. Отправь `/newbot`
3. Придумай имя: `Apart Guru Content Bot`
4. Username: `apartguru_content_bot`
5. Получишь token

**Как получить Channel ID:**
1. Добавь бота в свой канал как админ
2. Отправь любое сообщение в канал
3. Открой: `https://api.telegram.org/bot<TOKEN>/getUpdates`
4. Найди `"chat":{"id":-1001234567890}`

---

### VK Community Token
```
YOUR_VK_GROUP_ID = 123456789   (без минуса)
YOUR_VK_COMMUNITY_TOKEN = vk1.a.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Где взять:**
1. Зайди в группу VK → Управление
2. Настройки → Работа с API
3. Создать ключ → Выбери права: "Управление сообществом", "Фотографии"
4. Скопируй токен

**ID группы:**
- Зайди в группу, посмотри URL: `vk.com/club123456789`
- ID = `123456789` (в workflow используй с минусом: `-123456789`)

---

### Instagram (Meta Business API)
```
YOUR_IG_ACCOUNT_ID = 17841400000000000
YOUR_META_ACCESS_TOKEN = EAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Где взять:**
1. Зайди на https://developers.facebook.com
2. Создай приложение (тип: Business)
3. Добавь Instagram Graph API
4. Получи долгоживущий токен (60 дней): https://developers.facebook.com/docs/instagram-platform/instagram-graph-api/get-started
5. Instagram Account ID найди через Graph API Explorer: `me/accounts`

**Важно:**
- Instagram должен быть Business или Creator аккаунт
- Привязан к Facebook страницеМетод:
1. https://business.facebook.com/ → Settings → Instagram accounts
2. Connect Instagram account
3. Получи Access Token через Meta Business Suite

---

### Threads API
```
YOUR_THREADS_USER_ID = 123456789012345
YOUR_THREADS_ACCESS_TOKEN = THQxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Где взять:**
1. Threads использует тот же Meta Business API что и Instagram
2. Threads User ID = Instagram Account ID (тот же самый)
3. Access Token = тот же что для Instagram
4. Просто убедись что в Meta App включены права для Threads

**Документация:** https://developers.facebook.com/docs/threads

---

## 📋 Быстрый чеклист

- [ ] Claude API key получен
- [ ] OpenAI API key создан
- [ ] Telegram бот создан через @BotFather
- [ ] Telegram бот добавлен в канал как админ
- [ ] VK Community Token получен (с правами на посты)
- [ ] Instagram переведён в Business аккаунт
- [ ] Instagram привязан к Facebook странице
- [ ] Meta Access Token получен (60 days)
- [ ] Threads подключен к Meta Business API
- [ ] Все ключи подставлены в workflow
- [ ] Workflow сохранён и активирован
- [ ] Тестовый запуск прошёл успешно

---

## 🆘 Помощь

Если что-то не получается:
1. Проверь права API ключей
2. Убедись что боты/токены активны
3. Посмотри логи ошибок в n8n (внизу справа)
4. Напиши @apartgurusupp в Telegram
