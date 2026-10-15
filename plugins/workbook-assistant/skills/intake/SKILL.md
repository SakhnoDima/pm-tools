---
name: intake
description: >
  Start a new project from an Upwork job: read the job in the PM's Chrome, create the project's PM workbook
  from the template and fill the Overview and Lead Handoff sheets. Run by the PM as /intake <upwork-job-url>.
argument-hint: <upwork-job-url>
disable-model-invocation: true
---

# /intake

Upwork job URL: $ARGUMENTS

If the URL is empty or is not an `upwork.com` job link, ask the PM for the job link and stop.

Use the skills `upwork-intake` (what to read and how) and `pm-workbook` (the workbook structure,
[sheets.md](../pm-workbook/references/sheets.md)). Follow their rules.

## Steps

### 1. Read the job

Open the URL in the PM's Chrome with Claude in Chrome and extract the fields listed in `upwork-intake`.
If the browser is unavailable or Upwork is not logged in, follow the fallback in `upwork-intake`.

### 2. Confirm with the PM

Show a short summary: job title, contract type and budget, client country, key client stats, and the list of
fields that were not found. Propose the workbook name `PM Workbook: <short project name>` (from the job title).
Wait for the PM's OK or corrections before creating anything.

### 3. Create the workbook

Copy the template with the **google-drive** connector from this plugin (`copy_file`):

- Template file ID: `16qpyCn28FPPqV93rbRQ96-mXrH9ncZQU7itjLoP-LT8`
- Title: the agreed workbook name

Copying keeps formatting, dropdowns, formulas and conditional formats. Do not build the workbook from scratch.
If the connector is not connected or the copy fails, tell the PM what failed and stop: do not fill the
template itself.

### 4. Fill Overview and Lead Handoff

Write with the **google-sheets** connector from this plugin (`update_values`) into the **new** workbook only.

Write values as **RAW** (not user-entered), so that text from Upwork can never turn into a formula.
Dropdown cells take only their exact values.

First read both sheets of the new workbook (`'Overview'!A1:C200`, `'Lead Handoff'!A1:C200`) and find each
field's row by its label in column A, as described in
[Finding fields](../pm-workbook/references/sheets.md#finding-fields). The value goes into column B of that row.
If a label is not found, skip that field and list it in the report as "missing in the workbook".

`Overview`:

| Label | Value |
|---|---|
| title cell (first cell, `PM Workbook: [Назва проєкту]`) | `PM Workbook: <short project name>` |
| Проєкт | Short project name |
| Upwork | The Upwork job URL |
| Тип контракту | `Fixed Price` or `Hourly Rate` |

Leave `Етап` (`Лід`), `PM`, dates and other links as they are. `Клієнт` is a formula, do not touch it.

`Lead Handoff`:

| Label | Value |
|---|---|
| Клієнт (компанія, контакт) | Client company / contact, if shown |
| Проблема | Problem, in the client's words |
| Що хоче отримати | Expected result |
| Бюджет | Budget, as stated |
| Дедлайн | Deadline, if stated, with its reason |
| Галузь / compliance | Industry / compliance, if mentioned |
| Джерело ліда | `Upwork` |
| Job post URL | The Upwork job URL |
| Назва job post | Job title |
| Тип контракту | `Fixed Price` or `Hourly Rate` |
| Бюджет або rate у job post | Budget or hourly range |
| Payment verified | `Так` / `Ні` |
| Рейтинг клієнта, Кількість відгуків, Total spent, Hire rate, Кількість наймів, Відкриті вакансії, Країна / таймзона, Member since | Client stats |
| Proposals на job post, Interviewing, Invites sent | Activity on this job |

Do not fill `Хто приймає рішення`, `Нотатки сейла`, `Connects витрачено`, `Дата відправки proposal`: they come
from people, not from the job page. Leave not-found values empty.

### 5. Report

Reply with:
- the link to the new workbook;
- what was filled, in a short list;
- what stayed empty and who should fill it (from the "Who fills" notes in `sheets.md`).

Do not contact the client and do not apply to the job.
