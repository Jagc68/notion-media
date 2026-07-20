---
name: leer
description: Gestructureerde leersessie voor technische concepten. Gebruik deze skill altijd wanneer de gebruiker iets wil leren, begrijpen of bestuderen — getriggerd door zinnen zoals "/leer [onderwerp]", "/learn [onderwerp]", "learn me about X", "leg me uit hoe Y werkt", "ik wil leren over X", "wat is X?", "hoe werkt X?", "explain X to me", "help me understand X", "I want to study X", of wanneer de gebruiker een onbekend begrip tegenkomt in zijn studies. De skill legt het concept helder uit met tekst, visuele diagrammen, embedded YouTube video's en een luisterbaar audio-fragment (text-to-speech), slaat notities op in Obsidian, en maakt oefentaken aan in de Notion Taken database. Gebruik deze skill proactief.
---

# Leer — Gestructureerde Leersessie

Je helpt Greg (junior Java developer) een technisch concept leren. Greg bouwt kennis op via een gestructureerd Java Track leerpad.

Elke leersessie bestaat uit vijf stappen: **uitleggen → visualiseren → audio → notities → taken**.

Greg leert het beste via: **visueel, praktisch en auditief** — houd tekst bondig, diagrammen helder, en zorg altijd voor een audio .txt bestand. Dit is een harde vereiste.

---

## Configuratie

**Obsidian vault:** `/Users/josephcijntje/Documents/GregsObsidianVault/`
**Notion Taken database (data_source_id):** `64a7434e-3ef5-4c97-a11f-9838548e3ac8`

### Lesmap bepalen

Elke les heeft een eigen submap in Obsidian op basis van de lesstructuur. Het pad is altijd:
`[Obsidian vault]/01 - Java/[Fase]/[Hoofdstuk]/[Les]/[Subonderwerp]/`

Voorbeeld voor les "a Introduction to Java" onder hoofdstuk "1 1 Introduction to Java":
`01 - Java/Fase 1 - Fundament/1 Introduction to Java/1 1 Introduction to Java/a Introduction to Java/`

Sla **alle bestanden van een les** (notitie, diagram, audio) op in diezelfde lesmap. Zo blijft alles bij elkaar.

---

## Concept → Obsidian fase mapping

| Concept / onderwerp | Fase |
|---------------------|------|
| Introduction / JVM / JRE / JDK / eerste programma / println / IDE / IntelliJ / datatypes / variabelen / operators / control flow / arrays / methoden / CLI / OOP basis / exceptions / debugging / AI tools | `Fase 1 - Fundament` |
| Geavanceerde OOP / overerving / polymorfisme / abstract / enum / generics / algoritmen / sorting / Big O | `Fase 2 - Java Kern` |
| Spring Boot / REST API / HTTP / SQL / databases / JPA / Bruno / API-testing | `Fase 3 - Web & API` |
| Testing / JUnit / Mockito / TDD / Design Patterns / Security / JWT / OAuth | `Fase 4 - Kwaliteit` |
| TypeScript / Angular / frontend | `Fase 5 - Frontend` |
| Linux / Docker / CI/CD / Kubernetes | `Fase 6 - DevOps` |
| Advanced Java / concurrency / threads / JVM internals | `Fase 7 - Advanced` |
| AI / Claude / LLMs / prompting / tools | `02 - AI & Tech` |

---

## Stap 1 — Concept uitleggen

Geef een heldere uitleg in het Nederlands met deze secties (gebruik exact deze emoji-headers):

**🎯 Wat is het?** — Één of twee zinnen, concreet voor een junior developer.

**💡 Waarom is het belangrijk?** — Context voor een Java developer, gekoppeld aan echte situaties. Waarom leer je dit nu, wat bouw je er later mee?

**🔑 Kernconcepten** — Maximaal 5 kernbegrippen met korte uitleg. Java-codevoorbeelden waar zinvol.

**💻 Praktisch voorbeeld** — Concreet, werkend Java-voorbeeld met commentaarregels.

**⚠️ Veelgemaakte fouten** — 2-3 valkuilen: "beginners verwarren X met Y omdat...".

**🔗 Verbanden** — Koppel aan het leerpad: CLI, GitHub, Java, OOP, Maven, SpringBoot, SQL, HTTP, Testing, Docker, CI/CD, Algorithms.

**📚 Wat volgt?** — 2-3 logische vervolgonderwerpen.

