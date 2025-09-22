# Präsentation bauen mit GNU Troff und MOM

## Voraussetzungen

Installiere zunächst die benötigten Pakete:

```bash
sudo apt install groff grap
```

## Kompilierung

Die Präsentation wird mit folgendem Befehl gebaut:

```bash
pdfmom -G -t -mpic -Kutf8 Präsentation.mom > Präsentation.pdf
```

### Erklärung der Optionen
- `-G`: Aktiviert die Verarbeitung von grap (Diagrammen)
- `-t`: Aktiviert die Verarbeitung von Tabellen
- `-mpic`: Nutzt das pic-Makropaket für Diagramme
- `-Kutf8`: Setzt die Eingabekodierung auf UTF-8

## Bekannte (normale) Warnungen

Beim Kompilieren können folgende Warnungen auftreten. Diese sind normal und können ignoriert werden:

```
troff: Präsentation.mom:1501: can't translate character code 246 to special character ':o' in transparent throughput
troff: Präsentation.mom:1552: can't translate character code 220 to special character ':U' in transparent throughput
troff: Präsentation.mom:1697: can't translate character code 246 to special character ':o' in transparent throughput
troff: Präsentation.mom:1737: can't translate character code 252 to special character ':u' in transparent throughput
troff: Präsentation.mom:1760: can't translate character code 252 to special character ':u' in transparent throughput
troff: Präsentation.mom:1809: can't translate character code 220 to special character ':U' in transparent throughput
troff: Präsentation.mom:1927: can't translate character code 220 to special character ':U' in transparent throughput
```

Diese Meldungen entstehen durch bestimmte Umlaute oder Sonderzeichen im UTF-8-Text und führen in der Regel nicht zu einem fehlerhaften PDF.

## Ergebnis

Nach erfolgreichem Lauf des Befehls findest du die fertige PDF unter:

```
Präsentation.pdf
```
