---
name: info
description: >
  Explains the workbook-assistant plugin to the PM: what it does, which commands and skills it has, when to use
  each one, what to set up before first use and what the plugin never does. Use when the user asks what the
  plugin can do, how to use it, which commands exist or where to start, or asks about one of its commands.
  Run as /info, optionally with a command or skill name (/info bi-analys).
  Ukrainian triggers: "що вміє плагін", "як користуватись плагіном", "які є команди", "допомога по плагіну",
  "з чого почати", "як працює /intake", "як працює /bi-analys", "workbook-assistant".
argument-hint: "[command or skill name]"
---

# /info

Question: $ARGUMENTS

Answer in Ukrainian, using the guide below. Do not call any tools: this skill only explains.

- No question, or a general one ("що вміє плагін?") → show the whole guide.
- A question about one command or skill → answer only about it: what it does, when to use it, what it needs
  as input, what the PM gets back. Do not repeat the whole guide.
- A question about something the plugin does not do → say so plainly. Do not promise features that are not
  listed here.

## Guide

**workbook-assistant: помічник PM для роботи з воркбуком проєкту**

Воркбук — це Google Sheet на проєкт, створений із шаблону; кожен документ на своєму аркуші. Головне для роботи
з плагіном — посилання на воркбук. Виняток — `/intake`: вона створює воркбук, тож їй потрібне посилання на джобу.

**Команди (запускаєш сам)**

| Команда | Коли | Що отримаєш |
|---|---|---|
| `/intake <посилання на Upwork-джобу>` | Новий лід | Зведення джоби на підтвердження → новий воркбук із шаблону → заповнені `Overview` і `Lead Handoff` → список того, що лишилося заповнити і ким |
| `/bi-analys <посилання на воркбук>` | Після intake, перед дзвінком чи proposal | Google Doc з бізнес-аналізом клієнта (кожне твердження з міткою Факт / Оцінка / Гіпотеза); після твого ОК підтверджені факти потрапляють у `Lead Handoff` |
| `/info [команда]` | Коли треба нагадати, що вміє плагін | Ця довідка або пояснення однієї команди |

**Підказки (вмикаються самі, коли ти про це питаєш)**

- **pm-workbook**: «де у воркбуці…», «як заповнити аркуш…», «хто заповнює…»
- **client-tone**: «напиши клієнту…», «відповідь замовнику…». Дає чернетку англійською у твоєму стилі.
- **upwork-intake**: «розбери вакансію» або текст джоби, вставлений у чат.

**Перед першим використанням**

1. Підключи конектори плагіна `google-sheets` і `google-drive` (вкладка Connectors → Connect → вхід у Google).
2. Встанови Claude in Chrome і залогінься в Upwork у своєму Chrome.
3. Перевір, що маєш доступ до шаблону воркбуку на Drive.

**Що варто знати**

- Плагін **нічого не надсилає клієнту**, а лише показує тобі чернетку.
- У воркбук нічого не пишеться без твого підтвердження.
- Якщо браузер або конектор недоступні, плагін так і скаже і попросить вставити дані вручну.
- Якщо поля немає в шаблоні, плагін скаже про це, а не вгадуватиме.

**З чого почати:** `/intake <посилання на джобу>`.
