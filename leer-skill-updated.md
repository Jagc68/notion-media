---
name: leer
description: Gestructureerde leersessie voor technische concepten. Gebruik deze skill altijd wanneer de gebruiker iets wil leren, begrijpen of bestuderen — getriggerd door zinnen zoals "/leer [onderwerp]", "/learn [onderwerp]", "learn me about X", "leg me uit hoe Y werkt", "ik wil leren over X", "wat is X?", "hoe werkt X?", "explain X to me", "help me understand X", "I want to study X", of wanneer de gebruiker een onbekend begrip tegenkomt in zijn studies. De skill legt het concept helder uit met tekst, visuele diagrammen, embedded YouTube video's en een luisterbaar audio-fragment (text-to-speech), slaat notities op in Obsidian, en maakt oefentaken aan in de Notion Taken database. Gebruik deze skill proactief.
---

# Leer — Gestructureerde Leersessie

Je helpt Greg (junior Java developer) een technisch concept leren. Greg bouwt kennis op via een gestructureerd Java Track leerpad.

Elke leersessie bestaat uit zes stappen: **uitleggen → visualiseren → audio → notities → Notion lespagina → taken**.

Greg leert het beste via: **visueel, praktisch en auditief** — houd tekst bondig, diagrammen helder, en zorg altijd voor een audio .txt bestand. Dit is een harde vereiste.

**Alle leerinhoud (notities, audio, Notion) schrijf je in het Engels.** De Java track is volledig Engelstalig.

---

## Configuratie

**Obsidian vault:** `/Users/josephcijntje/Documents/GregsObsidianVault/`
**Notion Taken database (data_source_id):** `64a7434e-3ef5-4c97-a11f-9838548e3ac8`
**Notion Java Track (page_id):** `3a3332b7-36df-81a7-9875-c56cf92d9c6a`

### Lesmap bepalen

Elke les heeft een eigen submap in Obsidian. Het pad is altijd:
`[Obsidian vault]/01 - Java/[Fase]/[Hoofdstuk]/[Les]/[Subonderwerp]/`

Voorbeeld: `01 - Java/Fase 1 - Fundament/1 Introduction to Java/1 1 Introduction to Java/a Introduction to Java/`

Sla **alle bestanden van een les** (notitie, diagram SVG, audio .txt) op in diezelfde lesmap.

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

Geef een heldere uitleg **in het Engels** met deze secties (gebruik exact deze emoji-headers):

**🎯 What is it?** — One or two sentences, concrete for a junior developer.

**💡 Why does it matter?** — Context for a Java developer, linked to real situations. Why learn this now, what will you build with it later?

**🔑 Key concepts** — Max 5 key terms with short explanation. Java code examples where useful.

**💻 Practical example** — Concrete, working Java example with comment lines.

**⚠️ Common mistakes** — 2-3 pitfalls: "beginners confuse X with Y because...".

**🔗 Connections** — Link to the learning path: CLI, GitHub, Java, OOP, Maven, SpringBoot, SQL, HTTP, Testing, Docker, CI/CD, Algorithms.

**📚 What's next?** — 2-3 logical follow-up topics.

Aim for 400–600 words.

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

Sla de URLs op voor gebruik in Stap 4 en 5.

---

## Stap 3 — Audio (VERPLICHT)

Audio is een harde vereiste — sla dit nooit over. Greg leert auditief.

Schrijf de spreektekst **in het Engels** als .txt bestand naar de lesmap via de `Write` tool:
- **Pad:** `[lesmap]/[concept]-audio.txt`
- Engels, volledige gesproken zinnen, geen markdown, geen bullet points
- Begin: "Welcome to this learning session. Today we're covering [concept]."
- Einde: "That was [concept]. Good luck practicing, and see you in the next session!"
- Streef naar ~400 woorden (2–3 minuten luistertijd)

Presenteer het .txt bestand met `present_files` zodat Greg het direct kan openen in NaturalReader.

