# Deploy: Loomly via Zapier

## Overview

Publishing to Loomly is done through the **Zapier MCP tool** (loomly_create_quick_post or loomly_create_custom_post_idea).

This deploy module is shared across all clients. Each client's `CLIENT.md` specifies:
- Which Loomly **calendar** to use
- The **title format** convention
- Allowed **time slots**

---

## Pre-publish Checklist

Before calling the Zapier tool, verify:

- [ ] **Copy is final** — user has approved the text
- [ ] **Title is set** — generic, descriptive, no copy content
- [ ] **Date/time confirmed** — within client's allowed slots
- [ ] **Network selected** — Instagram / Twitter / Facebook
- [ ] **Image** — URL provided or explicitly "no image"
- [ ] **Date warning shown** — if copy contains a date, user confirmed it's correct

---

## Required Fields for Loomly Post

| Field       | Description                                              | Example                              |
|-------------|----------------------------------------------------------|--------------------------------------|
| `calendar`  | From client config                                       | `Ajuntament de Salt`                 |
| `title`     | Generic descriptive label (never the copy text)          | `Activitat - Farmàcia Guàrdia mar`   |
| `copy`      | Final approved post text                                 | `🗓️ Farmàcies de Guàrdia...`        |
| `date`      | ISO 8601 format                                          | `2026-03-10T10:00:00`                |
| `networks`  | List of target networks                                  | `["instagram", "facebook"]`          |
| `image_url` | Optional image URL                                       | `https://...` or null                |

---

## How to Publish

1. Load the Zapier tool via `tool_search("loomly zapier")`
2. Use `loomly_create_quick_post` for simple posts
3. Use `loomly_create_custom_post_idea` if the post needs per-network customization

**Always confirm with the user before calling the tool:**
> "Publico '{title}' al calendari '{calendar}' el [data] a les [hora]?"

Wait for explicit confirmation ("sí", "endavant", "publica").

---

## Title Convention by Client

| Client                | Title format                                              |
|-----------------------|-----------------------------------------------------------|
| Ajuntament de Salt    | `[Categoria] - [Descripció breu] [mes abreviat]`          |

Examples:
- `Activitat - Túnel del Terror feb`
- `NDP - Plans d'ocupació SOC 2025`
- `Farmàcia - Guàrdia setmana 10-16 mar`
- `Esports - Lliga Gimnàstica feb`

---

## Date/Time Slot Validation

Before publishing, check the proposed time slot against the client schedule.

Salt allowed slots: `10:00 | 11:00 | 12:00 | 16:00 | 17:00` — Monday to Friday only.

If the user proposes a time outside these slots, flag it:
> "⚠️ Els slots habituals per a Salt són 10h, 11h, 12h, 16h i 17h (dilluns a divendres). Confirmes igualment [hora proposada]?"
