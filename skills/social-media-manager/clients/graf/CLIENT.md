# CLIENT: GRAF Ibérica

## Identity
- **Client**: GRAF Ibérica Tecnología del Plástico S.L.U.
- **Location**: Aiguaviva, Girona (España)
- **Web**: grafiberica.com | graf.info/es
- **Language**: Castellano + Portugués (same copy, always both, no language labels)
- **Tone**: Formal pero cercano. Algún emoji permitido para facilitar la comprensión. Natural, sin títulos ni encabezados en el copy.

## Product Lines
For context, consult these catalog files in the client folder:

| Categoría                     | Archivo de referencia                                    |
|-------------------------------|----------------------------------------------------------|
| Jardín (general)              | `CATALEG_PRODUCTOS_DE_JARDIN_ESP.md`                     |
| Recuperación agua de lluvia   | `Catalogo-Recuperacion-agua-de-lluvia.md`, `Triptico-Sistemas-de-Recuperacion-de-Agua-de-Lluvia.md` |
| Compostadoras / Garantías     | `Catalogo_Garantia_Agua_de_lluvia_y_Compostadoras.md`    |
| Drenaje sostenible (SUDS)     | `Catalogo_SUDS_Drenaje_Sostenible.md`                    |
| Depuradoras (con electricidad)| `Catalogo_depuradoras_Espana_y_Portugal_(1).md`          |
| Depuradoras sin electricidad  | `Catalogo_depuradoras_sin_electricidad_ES.md`            |
| Web corporativa               | `grafiberica.com` + `grafiberica_web.md`                 |

### Terminology rules
- Use **"depósito"** for above-ground tanks
- Use **"depósito soterrado"** for underground tanks
- NEVER use "sostenible" unless it is technically proven in the catalog
- NEVER use "energéticamente eficiente" or "eco-friendly" unless explicitly backed by catalog data
- Do NOT invent technical specifications — only use data from the catalog files

## Networks & Publishing
| Network   | Active | Notes                                  |
|-----------|--------|----------------------------------------|
| Instagram | ✅     |                                        |
| LinkedIn  | ✅     |                                        |
| Facebook  | ⬜     | Not active                             |
| Twitter/X | ⬜     | Not active                             |

## Publishing Schedule (Loomly default)
- **Frequency**: 2–3 posts per week, alternating pattern: 2, 3, 2, 3, 2, 3...
- **Time**: 10:00h (always)
- **Days**: Monday/Wednesday(/Friday for 3-post weeks) — adjust if user specifies
- When publishing in bulk, calculate dates automatically following the 2-3 alternating pattern

## Loomly Config
- **Calendar**: GRAF Ibérica (confirm with user if first deploy)
- **Deploy mode**: Batch — up to 10 posts per API call. No per-post confirmation needed.
- **Title format**: Descriptive, ≤ 6 words
- **Networks**: Instagram + LinkedIn (always both)

---

## Post Format (STRICT — always follow this structure)

```
[copy en castellano]
----
[copy en portugués]
```

Rules:
- **No language labels** (no "Castellano:", "ES:", "PT:", etc.)
- **Same content** in both languages — not a summary, a full translation
- **Separator**: exactly `----` (four dashes) between the two versions
- Hashtags at the end of the **castellano block**, before the separator? NO — hashtags go **only once, at the very end**, after the Portuguese copy
- Actually: hashtags at the **bottom of the full post** (after Portuguese), or inline at end of castellano before `----`?
  → Place hashtags at the **end of the castellano block**, just before `----`. The Portuguese block has no hashtags.

Corrected structure:
```
[copy en castellano] #Hashtag1 #Hashtag2
----
[copy em português]
```

### Copy rules
- No titles or headers inside the copy
- Natural, flowing text — not bullet points
- Concrete product benefits, not vague claims
- 1–2 emojis max per post, used naturally (not forced)
- No quotes (" ") around product names or claims
- Short paragraphs, direct language

---

## Hashtag Rules

Always include `#GRAFIbérica` + 1–2 thematic hashtags.

**Hashtag pool by topic:**
| Topic                         | Hashtags                                                    |
|-------------------------------|-------------------------------------------------------------|
| Brand (always)                | `#GRAFIbérica`                                              |
| Water recovery / rain         | `#AguaDeLluvia` `#AhorroDeAgua` `#RecuperaciónDeAgua`       |
| Wastewater / depuradoras      | `#AguasResiduales` `#DepuraciónAutónoma` `#Saneamiento`     |
| Garden / exterior             | `#Jardín` `#ProductosDeJardín`                              |
| SUDS / drainage               | `#DrenajeUrbano` `#SUDS` `#DrenajeInteligente`              |
| Composting                    | `#Compostaje` `#Compostadora`                               |
| No electricity systems        | `#SinElectricidad` `#AutonomíaHídrica`                      |
| General sustainability        | `#GestiónDeAgua` `#MedioAmbiente`                           |

Maximum **3 hashtags** per post. Never repeat the same combination in a bulk batch.

---

## Efemérides
Read `EFEMERIDES.md` when planning weekly or monthly content.
If a relevant environmental/water date falls within the requested period, propose it as the basis for one of the posts in the batch. Always flag it explicitly to the user before including it.
Priority dates: 22 mar (Día Mundial del Agua), 22 abr (Día de la Tierra), 5 jun (Día Mundial del Medio Ambiente).

## Approved Examples
Read `examples/posts.csv` for reference (394 approved posts).
Key patterns observed:
- Copy castellano: avg 455 chars, range 55–1,958
- ~50% of posts start with emoji
- ≤3 hashtags per post; always `#GRAFIbérica`
- Common thematic hashtags from real posts: `#AguaDeLluvia` `#Sostenibilidad` `#MedioAmbiente` `#SUDS` `#Reciclaje` `#RecuperaciónAguaDeLluvia` `#AguaPotable` `#Jardín` `#ConsumoResponsable`
- Avoid multilingual hashtags (no `#water` `#sustainability` `#environment` — those are from older posts)
- Format: castellano block → `----` → portuguese block (no hashtags in PT block)

## Quality Checklist (apply before presenting output)

- [ ] Both languages present, same content
- [ ] Separator `----` correctly placed
- [ ] Hashtags only once (after castellano block, before `----`)
- [ ] No forbidden terms used (sostenible, eco-friendly, energéticamente eficiente) unless catalog-backed
- [ ] Correct terminology: depósito vs. depósito soterrado
- [ ] No invented technical data — all claims sourced from catalogs
- [ ] Max 3 hashtags
- [ ] `#GRAFIbérica` always included
- [ ] No titles or headers in copy body
- [ ] Natural, fluent tone — no marketing clichés

---

## Bulk Publishing Logic

When user requests multiple posts (e.g., "4 semanas de contenido"):

1. Calculate total posts using 2-3 alternating pattern:
   - Week 1: 2 posts (Mon, Wed)
   - Week 2: 3 posts (Mon, Wed, Fri)
   - Week 3: 2 posts (Mon, Wed)
   - ...
2. Assign dates starting from next Monday (or user-specified start date)
3. All at 10:00h
4. Group into batches of ≤10 for Loomly API calls
5. Publish all without per-post confirmation — user reviews in Loomly

## Loomly Title Examples
- `GRAF - Depósito soterrado agua lluvia`
- `GRAF - ecoRock sin electricidad`
- `GRAF - Compostadora jardín`
- `GRAF - Drenaje SUDS urbano`
- `GRAF - Recuperación agua exterior`
