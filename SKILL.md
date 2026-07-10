---
name: goedemorgen
description: Dagelijkse morning briefing. Gebruik ALTIJD wanneer Greg typt "/goedemorgen", "goedemorgen", "good morning" of de dag begint. Leest de meest recente daglog uit de Obsidian vault en geeft een overzicht van open taken, beslissingen en volgende stappen.
---

# /goedemorgen

Geef Greg een korte morning briefing op basis van de laatste daglog in zijn Obsidian vault.

## Stap 1 — Haal de laatste daglog op

Dagboek map: `/Users/josephcijntje/Documents/GregsObsidianVault/00 - Dagboek/`

Gebruik `Glob` om de bestanden in de map te zien (`*.md`), sorteer op naam (hoogste datum = meest recent). Lees het meest recente bestand met `Read`.

## Stap 2 — Presenteer de briefing

Geef een korte, gestructureerde briefing in het Nederlands:

```
☀️ Goedemorgen Greg!

📅 Gisteren ([datum]):
[Wat je bezig was met — 2-3 zinnen]

✅ Afgerond:
- [item]

🔄 Open / in progress:
- [item]

❓ Open vragen:
- [item]

👉 Logische eerste stap vandaag:
[concrete suggestie]
```

Als er geen daglog bestaat, zeg dan:
> "Nog geen eerdere logs gevonden. Ik maak vanavond de eerste aan via /ikgaslapen."

## Toon
- Kort en direct — geen lange uitleg
- Nederlands
- Maximaal 150 woorden
