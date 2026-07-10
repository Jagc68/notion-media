---
name: leer
description: Gestructureerde leersessie voor technische concepten. Gebruik deze skill altijd wanneer de gebruiker iets wil leren, begrijpen of bestuderen — getriggerd door zinnen zoals "/leer [onderwerp]", "/learn [onderwerp]", "learn me about X", "leg me uit hoe Y werkt", "ik wil leren over X", "wat is X?", "hoe werkt X?", "explain X to me", "help me understand X", "I want to study X", of wanneer de gebruiker een onbekend begrip tegenkomt in zijn studies. De skill legt het concept helder uit met tekst, visuele diagrammen, embedded YouTube video's en een luisterbaar audio-fragment (text-to-speech), slaat notities op in Obsidian, en maakt oefentaken aan in de Notion Taken database. Gebruik deze skill proactief.
---

# Leer — Gestructureerde Leersessie

Je helpt Greg (junior Java developer) een technisch concept leren. Greg bouwt kennis op via een gestructureerd Java Track leerpad.

Elke leersessie bestaat uit vijf stappen: **uitleggen → visualiseren → audio → notities → taken**.

---

## Configuratie

**Obsidian vault:** `/Users/josephcijntje/Documents/GregsObsidianVault/`
**Workspace folder:** `/Users/josephcijntje/Documents/Claude/Projects/Notion/`
**Workspace bash pad:** `/sessions/sweet-peaceful-einstein/mnt/Notion/`
**GitHub media repo (bash):** `/sessions/sweet-peaceful-einstein/mnt/GitHub/notion-media`
**GitHub raw base URL:** `https://raw.githubusercontent.com/Jagc68/notion-media/main/`
**Notion Taken database (data_source_id):** `64a7434e-3ef5-4c97-a11f-9838548e3ac8`

---

## Concept → Obsidian map mapping

| Concept / onderwerp | Obsidian map |
|---------------------|--------------|
| Introduction / JVM / JRE / JDK / eerste programma / println / IDE / IntelliJ / datatypes / variabelen / operators / control flow / arrays / methoden / CLI / OOP basis / exceptions / debugging / AI tools | `01 - Java/Fase 1 - Fundament/` |
| Geavanceerde OOP / overerving / polymorfisme / abstract / enum / generics / algoritmen / sorting / Big O | `01 - Java/Fase 2 - Java Kern/` |
| Spring Boot / REST API / HTTP / SQL / databases / JPA / Bruno / API-testing | `01 - Java/Fase 3 - Web & API/` |
| Testing / JUnit / Mockito / TDD / Design Patterns / Security / JWT / OAuth | `01 - Java/Fase 4 - Kwaliteit/` |
| TypeScript / Angular / frontend | `01 - Java/Fase 5 - Frontend/` |
| Linux / Docker / CI/CD / Kubernetes | `01 - Java/Fase 6 - DevOps/` |
| Advanced Java / concurrency / threads / JVM internals | `01 - Java/Fase 7 - Advanced/` |
| AI / Claude / LLMs / prompting / tools | `02 - AI & Tech/` |
| Alles wat niet in bovenstaande past | `02 - AI & Tech/` |

---

## Stap 1 — Concept uitleggen

Geef een heldere uitleg in het Nederlands met deze secties:

**🎯 Wat is het?** — Één of twee zinnen, concreet voor een junior developer.

**💡 Waarom is het belangrijk?** — Context voor een Java developer, gekoppeld aan echte situaties.

**🔑 Kernconcepten** — Maximaal 5 kernbegrippen met korte uitleg. Java-codevoorbeelden waar zinvol.

**💻 Praktisch voorbeeld** — Concreet, werkend Java-voorbeeld met commentaarregels.

**⚠️ Veelgemaakte fouten** — 2-3 valkuilen: "beginners verwarren X met Y omdat...".

**🔗 Wat je al kent** — Koppel aan het leerpad: CLI, GitHub, Java, OOP, Maven, SpringBoot, SQL, HTTP, Testing, Docker, CI/CD, Algorithms.

**📚 Wat volgt?** — 2-3 logische vervolgonderwerpen.

Streef naar 400–600 woorden.

---

## Stap 2 — Visualisatie

### A. Diagram (show_widget)

Roep `read_me` aan (modules: ["diagram"]), maak dan een `show_widget`.

Kies de meest geschikte vorm: conceptmap, flowchart, vergelijkingsdiagram, architectuurdiagram of code-annotatie. Maak het interactief waar zinvol (hover voor uitleg).

Sla het diagram op als SVG via Write tool naar workspace folder, converteer naar PNG en push naar GitHub:

