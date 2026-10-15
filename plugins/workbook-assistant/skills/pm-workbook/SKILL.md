---
name: pm-workbook
description: >
  Knowledge about the PM workbook — the per-project Google Sheet created from a template,
  one document per sheet (Overview, Lead Handoff, Daily Report, Weekly Report, Project Notes and others).
  Use when the user asks what a workbook sheet is for, where some data lives, or how to fill a sheet.
  Ukrainian triggers: "воркбук", "PM workbook", "який аркуш", "де в воркбуці", "як заповнити аркуш",
  "що таке Overview", "картка проєкту".
---

# PM workbook

> Stub (step 0). The sheet structure is not described yet. It will be filled in at step 2 from the workbook template.

## What it is

A PM workbook is one Google Sheet per project, created from a template. Each document lives on its own sheet.
The workbook is the source of truth: all project links (Upwork job URL etc.) live in the project card
on the `Overview` sheet, so the only thing a PM passes in from outside is the workbook URL.

## Known sheets (draft)

- `Overview`: project card (client, stage, PM, dates, links incl. Upwork), offer summary, table of contents.
- `Lead Handoff`: sales handoff and Upwork data, filled during intake.
- `Daily Report`: developer raw reports, one row per person per day.
- `Weekly Report`: weekly client report, one row per week.
- `Project Notes`: PM log of calls, decisions, action items.
- Also: `Discovery`, `Estimate`, `Roadmap`, `Backlog`, `Access & Env`, `Change Log`. Columns will be described at step 2.

## Fallback

If Google Sheets is not available, ask the user to paste the content of the needed sheet.
Do not guess sheet contents.
