# /instagram-ideation

Genereer content ideeën vanuit de Instagram Saves database en sla ze op in Content Ideas.

## Wat doet dit commando?

1. Haalt Instagram Saves op uit Notion (gefilterd op een categorie of Status naar keuze)
2. Analyseert de captions en context van de saves
3. Genereert concrete content ideeën: hook, format, platform, invalshoek
4. Slaat elk idee op in de Content Ideas database

---

## Stap 1 — Vraag om context

Vraag Greg het volgende (één vraag):
- "Voor welke categorie wil je ideeën genereren? (AI/Tech, Fitness, Eten, Reizen, etc.) Of gewoon alles?"

---

## Stap 2 — Haal saves op uit Notion

Query de Instagram Saves database (`390332b7-36df-81dc-a2f9-cc9e12d87fcc`) via de Notion MCP.

Filter op:
- Category = de gekozen categorie (of geen filter voor alles)
- Status = "New" of "Done" (niet "Queued" — die worden al verwerkt)

Haal maximaal 20 items op. Lees van elk item: **Caption** en **URL**.

---

## Stap 3 — Genereer ideeën

Voor elke relevante save, denk na over:

- **Kern**: wat is de essentie van dit item?
- **Greg's invalshoek**: hoe past dit bij zijn niche of perspectief?
- **Hook**: een pakkende openingszin voor een reel of post (< 10 woorden)
- **Format**: Reel, Carrousel, Story, of Blog
- **Platform**: Instagram Reel / Post / YouTube Short / TikTok
- **Prioriteit**: Hoog als viral potentieel hoog is, Laag als niche

Genereer minimaal 5, maximaal 10 ideeën. Presenteer ze eerst aan Greg ter review.

---

## Stap 4 — Bevestiging en opslaan

Vraag Greg: "Wil je alle ideeën opslaan, of alleen een selectie?"

Sla goedgekeurde ideeën op in de Content Ideas database (ID staat in config.json als `ideas_database_id`) via notion-create-pages:

Properties per idee:
- **Name**: korte pakkende titel
- **Platform**: het gekozen platform
- **Categorie**: passend bij het originele save-item
- **Status**: "Idee"
- **Prioriteit**: Hoog / Middel / Laag
- **Bron URL**: de Instagram URL van het originele save-item
- **Notities**: de hook + korte uitwerking
- **Aangemaakt**: vandaag

---

## Toon

- Schrijf in het Nederlands
- Denk als een content creator, niet als een assistent
- Wees concreet: geen vage ideeën maar echte hooks en formats
