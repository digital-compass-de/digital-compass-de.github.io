# Blueprint: n8n-Automation-Builder

## Zweck
Erstellen skalierbarer, wiederverwendbarer n8n-Workflows für flexible E-Book-Produktion und Content-Automation.

---

## Input-Parameter

| Parameter | Typ | Beschreibung | Beispiel |
|-----------|-----|--------------|----------|
| `zweck` | enum | Hauptfunktion | "ebook-produktion" \| "content-distribution" \| "lead-nurturing" |
| `trigger` | enum | Auslöser | "webhook" \| "schedule" \| "manual" \| "form" |
| `datenquellen` | array | APIs/Integrationen | ["notion", "openai", "gmail", "dropbox"] |
| `output_ziele` | array | Wo landet das Ergebnis | ["shopify", "email", "drive", "slack"] |
| `komplexität` | enum | Workflow-Tiefe | "einfach" \| "mittel" \| "komplex" |
| `error_handling` | boolean | Retry-Logik? | true/false |

---

## Output-Struktur
```
workflow-output/
├── workflow.json         # Exportierbarer n8n-Workflow
├── dokumentation.md      # Setup-Anleitung
├── env-template.env      # Benötigte Umgebungsvariablen
├── test-cases.json       # Test-Szenarien
└── flowchart.mmd         # Mermaid-Diagramm des Flows
```

---

## Prozess-Schritte

### Phase 1: Anforderungsanalyse (25%)
1. **User-Story formulieren**: "Als [Rolle] möchte ich [Ziel], damit [Nutzen]"
2. **Datenfluss mappen**: Input → Transformation → Output
3. **Fehler-Szenarien identifizieren**: Was kann schiefgehen?
4. **API-Limits prüfen**: Rate-Limits, Authentifizierung

### Phase 2: Workflow-Design (40%)
1. **Trigger konfigurieren** (Webhook-URL oder Schedule)
2. **Nodes auswählen**:
   - Daten holen (HTTP Request, Datenbank)
   - Verarbeiten (Function, Code-Node)
   - Transformieren (Set, Spreadsheet)
   - Versenden (Email, API-Call)
3. **Error-Handling einbauen**:
   - Try-Catch in Function-Nodes
   - Retry-Logik (3 Versuche, exponentielles Backoff)
   - Fallback-Notifications (Slack/Email)

### Phase 3: Testing & Dokumentation (35%)
1. **Test-Daten erstellen** (JSON-Mockups)
2. **Schritt-für-Schritt-Test**: Jeder Node einzeln prüfen
3. **Edge-Cases testen**: Leere Inputs, zu große Daten, API-Fehler
4. **Dokumentation schreiben**:
   - Setup-Schritte (API-Keys, Credentials)
   - Wartung (was bei Fehlern tun?)
   - Erweiterungsmöglichkeiten

---

## Qualitäts-Checkpoints

- [ ] Workflow ist modular (einzelne Nodes können getauscht werden)
- [ ] Keine hartcodierten Werte (alles über Variablen/Env)
- [ ] Credentials sind in n8n sicher gespeichert, nicht im Code
- [ ] Retry-Logik bei allen externen APIs
- [ ] Logging-Node am Ende für Monitoring

---

## Fehlerbehandlung

| Fehler | Lösung |
|--------|--------|
| API-Rate-Limit | Exponentielles Backoff (1s, 2s, 4s) |
| Authentifizierung fehlgeschlagen | Credential-Check + Benachrichtigung |
| Datenformat passt nicht | Validation-Node vor Verarbeitung |
| Workflow hängt | Timeout-Setting (5 Min max) |

---

## Sicherheits-Regeln

**ABSOLUTE GRENZEN:**
- 🔴 **Niemals** API-Keys in Workflow-JSON exportieren
- 🔴 **Niemals** Kundendaten in Logs speichern
- 🔴 **Niemals** Zahlungs-Daten ohne Verschlüsselung verarbeiten
- 🟡 **Immer** Webhook-URLs mit Secret-Token schützen

---

## Wiederverwendbare Templates

### Template A: E-Book-Produktions-Pipeline
Formular (Titel) → Notion (Datenbank) → OpenAI (Gliederung) →
Freigabe-Request (Email) → Nach Freigabe: Content-Generierung →
PDF-Erstellung → Upload Shopify → Benachrichtigung

### Template B: Content-Kalender-Automation
Airtable (Content-Ideen) → Due-Date-Check → OpenAI (Text generieren) →
Bild-Generierung → Buffer/Schedule → Veröffentlicht-Flag setzen

---

## Beispiel-Workflow-Struktur (Mermaid)

```mermaid
graph TD
    A[Webhook Trigger] --> B{Input valid?}
    B -->|Ja| C[Daten aus Notion holen]
    B -->|Nein| D[Error-Log + Benachrichtigung]
    C --> E[OpenAI: Gliederung erstellen]
    E --> F{Freigabe erhalten?}
    F -->|Ja| G[Content generieren]
    F -->|Nein| H[Warten + Reminder]
    G --> I[PDF erstellen]
    I --> J[Upload zu Shop]
    J --> K[Erfolgs-Benachrichtigung]