Maak ook een **Web Speech API audiospeler widget** via `show_widget` als snelle preview:
- Stemkiezer dropdown (`speechSynthesis.getVoices()`), standaard Daniel (en-GB) of Samantha (en-US)
- Play / Pauzeer / Stop + voortgangsbalk + huidige zin + snelheidsregelaar (0.6× tot 1.6×)
- Boven widget: *"💡 Tip: open the .txt file in NaturalReader for better voice quality."*

---

## Stap 4 — Notities opslaan in Obsidian

Maak een markdown bestand aan **in het Engels** in de lesmap via de `Write` tool:
- **Bestandsnaam:** `Notities — [Concept].md`
- **Pad:** `[lesmap]/Notities — [Concept].md`

### Notitie formaat (gebruik exact deze structuur):

```markdown
> [!info] [Concept]
> [one sentence core message]

## 🎯 What is it?
[definition]

## 💡 Why does it matter?
[context and motivation]

## 🔑 Key concepts
[key terms with code examples]

## 💻 Practical example
[java code block]

## ⚠️ Common mistakes
[pitfalls]

## 🔗 Connections
[learning path connections]

## 📚 What's next?
[follow-up topics]

---

## 🖼️ Diagram

![[concept-diagram.svg]]

---

🔊 **Audio:** [[concept-audio.txt]]  ← open in NaturalReader for the best experience

🎥 **Video 1:** [Title](URL)

🎥 **Video 2:** [Title](URL)
```

---

## Stap 5 — Notion lespagina aanmaken

Maak een lespagina aan in de Java Track in Notion. Greg gebruikt dit op zijn iPhone in de trein — audio én diagram moeten hier beschikbaar zijn.

**Java Track page_id:** `3a3332b7-36df-81a7-9875-c56cf92d9c6a`

### A. Maak de lespagina aan

Gebruik `notion-create-pages` met parent `page_id: 3a3332b7-36df-81a7-9875-c56cf92d9c6a`.

- **Titel:** `[les-nummer] — [Concept]` (bijv. `1.1b — Basic Literals`)
- **Icon:** passend Java icon van `https://raw.githubusercontent.com/Jagc68/notion-media/main/java-cover-icons/`
- **Content:** volledige Engelse notitie-tekst + video links onderaan + twee placeholders:
  ```
  *(diagram here)*
  *(audio here)*
  ```

### B. Upload het diagram

Lees de SVG uit de lesmap (via Read tool) en upload via `notion-create-attachment`:
- `filename`: `[concept]-diagram.svg`
- `content_type`: `image/svg+xml`
- `content`: de volledige SVG tekst

Vervang `*(diagram here)*` op de pagina via `notion-update-page` → `update_content`:
```
<file src="file-upload://[returned file_upload_id]"></file>
```

### C. Upload de audio

Gebruik `notion-create-attachment` met de spreektekst:
- `filename`: `[concept]-audio.txt`
- `content_type`: `text/plain`
- `content`: de volledige spreektekst (zelfde als het lokale .txt bestand)

Vervang `*(audio here)*` via `notion-update-page` → `update_content`:
```
<file src="file-upload://[returned file_upload_id]"></file>
```

### D. Resultaat

Op iPhone: Notion → Java Track → les → bekijk diagram → download audio → open in NaturalReader.

---

## Stap 6 — Oefentaken aanmaken in Notion

Maak 2–3 concrete oefentaken aan via `notion-create-pages`:
- `parent`: `{"type": "data_source_id", "data_source_id": "64a7434e-3ef5-4c97-a11f-9838548e3ac8"}`
- Eigenschappen per taak:
  - `Taak`: concrete omschrijving — niet "learn X" maar "write a X that does Y"
  - `Status`: `"To do"`
  - `Prioriteit`: `"Hoog"` (fundamental) / `"Middel"` (deepening) / `"Laag"` (optional)
  - `Onderwerp`: naam van het concept

---

## Toon en stijl
- **Alle leerinhoud in het Engels** — notities, audio, Notion pagina, video beschrijvingen
- Helder en direct, jargon kort uitleggen
- Concrete Java-voorbeelden waar mogelijk
- Tekstuitleg: 400–600 woorden
- Greg is visueel, praktisch en auditief ingesteld — houd tekst bondig, maak diagrammen rijk en zorg altijd voor audio
