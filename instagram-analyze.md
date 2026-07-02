---
name: instagram-analyze
description: Interactieve analysesessie van Instagram Saves voor persoonlijk gebruik. Gebruik ALTIJD wanneer de gebruiker typt /instagram-analyze, wil analyseren wat er in zijn saves zit, recepten wil opslaan, finance tips wil bewaren, AI/tech takeaways wil noteren, of Queued items wil verwerken voor eigen kennisgebruik. NIET voor content ideeën of posts bedenken — gebruik daarvoor /instagram-ideation.
---

# /instagram-analyze — Interactieve Analysesessie

Je verwerkt Greg's Instagram Saves één voor één, interactief. Greg kijkt mee en beslist per item wat ermee gebeurt.

## Voorbereiding — lees het JSON-bestand

Lees het bestand `~/Documents/Claude/Projects/Notion/queued_items.json` via de Read tool.

Als het bestand niet bestaat of leeg is:
> "Geen Queued items gevonden. Zet items op **Queued** in Notion en draai daarna:
> `python3 ~/Documents/Claude/Projects/Notion/export_queued.py`"

Als het bestand wel items bevat: meld "**X items in de wachtrij. We gaan ze één voor één bekijken.**" en begin.

---

## Per item — presenteer zo

```
─────────────────────────────────
📌 Item [Nr] — [N/Totaal]
👤 [account uit name, bijv. @account]
🏷️  Categorie: [category]
🔗 [url]

📝 Caption:
[volledige caption — niet inkorten]

💡 Eerste indruk: [1 zin wat dit item bevat]
─────────────────────────────────

Wat wil je doen?
A) 🍳 Opslaan als recept
B) 💰 Bewaren als finance tip
C) 🤖 Samenvatten als AI/Tech notitie
D) ⏭️  Overslaan
E) 🗑️  Markeren als Done (later cleanup van Instagram)
```

Wacht op Greg's antwoord voor je iets doet.

---

## Acties

### A) 🍳 Recept opslaan

Extraheer uit de caption:
- Naam van het gerecht
- Ingrediënten (lijst)
- Bereidingsstappen (in volgorde)
- Tips

Maak een Notion pagina aan via `notion-create-pages`:
- Parent page_id: `37db9e5a-6384-8157-9c71-db450a6e0b35` (SQL/Recepten — gebruik Kennisbank `37ab9e5a-6384-8185-962f-d07b1fefe502` als fallback)
- Icon: 🍳
- Title: naam van het gerecht
- Content:
```
## Ingrediënten
- ...

## Bereidingswijze
1. ...

## Tips
- ...

Bron: [url]
```

Daarna: update het Notion item via `notion-update-page` → Status = **Done**.

### B) 💰 Finance tip bewaren

Extraheer:
- Kernpunt / les (1-2 zinnen)
- Concrete stappen of cijfers
- Hoe Greg dit zelf kan toepassen

Maak een Notion pagina aan via `notion-create-pages`:
- Parent page_id: `37ab9e5a-6384-8185-962f-d07b1fefe502` (Kennisbank)
- Icon: 💰
- Title: korte titel van het inzicht
- Content:
```
## Kernpunt
...

## Details / Cijfers
...

## Hoe toe te passen
...

Bron: [url]
```

Daarna: update Status → **Done**.

### C) 🤖 AI/Tech notitie

Extraheer:
- Samenvatting (3-5 zinnen)
- Key takeaways (max 5 bullets)
- Tools / namen / links die genoemd worden
- Acties: wat kan Greg concreet doen met deze info?

Maak een Notion pagina aan via `notion-create-pages`:
- Parent page_id: `37db9e5a-6384-8105-ab14-c376455332ff` (Claude/AI sectie)
- Icon: 🤖
- Title: pakkende titel
- Content:
```
## Samenvatting
...

## Key takeaways
- ...

## Tools & Links
- ...

## Acties voor Greg
- ...

Bron: [url]
```

Daarna: update Status → **Done**.

### D) ⏭️ Overslaan

Geen actie, geen Notion update. Ga naar het volgende item.

### E) 🗑️ Done markeren

Update via `notion-update-page`:
- Page ID: het id uit het JSON-item
- Status → **Done**

---

## Na elke actie

Bevestig in één zin wat je gedaan hebt, ga dan meteen naar het volgende item zonder te wachten.

## Na het laatste item

```
✅ Sessie klaar — [N] items verwerkt
🍳 Recepten: X  💰 Finance: X  🤖 AI/Tech: X  ⏭️ Overgeslagen: X  🗑️ Done: X
```

Herinner Greg eraan dat Done-items later verwijderd worden via:
`python3 ~/Documents/Claude/Projects/Notion/cleanup.py`

---

## Stijlregels

- Schrijf in het Nederlands
- Wees bondig in bevestigingen — Greg hoeft niet elke actie uitgelegd te krijgen
- Als de caption te kort is om iets zinvols uit te halen, zeg dit eerlijk en stel D of E voor
- Forceer geen categorie — als iets niet duidelijk past, vraag Greg
