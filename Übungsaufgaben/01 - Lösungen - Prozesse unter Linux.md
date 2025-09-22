# Lösungen: Übungsaufgaben – Prozesse unter Linux

## Aufgabe 1: Alle laufenden Prozesse anzeigen

**Befehl:**
```bash
top
```

**Erwartete Ausgabe (Beispiel):**
```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM   TIME+   COMMAND
  1 root      20   0  167404  11976   9176 S   0.0   0.1   0:00.39 systemd
 88 root      20   0    6608   2616   2372 S   0.0   0.0   0:00.02 cron
```

## Aufgabe 2: PID der aktuellen Shell finden

**Befehl:**
```bash
pgrep bash
```

**Erwartete Ausgabe (Beispiel):**
```
12345
```

## Aufgabe 3: Hintergrundprozess starten

**Befehl:**
```bash
sleep 60 &
```

**Erwartete Ausgabe:**
```
[1] 6789
```

## Aufgabe 4: Prozess mit niedriger Priorität starten

**Befehl:**
```bash
nice -n 10 sleep 30
```

**Erwartete Ausgabe:**
```
(keine unmittelbare Ausgabe, Prozess läuft 30 Sekunden mit niedriger Priorität)
```

## Aufgabe 5: Prozess pausieren und im Hintergrund fortsetzen

**Befehle:**
```bash
sleep 100
(STRG+Z drücken)
bg
```

**Erwartete Ausgabe:**
```
[1]+  Stopped                 sleep 100
[1]+ sleep 100 &
```

## Aufgabe 6: Hintergrundprozess erstellen und kontrolliert beenden

**Befehle:**
```bash
sleep 120 &
pgrep sleep
kill -15 <PID>
```

**Erwartete Ausgabe (Beispiel):**
```
[1] 7890
```
*(Keine weitere Ausgabe; Prozess wird kontrolliert beendet.)*

## Aufgabe 7: Prozess sofort erzwingen zu beenden

**Befehle:**
```bash
sleep 300 &
kill -9 "$(pgrep sleep)"
```

**Erwartete Ausgabe (Beispiel):**
```
[1] 7891
```
*(Keine weitere Ausgabe; Prozess wird sofort beendet.)*


