# Blueprint: Ebook-Creator-Agent

## Zweck
Autonomes Erstellen von professionellen E-Books nach vorgegebenem Titel und Zi>

---

## Input-Parameter

| Parameter | Typ | Beschreibung | Beispiel |
|-----------|-----|--------------|----------|
| `titel` | string | Haupttitel des E-Books | "KI für Anfängerinnen" |
| `untertitel` | string | Optionaler Untertitel | "Wie du deinen Alltag smart automatisierst" |
| `zielgruppe` | enum | Erfahrungslevel | "anfänger" \| "fortgeschritten" \| "expertin" |
| `themen` | array | 3-5 Hauptkapitel | ["Grundlagen", "Tools", "Automation", "Ethik"] |
| `tonfall` | enum | Schreibstil | "ermutigend" \| "sachlich" \| "pragmatisch" |
| `seitenzahl` | number | Ziel-Umfang | 25-50 Seiten |
| `cta_ziel` | string | Call-to-Action am Ende | "Newsletter-Anmeldung", "Kurs-Kauf" |



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

### Phase 1: Strukturierung (20%)
1. **Gliederung erstellen** basierend auf `themen`
2. **Seitenzahl verteilen** pro Kapitel (Einleitung 10%, Hauptteil 70%, Fazit >
3. **Lernziele definieren** pro Kapitel (Was soll die Leserin können?)
4. **Freigabe einholen** vor Textproduktion

### Phase 2: Content-Produktion (60%)
1. **Einleitung schreiben**: Problem → Lösung → Versprechen
2. **Hauptkapitel**:
   - Theorie-Block (max. 30%)
   - Praxis-Beispiel (40%)
   - Übung/Aufgabe (30%)
3. **Zwischen-Fazits** nach jedem Kapitel
4. **Finale CTA** am Ende

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
- [ ] CTA ist klar, aber nicht aufdringlich

---

## Fehlerbehandlung

| Fehler | Lösung |
|--------|--------|
| Titel zu generisch | Nach USP fragen ("Was macht dieses E-Book einzigartig?">
| Zielgruppe unklar | Persona-Fragebogen durchgehen |
| Zu theoretisch | 50% mehr Praxis-Beispiele einbauen |
| Zu lang | Kapitel splitten oder kürzen |

---

## n8n-Integration

**Trigger:** Webhook von Kurs-Plattform oder manueller Start
**Workflow:**
1. Input validieren → 2. Struktur generieren → 3. Freigabe-Request → 4. Conten>

**Output:** Download-Link oder direkter Upload zu Shopify/Kajabi

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
[Zusammenfassung + CTA]




