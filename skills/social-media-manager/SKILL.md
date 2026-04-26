---
name: social-media-manager
description: Create social media copies for multiple clients with automatic or manual publishing via Loomly/Zapier. Use this skill whenever the user asks to create posts, copies, or social media content for any client, or when they want to publish content to Loomly or social networks. Also trigger when the user mentions a client name, asks for post alternatives, farmàcia de guàrdia, NDP/nota de premsa, or any content scheduling task. Always use this skill when working with client-specific tone, hashtags, or publishing workflows.
---

# Social Media Manager

A modular skill for generating and publishing social media content for multiple clients. Each client has its own configuration, tone guide, examples, and publishing rules.

## Workflow Overview

```
1. IDENTIFY CLIENT         → Load client config from clients/<client>/
2. UNDERSTAND REQUEST      → Post type, content, target date/time
3. GENERATE COPY           → Apply client rules + post-type templates
4. VALIDATE                → Check style against examples
5. DEPLOY                  → Manual review OR auto-publish via Loomly
```

## Step 1 — Identify the Client

Read the client directory: `clients/<client-slug>/CLIENT.md`

Current clients:
| Slug        | Client                   | Config file                         |
|-------------|--------------------------|-------------------------------------|
| `salt`      | Ajuntament de Salt       | `clients/salt/CLIENT.md`            |
| `efimatica` | Efimàtica                | `clients/efimatica/CLIENT.md`       |
| `graf`      | GRAF Ibérica             | `clients/graf/CLIENT.md`            |
| `nix`       | NIX Grupo de Seguridad   | `clients/nix/CLIENT.md`             |

> If the client is not listed, ask the user which client they're working with before proceeding.

## Step 2 — Understand the Request

Identify the **post type** from the user's message:

| Post Type         | Trigger keywords                                      | Template section            |
|-------------------|-------------------------------------------------------|-----------------------------|
| `generic`         | Default, event, activity, news without structured format | CLIENT.md → Generic Posts   |
| `ndp`             | "nota de premsa", "NDP", 3–4 headline bullets         | CLIENT.md → NDP Posts       |
| `farmacia`        | "farmàcia de guàrdia", pharmacy schedule              | CLIENT.md → Farmàcia Posts  |
| `ideas_tweet`     | "idees de contingut", "genera posts", topic + N posts | CLIENT.md → Content Ideas   |
| `curated`         | User shares URL/article and asks to post about it     | Short intro + ➡️ URL (Efimàtica style) |
| `loomly-publish`  | "publica a loomly", "programa", "deploy"              | deploy/LOOMLY.md            |
| `linkedin-educatiu`  | "normativa", "RGPD", "RIPCI", "Grau 3", "CRA" (NIX) | CLIENT.md → Educatiu        |
| `linkedin-sector`    | "industrial", "retail", "oficines", "pisos" (NIX)    | CLIENT.md → Sector          |
| `linkedin-tech`      | "tecnologia", "IA", "analítica", "LPR" (NIX)         | CLIENT.md → Tecnologia      |
| `linkedin-empresa`   | "40 anys", "empresa", "certificació", "ISO" (NIX)    | CLIENT.md → Credibilitat    |
| `linkedin-consell`   | "consell", "tip", "consells" (NIX)                   | CLIENT.md → Consell pràctic |

Collect these fields before generating:
- **Content**: text, bullets, or image/poster provided
- **Publish date**: explicit (e.g., "el dilluns 10") or implicit ("aquesta setmana")
- **Publish time**: slot requested or auto-assign per client schedule
- **Networks**: from client config or user specification
- **Image**: URL, file, or "no image"
- **Title** (for Loomly): generic descriptive label

> If a date is mentioned in the content, always remind the user: "⚠️ Verifica que el dia de la setmana i el mes siguin correctes."

## Step 3 — Generate Copy

Read the full `clients/<client>/CLIENT.md` for:
- Tone and voice rules
- Post-type specific templates
- Hashtag rules
- Formatting restrictions (e.g., no bold/markdown)
- Networks and character limits

**Always validate** generated copies against `clients/<client>/examples/` before presenting.

**Output format:**
- For generic posts: 3 numbered alternatives
- For NDP: single structured post (no alternatives)
- For farmàcia: single formatted post (no alternatives)
- No intro text, no titles — just the numbered copies directly

## Step 4 — Deploy

See `deploy/LOOMLY.md` for publishing instructions.

Deploy modes:
- **Manual**: Present copies for user to copy-paste
- **Loomly via Zapier**: Use the Zapier MCP tool to publish directly

---

## Adding a New Client

To onboard a new client, create:
```
clients/<new-client>/
├── CLIENT.md          ← tone, rules, templates, networks, schedule
├── users.csv          ← Twitter/Instagram handles for mentions
└── examples/          ← approved past posts (CSV or text)
    └── posts.csv
```

Then add the client to the table in Step 1 above.
