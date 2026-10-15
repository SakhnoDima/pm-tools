# PM workbook: sheet reference

This file describes the **meaning** of the workbook's sheets and fields. It does not store cell positions:
the template is edited by managers, so rows and columns move. Always find fields in the live sheet by their
label, as described in [Finding fields](#finding-fields).

Sheet names, labels and dropdown values are quoted exactly as in the workbook (Ukrainian).

Contents:
[Finding fields](#finding-fields) · [Conventions](#conventions) ·
[Overview](#overview) · [Lead Handoff](#lead-handoff) · [Discovery](#discovery) · [Estimate](#estimate) ·
[Roadmap](#roadmap) · [Backlog](#backlog) · [Access & Env](#access--env) · [Daily Report](#daily-report) ·
[Weekly Report](#weekly-report) · [Change Log](#change-log) · [Project Notes](#project-notes) ·
[How sheets connect](#how-sheets-connect)

## Finding fields

Read the sheet first (`get_values` on the whole sheet, e.g. `'Lead Handoff'!A1:Z200`), then locate fields:

- **Form sheets** (`Overview`, `Lead Handoff`): the label is in column A, the value is in column B
  (`Lead Handoff` also has a hint in column C). Find the row whose column A equals the label exactly.
- **Table sheets** (all others): find the header row, the one that contains the column headers listed below.
  Locate each column by its header text. Records are the rows below the header.
- **Summary cells** at the top of table sheets (counts, totals, inputs): the label is in one cell and the value is
  in the cell to its right.
- **Label not found:** do not guess a position. Tell the PM which field is missing in this workbook.
- **Unknown labels or headers** (added by managers, not described here): you may read them, but say they are not
  described in the plugin, and do not infer their meaning beyond the label text.
- To tell formulas from values, read with the formula render option (cells starting with `=` are formulas).

## Conventions

| Look | Meaning |
|---|---|
| Yellow cell | Filled by the person responsible for the sheet (see "Who fills" for each sheet) |
| Grey row | Example of the format, not real data. Skip it when reading |
| White cell with a formula | Calculated. Never write into it |
| Dark blue row | Table header |
| Light blue row | Section title inside a form sheet |
| Red cell (conditional) | Something required is missing (e.g. no demo plan) |

- Each sheet starts with a title and a one-line purpose above the table.
- Dropdown cells accept only listed values. The values below are from the template; if the live cell's validation
  differs, the live sheet wins.
- In ranges, quote sheet names with spaces or `&`: `'Lead Handoff'!A1:C200`, `'Access & Env'!A1:I200`.
- A new record goes into the first empty row under the header (after the grey example row if it is still there).
- Formula columns are not always extended down a table. When writing a new row into a table with formula
  columns, copy the formula from the row above if the new row has none.

---

## Overview

Project card, offer summary and table of contents. The entry point of the workbook. **Form sheet.**

**Who fills:** PM.

Title cell: the first cell of the sheet, `PM Workbook: [Назва проєкту]`. Replace `[Назва проєкту]` with the
project name.

| Label (column A) | Meaning | Type |
|---|---|---|
| **Картка проєкту** | section | |
| Проєкт | Project name | text |
| Клієнт | Client | formula from `Lead Handoff` → `Клієнт (компанія, контакт)`. Do not edit here |
| Етап | Project stage | dropdown: `Лід`, `Discovery`, `Оцінка`, `Офер`, `Контракт`, `В роботі`, `Підтримка`, `Закрито`, `Відмова` |
| PM | PM name | text |
| Старт | Start date | date |
| Дедлайн | Project deadline | date |
| **Посилання** | section | |
| Upwork | Upwork job URL. The plugin reads the job link from here | URL |
| Репозиторій | Repository | URL |
| Трекер (Jira / Linear) | Task tracker | URL |
| Канал комунікації | Slack / Upwork chat / email etc. | text |
| **Офер** | section | |
| Тип контракту | Contract type | dropdown: `Fixed Price`, `Hourly Rate` |
| Оцінка, год (In scope, з буфером) | Hours in the offer | formula from `Estimate` |
| Ціна оферу, $ | Offer price | formula from `Estimate` |
| Зміни scope, $ (затверджені) | Approved scope changes | formula from `Change Log` |
| Поточна вартість, $ | Offer price + approved changes | formula |
| Дата відправки оферу | When the offer was sent | date |
| Статус оферу | Offer status | dropdown: `Готується`, `Відправлено`, `Переговори`, `Прийнято`, `Відхилено` |

Below the card: table of contents (`Лист` / `Навіщо` / `Хто заповнює`) and the colour legend. Static text.

---

## Lead Handoff

What sales knows about the client and the project at handoff. Upwork data shows whether the client can pay and
is serious, before the first call. Filled once, updated when needed. **Form sheet**: `Поле` (A), `Значення` (B),
`Примітка / звідки` (C).

**Who fills:** Sales, before the first call. PM complements after the first call.
The section `Дослідження клієнта` is filled during client research (business analysis), by the PM or with Claude.
**Main target of Upwork intake** (sections `Про клієнта і проєкт` and `Дані з Upwork`).

| Label (column A) | Meaning / hint | Source for intake |
|---|---|---|
| **Про клієнта і проєкт** | section | |
| Клієнт (компанія, контакт) | Who the client is, site, LinkedIn | Job post / client profile |
| Проблема | What hurts, in the client's words | Job post text |
| Що хоче отримати | Expected result | Job post text |
| Бюджет | Stated or from the job post | Job post |
| Дедлайн | Hard or desired, and why | Job post, if stated |
| Хто приймає рішення | Decision maker, who else influences | People, not the job post |
| Галузь / compliance | Fintech, healthcare; HIPAA, PCI DSS, GDPR etc. | Job post, if stated |
| Джерело ліда | Upwork / referral / other | `Upwork` for intake |
| Нотатки сейла | Impressions, risks, agreements | Sales only |
| **Дані з Upwork** | section | |
| Job post URL | Same URL as `Overview` → `Upwork` | The job link |
| Назва job post | Job title | Job post |
| Тип контракту | dropdown: `Fixed Price`, `Hourly Rate` | Job post |
| Бюджет або rate у job post | | Job post |
| Payment verified | `Так` / `Ні` | Client sidebar |
| Рейтинг клієнта | Stars | Client sidebar |
| Кількість відгуків | | Client sidebar |
| Total spent | $ | Client sidebar |
| Hire rate | % | Client sidebar |
| Кількість наймів | | Client sidebar |
| Відкриті вакансії | How many job posts are active now | Client sidebar |
| Країна / таймзона | | Client sidebar |
| Member since | | Client sidebar |
| Proposals на job post | Competition | "Activity on this job" |
| Interviewing | How many are already interviewing | "Activity on this job" |
| Invites sent | | "Activity on this job" |
| Connects витрачено | | Our proposal, people |
| Дата відправки proposal | | Our proposal, people |
| **Дослідження клієнта** | section: who the client really is, for business analysis | |
| Назва компанії | Official company name. Main search key, but ambiguous on its own. Often hidden on Upwork: clarified in the chat or the contract | Chat / contract, not the job post |
| Сайт компанії | Company domain. The most reliable anchor: unique, and the rest (LinkedIn, product, social) is found from it | Research |
| LinkedIn компанії | Company page URL. Gives size, industry, company age, and confirms it is the right company | Research |
| Контактна особа | Name of the person we talk to | Chat / contract |
| Роль контакту | Founder, CTO, Product Manager etc. Defines the tone and content of the conversation | Research / chat |
| LinkedIn контакту | Profile URL. More precise than a name search, which returns namesakes | Research |
| Інші посилання | Product, App Store, GitHub, Crunchbase etc. Extra sources and disambiguators against false matches | Research |
| Статус дослідження | So research is not repeated and gaps are visible. Dropdown: `Не почато`, `Готово`, `Не знайдено` (template default `Не почато`) | Research |
| Дата дослідження | When the research was last updated, `yyyy-mm-dd`. Shows how fresh the data is | Research |

---

## Discovery

Questions to clarify with the client, grouped by block. Status `Відкрите` is a gap in our understanding of the
project: before the offer there must be no open questions that affect the estimate. **Table sheet.**

**Who fills:** PM. Lead answers the blocks `Інтеграції`, `Дані`, `Compliance`.

Summary cells: `Відкритих питань` (count of open questions), `з них впливають на оцінку`.

| Header | Meaning | Type |
|---|---|---|
| Блок | Question block | dropdown: `Бізнес-ціль`, `Користувачі`, `Інтеграції`, `Дані`, `Compliance`, `Критерії успіху`, `Інше` |
| Питання | The question. The template comes with prefilled questions per block; add new ones below | text |
| Відповідь | Answer | text |
| Статус | | dropdown: `Відкрите`, `Відповіли`, `Не актуально` (prefilled `Відкрите`) |
| Впливає на оцінку | Does the answer change the estimate | dropdown: `Так`, `Ні` (prefilled `Так`) |
| Хто відповів | | text |
| Дата | | date |

---

## Estimate

Work breakdown (WBS) and estimate in hours. Scope lives only here (`Scope` and `Припущення`). The offer price
and the Roadmap come from here. The sheet has a built-in glossary of the metrics on the right. **Table sheet.**

**Who fills:** Lead + Dev: tasks and hours (Min / Likely / Max). PM: rate, buffer, Scope, the demo row.

Summary cells:

| Label | Meaning |
|---|---|
| Ставка, $/год | Hourly rate for the client (input, yellow) |
| Буфер на ризики | Risk buffer as a fraction, 0.15 = 15% (input, yellow). 10–15% for a clear project, 20–30% for a new domain or complex integrations |
| Разом In scope, год (з буфером) | Sum of `З буфером` for `In` tasks. Goes to `Overview` |
| Ціна оферу, $ | `Разом In scope` × rate. Goes to `Overview` |
| PERT In scope, год | Sum without buffer; the difference shows the hours reserved for risks |
| Out of scope, год | Work consciously left out: next phase or upsell candidates |
| Діапазон In scope, год (Min) / (Max) | Best / worst case for the project |

| Header | Meaning | Type |
|---|---|---|
| WBS ID | `1.1`, `1.2`… The demo row is `0.1` | text |
| Етап / Epic | | text |
| Задача | | text |
| Роль | | dropdown: `Backend`, `Frontend`, `Mobile`, `DevOps`, `QA`, `Design`, `PM`, `AI/ML` |
| Min, год / Likely, год / Max, год | Optimistic / most likely / pessimistic but realistic | numbers |
| PERT, год | `(Min + 4×Likely + Max) / 6` | formula |
| З буфером, год | `PERT × (1 + buffer)` | formula |
| Вартість, $ | `З буфером × rate` | formula |
| Scope | `In` = in the offer and the totals; `Out` = discussed, not doing, recorded to avoid disputes | dropdown |
| Припущення / коментар | What the estimate relies on. A broken assumption is a reason for a `Change Log` entry | text |

Rule from the glossary: a demo row with WBS `0.1` ("Демо / презентації") is mandatory, one demo per milestone.

---

## Roadmap

Stages and milestones built from the WBS. Dependencies show what blocks a stage. A paid milestone ties money to a
result (Fixed Price). A demo is mandatory for every milestone and its plan is filled before the stage starts.
A stage is closed when the client is ready for the next step: the result is accepted or they ask "what's next".
**Table sheet.**

**Who fills:** PM. Lead checks dependencies and dates.

| Header | Meaning | Type |
|---|---|---|
| Етап / Milestone | `M1: …` | text |
| WBS ID | Range from `Estimate`, e.g. `1.1–1.4` | text |
| Результат (що отримує клієнт) | | text |
| Початок / Кінець | | dates |
| Тривалість, днів | Working days between start and end | formula |
| Залежить від | | text |
| Відповідальний | | text |
| Статус | | dropdown: `Заплановано`, `В роботі`, `На прийомі`, `Прийнято`, `Заблоковано` |
| Оплата за milestone, $ | | number |
| Демо: що показуємо і як | Red when the stage exists and this is empty | text |
| Дата демо | | date |
| Результат демо | | dropdown: `Не заплановано`, `Заплановано`, `Прийнято`, `Клієнт питає «що далі»`, `Є зауваження`, `Перенесено` |

---

## Backlog

Tasks for the team, each linked to a WBS ID to see how much of the estimate is used. If tasks live in Jira, keep
only the link and plan/fact hours here. Every `Feature` needs a demo decision. A feature is closed for the
client when it was shown at a demo, not when its status is `Done`. **Table sheet.**

**Who fills:** PM creates tasks. Dev updates status and actual hours. Lead adds technical tasks.

Summary cells: `Оцінка, год`, `Факт, год`, `Факт / оцінка`.

| Header | Meaning | Type |
|---|---|---|
| ID | `B-1`, `B-2`… | text |
| WBS ID | From `Estimate` | text |
| Задача | | text |
| Тип | | dropdown: `Feature`, `Bug`, `Tech task`, `Research` |
| Пріоритет | | dropdown: `Critical`, `High`, `Medium`, `Low` |
| Статус | | dropdown: `To Do`, `In Progress`, `Review`, `QA`, `Done`, `Blocked` |
| Виконавець | | text |
| Спринт | | text |
| Оцінка, год / Факт, год | Plan / actual hours | numbers |
| Посилання | Jira / Linear | URL |
| На демо | Red when `Тип` = `Feature` and this is empty | dropdown: `Так`, `Ні` |
| Показано на демо | | date |

---

## Access & Env

Mandatory checklist at the start and when the team changes. **No passwords, keys or tokens here**, only where
they are stored (password manager, vault). **Table sheet**; the template comes with a real prefilled list of
resources (repository, CI/CD, environments, cloud, database, tools, integrations, monitoring, DNS, vault,
BAA / DPA). These rows are not examples.

**Who fills:** PM requests access from the client. Lead / Dev confirm they received it.

Summary cell: `Не отримано` (count of `Запитано` + `Не запитано`).

| Header | Meaning | Type |
|---|---|---|
| Ресурс | | text |
| Тип | Code, DevOps, Environment, Cloud, Data, Tool, Integration, Infra, Security, Compliance | text |
| Середовище | | dropdown: `Dev`, `Stage`, `Prod`, `—` |
| URL | | text |
| Хто надає / Хто має доступ | | text |
| Статус | | dropdown: `Не запитано`, `Запитано`, `Отримано`, `Не потрібно`, `Відкликано` |
| Дата | | date |
| Примітка | Where the secret is stored, never the secret itself | text |

---

## Daily Report

Used when the client asks for daily updates. One row per person per day. Blockers that live longer than a day
move to `Weekly Report` as risks. **Table sheet. Raw input for daily client updates.**

**Who fills:** each Dev fills their own row. The sheet holds only developers' updates.
The daily client update is not stored here: `/client-daily-update` reads the rows for the day and drafts one short
message for the PM, who sends it.

| Header | Meaning |
|---|---|
| Дата | |
| Хто | Developer |
| Зроблено | Done today |
| План | Plan for the next day |
| Message to the client | Filled by the Dev |
| Год | Hours |
| Посилання (PR, задачі) | e.g. `B-1, PR #12` |

---

## Weekly Report

Weekly report to the client based on the work actually done. One row per week. "Що потрібно від клієнта" is the
most important column: it makes blockers visible to the person who can remove them. **Table sheet.**

**Who fills:** PM, based on `Daily Report` and `Backlog`.

| Header | Meaning | Type |
|---|---|---|
| Тиждень з / Тиждень по | | dates |
| Статус (RAG) | | dropdown: `Зелений`, `Жовтий`, `Червоний` |
| Що зробили | | text |
| Закриті фічі | Closed = shown at a demo (see `Backlog`) | text |
| План на наступний тиждень | | text |
| Ризики | Includes blockers older than a day from `Daily Report` | text |
| Що потрібно від клієнта | Concrete asks with deadlines | text |
| Год за тиждень | | number |
| Год всього | Running total of `Год за тиждень` | formula |
| Відправлено | When the report was sent | date |

---

## Change Log

Every scope change after the offer: what changed and what it costs in hours, money and days. Without it the
estimate gets stale and a deadline shift cannot be explained to the client. **Table sheet.**

**Who fills:** PM + Lead estimates the impact in hours. Sales approves if the change affects the contract.

Summary cells: `Затверджено, год`, `Затверджено, $` (goes to `Overview`).

| Header | Meaning | Type |
|---|---|---|
| CR ID | `CR-1`, `CR-2`… | text |
| Дата | | date |
| Запит | | text |
| Ініціатор | | text |
| Вплив, год | | number |
| Вплив, $ | `Вплив, год × Estimate rate` | formula |
| Вплив на дедлайн, днів | | number |
| Рішення | | dropdown: `На розгляді`, `Затверджено`, `Відхилено`, `Відкладено` |
| Дата рішення | | date |
| WBS ID | | text |

---

## Project Notes

PM log for the whole project: calls, decisions, questions, ideas. Decisions are recorded with a date so that a
month later it is clear who agreed to what and why. **Table sheet.**

**Who fills:** PM.

| Header | Meaning | Type |
|---|---|---|
| Дата | | date |
| Тип | | dropdown: `Дзвінок`, `Рішення`, `Питання`, `Ризик`, `Ідея`, `Інше` |
| Учасники | | text |
| Зміст | | text |
| Рішення / Action items | | text |
| Відповідальний | | text |
| Дедлайн | | date |
| Статус | | dropdown: `Відкрите`, `Виконано`, `Скасовано` |

---

## How sheets connect

```
Lead Handoff "Клієнт (компанія, контакт)" ──► Overview "Клієнт"
Estimate "Разом In scope, год (з буфером)" ─► Overview "Оцінка, год (In scope, з буфером)"
Estimate "Ціна оферу, $" ───────────────────► Overview "Ціна оферу, $" ─┐
Change Log "Затверджено, $" ────────────────► Overview "Зміни scope, $" ┴► Overview "Поточна вартість, $"
Estimate "Ставка, $/год" ───────────────────► Change Log "Вплив, $"
Estimate WBS IDs ───────────────────────────► Roadmap, Backlog, Change Log "WBS ID"
Daily Report (blockers > 1 day) ────────────► Weekly Report "Ризики"
Daily Report + Backlog ─────────────────────► Weekly Report
Daily Report (rows for one day) ────────────► /client-daily-update ─► draft for the PM (not written back)
```
