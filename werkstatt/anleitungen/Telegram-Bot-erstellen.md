# Telegram Bot für n8n, make oder OpenClaw erstellen
### Als Trigger oder für die Kommunikation zwischen User und KI wird oft Telegram benutzt.
Um Telegram für diese Zwecke nutzen zu können benötigt man zunächst einen Telegram Account. 
Mit diesem Account können anschiessend bis zu 20 Bots erstellt werden. 
## Wie viele Bots brauche ich?
Für jede laufende Automatisierung brauche ich einen Bot. Sollen mehrere Automatisierungen gleichzeitig laufen, sagen wir
5 Automatisierungen gleichzeitig, bauche ich 5 Bots. <br>
Läuft aber immer nur EINE Automatisierung, könnten alle 5 Automatisierungen den selben Bot benutzen.

## Schritt für Schritt zum eigenen Telegram Bot
### Schritt 1
Im chat nach BotFather suchen, dem "SuperBot" von Telegram, der neue Bots erstellen kann und mit dem
eigene Bots verwaltet werden können.<br>
<img src="bilder/chatBot-erstellen-1.png" alt="Schritt 1 Telegram Bot" width="300" height="600">

### Schritt 2
<img src="bilder/chatBot-erstellen-2.png" alt="Schritt 2 Telegram Bot" width="300" height="600">

### Schritt 3
<img src="bilder/chatBot-erstellen-3.png" alt="Schritt 3 Telegram Bot" width="300" height="600">

### Schritt 4
<img src="bilder/chatBot-erstellen-4.png" alt="Schritt 4 Telegram Bot" width="300" height="600">

### Schritt 5
<img src="bilder/chatBot-erstellen-5.png" alt="Schritt 5 Telegram Bot" width="300" height="600">

### Schritt 6
<img src="bilder/chatBot-erstellen-6.png" alt="Schritt 6 Telegram Bot" width="300" height="600">

### Schritt 7
Auf COPY klicken und den Token für diesen Bot in die KI Automatisierung einfügen.
<img src="bilder/chatBot-erstellen-7.png" alt="Schritt 7 Telegram Bot" width="300" height="600">

### Schritt 8
<img src="bilder/chatBot-erstellen-8.png" alt="Schritt 8 Telegram Bot" width="300" height="600">

### Schritt 9
<img src="bilder/chatBot-erstellen-9.png" alt="Schritt 9 Telegram Bot" width="300" height="600">

### Schritt 10
<img src="bilder/chatBot-erstellen-10.png" alt="Schritt 10 Telegram Bot" width="300" height="600">

### Schritt 11
<img src="bilder/chatBot-erstellen-11-mybots.png" alt="Schritt 11 Telegram Bot" width="300" height="600">

## Sicherheit
Bots sind public und können von jedem Telegram der Telegram nutzt gefunden werden. Um zu verhindern, das dein Bot
von anderen benutzt werden kann, wird die User ID (also die ID des Accounts, nicht des Bots) in die KI Software 
eingetragen, so das nur mit Bots von diesem Account gearbeitet wird.
#### Abfragen der User ID
Im chat Fenster nach "my_id_bot" suchen, auswählen und auf /start klicken, anschliessend gibt der Bot die User ID zurück.





