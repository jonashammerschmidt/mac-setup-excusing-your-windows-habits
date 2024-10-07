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


# Sound
`System-Settings -> Sound -> Play Sound on startup` -> uncheck

# Weitere Shortcuts

## System-Settings

In `System-Settings -> Keyboard -> Keyboard Shortcuts` sollten noch ein paar weiteres Änderungen gemacht werden, um mehr Shortcuts auf die gewohnten Windows-Tastenkombinationen zu ändern:

- "Mission Control
  - Show Desktop: `WIN + D`
  - Mission Control: Win + Tab
  - Application windows: Uncheck
  - Mission Control -> Move left a space: Uncheck
  - Mission Control -> Move right a space: Uncheck
- "Screenshots -> Screenshot and recording options": `WIN + Shift + S`
- "Services -> Searching -> Search With Google": Uncheck 
- "Function Keys -> Use F1, F2, ...": Check
- "Input Sources -> Uncheck everything!!!"

## Rectangle: Andock-Bereiche für Fenstern

Um das bekannte Andocken von Programmfenstern auch auf Mac zu erhalten ist das Tool "Rectangle" zu installieren:

```
brew install --cask rectangle
```

Für die optimale Windows-Nachahmung sind folgenden Konfigurationen in Rectangle zu treffen:

- "Left Half": `WIN + Pfeiltaste Links`
- "Right Half": `WIN + Pfeiltaste Rechts`
- "Center Half": `WIN + Pfeiltaste unten`
- "Maximize": `WIN + Pfeiltaste oben`
- "Settings Tab -> Launch on login": Check
- "Settings Tab -> Hide menu bar icon": Check

Falls bestimmte Keybinds nicht funktionieren muss in den Einstellungen von Rectangle `remove Keyboard shortcut restrictions` ausgewählt werden.
## Maccy: Zwischenablagen-Historie

Um die Windows-Zwischenablagen-Historie auch auf Mac zu bekommen ist das Tool "Maccy" zu installieren:

```
brew install --cask maccy
```

Für die optimale Windows-Nachahmung sind folgenden Konfigurationen in Maccy zu treffen:

"Preferences":
- "General -> Open": `WIN + V`
- "General -> Launch at login": Check
- "General -> Behaviour -> Paste automatically": Check
- "Appearance -> Image height": 30
- "Appearance -> Number of items": 30
- "Appearance -> Show menu icon": Uncheck
- "Advanced -> Avoid taking application focus": Check

# Scrolling

Damit das Mausrad der Maus in die gewohnte Richtung scrollt UND das Trackpad weiterhin die "intuitive" Richtung beibehält, müssen folgende Einstellungen in Karabiner-Elements vorgenommen werden.

- "Devices" -> "Modify events" bei angeschlossener Maus -> "Flip mouse vertical wheel"
- "Devices" -> "Modify events" bei angeschlossener Maus -> "Flip mouse horizontal wheel"

![image.png](/.attachments/image-44e1eb31-8933-4ff9-9e15-62052904b48a.png =350x)


# Dock

Folgende Einstellungen sollten für das Dock getroffen werden:

- "System-Settings -> Desktop & Dock -> Show suggested and recent apps in Dock": Uncheck

Dies räumt das Dock ein wenig mehr auf. Wenn nun noch Trenner in das Dock hinzugefügt werden sollen, dann kann der folgenden Befehl ausgeführt werden:

```
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="small-spacer-tile";}'; killall Dock

killall Dock
```

Für mehr Divider den ersten Befehl mehrfach ausführen vor dem  `killall Dock`.

Falls du das Dock lieber links oder rechts anbinden möchtest, kannst du mit Rechtsklick auf dem Dock unter "Position On Screen" dies einstellen.

# Finder

Empfohlene Einstellungen: <br>
![image.png](/.attachments/image-0f4a5507-c715-4690-982f-f961876dbc31.png =500x)

(Dafür: Finder öffnen -> dann in der **Leiste am oberen Rand**, neben dem Apple Logo: Finder auswählen  -> und dann `Settings` anklicken!)
- "Finder-Settings -> General -> New Finder windows show": Home-Verzeichnis
- "Finder-Settings -> Sidebar": _Aufräumen_
- "Finder-Settings -> Advanced"
  - "Show all filename extensions": Check
  - "When performing a search": Search the Current Folder

In der **Leiste oben** befindet sich auch `View`. <br>
Achtung: Finder muss das aktive Fenster sein. 
- "View -> as List": Check
- "View -> Show Tab Bar": Check
- "View -> Show Status Bar": Check
- "View -> Show Path Bar": Check
- "View -> Show View Options": Check
- "View Options -> Use as Defaults"
- "View -> Show View Options": Uncheck

Im Terminal folgendes ausführen, damit **versteckte Dateien** angezeigt werden:
- `defaults write com.apple.Finder AppleShowAllFiles true; killall Finder `

# Shortcuts und Automator
- ermöglicht das Automatisieren von verschiedenen Apps, inklusive dem Terminal
- mögliche Beispiele [hier](https://gist.github.com/Taekaze/d97c6f5d0af72913a5c6ae451e5ec306)
  - Die Anwendung `Shortcuts` öffnen und per Plus-Icon ein neues Shortcut erzeugen
  - Terminal-Step auswählen, Beispiel kopieren und einfügen, z.B. <br>
![image.png](/.attachments/image-a4a5ad05-0144-4485-acb4-88b05274fc2f.png =500x)
- erstellte Shortcuts sind über verschiedene Wege zu erreichen
  - Shortcuts können per Spotlight gefunden und ausgeführt werden
  - Folgende weitere Möglichkeiten bestehen:<br>
![image.png](/.attachments/image-296bb893-6328-4c8b-8143-3c9db98394ce.png =200x)
- Ihr müsst bei Keyboard Shortcuts selbst auf Konflikte achten
- Alternativ dazu bietet Automator ähnliche Funktionalität für komplexere Fälle

# Sonstige Empfehlungen

- Repeat character while key held: `defaults write -g ApplePressAndHoldEnabled -bool false`
- System Settings -> Desktop & Dock
  - Minimize windows: Scale Effect
  - Show suggested and recent apps in Dock: Uncheck
  - Minimise windows into application icon: Uncheck
  - Click wallpaper to reveal desktop: Only in Stage Manager
- System Settings -> Accessibility -> Display -> Pointer -> 'Shake mouse pointer to locate' deaktivieren 