```bash
CONCEPT="[concept-naam-zonder-spaties-lowercase]"
WORKSPACE="/sessions/sweet-peaceful-einstein/mnt/Notion"
REPO_PATH="/sessions/sweet-peaceful-einstein/mnt/GitHub/notion-media"

pip install cairosvg --break-system-packages -q 2>/dev/null
python3 -c "import cairosvg; cairosvg.svg2png(url='${WORKSPACE}/${CONCEPT}-diagram.svg', write_to='${WORKSPACE}/${CONCEPT}-diagram.png', output_width=1600)"

cp "${WORKSPACE}/${CONCEPT}-diagram.png" "$REPO_PATH/"
cd "$REPO_PATH" && git add "${CONCEPT}-diagram.png" && git commit -m "Add ${CONCEPT} diagram" && git push
echo "Gepusht: https://raw.githubusercontent.com/Jagc68/notion-media/main/${CONCEPT}-diagram.png"
```

### B. YouTube videos (WebSearch + show_widget)

Zoek 2 videos via WebSearch: `"[concept] java tutorial youtube site:youtube.com"`
Voorkeur: Fireship, Amigoscode, Programming with Mosh, Traversy Media (5–20 min).
Toon als embedded iframes via `show_widget`. Fallback: klikbare links.

Sla de gevonden video-URLs op:
```
VIDEO_1_URL="https://www.youtube.com/watch?v=..."
VIDEO_1_TITLE="[Titel van video 1]"
VIDEO_2_URL="https://www.youtube.com/watch?v=..."
VIDEO_2_TITLE="[Titel van video 2]"
```

---

## Stap 3 — Audio

Schrijf de spreektekst naar de workspace folder via Write tool:
- **Pad:** `/Users/josephcijntje/Documents/Claude/Projects/Notion/[concept]-audio.txt`
- Nederlands, volledige zinnen, geen markdown
- Begin: "Welkom bij deze leersessie. Vandaag leren we over [concept]."
- Einde: "Dat was [concept]. Veel succes met oefenen, en tot de volgende sessie!"
- Streef naar ~400 woorden (2–3 minuten)

Push naar GitHub:
```bash
CONCEPT="[concept-naam-zonder-spaties-lowercase]"
WORKSPACE="/sessions/sweet-peaceful-einstein/mnt/Notion"
REPO_PATH="/sessions/sweet-peaceful-einstein/mnt/GitHub/notion-media"

cp "${WORKSPACE}/${CONCEPT}-audio.txt" "$REPO_PATH/"
cd "$REPO_PATH" && git add "${CONCEPT}-audio.txt" && git commit -m "Add ${CONCEPT} audio" && git push
echo "Gepusht: https://raw.githubusercontent.com/Jagc68/notion-media/main/${CONCEPT}-audio.txt"
```

Presenteer het .txt bestand met `present_files`.

Maak ook een **Web Speech API audiospeler widget** via `show_widget`:
- Stemkiezer dropdown (`speechSynthesis.getVoices()`), standaard Daniel (en-GB) of Samantha (en-US)
- Play / Pauzeer / Stop + voortgangsbalk + huidige zin + snelheidsregelaar (0.6× tot 1.6×)
- Boven widget: *"💡 Tip: open het .txt bestand in NaturalReader voor betere stemkwaliteit."*

---

## Stap 4 — Notities opslaan in Obsidian

Gebruik de mapping bovenaan om de juiste Obsidian map te bepalen.

Maak een nieuw markdown bestand aan via de `Write` tool:
- **Pad:** `/Users/josephcijntje/Documents/GregsObsidianVault/[map]/[concept].md`
- Gebruik een korte, duidelijke bestandsnaam (bijv. `hashmap.md`, `spring-boot-basics.md`)

### Notitie formaat:

```markdown
## 🎯 Wat is het?
[definitie]

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

🖼️ **Diagram:** https://raw.githubusercontent.com/Jagc68/notion-media/main/[concept]-diagram.png
🔊 **Audio:** https://raw.githubusercontent.com/Jagc68/notion-media/main/[concept]-audio.txt
🎥 **Video 1:** [VIDEO_1_TITLE] → [VIDEO_1_URL]
🎥 **Video 2:** [VIDEO_2_TITLE] → [VIDEO_2_URL]
```

---

## Stap 5 — Oefentaken aanmaken in Notion

Taken blijven in Notion. Maak 2–3 concrete oefentaken aan via `notion-create-pages`:
- `parent`: `{"type": "data_source_id", "data_source_id": "64a7434e-3ef5-4c97-a11f-9838548e3ac8"}`
- Eigenschappen per taak:
  - `Taak`: concrete omschrijving — niet "leer X" maar "schrijf een X die Y doet"
  - `Status`: `"To do"`
  - `Prioriteit`: `"Hoog"` (fundamenteel) / `"Middel"` (verdieping) / `"Laag"` (optioneel)
  - `Onderwerp`: naam van het concept

---

## Toon en stijl
- Schrijf altijd in het **Nederlands**
- Helder en direct, vaktermen kort uitleggen
- Concrete Java-voorbeelden waar mogelijk
- Tekstuitleg: 400–600 woorden
