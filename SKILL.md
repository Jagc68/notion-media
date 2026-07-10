---
name: goedemorgen
description: Dagelijkse morning briefing. Gebruik ALTIJD wanneer Greg typt "/goedemorgen", "goedemorgen", "good morning" of de dag begint. Haalt de sessie-log van gisteren op uit Notion en geeft een overzicht van open taken, beslissingen en volgende stappen.
---

# /goedemorgen

Geef Greg een korte morning briefing op basis van de laatste daglog in zijn Notion Dagboek.

## Stap 1 — Haal de laatste daglog op

Gebruik `notion-search` om de meest recente subpagina op te halen onder het Dagboek (page_id: `399332b7-36df-8181-ae6b-e24f1e05514e`).

Zoek op: "daglog" of gebruik `notion-fetch` op de Dagboek pagina om de lijst van subpagina's te zien. Haal de meest recente op (hoogste datum in de titel).

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

Als er geen daglog bestaat (eerste keer), zeg dan:
> "Nog geen eerdere logs gevonden. Ik maak vanavond de eerste aan via /ikgaslapen."

## Toon
- Kort en direct — geen lange uitleg
- Nederlands
- Maximaal 150 woorden
