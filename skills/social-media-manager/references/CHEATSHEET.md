# References: Quick Lookup

## Post Type Decision Tree

```
User message contains...
│
├── "nota de premsa" / "NDP" / 3-4 headline bullets?
│   └── → POST TYPE: ndp
│
├── "farmàcia de guàrdia" / pharmacy list with days?
│   └── → POST TYPE: farmacia
│
├── "publica" / "programa" / "loomly" / "deploy"?
│   └── → DEPLOY MODE: loomly  (read deploy/LOOMLY.md)
│
└── Everything else
    └── → POST TYPE: generic (3 alternatives)
```

---

## Date Warning Trigger

If the copy or user input contains any of these, always show the date warning:

- A day name (dilluns, dimarts, dimecres, dijous, divendres, dissabte, diumenge)
- A date pattern (DD de MMMM, DD/MM)
- "aquesta setmana", "el proper", "avui", "demà"

Warning text:
> ⚠️ Verifica que el dia de la setmana es correspongui amb la data, i que el mes sigui el correcte.

---

## Emoji Usage Guide

| Context                | Recommended emojis                              |
|------------------------|-------------------------------------------------|
| Dates / Calendar       | 🗓️ 📅                                          |
| Location               | 📍                                              |
| Time                   | ⏰ 🕔                                           |
| Urgent / Important     | ⚠️ 🔴                                           |
| Registration           | 📝 ✍️                                           |
| Price                  | 💶                                              |
| Phone                  | 📞                                              |
| Email                  | 📧                                              |
| Link / Info            | 📲 🔗 ℹ️                                        |
| Health                 | 🚑 💊 🏥                                        |
| Sports                 | 🏆 🤸 ⚽ 🏀                                     |
| Culture / Events       | 🎭 🎪 🎨 🎶                                     |
| Youth                  | 👧🧒                                            |
| Seniors                | 👴👵                                            |
| Environment            | 🌿 🌱                                           |
| Economy / Work         | 💼 📈 👷                                        |
| Institutional          | 🏛️ 🤝                                          |

---

## Common Mistakes to Avoid

| ❌ Wrong                                  | ✅ Correct                                      |
|-------------------------------------------|-------------------------------------------------|
| **Bold text** with asterisks              | Plain text only                                 |
| Hashtags inline in body text              | Hashtags after blank line at end                |
| Inventing phone numbers or addresses      | Ask the user if data is missing                 |
| Long bullet-point lists                   | Short paragraphs with line breaks               |
| Posting intro like "Aquí tens el post:"   | Start directly with the copy                   |
| Loomly title = copy text                  | Loomly title = generic descriptive label        |
| Publishing without user date confirmation | Always warn + wait for confirmation             |
