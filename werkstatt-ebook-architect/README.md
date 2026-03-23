# Master eBook Architekt
### eBook Automatisierung mit n8n

## 1. Die Logik-Skizze (Der Master-Workflow)

**EINGANG** (Telegram Bot)<br>
[Nachricht empfangen]<br>
↓<br>
**ROUTER** (Python Code Node)<br>
[Analysiert den Text: Ist es Thema, Kapitel oder Finale?]<br>
[Extrahiert das "Thema" als Suchbegriff]<br>
↓<br>
**WEICHE** (n8n Switch Node)<br>
[Leitet die Daten auf die Routen 1, 2 oder 3]<br>
<br>
## 2. Die 3 Produktionsstraßen (Routen)

**ROUTE 1:** Projekt-Taufe (Befehl: thema: ...)
- Google Sheets (Create): Erstellt das Sheet EBOOK_Projektname.
- OpenAI: Erstellt die Gliederung (5 Kapitel).
- Python (Zerleger): Verwandelt den Textblock der KI in 5 saubere Zeilen für die Tabelle. [1, 2, 3]
- Google Sheets (Append): Schreibt die Kapitelnamen in das neue Sheet.
- Telegram (Feedback): Meldet dir den Erfolg ins Café.
<br>
**ROUTE 2:** Schreib-Modus (Befehl: thema: ..., kapitel: 2)
* Google Drive (Search): Sucht Datei EBOOK_Projektname -> ID gefunden!
* Google Sheets (Read): Holt die Überschrift von Kapitel 2 aus dieser ID.
* OpenAI: Schreibt den Text für Kapitel 2.
* Python (Formatter): Bereinigt den KI-Text (entfernt unnötige Zeichen, korrigiert Abstände). [2, 3]
* Google Sheets (Update): Schreibt den sauberen Text zurück ins Sheet.
* Telegram (Feedback): Meldet: "Kapitel 2 ist im Kasten, Agent!"
<br>
**ROUTE 3:** Finale (Befehl: thema: ..., finale)
+ Google Drive (Search): Sucht Datei EBOOK_Projektname -> ID gefunden!
+ Google Sheets (Read All): Holt alle 5 Kapitel ab.
+ Python (Assembler): Das Herzstück! Klebt alles zusammen, baut das Inhaltsverzeichnis und setzt das Layout. [3]
+ Google Doc (Upload): Erstellt das finale Dokument.
+ Telegram (Abschluss): Schickt dir den Download-Link direkt aufs Handy.
<br>



