# Lösungen: Übungsaufgabe - Benutzer-Log

## 1. Bash-Skript erstellen

```bash
# @user
nano benutzer_log.sh
```

**Inhalt eintragen:**

```bash
#!/bin/bash

# 1. Benutzer nach Namen fragen
echo -n "Bitte geben Sie Ihren Namen ein: "
read BENUTZERNAME

# 2. Aktuelles Datum und Uhrzeit speichern
DATUM=$(date +"%Y-%m-%d %H:%M:%S")

# 3. Informationen in eine Datei schreiben
LOGDATEI="benutzer_log.txt"
echo "$DATUM - Benutzer: $BENUTZERNAME" >> "$LOGDATEI"

# 4. Freundliche Begrüßung ausgeben
echo "Hallo, $BENUTZERNAME! Ihre Anmeldung wurde erfasst."
```

Datei speichern (STRG + O) und Nano beenden (STRG + X).

## 2. Skript ausführbar machen

```bash
# @user
chmod +x ~/benutzer_log.sh
```

## 3. Skript ausführen

```bash
# @user
./benutzer_log.sh
```

**Beispielhafte Eingabe:**
```
Bitte geben Sie Ihren Namen ein: Alex
```

**Erwartete Ausgabe:**
```
Hallo, Alex! Ihre Anmeldung wurde erfasst.
```

## 4. Logdatei überprüfen

```bash
# @user
cat benutzer_log.txt
```

**Beispielhafte Ausgabe:**
```
2025-03-20 14:30:45 - Benutzer: Alex
```
