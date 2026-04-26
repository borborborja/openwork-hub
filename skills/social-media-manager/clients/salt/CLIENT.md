# CLIENT: Ajuntament de Salt

## Identity
- **Client**: Ajuntament de Salt
- **Persona**: XXSS_Salt
- **Language**: Català
- **Tone**: Formal però proper. Institucional, transparent i eficaç.

## Networks & Character Limits
| Network          | Active | Char limit | Notes                                        |
|------------------|--------|------------|----------------------------------------------|
| Instagram        | ✅     | 2,200      | Main channel                                 |
| Facebook         | ✅     | —          | Same copy as Instagram                       |
| Twitter/X        | ✅     | 280        | Shorter copy when needed                     |
| LinkedIn         | ✅     | —          | Same copy as Instagram                       |
| WhatsApp/Telegram| ✅     | —          | Shorter, more direct copy — no hashtags      |

## Publishing Schedule (Loomly slots)
Monday–Friday only:
- 10:00, 11:00, 12:00, 16:00, 17:00

## Hashtag Rules
- Always include `#ViuSalt`
- Add `#Salt` when contextually appropriate (not every post)
- Add thematic hashtags when relevant (e.g., `#FarmàciaDeGuàrdia`, `#ViuSalt`)
- Hashtags go after a line break, never inline with body text

## Formatting Rules
- **No bold, no italic, no markdown** (no asterisks) — Loomly does not render them
- No intro titles or section headers in the copy
- Short copies, no excessive bullet points
- Use line breaks to space content
- Emojis: rich use, one per key idea/line
- Mentions: include `@handle` (Instagram) when referencing entities — check `users.csv`
- No invented information — ask if unsure

## Mention Lookup
Before publishing, check `users.csv` for Instagram handles of any mentioned entity.
Format: `@handle` inline in the post body where the entity is named.

---

## Post Types

### 1. Generic Post (3 alternatives)

**Rules:**
- 3 numbered alternatives, each with a different angle or emphasis
- Rich in emojis, short paragraphs
- Hashtags after line break at end
- Mention relevant entities with @handle

**Output structure:**
```
1
[copy text with emojis]

#Hashtag1 #Hashtag2

2
[copy text with emojis]

#Hashtag1 #Hashtag2

3
[copy text with emojis]

#Hashtag1 #Hashtag2
```

---

### 2. NDP — Nota de Premsa

Triggered when user provides 3–4 headline-style bullets and says "NDP" or "nota de premsa".

**Rules:**
- One single post, no alternatives
- Add a descriptive emoji at the START of each headline bullet (do not modify the text)
- End with the link and hashtag block
- No bold, no markdown

**Output structure:**
```
[emoji] [Titular 1 sense modificar].

[emoji] [Titular 2 sense modificar].

[emoji] [Titular 3 sense modificar].

Tota la informació a 📲 https://www.infosalt.cat

#ViuSalt
```

---

### 3. Farmàcia de Guàrdia

Triggered when user provides a pharmacy schedule PDF or data, or says "farmàcia de guàrdia".

**Input:** PDF or raw data from Col·legi de Farmacèutics de Girona (cofgi.org) with columns: DATA | HORARI | FARMÀCIA - MUNICIPI | TELÈFON

**Output:** One post per calendar week (Mon–Sun). If PDF covers multiple weeks, generate one post per week automatically.

---

**PARSING RULES (read PDF carefully):**
- Extract: day name, day number, month, pharmacy name, address, schedule
- Normal days: 09:30 - 09:30 (Dia Seg.) → standard entry, no need to show hours
- Special days (usually Sunday): two pharmacies with split hours:
  - First: 09:30 - 22:00 → show `(09:30 - 22:00)` after name
  - Second: 22:00 - 09:30 → show `(22:00 - 09:30)` after name
- If a Sunday only has one pharmacy (09:30 - 09:30), treat it as a normal day

**ADDRESS NORMALISATION (apply always):**
- `Avgda.` / `Avda.` → `Av.`
- `Pg.` / `Passeig` → `Pg.`
- `C/` → `C/` (keep as-is)
- `Camí dels Carlins` → keep as-is
- `Pla de Salt` → keep as-is
- Correct obvious OCR errors (e.g. `Capdefierro` → `Capdeferro`, `Llevadores` → `Llevadores`)
- Do not add or remove street numbers

**WEEK HEADER:**
- Format: `del DD al DD de MES` (lowercase month in Catalan)
- Week = Monday to Sunday
- If week spans two months: `del DD de MES al DD de MES` (e.g. `del 31 de març al 6 d'abril`)

**OUTPUT STRUCTURE (strict, one post per week):**
```
🗓️ Farmàcies de Guàrdia a #Salt per la setmana del [X al Y de MES]! 🚑

DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA. Adreça
DD/MM: NOM FARMÀCIA (09:30 - 22:00). Adreça
DD/MM: NOM FARMÀCIA (22:00 - 09:30). Adreça

🕤 Horari: 09:30 - 09:30 (de l'endemà)

#FarmàciaDeGuàrdia #ViuSalt
```

**FORMATTING RULES — LINE BREAKS (critical):**
- Each pharmacy entry on its own line — NEVER two entries on the same line
- NO blank lines between pharmacy entries (tight list)
- ONE blank line between the header line and the first pharmacy entry
- ONE blank line between the last pharmacy entry and the `🕤 Horari` line
- ONE blank line between `🕤 Horari` line and the hashtags
- No phone numbers in the post
- Day format: DD/MM (always two digits, e.g. `09/03` not `9/3`)
- Month in header: lowercase Catalan (`març`, `abril`, `maig`...)
- No trailing spaces

**EXACT LINE BREAK TEMPLATE:**
```
🗓️ Farmàcies de Guàrdia a #Salt per la setmana del X al Y de MES! 🚑
← blank line
DD/MM: NOM. Adreça
DD/MM: NOM. Adreça
DD/MM: NOM. Adreça
DD/MM: NOM. Adreça
DD/MM: NOM. Adreça
DD/MM: NOM. Adreça
DD/MM: NOM (09:30 - 22:00). Adreça
DD/MM: NOM (22:00 - 09:30). Adreça
← blank line
🕤 Horari: 09:30 - 09:30 (de l'endemà)
← blank line
#FarmàciaDeGuàrdia #ViuSalt
```

**PUBLISHING SCHEDULE:**
- Every Monday at 10:00h
- When user provides PDF, automatically assign each post to the Monday of that week at 10:00h
- If deploying to Loomly, schedule all posts in one batch without per-post confirmation

**AFTER GENERATING:**
Always add: `⚠️ Verifica que els dies de la setmana coincideixen amb les dates correctes.`

---

## Loomly Config
- **Calendar**: Ajuntament de Salt
- **Title format**: Generic and descriptive (e.g., "Activitat - Túnel del Terror febrer")
- **Deploy**: See `../../deploy/LOOMLY.md`

---

## Validated Examples
See `examples/posts.csv` — use these to validate tone, emoji density, and structure before presenting output.

Key patterns from approved posts:
- Emojis used liberally: one per key idea
- Short sentences, line breaks between ideas
- Entity mentions with @handle
- Hashtags always at the end after a blank line
- Infosalt.cat link for NDP posts
- Never invents data — asks if unsure
