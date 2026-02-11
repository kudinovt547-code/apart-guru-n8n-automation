# 🔄 Автозагрузка из Git в n8n

## 3 способа загрузить workflow из GitHub в n8n

---

## Способ 1: Прямая ссылка на JSON (самый простой)

### В n8n:

1. **Workflows** → **Add Workflow** → **Import from URL**
2. Вставь ссылку на **raw** файл:
   ```
   https://raw.githubusercontent.com/kudinovt547-code/apart-guru-n8n-automation/main/apart-guru-content-factory-UPDATED.json
   ```
3. Нажми **Import**
4. Готово! ✅

---

## Способ 2: GitHub Integration (встроенная в n8n)

### Настройка:

1. **Settings** → **Environments** → **Source Control**
2. Выбери **GitHub**
3. Подключи репозиторий:
   - Repository: `kudinovt547-code/apart-guru-n8n-automation`
   - Branch: `main`
   - Folder: `/` (корень)
4. **Connect**

### Синхронизация:

- **Pull from Git** — загрузить все workflows из GitHub
- **Push to Git** — сохранить изменения в GitHub
- Авто-синхронизация каждые X минут (настраивается)

**Плюсы:**
- Двусторонняя синхронизация
- История изменений
- Командная работа

---

## Способ 3: API n8n (программно)

### Через curl:

```bash
# 1. Скачай workflow из GitHub
curl -o workflow.json https://raw.githubusercontent.com/kudinovt547-code/apart-guru-n8n-automation/main/apart-guru-content-factory-UPDATED.json

# 2. Импортируй в n8n через API
curl -X POST http://your-n8n-url/api/v1/workflows \
  -H "X-N8N-API-KEY: your-api-key" \
  -H "Content-Type: application/json" \
  -d @workflow.json
```

### Автообновление (webhook):

Создай workflow в n8n:
```
Webhook Trigger (GitHub push event)
    ↓
HTTP Request (скачать JSON из GitHub)
    ↓
Update Workflow (обновить существующий workflow)
```

---

## 🔄 Workflow для автообновления

Хочешь чтобы при пуше в GitHub workflow автоматически обновлялся в n8n?

### Создай в n8n:

```json
{
  "nodes": [
    {
      "name": "GitHub Webhook",
      "type": "n8n-nodes-base.webhook",
      "webhookId": "auto-update"
    },
    {
      "name": "Download from GitHub",
      "type": "n8n-nodes-base.httpRequest",
      "url": "https://raw.githubusercontent.com/kudinovt547-code/apart-guru-n8n-automation/main/apart-guru-content-factory-UPDATED.json"
    },
    {
      "name": "Update Workflow",
      "type": "n8n-nodes-base.n8n",
      "operation": "update",
      "workflowId": "ТВОЙ_WORKFLOW_ID"
    }
  ]
}
```

### В GitHub:

1. **Settings** → **Webhooks** → **Add webhook**
2. Payload URL: `https://your-n8n.com/webhook/auto-update`
3. Content type: `application/json`
4. Events: `push`
5. **Add webhook**

Теперь при каждом `git push` workflow обновится автоматически!

---

## 📝 Обновление workflow

### Локально изменил workflow?

```bash
cd ~/apart-guru-n8n-automation

# 1. Экспортируй из n8n обновлённый JSON
# 2. Замени файл apart-guru-content-factory-UPDATED.json
# 3. Закоммить и запушить:

git add apart-guru-content-factory-UPDATED.json
git commit -m "Update workflow: добавил новые вопросы для Threads"
git push origin main
```

### На других серверах n8n:

Просто сделай **Pull from Git** или импорт по ссылке — получишь обновлённую версию.

---

## 🔐 Безопасность

**ВАЖНО:** Не коммить в Git:
- API ключи
- Токены
- Пароли
- Channel IDs (если приватные)

В workflow замени на плейсхолдеры:
```json
"x-api-key": "YOUR_ANTHROPIC_API_KEY"
```

Реальные ключи храни в:
- **n8n Credentials** (зашифрованы)
- **Environment Variables**
- **Secrets Manager**

---

## 🎯 Рекомендуемый способ

**Для личного использования:**
→ Способ 1 (прямая ссылка) — быстро и просто

**Для команды/нескольких серверов:**
→ Способ 2 (GitHub Integration) — синхронизация и версионирование

**Для CI/CD:**
→ Способ 3 (API + webhook) — полная автоматизация

---

## 📦 Репозиторий

https://github.com/kudinovt547-code/apart-guru-n8n-automation

- **Смотреть workflow:** `apart-guru-content-factory-UPDATED.json`
- **Raw ссылка для импорта:** [кликабельная ссылка](https://raw.githubusercontent.com/kudinovt547-code/apart-guru-n8n-automation/main/apart-guru-content-factory-UPDATED.json)

---

## 🆘 Проблемы

**"Import failed":**
- Проверь что ссылка на **raw** файл (не на GitHub UI)
- Убедись что JSON валиден

**"Webhook не срабатывает":**
- Проверь что n8n доступен из интернета
- Webhook должен быть Active
- Проверь логи GitHub webhook deliveries

---

**Готово!** Теперь workflow всегда в Git и можно загружать из любого n8n! 🚀
