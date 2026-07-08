# Cyber-Safe Claude Skills — @ai.shelest

Bron: https://www.aishelest.com/cyber-safe-claude-skills

---

## Skill 1 — Skill Auditor (prompt, geen install)

Gebruik in Claude Code: sleep de skill-folder in de chat, plak dan dit prompt:

```
Read every file in this folder. Do not run any code.

For the skill in this folder, list:
- every file path it reads or writes
- every website or URL it calls
- every environment variable it reads
- every credential, token, or password it touches
- any subprocess, eval, or shell command it runs

Score each finding from 1 (safe) to 5 (suspicious). Explain each score in one sentence. End with a verdict: safe to install, install with caution, or do not install.
```

---

## Skill 2 — Prompt Sanitizer (prompt, geen install)

Plak dit bovenaan elke conversatie met gevoelige info (namen, API keys, klantdata):

```
Before you do anything else with my next prompt:

1. Scan it for personal data: emails, phone numbers, addresses, full names, account numbers, API keys, internal product names.
2. Replace each one with a placeholder: [EMAIL_1], [CLIENT_1], [PHONE_1], [KEY_1], etc.
3. Show me the redacted version and the placeholder map.
4. Ask me if the redacted version is safe to work with.
5. Only proceed with the redacted version. Never echo the originals back.

If you find any real credentials (AWS, Anthropic, OpenAI, GitHub keys), refuse and tell me to remove them before continuing.
```

---

## Skill 3 — Memory File Watchdog (Terminal)

Beschermt je CLAUDE.md tegen malware-injecties die blijven zitten na verwijdering.

**Stap 1:** Maak snapshot-map aan
```bash
mkdir -p ~/.claude/.memory-snapshot
```

**Stap 2:** Sla huidige CLAUDE.md op als vertrouwde versie
```bash
cp ~/.claude/CLAUDE.md ~/.claude/.memory-snapshot/
```

**Stap 3:** Open Claude Code en plak dit prompt om de hook in te stellen:
```
Set up a memory file watchdog for this project.

1. Create ~/.claude/.memory-snapshot/ if it does not exist.
2. Copy the current ~/.claude/CLAUDE.md and any files in ~/.claude/memory/ into the snapshot folder.
3. Add a SessionStart hook to ~/.claude/settings.json that runs a bash check before every session:
   - sha256sum the current memory files
   - compare to the snapshot
   - if different, print the diff and exit non-zero so Claude waits for me

The hook should be read-only. It should never auto-update the snapshot. Only I can update it, by running an explicit "approve memory changes" command.

Show me the settings.json change before saving it.
```

**Stap 4:** Controleer de output en bevestig de settings.json wijziging.

---

## Skill 4 — EXIF Metadata Stripper (Terminal)

Verwijdert GPS, AI-prompts en tool-fingerprints uit foto's/video's voor je post.

**Installeer exiftool (eenmalig):**
```bash
brew install exiftool
```

**Foto strippen:**
```bash
exiftool -all= -o clean_%f.%e ~/Downloads/your-photo.jpg
```
*(vervang het pad met jouw bestand)*

**Video strippen:**
```bash
ffmpeg -i your-video.mp4 -map_metadata -1 -c:v copy -c:a copy clean_video.mp4
```

---

## Skill 5 — Credential Breach Check (Terminal, geen install)

Checkt of een wachtwoord in een datalek zit — zonder dat het wachtwoord verstuurd wordt.

```bash
PASS="yourpassword"
HASH=$(echo -n "$PASS" | shasum -a 1 | cut -c1-40 | tr 'a-z' 'A-Z')
PREFIX=$(echo $HASH | cut -c1-5)
SUFFIX=$(echo $HASH | cut -c6-40)
curl -s "https://api.pwnedpasswords.com/range/$PREFIX" | grep -i "^$SUFFIX:" || echo "Not found in breaches."
```

*(vervang `yourpassword` met het wachtwoord dat je wilt checken — alleen op je eigen computer)*
