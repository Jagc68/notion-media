---
name: instagram-analyze
description: Interactieve analysesessie van Instagram Saves. Gebruik ALTIJD wanneer de gebruiker typt /instagram-analyze, wil analyseren wat er in zijn saves zit, wil meekijken bij de verwerking van saves, recepten wil opslaan, finance tips wil bewaren, AI/tech takeaways wil noteren, of items wil verwerken uit zijn Queued lijst.
---

# /instagram-analyze — Interactieve Analysesessie

Je verwerkt Greg's Instagram Saves één voor één, interactief. Greg kijkt mee en beslist per item wat ermee gebeurt.

## Werkwijze

Verwerk items één voor één. Presenteer elk item helder, wacht op Greg's keuze, voer die uit, ga dan pas naar het volgende. Haast je niet.

---

## Stap 1 — Haal Queued items op

Query de Instagram Saves database via de Notion MCP:
- Database ID: `390332b7-36df-81dc-a2f9-cc9e12d87fcc`
- Filter: Status = "Queued"

Haal alle properties op: Name, Caption, URL, Category, Status.

Als er geen Queued items zijn, zeg dit en stop.

Meld aan het begin: "X items in de wachtrij. We gaan ze één voor één bekijken."

---

## Stap 2 — Presenteer elk item

Toon per item:

```
─────────────────────────────────
📌 Item [N/Totaal]
👤 [naam uit title, bijv. @account]
🏷️  Categorie: [category]
🔗 [URL]

📝 Caption:
[volledige caption — niet inkorten]

💡 Eerste indruk: [1 zin wat dit item bevat]
─────────────────────────────────

Wat wil je doen met dit item?
A) 🍳 Opslaan als recept
B) 💰 Bewaren als finance tip / inzicht
C) 🤖 Samenvatten als AI/Tech notitie
D) 💡 Toevoegen als content idee
E) ⏭️  Overslaan (geen actie)
F) 🗑️  Done + cleanup (later verwijderen van Instagram)
```

Wacht op Greg's antwoord voor je iets doet.

---

## Stap 3 — Voer de gekozen actie uit

### A) 🍳 Recept opslaan

Extraheer uit de caption:
- **Naam** van het gerecht
- **Ingrediënten** (als genummerde of bulleted lijst)
- **Bereidingsstappen** (in volgorde)
- **Tips** die vermeld worden

Maak een Notion pagina aan als kind van de Recepten pagina (page_id: `37db9e5a-6384-8157-9c71-db450a6e0b35` valt terug op Kennisbank als niet beschikbaar).

Gebruik deze structuur:
```
🍳 [Naam gerecht]

## Ingrediënten
- ...

## Bereidingswijze
1. ...

## Tips
- ...

Bron: [Instagram URL]
```

### B) 💰 Finance tip bewaren

Extraheer:
- **Kernpunt / les** (1-2 zinnen)
- **Concrete stappen of cijfers** die genoemd worden
- **Toepassing**: hoe kan Greg dit zelf gebruiken?

Maak een Notion pagina aan onder de Finance sectie (page_id: `37db9e5a-6384-8185-962f-d07b1fefe502` — Kennisbank als fallback).

Structuur:
```
💰 [Titel van het inzicht]

## Kernpunt
...

## Details / Cijfers
...

## Hoe toe te passen
...

Bron: [Instagram URL]
```

### C) 🤖 AI/Tech notitie

Extraheer:
- **Samenvatting** (3-5 zinnen)
- **Key takeaways** (max 5 bullets)
- **Tools / links / namen** die genoemd worden
- **Acties**: wat kan Greg concreet doen met deze info?

Maak een Notion pagina aan onder de Claude/AI sectie (page_id: `37db9e5a-6384-8105-ab14-c376455332ff`).

Structuur:
```
🤖 [Titel]

## Samenvatting
...

## Key takeaways
- ...

## Tools & Links
- ...

## Acties voor Greg
- ...

Bron: [Instagram URL]
```

### D) 💡 Content idee

Bedenk op basis van de caption:
- **Hook** (pakkende eerste zin, < 10 woorden)
- **Format**: Reel / Carrousel / Post / Story
- **Platform**: Instagram / YouTube Short / TikTok
- **Greg's invalshoek**: hoe maakt hij dit zijn eigen?
- **Prioriteit**: Hoog / Middel / Laag

Voeg toe aan de Content Ideas database (`ideas_database_id` uit config.json).

### E) ⏭️ Overslaan

Geen actie. Ga naar het volgende item.

### F) 🗑️ Done markeren

Update de Status van dit item naar "Done" in de Notion database. Het wordt opgepikt door cleanup.py wanneer Greg dat runt.

---

## Stap 4 — Na elke actie

Bevestig kort wat je gedaan hebt (één zin), dan meteen naar het volgende item.

Hou bij hoeveel je verwerkt hebt. Na het laatste item geef je een korte samenvatting:

```
✅ Sessie klaar — [N] items verwerkt
🍳 Recepten: X  💰 Finance: X  🤖 AI/Tech: X  💡 Ideeën: X  ⏭️ Overgeslagen: X
```

---

## Stijlregels

- Schrijf in het Nederlands
- Wees bondig in je bevestigingen — Greg hoeft niet elke actie uitgelegd te krijgen
- Als de caption te kort is om iets zinvols uit te halen, zeg dit eerlijk en stel optie E of F voor
- Forceer geen categorie — als iets niet duidelijk past, vraag Greg
