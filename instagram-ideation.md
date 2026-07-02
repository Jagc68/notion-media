---
name: instagram-ideation
description: Genereer content ideeën voor reels, posts en video's vanuit Instagram Saves. Gebruik ALTIJD wanneer de gebruiker typt /instagram-ideation, content ideeën wil bedenken, posts of reels wil maken op basis van saves, wil weten wat hij kan posten, of ideation wil doen voor zijn eigen kanaal. NIET voor persoonlijk kennisgebruik (recepten, finance, tech) — gebruik daarvoor /instagram-analyze.
---

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

Sla goedgekeurde ideeën op in de Content Ideas database via **notion-duplicate-page** + **notion-update-page**.

### Waarom duplicate en niet create?
`notion-create-pages` maakt geen database-rijen aan — pagina's komen op de verkeerde plek terecht. De enige werkende aanpak is een bestaande entry dupliceren en daarna updaten.

### Werkwijze per idee:
1. Roep `notion-duplicate-page` aan met page_id: `391332b7-36df-812a-8b16-c6b7c0dbc46d` (bestaande Content Ideas entry)
2. Gebruik de teruggegeven `page_id` in een `notion-update-page` aanroep met `command: "update_properties"`

Properties per idee (zet allemaal in één `properties` object — NIET als losse `title` parameter):
```
{
  "Name": "korte pakkende titel (Engels)",
  "Status": "Idee",
  "Prioriteit": "Hoog" | "Middel" | "Laag",
  "Platform": "Instagram Reel" | "Instagram Post" | "YouTube Short" | "TikTok" | "Blog",
  "Categorie": "AI / Tech" | "Fitness" | "Finance" | "Eten / Recepten" | "Overig",
  "Bron URL": "https://www.instagram.com/reel/...",
  "Notities": "Hook: ... | Uitwerking: ..."
}
```

Doe ideeën sequentieel (duplicate → update → volgende), niet parallel — anders raken IDs door elkaar.

---

## Toon

- Conversatie met Greg: Nederlands
- Alle content output (hooks, captions, titels, video-scripts): **Engels** — Greg publiceert op zijn eigen Engelstalig kanaal
- Denk als een content creator, niet als een assistent
- Wees concreet: geen vage ideeën maar echte hooks en formats klaar voor gebruik
