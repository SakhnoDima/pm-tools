# PM workbook: sheet reference

Generated from the workbook template (`.workbook_template.xlsx` in the repo root). Sheet names, labels and
dropdown values are quoted exactly as they appear in the workbook (Ukrainian); use them verbatim.

Contents:
[Conventions](#conventions) ·
[Overview](#overview) · [Lead Handoff](#lead-handoff) · [Discovery](#discovery) · [Estimate](#estimate) ·
[Roadmap](#roadmap) · [Backlog](#backlog) · [Access & Env](#access--env) · [Daily Report](#daily-report) ·
[Weekly Report](#weekly-report) · [Change Log](#change-log) · [Project Notes](#project-notes) ·
[How sheets connect](#how-sheets-connect)

## Conventions

| Look | Meaning |
|---|---|
| Yellow cell (`#FFF2CC`) | Filled by a person (the legend says "PM", but the "Who fills" notes below are more precise) |
| Grey row (`#EDEDED`) | Example of the format. Must be deleted before real work |
| White cell with a formula | Calculated. Never write into it |
| Dark blue row (`#1F3864`) | Table header |
| Light blue row (`#D9E1F2`) | Section title inside a sheet |
| Red cell (conditional) | Something required is missing (e.g. no demo plan) |

- Every sheet has a title in `A1` and a one-line purpose in `A2` (merged across the table).
- Dropdown cells accept only the listed values. Write them exactly, including case and punctuation.
- In A1 notation, quote sheet names with spaces or `&`: `'Lead Handoff'!B16`, `'Access & Env'!A7`.
- Tables grow downwards: a new record goes into the first empty row under the header (after the example row
  if it still exists).
- Grey example rows (text often starts with `Приклад:`) are not real data. Skip them when reading reports.
- Formula columns are not always extended down the table. When writing a new row into a table that has formula
  columns (e.g. `Estimate` H–J, `Roadmap` F, `Weekly Report` J), copy the formula from the row above if the
  target row has none.

---

## Overview

Project card, offer summary and table of contents. The entry point of the workbook.

**Who fills:** PM.

| Cell | Field | Type | Notes |
|---|---|---|---|
| A1 | `PM Workbook: [Назва проєкту]` | title | Replace `[Назва проєкту]` with the project name |
| **Картка проєкту** (row 4) | | | |
| B5 | Проєкт | yellow | Project name |
| B6 | Клієнт | formula `='Lead Handoff'!B6` | Do not edit. Fill `Lead Handoff`!B6 instead |
| B7 | Етап | yellow, dropdown | `Лід`, `Discovery`, `Оцінка`, `Офер`, `Контракт`, `В роботі`, `Підтримка`, `Закрито`, `Відмова`. Default `Лід` |
| B8 | PM | yellow | PM name |
| B9 | Старт | yellow | Date |
| B10 | Дедлайн | yellow | Date |
| **Посилання** (row 11) | | | |
| B12 | Upwork | yellow | Upwork job URL. The plugin reads the job link from here |
| B13 | Репозиторій | yellow | URL |
| B14 | Трекер (Jira / Linear) | yellow | URL |
| B15 | Канал комунікації | yellow | Slack / Upwork chat / email etc. |
| **Офер** (row 16) | | | |
| B17 | Тип контракту | yellow, dropdown | `Fixed Price`, `Hourly Rate` |
| B18 | Оцінка, год (In scope, з буфером) | formula `=Estimate!C7` | |
| B19 | Ціна оферу, $ | formula `=Estimate!C8` | |
| B20 | Зміни scope, $ (затверджені) | formula `='Change Log'!B5` | |
| B21 | Поточна вартість, $ | formula `=B19+B20` | |
| B22 | Дата відправки оферу | yellow | Date |
| B23 | Статус оферу | yellow, dropdown | `Готується`, `Відправлено`, `Переговори`, `Прийнято`, `Відхилено` |

Rows 30–40: table of contents (`Лист` / `Навіщо` / `Хто заповнює`). Rows 42–45: colour legend. Static text.

---

## Lead Handoff

What sales knows about the client and the project at handoff. Upwork data shows whether the client can pay and
is serious, before the first call. Filled once, updated when needed.

**Who fills:** Sales, before the first call. PM complements after the first call.
**Main target of Upwork intake.**

Layout: `A` = field, `B` = value (yellow), `C` = hint / source. Header in row 4.

| Cell | Field | Hint (column C) | Source for intake |
|---|---|---|---|
| **Про клієнта і проєкт** (row 5) | | | |
| B6 | Клієнт (компанія, контакт) | Хто він, сайт, LinkedIn | Job post / client profile |
| B7 | Проблема | Що болить своїми словами клієнта | Job post text, in the client's words |
| B8 | Що хоче отримати | Очікуваний результат | Job post text |
| B9 | Бюджет | Озвучений або з job post | Job post |
| B10 | Дедлайн | Жорсткий чи бажаний, чим зумовлений | Job post, if stated |
| B11 | Хто приймає рішення | ЛПР, хто ще впливає | Usually unknown before the call |
| B12 | Галузь / compliance | Fintech, healthcare; HIPAA, PCI DSS, GDPR тощо | Job post, if stated |
| B13 | Джерело ліда | Upwork / рекомендація / інше | `Upwork` for intake |
| B14 | Нотатки сейла | Враження, ризики, домовленості | Sales only, do not fill from Upwork |
| **Дані з Upwork** (row 15) | | | |
| B16 | Job post URL | | Same URL as `Overview`!B12 |
| B17 | Назва job post | | Job title |
| B18 | Тип контракту | Hourly / Fixed. Dropdown: `Fixed Price`, `Hourly Rate` | Job post |
| B19 | Бюджет або rate у job post | | Job post |
| B20 | Payment verified | Так / Ні | Client sidebar |
| B21 | Рейтинг клієнта | Зірки | Client sidebar |
| B22 | Кількість відгуків | | Client sidebar |
| B23 | Total spent | $ | Client sidebar |
| B24 | Hire rate | % | Client sidebar |
| B25 | Кількість наймів | | Client sidebar |
| B26 | Відкриті вакансії | Скільки job posts активні зараз | Client sidebar |
| B27 | Країна / таймзона | | Client sidebar |
| B28 | Member since | | Client sidebar |
| B29 | Proposals на job post | Конкуренція | "Activity on this job" |
| B30 | Interviewing | Скільки вже на співбесідах | "Activity on this job" |
| B31 | Invites sent | | "Activity on this job" |
| B32 | Connects витрачено | | Our proposal |
| B33 | Дата відправки proposal | | Our proposal |

---

## Discovery

Questions to clarify with the client, grouped by block. Status `Відкрите` is a gap in our understanding of the
project: before the offer there must be no open questions that affect the estimate.

**Who fills:** PM. Lead answers the blocks `Інтеграції`, `Дані`, `Compliance`.

Summary: `B4` = open questions (`=COUNTIF(D7:D500,"Відкрите")`), `D4` = open and affecting the estimate.

Header row 6, example row 7 (grey), questions from row 8.

| Col | Header | Type | Values |
|---|---|---|---|
| A | Блок | dropdown | `Бізнес-ціль`, `Користувачі`, `Інтеграції`, `Дані`, `Compliance`, `Критерії успіху`, `Інше` |
| B | Питання | text | Prefilled questions; add new ones below |
| C | Відповідь | yellow | |
| D | Статус | yellow, dropdown | `Відкрите`, `Відповіли`, `Не актуально`. Prefilled `Відкрите` |
| E | Впливає на оцінку | yellow, dropdown | `Так`, `Ні`. Prefilled `Так` |
| F | Хто відповів | yellow | |
| G | Дата | yellow | |

Prefilled question rows: `Бізнес-ціль` 8–12, `Користувачі` 13–16, `Інтеграції` 17–20, `Дані` 21–24,
`Compliance` 25–29, `Критерії успіху` 30–33.

---

## Estimate

Work breakdown (WBS) and estimate in hours. Scope lives only here (columns `Scope` and `Припущення`).
The offer price and the Roadmap come from here. Columns N–O hold a built-in glossary of the metrics.

**Who fills:** Lead + Dev: tasks and hours (Min / Likely / Max). PM: rate, buffer, Scope, the demo row.

Inputs and totals:

| Cell | Field | Type |
|---|---|---|
| C5 | Ставка, $/год | yellow (template: 40) |
| C6 | Буфер на ризики | yellow, fraction (0.15 = 15%). 10–15% for a clear project, 20–30% for a new domain or complex integrations |
| C7 | Разом In scope, год (з буфером) | formula: sum of `I` where `K` = `In`. Goes to `Overview`!B18 |
| C8 | Ціна оферу, $ | formula `=C7*C5`. Goes to `Overview`!B19 |
| F5 | PERT In scope, год | formula: sum of `H` where `K` = `In` (no buffer) |
| F6 | Out of scope, год | formula: sum of `I` where `K` = `Out` |
| F7 / F8 | Діапазон In scope Min / Max | formulas: sum of `E` / `G` where `K` = `In` |

Header row 10, example row 11 (grey), task rows 12–41 (yellow).

| Col | Header | Type | Notes |
|---|---|---|---|
| A | WBS ID | yellow | `1.1`, `1.2`… Demo row must be `0.1` |
| B | Етап / Epic | yellow | |
| C | Задача | yellow | |
| D | Роль | yellow, dropdown | `Backend`, `Frontend`, `Mobile`, `DevOps`, `QA`, `Design`, `PM`, `AI/ML` |
| E / F / G | Min / Likely / Max, год | yellow | Optimistic / most likely / pessimistic but realistic |
| H | PERT, год | formula | `(Min + 4×Likely + Max) / 6`, empty unless all three are filled |
| I | З буфером, год | formula | `PERT × (1 + C6)` |
| J | Вартість, $ | formula | `I × C5` |
| K | Scope | yellow, dropdown | `In` (in the offer and the totals) / `Out` (discussed, not doing; recorded to avoid disputes) |
| L | Припущення / коментар | yellow | What the estimate relies on. A broken assumption is a reason for a `Change Log` entry |

Rule from the glossary: a demo row with WBS `0.1` ("Демо / презентації") is mandatory, one demo per milestone.

---

## Roadmap

Stages and milestones built from the WBS. Dependencies show what blocks a stage. A paid milestone ties money to a
result (Fixed Price). A demo is mandatory for every milestone and its plan is filled before the stage starts.
A stage is closed when the client is ready for the next step: the result is accepted or they ask "what's next".

**Who fills:** PM. Lead checks dependencies and dates.

Header row 4, example row 5 (grey), stages from row 6.

| Col | Header | Type | Values / notes |
|---|---|---|---|
| A | Етап / Milestone | text | `M1: …` |
| B | WBS ID | text | Range from `Estimate`, e.g. `1.1–1.4` |
| C | Результат (що отримує клієнт) | text | |
| D / E | Початок / Кінець | date | |
| F | Тривалість, днів | formula | `NETWORKDAYS(D, E)` |
| G | Залежить від | text | |
| H | Відповідальний | text | |
| I | Статус | dropdown | `Заплановано`, `В роботі`, `На прийомі`, `Прийнято`, `Заблоковано` |
| J | Оплата за milestone, $ | number | |
| K | Демо: що показуємо і як | text | **Red** if the stage exists (A filled) and K is empty |
| L | Дата демо | date | |
| M | Результат демо | dropdown | `Не заплановано`, `Заплановано`, `Прийнято`, `Клієнт питає «що далі»`, `Є зауваження`, `Перенесено` |

---

## Backlog

Tasks for the team, each linked to a WBS ID to see how much of the estimate is used. If tasks live in Jira, keep
only the link and plan/fact hours here. Every `Feature` needs a demo decision. A feature is closed for the
client when it was shown at a demo, not when its status is `Done`.

**Who fills:** PM creates tasks. Dev updates status and actual hours. Lead adds technical tasks.

Summary row 4: `B4` estimate total, `D4` actual total, `F4` actual / estimate.

Header row 6, example row 7 (grey), tasks from row 8.

| Col | Header | Type | Values / notes |
|---|---|---|---|
| A | ID | text | `B-1`, `B-2`… |
| B | WBS ID | text | From `Estimate` |
| C | Задача | text | |
| D | Тип | dropdown | `Feature`, `Bug`, `Tech task`, `Research` |
| E | Пріоритет | dropdown | `Critical`, `High`, `Medium`, `Low` |
| F | Статус | dropdown | `To Do`, `In Progress`, `Review`, `QA`, `Done`, `Blocked` |
| G | Виконавець | text | |
| H | Спринт | text | |
| I | Оцінка, год | number | |
| J | Факт, год | number | |
| K | Посилання | URL | Jira / Linear |
| L | На демо | dropdown | `Так`, `Ні`. **Red** if `D` = `Feature` and L is empty |
| M | Показано на демо | date | |

---

## Access & Env

Mandatory checklist at the start and when the team changes. **No passwords, keys or tokens here**, only where
they are stored (password manager, vault).

**Who fills:** PM requests access from the client. Lead / Dev confirm they received it.

`B4` = not received yet (count of `Запитано` + `Не запитано`).

Header row 6. Rows 7–22 are a real prefilled checklist (not examples): Репозиторій, CI/CD, Dev / Staging /
Production середовище, Хмарна консоль, База даних, Трекер задач, Канал комунікації, Дизайн (Figma),
API ключі сторонніх сервісів, Sandbox платіжного шлюзу / EHR, Моніторинг і логи, Домен і DNS,
Менеджер паролів / vault, BAA / DPA підписані.

| Col | Header | Type | Values |
|---|---|---|---|
| A | Ресурс | text | |
| B | Тип | text | Code, DevOps, Environment, Cloud, Data, Tool, Integration, Infra, Security, Compliance |
| C | Середовище | dropdown | `Dev`, `Stage`, `Prod`, `—` |
| D | URL | text | |
| E | Хто надає | text | |
| F | Хто має доступ | text | |
| G | Статус | dropdown | `Не запитано`, `Запитано`, `Отримано`, `Не потрібно`, `Відкликано` |
| H | Дата | date | |
| I | Примітка | text | Where the secret is stored, never the secret itself |

---

## Daily Report

Used when the client asks for daily updates. One row per person per day. Blockers that live longer than a day
move to `Weekly Report` as risks. **Raw input for daily client updates.**

**Who fills:** each Dev fills their own row. The sheet holds only developers' updates.
The daily client update is not stored here: `/client-daily-update` reads the rows for the day and drafts one short
message for the PM, who sends it.

Header row 4, example row 5 (grey), records from row 6.

| Col | Header | Notes |
|---|---|---|
| A | Дата | |
| B | Хто | Developer |
| C | Зроблено | Done today |
| D | План | Plan for the next day |
| E | Message to the client | Filled by the Dev |
| F | Год | Hours |
| G | Посилання (PR, задачі) | `B-1, PR #12` |

---

## Weekly Report

Weekly report to the client based on the work actually done. One row per week. The column "Що потрібно від
клієнта" is the most important one: it makes blockers visible to the person who can remove them.

**Who fills:** PM, based on `Daily Report` and `Backlog`.

Header row 4, example row 5 (grey), weeks from row 6.

| Col | Header | Type | Notes |
|---|---|---|---|
| A / B | Тиждень з / Тиждень по | date | |
| C | Статус (RAG) | dropdown | `Зелений`, `Жовтий`, `Червоний` |
| D | Що зробили | text | |
| E | Закриті фічі | text | Closed = shown at a demo (see `Backlog`) |
| F | План на наступний тиждень | text | |
| G | Ризики | text | Includes blockers older than a day from `Daily Report` |
| H | Що потрібно від клієнта | text | Concrete asks with deadlines |
| I | Год за тиждень | number | |
| J | Год всього | formula | Running total of `I` |
| K | Відправлено | date | When the report was sent |

---

## Change Log

Every scope change after the offer: what changed and what it costs in hours, money and days. Without it the
estimate gets stale and a deadline shift cannot be explained to the client.

**Who fills:** PM + Lead estimates the impact in hours. Sales approves if the change affects the contract.

Totals: `B4` approved hours, `B5` approved $ (goes to `Overview`!B20).

Header row 7, example row 8 (grey), changes from row 9.

| Col | Header | Type | Values / notes |
|---|---|---|---|
| A | CR ID | text | `CR-1`, `CR-2`… |
| B | Дата | date | |
| C | Запит | text | |
| D | Ініціатор | text | |
| E | Вплив, год | number | |
| F | Вплив, $ | formula | `E × Estimate!C5`, prefilled down to row 207 |
| G | Вплив на дедлайн, днів | number | |
| H | Рішення | dropdown | `На розгляді`, `Затверджено`, `Відхилено`, `Відкладено` |
| I | Дата рішення | date | |
| J | WBS ID | text | |

---

## Project Notes

PM log for the whole project: calls, decisions, questions, ideas. Decisions are recorded with a date so that a
month later it is clear who agreed to what and why.

**Who fills:** PM. Intake adds a note here.

Header row 4, example row 5 (grey), records from row 6.

| Col | Header | Type | Values |
|---|---|---|---|
| A | Дата | date | |
| B | Тип | dropdown | `Дзвінок`, `Рішення`, `Питання`, `Ризик`, `Ідея`, `Інше` |
| C | Учасники | text | |
| D | Зміст | text | |
| E | Рішення / Action items | text | |
| F | Відповідальний | text | |
| G | Дедлайн | date | |
| H | Статус | dropdown | `Відкрите`, `Виконано`, `Скасовано` |

---

## How sheets connect

```
Lead Handoff!B6 ──────────────► Overview!B6 (Клієнт)
Estimate!C7 (hours w/ buffer) ─► Overview!B18
Estimate!C8 (offer price) ─────► Overview!B19 ─┐
Change Log!B5 (approved $) ────► Overview!B20 ─┴► Overview!B21 (current value)
Estimate!C5 (rate) ────────────► Change Log!F (impact $)
Estimate WBS IDs ──────────────► Roadmap!B, Backlog!B, Change Log!J
Daily Report (blockers > 1 day) ► Weekly Report!G (risks)
Daily Report + Backlog ────────► Weekly Report
Daily Report (rows for one day) ► /client-daily-update ─► draft for the PM (not written back)
```
