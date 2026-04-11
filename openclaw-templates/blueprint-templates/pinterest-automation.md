# Blueprint: Pinterest-Automation

## Zweck
Vollständige Automatisierung von Pinterest-Marketing: Pin-Erstellung, Text-Optimierung, Scheduling und Performa>

---

## Input-Parameter

| Parameter | Typ | Beschreibung | Beispiel |
|-----------|-----|--------------|----------|
| `kampagne` | string | Themen-Fokus | "KI-Produktivität für Mütter" |
| `pin_typ` | enum | Format | "standard" \| "idea-pin" \| "video-pin" |
| `board_strategie` | enum | Organisations-Modus | "themenbasiert" \| "zielgruppenbasiert" |
| `farbschema` | string | Visuelle Identität | "warm-neutral", "pastell-tech", "minimal-schwarz-weiss" |
| `posting_frequenz` | number | Pins pro Tag | 3-5 empfohlen |
| `seo_keywords` | array | Pinterest-Suchbegriffe | ["KI Tipps", "Produktivität", "Zeitmanagement"] |

---

## Output-Struktur
```
pinterest-output/
├── board-strategie.md        # Board-Konzept + Beschreibungen
├── pin-kalender/
│   ├── woche-01/
│   │   ├── pin-01/
│   │   │   ├── titel.txt
│   │   │   ├── beschreibung.txt
│   │   │   ├── bild-prompt.md
│   │   │   └── link-ziel.url
│   │   └── pin-02/
│   └── woche-02/
├── templates/
│   ├── canva-link.txt        # Oder eigene Design-Vorlagen
│   └── farbpalette.hex
└── analytics-template.csv     # Tracking-Struktur
```

---

## Prozess-Schritte

### Phase 1: Board-Struktur (25%)
1. **Zielgruppen-Recherche**: Was sucht deine ideale Kundin auf Pinterest?
2. **Boards anlegen** (8-10 Boards empfohlen):
   - 3-4 themenbezogene Boards (z.B. "KI für Anfängerinnen")
   - 2-3 lösungsorientierte Boards (z.B. "Mehr Zeit für dich")
   - 2-3 persönliche/Story-Boards (z.B. "Mein Entrepreneur-Journey")
3. **SEO-Optimierung**: Board-Namen und Beschreibungen mit Keywords

### Phase 2: Pin-Produktion (50%)

#### Bild-Erstellung:
- **Format**: 1000x1500px (2:3 Ratio) – optimal für Mobile
- **Text-Overlay**: Max. 20% des Bildes, lesbar auf Mobile
- **Farbschema**: Konsistent zu Marken-Identity
- **Stil**: Hochwertig, "save-worthy", aspirational aber erreichbar

#### Text-Optimierung:
1. **Titel** (max. 100 Zeichen):
   - Keyword vorne platzieren
   - Neugier wecken: "So sparst du 10h/Woche mit KI"
2. **Beschreibung** (max. 500 Zeichen):
   - Erster Satz: Hook mit Keyword
   - Dann: Wertversprechen + Call-to-Save
   - 3-5 relevante Hashtags (nicht zu viele!)
3. **Alt-Text**: Barrierefreiheit + SEO

### Phase 3: Scheduling & Distribution (25%)
1. **Beste Zeiten**:
   - Mo-Fr: 12:00-14:00, 20:00-23:00
   - Sa-So: 9:00-11:00, 20:00-23:00
2. **Tailwind/Buffer-Integration** oder n8n-Scheduling
3. **Fresh-Pins-Strategie**: Neue Bilder bevorzugt (nicht nur Repins)

---

---

## Qualitäts-Checkpoints

- [ ] Jedes Bild ist "save-worthy" (würde ich das speichern?)
- [ ] Titel enthält Haupt-Keyword in den ersten 30 Zeichen
- [ ] Beschreibung liest sich natürlich, nicht keyword-gestopft
- [ ] Link führt zu spezifischem Ziel, nicht nur Homepage
- [ ] Konsistente Branding-Elemente (Farben, Fonts, Logo-Platzierung)

---

## Pinterest-SEO-Regeln

**Keyword-Recherche:**
- Pinterest-Suchvorschläge nutzen (Dropdown)
- Pinterest Trends Tool checken
- Wettbewerber analysieren (was rankt gut?)

**Ranking-Faktoren:**
1. Engagement (Saves > Klicks > Comments)
2. Fresh Content (neue Bilder, nicht Repins)
3. Domain-Qualität (verifizierte Website)
4. Pinner-Qualität (konsistentes Posten)

---

## Fehlerbehandlung

| Fehler | Lösung |
|--------|--------|
| Wenige Impressions | Keywords überprüfen, Bild-Qualität erhöhen |
| Viele Impressions, wenige Klicks | Titel stärker machen, CTA verbessern |
| Board wird nicht gefunden | Board-Beschreibung SEO-optimieren |
| Pin abgelehnt | Community Guidelines checken (kein Clickbait) |

---

## n8n-Automation-Workflow
Trigger (Content-Idee) →
OpenAI (Titel + Beschreibung + Keywords) →
Bild generieren (DALL-E/Midjourney API) →
Canva-Template anpassen (optional) →
Freigabe-Request →
Tailwind API (Scheduling) oder
Manueller Upload →
Tracking-URL generieren


**Besonderheit Pinterest:**
- Rich Pins aktivieren (Produkt-Infos automatisch ziehen)
- Shop-Tab verbinden (falls Shopify vorhanden)

---

## Board-Struktur-Beispiel

| Board-Name | Beschreibung | Pin-Frequenz |
|------------|--------------|--------------|
| KI für Anfängerinnen | Einfache KI-Tools für Frauen, die Zeit sparen wollen | 5x/Woche |
| Produktivität & Zeitmanagement | Smarte Routinen für mehr Lebensqualität | 3x/Woche |
| Online Business Tipps | KI im Business nutzen, skalieren | 4x/Woche |
| Mompreneur Inspiration | Erfolgsgeschichten von Frauen wie du und ich | 2x/Woche |
| Tools & Ressourcen | Die besten KI-Tools getestet | 3x/Woche |

---

## Pin-Text-Templates

**Template A: How-To**
Titel: "Wie du mit KI 10 Stunden/Woche sparst (Schritt-für-Schritt)"
Beschreibung: "Du fühlst dich überfordert von deiner To-Do-Liste?
Mit diesen 3 KI-Tools automatisierst du repetitive Aufgaben
und gewinnst Zeit für das, was wirklich zählt. 💪
Speichern für später! #KI #Produktivität #Zeitmanagement"

**Template B: Listicle**
Titel: "5 KI-Tools, die jede Frau kennen sollte"
Beschreibung: "Nr. 3 hat meinen Alltag komplett verändert!
Swipe für die komplette Liste und sag mir:
Welches Tool testest du als erstes? 👇
#KIFürFrauen #DigitalLife #Effizienz"


---

*Version: 1.0*
*Zuständig: Clara (KI-Kurs Assistentin)*
*Letzte Aktualisierung: 2026-04-10*
