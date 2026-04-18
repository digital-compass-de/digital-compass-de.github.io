# Blueprint: Youtube-to-Ebook-Creator-Agent

## Zweck
Autonomes Erstellen von professionellen E-Books aus Youtube URL

---

## Input-Parameter
Youtube URL 

---

## Output-Struktur
```
ebook-output/
├── ebook.md              # Vollständiger Markdown-Text
├── struktur.json         # Kapitel-Übersicht mit Seitenzahlen
├── assets/
│   ├── cover-prompt.md   # Midjourney/DALL-E Prompt für Cover
│   └── kapitel-bilder/   # Bild-Prompts pro Kapitel
└── metadaten.yaml        # Titel, Autorin, Keywords, Beschreibung
```


---

## Prozess-Schritte
### Überblick Workflow
| Reihenfolge | Schritt             | Tool                  |
| ----------- | ------------------- | --------------------- |
| 1           | Transkript laden    | yt-dlp                |
| 2           | Struktur erstellen  | OpenRouter (Claude)   |
| 3           | Übersetzen          | OpenRouter (Claude)   |
| 4           | **Review**          | Telegram + GitHub     |
| 5           | **Freigabe**        | Telegram Callback     |
| 6           | **Cover erstellen** | OpenRouter (DALL-E 3) |
| 7           | **PDF fertig**      | Pandoc                |

### Phase 0: Youtube Transcript Download
1. **Download Transcript von URL laden
2. **Entfernen von Time Stamps
3. **Speichern als .txt Datei


### Phase 1: Strukturierung (20%)
1. **Gliederung erstellen** basierend auf `Themen des Transcripts`
2. **Seitenzahl verteilen** pro Kapitel (Einleitung 10%, Hauptteil 70%, Fazit 
3. **Freigabe einholen** vor Textproduktion

### Phase 2: Content-Produktion (60%)
1. **Einleitung schreiben**: Problem → Lösung → Versprechen
2. **Hauptkapitel**:
   - Theorie-Block (max. 40%)
   - Praxis-Beispiel (60%)
3. **Zwischen-Fazits** nach jedem Kapitel

### Phase 3: Optimierung (20%)
1. **Längen-Check**: Seitenzahl anpassen
2. **Lesbarkeit**: Flesch-Reading-Ease > 60
3. **Gender-Check**: Inklusive Sprache
4. **Formatierung**: Markdown-Struktur für PDF-Export

---

## Qualitäts-Checkpoints

- [ ] Titel ist spezifisch und versprechend (nicht generisch)
- [ ] Jedes Kapitel hat mindestens eine "Aha-Moment"-Passage
- [ ] Praxisbeispiele sind relevant für die Zielgruppe "Frauen 30-50"
- [ ] Keine übermäßigen Fachbegriffe ohne Erklärung

---

## Fehlerbehandlung

| Fehler | Lösung |
|--------|--------|
| Titel zu generisch | Nach USP fragen ("Was macht dieses E-Book einzigartig?">
| Zielgruppe unklar | Persona-Fragebogen durchgehen |
| Zu theoretisch | 50% mehr Praxis-Beispiele einbauen |
| Zu lang | Kapitel splitten oder kürzen |

---

## Beispiel-Template

```markdown
# [Titel]

## Einleitung
[Persönliche Geschichte/Problem-Schilderung]

## Kapitel 1: [Thema]
### Was du lernst
- Punkt 1
- Punkt 2

### Theorie
[Erklärung]

### Praxis: [Konkretes Beispiel]
[Schritt-für-Schritt]

### Deine Übung
[Aufgabe]

## Fazit & Nächste Schritte
[Zusammenfassung]



