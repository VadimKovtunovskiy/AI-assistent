# ✨ ИИ-ассистент для салона красоты

ссылка на поект @Absolute_beautyBot

![Скриншот №1](https://github.com/VadimKovtunovskiy/AI-assistent/blob/main/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-05-2025%20194650.jpg?raw=true)

Умный чат-бот, который ведёт осмысленную переписку с клиентами, отвечает на часто задаваемые вопросы из базы знаний и бронирует визиты прямо в Google Календаре.  
Построен на связке **Qwen + GPT-4o** (семантическая память / генерация) и **Suvvy.ai** (NLU-платформа).

---

## 📌 Основные функции

- **Диалог на естественном языке** – уточняет предпочтения клиента, рекомендует услуги и уход.  
- **Ответы из базы знаний** – цены, длительность процедур, акции — всё подтягивается автоматически.  
- **Онлайн-запись** – предлагает свободные слоты, создаёт событие в Google Calendar и шлёт инвайт.  
- **Мультиязычность** – русский и английский «из коробки», легко добавить новые языки.  
- **Аналитика** – конверсия диалог → запись, средняя длина сессии, топ-вопросы.  

---

## 🏗️ Технологический стек

| Слой | Инструменты |
|------|-------------|
| NLU / маршрутизация | **Suvvy.ai** |
| Семантическая база | **Qwen** |
| Генерация ответов | **GPT-4o** |
| Бэкенд-оркестратор | **FastAPI**, **PostgreSQL**, **Redis** |
| Интеграции | **Google Calendar API**, **Webhooks** |
| Деплой | Docker, Kubernetes / Cloud Run |

---

## 🔍 Архитектура (Mermaid)

```mermaid
graph LR
  subgraph Client
    A(WhatsApp / Telegram / Web Chat)
  end
  subgraph Suvvy.ai
    B(NLU Engine)
  end
  subgraph Backend
    C(FastAPI Orchestrator)
    D(Qwen Vector DB)
    E(GPT-4o Gateway)
    F(Google Calendar Service)
  end
  A --> B
  B -->|intent/slots| C
  C --> D
  D --> E
  E -->|response| C
  C --> F
  F -->|invite| C
  C --> B
  B --> A
