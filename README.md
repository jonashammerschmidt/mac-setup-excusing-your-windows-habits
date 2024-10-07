# mac-setup-excusing-your-windows-habits

Dieser Guide bietet praktische Anleitungen und Tools, um Mac-Einstellungen oder Programme so anzupassen, dass sie die gewohnten Arbeitsabläufe aus der Windows-Welt beibehalten.

[TOC]

## Homebrew: Der fehlende Paketmanager für macOS

Wir werden viel mit dem Paketmanager "Homebrew" installieren. Hier der Befehl zur Installation, der kopiert werden sollte:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Wichtiger Hinweis:** Sowohl bei dieser Installation, als auch bei anderen Installationen sollte die  **Konsole geprüft werden**, ob man dazu aufgefordert wird noch **weitere Befehle** auszuführen.

_Username durch eigenen Username ergänzen!_

```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/username/.zprofile)
```
```
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Homebrew sendet automatisch Analytics-Daten. Um dies zu verhindern und gleichzeitig zu testen, ob man alles richtig gemacht hat, kann man nach der Installation folgenden Befehl ausführen:

```
brew analytics off
```
Falls an dieser Stelle die Meldung kommt, dass der Befehl nicht erkannt wurde, hat man ggf. **nicht die weiteren Meldungen bei der Installation beachtet**.

## Karabiner-Elements: Tastatur ummappen

Fangen wir mit dem Wichtigsten an. Installiere zunächst das Tool "Karabiner-Elements":

```
brew install --cask karabiner-elements
```

Nun lade folgende Datei herunter:
- [Für Mac-Tastaturen](https://gist.github.com/jonashammerschmidt/5023756948b67009b33afde97f35e383)
- [Für normale Tastaturen](https://gist.github.com/jonashammerschmidt/170d7559139cd3b25c1553a1ea7b9f2a)

Die **json-Datei(en)** sollte(n) in einem Ordner abgelegt werden, der wie folgt erzeugt und geöffnet werden kann:

```
mkdir -p ~/.config/karabiner/assets/complex_modifications
open ~/.config/karabiner/assets/complex_modifications
``` 

Anschließend kann mit Spotlight (Command + Leertaste) das Tool "Karabiner-Elements" gesucht und gestartet werden.

**1. Schritt:**
Nun müssen Profiles für die unterschiedlichen Tastaturen angelegt werden:

![Screenshot 2024-01-26 at 10.43.36.png](/.attachments/Screenshot%202024-01-26%20at%2010.43.36-d1ce0101-267b-4233-8e0a-102e9ea88125.png)

**2. Schritt:** Anschließend aktivieren wir die Tastatur-Remaps:
 - in dem Mac-Keyboard Profile wird das `Mac-Tastatur-Remap` ausgewählt
 - in dem Windows-Keyboard Profile wird das `Windows-Tastatur-Remap` ausgewählt 

![Screenshot 2023-07-10 at 22.28.56.png](/.attachments/Screenshot%202023-07-10%20at%2022.28.56-9b0e227b-0a19-4e64-a710-9967b92aa29a.png =400x)

![Screenshot 2023-07-10 at 22.38.11.png](/.attachments/Screenshot%202023-07-10%20at%2022.38.11-799584da-94c2-4b44-877d-b707b0a6cc27.png =600x)

Jetzt sollte ein Großteil der Windows-Shortcuts wie bekannt funktionieren.

Wenn du gerade schon dabei bist Karabiner einzurichten, dann interessiert dich vielleicht auch, wie du mit dem Mausrad in die gewohnte Richtung scrollen kannst, ohne die Funktion des Trackpads zu verändern. Wie Karabiner-Elements dir dabei helfen kann, erfährst du [hier](https://dev.azure.com/krz-devops/DeveloperGuide/_wiki/wikis/DeveloperGuide/12343/Useful-Stuff#scrolling).

