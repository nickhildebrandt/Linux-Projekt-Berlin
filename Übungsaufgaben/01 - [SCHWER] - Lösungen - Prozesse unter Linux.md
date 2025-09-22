# Lösungen: Übungsaufgaben – Prozesse unter Linux (für Fortgeschrittene)

## Aufgabe 1: Liste die fünf Prozesse mit dem höchsten Speicherverbrauch auf

**Befehl:**
```bash
ps aux --sort=-%mem | head -n 5
```

**Erwartete Ausgabe (Beispiel):**
```
PID USER      %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
1234 nick      5.0  2.5 515400 84240 ?        Sl   12:10   2:15 firefox
```

## Aufgabe 2: Zeige alle Kindprozesse eines bestimmten Prozesses (z.B. Shell) an

**Befehl:**
```bash
pstree -p <PID>
```

**Erwartete Ausgabe (Beispiel):**
```
1234 bash
 └─5678 sleep
```

## Aufgabe 3: Ändere die Priorität eines laufenden Prozesses (`sleep`) auf den Nice-Wert 5

**Befehle:**
```bash
pidof sleep
renice -n 5 -p <PID>
```

**Erwartete Ausgabe (Beispiel):**
```
12345: alter Prioritätswert 0, neuer Prioritätswert 5
```

## Aufgabe 4: Überwache CPU- und Speicherverbrauch eines spezifischen Prozesses

**Befehl:**
```bash
pidstat -p <PID> 2 5
```

**Erwartete Ausgabe (Beispiel):**
```
PID    %CPU  %MEM   VSZ  RSS
12345   0.00   0.1 20000 1000
```

## Aufgabe 5: Erzeuge bewusst einen Zombie-Prozess und finde ihn anschließend

**Befehle:**
```bash
bash -c '(sleep 5 & exec sleep 10)'
ps aux | grep defunct
```

**Erwartete Ausgabe (Beispiel):**
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
nick      12346  0.0  0.0      0     0 ?        Zs   12:00   0:00 [bash] <defunct>
```

## Aufgabe 6: Starte einen Hintergrundprozess und beende diesen anschließend über seinen Namen

**Befehle:**
```bash
sleep 400 &
pkill -f sleep
```

**Erwartete Ausgabe:**
```
(keine Ausgabe, Prozess wird beendet)
```

## Aufgabe 6: Starte einen Prozess, der viel CPU-Leistung nutzt, und beende diesen nach Identifikation der PID

**Befehle:**
```bash
stress -c 1 &
top (zum Ablesen der PID)
kill -9 <PID>
```

**Erwartete Ausgabe:**
```
(keine Ausgabe, Prozess wird sofort beendet)
```

## Aufgabe 7: Speichere alle Prozesse eines Benutzers in einer Textdatei

**Befehl:**
```bash
ps -u BENUTZERNAME > prozesse.txt
```

**Erwartete Ausgabe:**
```
Datei prozesse.txt mit der Liste der Prozesse des Benutzers
```


