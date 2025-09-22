# Lösungen: Übungsaufgabe - Interaktives Skript mit Argumenten

## 1. Fehlerbehandlung aktivieren

```bash
#!/bin/bash
set -euo pipefail
```

## 2. Benutzereingabe abfragen

```bash
echo -n "Bitte gib deinen Namen ein: "
read NAME
```

## 3. Datum, Uhrzeit und Hostname speichern

```bash
DATUM=$(date +%F)
UHRZEIT=$(date +%T)
HOSTNAME=$(hostname)
```

## 4. Benutzer begrüßen

```bash
echo "Hallo $NAME auf $HOSTNAME!"
```

## 5. Daten in Logdatei schreiben

```bash
LOGDATEI="benutzer.log"
echo "$DATUM $UHRZEIT - Benutzer: $NAME auf $HOSTNAME" >> "$LOGDATEI"
```

## 6. Umgebungsvariablen für 'azubi' anzeigen

```bash
if [[ "$NAME" == "azubi" ]]; then
    echo "Dein HOME-Verzeichnis: $HOME"
    echo "Deine Shell: $SHELL"
fi
```

## 7. Array mit Hinweisen ausgeben

```bash
HINWEISE=(
  "Tipp: Verwende 'man' für Hilfe zu Befehlen."
  "Tipp: Mit 'cd -' kehrst du ins vorherige Verzeichnis zurück."
  "Tipp: 'history' zeigt deine letzten Befehle."
)

for HINWEIS in "${HINWEISE[@]}"; do
    echo "$HINWEIS"
done
```

## 8. Übergabeparameter mit while und shift verarbeiten

```bash
while [[ $# -gt 0 ]]; do
    ARG="$1"
    echo "Verarbeite Argument: $ARG"
    shift
done
```

## 9. case-Anweisung für spezielle Argumente

```bash
for ARG in "$@"; do
  case "$ARG" in
    --debug)
      echo "Debug-Modus aktiviert"
      ;;
    --help)
      echo "Verwendung: skript.sh [--debug] [--help] [weitere Argumente]"
      ;;
    *)
      echo "Unbekanntes Argument: $ARG"
      ;;
  esac
done
```
