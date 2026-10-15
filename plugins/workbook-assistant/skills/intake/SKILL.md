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

`Overview`:

| Cell | Value |
|---|---|
| A1 | `PM Workbook: <short project name>` |
| B5 | Short project name |
| B12 | The Upwork job URL |
| B17 | `Fixed Price` or `Hourly Rate` |

Leave `B7` (`Лід`), the PM name, dates and other links as they are. `B6` is a formula, do not touch it.

`Lead Handoff`, column B:

| Cells | Value |
|---|---|
| B6 | Client company / contact, if shown |
| B7 | Problem, in the client's words |
| B8 | Expected result |
| B9 | Budget, as stated |
| B10 | Deadline, if stated, with its reason |
| B12 | Industry / compliance, if mentioned |
| B13 | `Upwork` |
| B16 | The Upwork job URL |
| B17–B31 | Job and client data in the row order of the sheet (title, contract type, budget/rate, payment verified, rating, reviews, total spent, hire rate, hires, open jobs, country/timezone, member since, proposals, interviewing, invites sent) |

Do not fill `B11` (decision maker), `B14` (sales notes), `B32`–`B33` (our proposal): they come from people,
not from the job page. Leave not-found fields empty.

### 5. Report

Reply with:
- the link to the new workbook;
- what was filled, in a short list;
- what stayed empty and who should fill it (from the "Who fills" notes in `sheets.md`).

Do not contact the client and do not apply to the job.