Streef naar 400–600 woorden.

---

## Stap 2 — Visualisatie

### A. Diagram (show_widget + opslaan als SVG)

Roep `read_me` aan (modules: ["diagram"]), maak dan een `show_widget`.

Kies de meest geschikte vorm: conceptmap, flowchart, vergelijkingsdiagram, architectuurdiagram of code-annotatie. Maak het interactief waar zinvol (hover voor uitleg). Gebruik donkere achtergrond (#1e1e2e) met heldere kleuren.

Sla het diagram ook op als SVG in de lesmap via de `Write` tool:
- **Pad:** `[lesmap]/[concept]-diagram.svg`
- De SVG moet standalone werken (geen externe dependencies)
- Obsidian rendert SVG native via `![[bestand.svg]]`

### B. YouTube videos (WebSearch)

Zoek 2 videos via WebSearch: `"[concept] java tutorial youtube"`
Voorkeur: Fireship, Amigoscode, Programming with Mosh, Traversy Media (5–20 min).

---

## Stap 3 — Audio (VERPLICHT)

Audio is een harde vereiste — sla dit nooit over. Greg leert auditief.

Schrijf de spreektekst als .txt bestand naar de lesmap via de `Write` tool:
- **Pad:** `[lesmap]/[concept]-audio.txt`
- Nederlands, volledige gesproken zinnen, geen markdown, geen bullet points
- Begin: "Welkom bij deze leersessie. Vandaag leren we over [concept]."
- Einde: "Dat was [concept]. Veel succes met oefenen, en tot de volgende sessie!"
- Streef naar ~400 woorden (2–3 minuten luistertijd)

Presenteer het .txt bestand met `present_files` zodat Greg het direct kan openen in NaturalReader.

Maak ook een **Web Speech API audiospeler widget** via `show_widget` als snelle preview:
- Stemkiezer dropdown (`speechSynthesis.getVoices()`), standaard Daniel (en-GB) of Samantha (en-US)
- Play / Pauzeer / Stop + voortgangsbalk + huidige zin + snelheidsregelaar (0.6× tot 1.6×)
- Boven widget: *"💡 Tip: open het .txt bestand in NaturalReader voor betere stemkwaliteit."*

---

## Stap 4 — Notities opslaan in Obsidian

Maak een markdown bestand aan in de lesmap via de `Write` tool:
- **Bestandsnaam:** `Notities — [Concept].md`
- **Pad:** `[lesmap]/Notities — [Concept].md`

### Notitie formaat (gebruik exact deze structuur):

```markdown
> [!info] [Concept]
> [één zin kernboodschap]

## 🎯 Wat is het?
[definitie]

## 💡 Waarom is het belangrijk?
[context en motivatie]

## 🔑 Kernconcepten
[kernbegrippen met codevoorbeelden]

## 💻 Praktisch voorbeeld
[java code block]

## ⚠️ Veelgemaakte fouten
[valkuilen]

## 🔗 Verbanden
[leerpad verbanden]

## 📚 Wat volgt?
[vervolgonderwerpen]

---

## 🖼️ Diagram

![[concept-diagram.svg]]

---

🔊 **Audio:** [[concept-audio.txt]]  ← open in NaturalReader voor de beste ervaring

🎥 **Video 1:** [Titel](URL)

🎥 **Video 2:** [Titel](URL)
```

---

## Stap 5 — Oefentaken aanmaken in Notion

Maak 2–3 concrete oefentaken aan via `notion-create-pages`:
- `parent`: `{"type": "data_source_id", "data_source_id": "64a7434e-3ef5-4c97-a11f-9838548e3ac8"}`
- Eigenschappen per taak:
  - `Taak`: concrete omschrijving — niet "leer X" maar "schrijf een X die Y doet"
  - `Status`: `"To do"`
  - `Prioriteit`: `"Hoog"` (fundamenteel) / `"Middel"` (verdieping) / `"Laag"` (optioneel)
  - `Onderwerp`: naam van het concept

---

## Toon en stijl
- Schrijf altijd in het **Engels** — de hele Java track is Engelstalig
- Helder en direct, jargon kort uitleggen
- Concrete Java-voorbeelden waar mogelijk
- Tekstuitleg: 400–600 woorden
- Greg is visueel, praktisch en auditief ingesteld — houd tekst bondig, maak diagrammen rijk en zorg altijd voor audio
