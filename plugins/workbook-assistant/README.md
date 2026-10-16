# workbook-assistant

Помічник PM для роботи з **PM workbook**: Google Sheet на проєкт, створений із шаблону.

## Що вміє

| Команда / skill             | Що робить                                                                              |
| --------------------------- | -------------------------------------------------------------------------------------- |
| `/intake <upwork-job-url>`  | Читає джобу з Upwork, створює воркбук із шаблону, заповнює `Overview` і `Lead Handoff` |
| `/bi-analys <workbook-url>` | Бізнес-аналіз клієнта: Google Doc з аналізом і підтверджені факти в `Lead Handoff`     |
| `/info [команда]`           | Довідка: що вміє плагін, з чого почати («що вміє плагін», «як користуватись»)          |
| `pm-workbook`               | Знає аркуші воркбуку, їхні поля і хто що заповнює («де в воркбуці…», «як заповнити…»)  |
| `upwork-intake`             | Що брати з Upwork-джоби і як це нормалізувати                                          |
| `client-tone`               | Тон і правила листів клієнту («напиши клієнту…»)                                       |

Плагін **нічого не надсилає клієнту**: він лише показує PM чернетку.

## Встановлення

- **Claude Desktop:** Customize → Plugins → Discover → `+` → `SakhnoDima/pm-tools`, потім Install `workbook-assistant`.
- **Claude Code:**
    ```
    /plugin marketplace add SakhnoDima/pm-tools
    /plugin install workbook-assistant@pm-tools
    ```

## Перед першим використанням

1. **Підключи конектори плагіна** `google-sheets` і `google-drive`: у вкладці Connectors плагіна натисни Connect і увійди в Google.
2. **Встанови Claude in Chrome** і залогінься в Upwork у своєму Chrome. Без цього `/intake` і `/bi-analys` попросять вставити текст вручну.
3. Переконайся, що маєш доступ до шаблону воркбуку на Google Drive.

## Структура

```
.claude-plugin/plugin.json   маніфест і версія
.mcp.json                    Google Sheets + Google Drive MCP (віддалені, OAuth)
skills/                      skills; команди = skills з disable-model-invocation
```
