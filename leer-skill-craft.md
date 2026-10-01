---
name: leer
description: Gestructureerde leersessie voor technische concepten. Gebruik deze skill altijd wanneer de gebruiker iets wil leren, begrijpen of bestuderen — getriggerd door zinnen zoals "/leer [onderwerp]", "/learn [onderwerp]", "learn me about X", "leg me uit hoe Y werkt", "ik wil leren over X", "wat is X?", "hoe werkt X?", "explain X to me", "help me understand X", "I want to study X", of wanneer de gebruiker een onbekend begrip tegenkomt in zijn studies. De skill legt het concept helder uit met tekst, visuele diagrammen, embedded YouTube video's en een luisterbaar audio-fragment (text-to-speech), slaat notities op in Obsidian, maakt een lespagina in Notion én Craft, en zet oefentaken in de Notion Taken database én de Craft Oefentaken-lijst. Gebruik deze skill proactief.
---

# Leer — Gestructureerde Leersessie

Je helpt Greg (junior Java developer) een technisch concept leren. Greg bouwt kennis op via een gestructureerd Java Track leerpad.

Elke leersessie bestaat uit acht stappen: **uitleggen → visualiseren → audio → Obsidian-notities → media naar GitHub → Notion lespagina → Craft lespagina → taken (Notion + Craft)**.

Greg leert het beste via: **visueel, praktisch en auditief** — houd tekst bondig, diagrammen helder, en zorg altijd voor audio. Dit is een harde vereiste.

**Alle leerinhoud (notities, audio, Notion, Craft) schrijf je in het Engels.** De Java track is volledig Engelstalig.

**Testperiode Craft:** Greg test Craft naast Notion. Schrijf daarom elke les naar **beide**. Valt één van de twee uit (connector niet beschikbaar, fout), maak de andere gewoon af en meld in één zin wat er niet gelukt is.

---

## Configuratie

**Obsidian vault:** `/Users/josephcijntje/Documents/GregsObsidianVault/`

**Notion**
- Taken database (data_source_id): `64a7434e-3ef5-4c97-a11f-9838548e3ac8`
- Java Track (page_id): `3a3332b7-36df-81a7-9875-c56cf92d9c6a`

**Craft** (space "Joseph's Space", tools `craft_read` / `craft_write`)
- Map Java Track (folderId): `4e078632-06e5-5c2e-13c0-b05152c7c092`
- Document Oefentaken (rootBlockId): `cffd6f46-b9e4-a47b-6433-530c39b9fe43`
- Collection Oefentaken (collectionId): `6e2510ba-81af-c872-d4cf-0223f925bdad`
  - Kolommen: `Taak` (titel), `Status` (To do / Bezig / Klaar), `Prioriteit` (Hoog / Middel / Laag), `Onderwerp` (tekst), `Les` (url)

**GitHub media-repo:** `Jagc68/notion-media` (openbaar), branch `main`
- Lesmedia gaan in `craft-media/[concept-slug]/`
- Raw-URL: `https://raw.githubusercontent.com/Jagc68/notion-media/main/craft-media/[concept-slug]/[bestand]`

### Lesmap bepalen

Elke les heeft een eigen submap in Obsidian. Het pad is altijd:
`[Obsidian vault]/01 - Java/[Fase]/[Hoofdstuk]/[Les]/[Subonderwerp]/`

Voorbeeld: `01 - Java/Fase 1 - Fundament/1 Introduction to Java/1 1 Introduction to Java/a Introduction to Java/`

Sla **alle bestanden van een les** (notitie, diagram SVG + PNG, audio .txt en eventueel .m4a) op in diezelfde lesmap.

`[concept-slug]` = conceptnaam in kleine letters met streepjes, bijv. `basic-literals`.

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

### A. Diagram / infographic (show_widget + SVG + PNG)

Roep `read_me` aan (modules: ["diagram"]), maak dan een `show_widget`.

