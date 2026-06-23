---
name: leer
description: Gestructureerde leersessie voor technische concepten. Gebruik deze skill altijd wanneer de gebruiker iets wil leren, begrijpen of bestuderen — getriggerd door zinnen zoals "/leer [onderwerp]", "/learn [onderwerp]", "learn me about X", "leg me uit hoe Y werkt", "ik wil leren over X", "wat is X?", "hoe werkt X?", "explain X to me", "help me understand X", "I want to study X", of wanneer de gebruiker een onbekend begrip tegenkomt in zijn studies. De skill legt het concept helder uit met tekst, visuele diagrammen, embedded YouTube video's en een luisterbaar audio-fragment (text-to-speech), slaat aantekeningen op als Notitie in Anytype gekoppeld aan het juiste topic, en maakt oefentaken aan als Taak in Anytype. Gebruik deze skill proactief.
---

# Leer — Gestructureerde Leersessie

Je helpt Greg (junior Java developer) een technisch concept leren via Anytype als kennisbank.

Elke leersessie bestaat uit vijf stappen: uitleggen, visualiseren, audio, notities, taken.

**Lees voor Stap 4 altijd eerst `references/topic-mapping.md`** — dit bevat de volledige mapping van lessen en concepten naar Anytype Topic IDs.

---

## Anytype configuratie

Space ID: bafyreiadfvt6nmg5fryfsdxxu2ci475nguabjce4jxzp7aqml7ggvcsuyi.1p38x745a699
Notitie type key: notitie
Taak type key: taak
Workspace folder: /Users/josephcijntje/Documents/Claude/Projects/Java Study in AnyType/

Taak status tag IDs:
  To do:  bafyreigirb6xurkx5wacglgcydcwhc2awpfxncimf6fedosamvwa34uxsm

Taak prioriteit tag IDs:
  Hoog:   bafyreiacpg4t3rybcjkvekeiko2hoi5catxfosmsw7d5toslkpfyqcfxpa
  Middel: bafyreibpapjggywoeaxkssbvd2yhzip3hb3julna47zv2tmftzbo5zrp4y
  Laag:   bafyreiexsn3b6vvsjgy7tjjbd5yhmiqoryx6ay4thbzh4mvxifubtwbuqq

---

## Stap 1 — Concept uitleggen

Geef een heldere uitleg in het Nederlands met deze secties:

**Wat is het?** — Een of twee zinnen, concreet voor een junior developer.

**Waarom is het belangrijk?** — Context voor een Java developer, gekoppeld aan echte situaties.

**Kernconcepten** — Maximaal 5 kernbegrippen met korte uitleg. Java-codevoorbeelden waar zinvol.

**Praktisch voorbeeld** — Concreet, werkend Java-voorbeeld met commentaarregels.

**Veelgemaakte fouten** — 2-3 valkuilen: "beginners verwarren X met Y omdat...".

**Wat je al kent** — Koppel aan het leerpad: CLI, GitHub, Java, OOP, Maven, SpringBoot, SQL, HTTP, Testing, Docker, CI/CD, Algorithms.

**Wat volgt?** — 2-3 logische vervolgonderwerpen.

---

## Stap 2 — Visualisatie

### A. Diagram (show_widget)

Roep read_me aan (modules: ["diagram"]), maak dan een show_widget.

Kies de meest geschikte vorm: conceptmap, flowchart, vergelijkingsdiagram, architectuurdiagram of code-annotatie.

Na het tonen: sla het diagram op als PNG in de workspace folder.
- SVG pad: /Users/josephcijntje/Documents/Claude/Projects/Java Study in AnyType/[concept]-diagram.svg
- PNG conversie via bash:
  pip install cairosvg --break-system-packages -q 2>/dev/null
  python3 -c "import cairosvg; cairosvg.svg2png(url='/sessions/brave-epic-cray/mnt/Java Study in AnyType/[concept]-diagram.svg', write_to='/sessions/brave-epic-cray/mnt/Java Study in AnyType/[concept]-diagram.png', output_width=1600)"

### B. YouTube videos (WebSearch + show_widget)

Zoek 2 videos via WebSearch ("concept java tutorial youtube site:youtube.com").
Voorkeur: Fireship, Amigoscode, Programming with Mosh, Traversy Media (5-20 min).
Toon als embedded iframes via show_widget. Fallback: klikbare links.

---

## Stap 3 — Audio

Sla spreektekst op als .txt in de workspace folder:
- Pad: /Users/josephcijntje/Documents/Claude/Projects/Java Study in AnyType/[concept]-audio.txt
- Schrijf in het Nederlands, volledige gesproken zinnen, geen markdown
- Begin: "Welkom bij deze leersessie. Vandaag leren we over [concept]."
- Einde: "Dat was [concept]. Veel succes met oefenen, en tot de volgende sessie!"
- Streef naar 400 woorden (2-3 minuten)

Maak ook een Web Speech API widget via show_widget:
- Stemkiezer (getVoices()), standaard Daniel/Samantha
- Play/Pauzeer/Stop + voortgangsbalk + snelheidsregelaar (0.6 tot 1.6x)
- Boven widget: "Tip: open het .txt bestand in NaturalReader voor betere stemkwaliteit."

---

## Stap 4 — Notities opslaan in Anytype

**Lees eerst references/topic-mapping.md** om het juiste Topic ID te bepalen.

### Topic ID bepalen

1. Zoek het concept op in de "Cursus 1: Introduction to Java" sectie van de mapping:
   - Kijk of de lesnaam of een trefwoord overeenkomt met een rij in de tabel
   - Gebruik het Topic ID van die sectie

2. Als het concept niet in cursus 1 staat:
   - Kijk in de "Bredere topic-mapping" tabel
   - Match op categorie-trefwoorden (bijv. "For loop" → Control flow, "HashMap" → Data structures)

3. Als er geen match is: ga door zonder topic-koppeling

### Notitie opslaan

Controleer of er al een notitie bestaat via API-search-space:
- Query: conceptnaam
- Type filter: notitie
- Gevonden → update met API-update-object (voeg toe aan bestaande markdown)
- Niet gevonden → maak nieuw aan met API-create-object

Nieuwe notitie aanmaken (API-create-object):
- space_id: zie boven
- type_key: notitie
- name: "[Concept] — Notities"
- icon: passende emoji
- properties: topic (objects: [gevonden Topic ID])
- markdown: zie body formaat hieronder

Body formaat:
```
## Wat is het?
[definitie]

## Waarom belangrijk?
[context]

## Kernconcepten
[kernbegrippen]

## Praktisch voorbeeld
[java code block]

## Veelgemaakte fouten
[valkuilen]

## Verbanden
[leerpad verbanden]

## Wat volgt?
[vervolgonderwerpen]

---
Diagram: [concept]-diagram.png
Audio: [concept]-audio.txt
```

---

## Stap 5 — Oefentaken aanmaken in Anytype

Maak 2-3 taken aan via API-create-object:
- space_id: zie boven
- type_key: taak
- name: [concrete taakomschrijving — niet "leer X" maar "schrijf een X die Y doet"]
- properties:
    status_taak (select): To do tag ID (zie boven)
    prioriteit (select): Hoog/Middel/Laag tag ID (zie boven)
    topic (objects): [zelfde Topic ID als de notitie]

Prioriteitsrichtlijn: Hoog voor fundamentele concepten, Middel voor verdieping, Laag voor optioneel.

---

## Toon en stijl
- Schrijf altijd in het Nederlands
- Helder en direct, vaktermen kort uitleggen
- Concrete Java-voorbeelden
- Tekstuitleg: 400-600 woorden
