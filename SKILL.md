---
name: ikgaslapen
description: Dagelijkse afsluiting. Gebruik ALTIJD wanneer Greg typt "/ikgaslapen", "/goedenavond", "ik ga slapen", "tot morgen" of de dag afsluit. Vat de dag samen en schrijft het weg naar het Notion Dagboek.
---

# /ikgaslapen

Vat de huidige sessie samen en sla het op als daglog in Greg's Notion Dagboek.

## Stap 1 — Maak de samenvatting

Analyseer de huidige conversatie en maak een gestructureerde samenvatting:

**Besproken / gebouwd:**
- Wat hebben we vandaag gedaan? (concreet, niet vaag)

**Beslissingen genomen:**
- Welke keuzes zijn gemaakt en waarom?

**Geleerd:**
- Nieuwe concepten, tools of inzichten

**Open vragen / volgende stappen:**
- Wat is nog niet afgerond?
- Wat is de logische volgende stap?

Houd het onder 300 woorden — kort en to the point.

## Stap 2 — Schrijf weg naar Notion

Maak een nieuwe subpagina aan onder het Dagboek via `notion-create-pages`:

- **Parent page_id:** `399332b7-36df-8181-ae6b-e24f1e05514e`
- **Titel:** datum van vandaag, bijv. `2026-07-10`
- **Icon:** `https://raw.githubusercontent.com/Jagc68/notion-media/main/wiki-cover-icons/02-wiki-notebook-pen.png`
- **Content:** de samenvatting uit Stap 1 in dit format:

```markdown
## 🛠️ Besproken / gebouwd
[inhoud]

## ✅ Beslissingen
[inhoud]

## 💡 Geleerd
[inhoud]

## 👉 Volgende stappen
[inhoud]
```

## Stap 3 — Bevestig

Zeg kort:
> "Daglog opgeslagen voor [datum]. Welterusten! 👋"

## Toon
- Nederlands
- Bondig en feitelijk — dit is een log, geen essay
- Maximaal 300 woorden in de Notion pagina