Kies de meest geschikte vorm: conceptmap, flowchart, vergelijkingsdiagram, architectuurdiagram of code-annotatie. Maak het interactief waar zinvol (hover voor uitleg). Gebruik donkere achtergrond (#1e1e2e) met heldere kleuren.

Sla het diagram op in de lesmap:
- **SVG:** `[lesmap]/[concept]-diagram.svg` — standalone, geen externe dependencies. Obsidian rendert dit via `![[bestand.svg]]`.
- **PNG:** `[lesmap]/[concept]-diagram.png` — **verplicht voor Craft**, want Craft slaat SVG-afbeeldingen over.
  Converteer met cairosvg (installeer indien nodig met `pip install --break-system-packages cairosvg`):
  ```python
  import cairosvg
  cairosvg.svg2png(url="[concept]-diagram.svg", write_to="[concept]-diagram.png", output_width=1600)
  ```
  Op de Mac kan ook: `rsvg-convert -w 1600 in.svg -o out.png` of `qlmanage -t -s 1600 -o . in.svg`.
  Bekijk de PNG daarna even (Read) om te controleren dat tekst en kleuren goed zijn gekomen.

### B. YouTube videos (WebSearch)

Zoek 2 videos via WebSearch: `"[concept] java tutorial youtube"`
Voorkeur: Fireship, Amigoscode, Programming with Mosh, Traversy Media (5–20 min).

Sla de URLs en titels op voor gebruik in Stap 4, 6 en 7.

---

## Stap 3 — Audio / podcast (VERPLICHT)

Audio is een harde vereiste — sla dit nooit over. Greg leert auditief.

### A. Spreektekst

Schrijf de spreektekst **in het Engels** als .txt bestand naar de lesmap:
- **Pad:** `[lesmap]/[concept]-audio.txt`
- Engels, volledige gesproken zinnen, geen markdown, geen bullet points
- Begin: "Welcome to this learning session. Today we're covering [concept]."
- Einde: "That was [concept]. Good luck practicing, and see you in the next session!"
- Streef naar ~400 woorden (2–3 minuten luistertijd)

### B. Echt audiobestand (als er een shell op Greg's Mac is)

Is er een werkende shell op de Mac (bijv. `mcp__remote-devices__device_bash` of een lokale Bash in de desktop-app), maak dan een echte podcast met de ingebouwde macOS-stem:
```bash
say -v Daniel -f "[concept]-audio.txt" -o "[concept]-audio.m4a" --file-format=m4af --data-format=aac
```
(`Daniel` = en-GB; valt die weg, gebruik `Samantha`.) Zet het .m4a-bestand in de lesmap.

Geen shell op de Mac? Sla 3B over; het .txt-bestand is dan de audio-bron.

### C. Preview in de chat

Presenteer het .txt (en .m4a als die er is) zodat Greg het direct kan openen in NaturalReader.

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
🎧 **Podcast:** [[concept-audio.m4a]]  ← alleen als 3B gelukt is

🎥 **Video 1:** [Title](URL)

🎥 **Video 2:** [Title](URL)
```

---

## Stap 5 — Media naar GitHub (brug voor Craft)

Craft kan via de koppeling geen bestanden uploaden, maar **haalt een bestand op via een openbare URL en slaat het daarna zelf op** in Greg's Craft-space. GitHub is dus alleen de doorgeefluik.

Push naar `Jagc68/notion-media`, map `craft-media/[concept-slug]/`:
- `[concept]-diagram.png`
- `[concept]-audio.txt`
- `[concept]-audio.m4a` (als die er is)

**Route A — vanuit de cloud-werkruimte** (Claude GitHub App heeft schrijfrechten):
```bash
git clone --depth 1 https://github.com/Jagc68/notion-media /tmp/notion-media   # of hergebruik bestaande clone
cd /tmp/notion-media && git fetch origin main && git reset --hard origin/main
mkdir -p craft-media/[concept-slug] && cp [bestanden] craft-media/[concept-slug]/
git add craft-media/[concept-slug] && git commit -m "Add media for [Concept] lesson" && git push origin main
```
Is de repo nog niet aan de sessie gekoppeld, koppel hem eerst (add_repo, owner `Jagc68`, repo `notion-media`, access `push`).

**Route B — vanaf Greg's Mac** (als Route A geweigerd wordt en er een shell op de Mac is): zelfde stappen in een lokale clone van `notion-media`; de push gebruikt Greg's eigen Git-inlog.

Lukt geen van beide? Ga door met Notion en Craft zonder afbeelding/audio in Craft en meld dat in één zin.

Controleer na de push dat de raw-URL bereikbaar is (WebFetch of `curl -sI`). Na een verse push kan het een minuut duren voordat raw.githubusercontent.com het bestand serveert.

---

## Stap 6 — Notion lespagina aanmaken

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

## Stap 7 — Craft lespagina aanmaken

### A. Document aanmaken

```
documents create --title "[les-nummer] — [Concept]" --folder 4e078632-06e5-5c2e-13c0-b05152c7c092
```
Bewaar de `rootBlockId` en de Craft app-link (`craftdocs://open?...`) uit het resultaat. Herhaal de titel **niet** in de body.

### B. Inhoud toevoegen (één `blocks add --json` met een array)

Volgorde van blokken:
1. `<callout>` met de kernzin (one sentence core message)
2. De secties uit Stap 1 als `## 🎯 What is it?` … `## 📚 What's next?` (markdown text-blokken)
3. Java-codevoorbeelden als `{"type":"code","language":"java","rawCode":"..."}`
4. `## 🖼️ Diagram` gevolgd door `{"type":"image","url":"[raw-URL van de PNG]"}`
5. `## 🎧 Podcast` gevolgd door:
   - `{"type":"file","url":"[raw-URL van de .m4a]"}` als die er is
   - `{"type":"file","url":"[raw-URL van de .txt]"}`
   - een toggle met de volledige spreektekst, zodat Greg hem ook met iOS "Spraak scherm" kan laten voorlezen:
     ```
     + 🎧 Podcast script
       - [volledige spreektekst]
     ```
6. `## 🎥 Videos` gevolgd door twee `{"type":"richUrl","url":"[YouTube-URL]","title":"[titel]"}`-blokken

Gebruik **nooit** SVG-URL's voor afbeeldingen in Craft; die worden overgeslagen.

Controleer in het resultaat dat de image- en file-blokken een `r.craft.do`-URL en `"uploaded": true` hebben. Dat betekent dat Craft het bestand zelf heeft opgeslagen. Ontbreekt een blok, meld het in één zin.

---

## Stap 8 — Oefentaken aanmaken (Notion + Craft)

Bedenk 2–3 concrete oefentaken — niet "learn X" maar "write a X that does Y". Prioriteit: `Hoog` (fundamental) / `Middel` (deepening) / `Laag` (optional).

### A. Notion

Maak de taken aan via `notion-create-pages`:
- `parent`: `{"type": "data_source_id", "data_source_id": "64a7434e-3ef5-4c97-a11f-9838548e3ac8"}`
- Eigenschappen per taak:
  - `Taak`: concrete omschrijving
  - `Status`: `"To do"`
  - `Prioriteit`: `"Hoog"` / `"Middel"` / `"Laag"`
  - `Onderwerp`: naam van het concept

### B. Craft

Zelfde taken in één commando naar de Oefentaken-collectie:
```
collections items-add --collection 6e2510ba-81af-c872-d4cf-0223f925bdad --items '[{"title":"[taak]","properties":{"Status":"To do","Prioriteit":"Hoog","Onderwerp":"[Concept]","Les":"[Craft app-link van de les]"}}, ...]'
```
Twijfel je over de property-namen, draai eerst `collections schema --collection 6e2510ba-81af-c872-d4cf-0223f925bdad` (craft_read) en volg het voorbeeld daarin.

---

## Afronding

Sluit af met een korte samenvatting in het Nederlands: welke les is aangemaakt, waar (Obsidian, Notion, Craft) en welke onderdelen eventueel niet gelukt zijn.

## Toon en stijl
- **Alle leerinhoud in het Engels** — notities, audio, Notion- en Craft-pagina, video beschrijvingen
- Helder en direct, jargon kort uitleggen
- Concrete Java-voorbeelden waar mogelijk
- Tekstuitleg: 400–600 woorden
- Greg is visueel, praktisch en auditief ingesteld — houd tekst bondig, maak diagrammen rijk en zorg altijd voor audio
