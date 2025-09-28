# Lösungen: Kommandozeilen-Basics & Editoren

## Aufgabe 1
Lege in deinem Home-Verzeichnis einen neuen Ordner `uebung` an und wechsle in diesen Ordner.

```bash
mkdir ~/uebung
cd ~/uebung
```

---

## Aufgabe 2
Erstelle darin eine neue Datei `test.txt` und schreibe mit einem Editor einen kurzen Text hinein.

```bash
nano test.txt
# oder:
vim test.txt
```

---

## Aufgabe 3
Zeige dein aktuelles Arbeitsverzeichnis an und überprüfe den Inhalt des Ordners.

```bash
pwd
ls -l
```

---

## Aufgabe 4
Kopiere die Datei `test.txt` in eine neue Datei `kopie.txt` im selben Ordner.

```bash
cp test.txt kopie.txt
```

---

## Aufgabe 5
Verschiebe die Datei `kopie.txt` in ein neu erstelltes Unterverzeichnis `backup`.

```bash
mkdir backup
mv kopie.txt backup/
```

---

## Aufgabe 6
Lösche anschließend den gesamten Ordner `backup`.

```bash
rm -r backup
```

---

## Aufgabe 7
Lege einen symbolischen Link **eine Ebene über** deinem aktuellen Verzeichnis auf `test.txt` an.

```bash
ln -s ~/uebung/test.txt ../link-auf-test.txt
```

---

## Aufgabe 8
Zeige die **ersten 2** und **letzten 10** Zeilen von `test.txt`, sowie einmal die **gesamte** Datei an.

```bash
head -n 2 test.txt
tail -n 10 test.txt
cat test.txt
```

---

## Aufgabe 9
Suche in `test.txt` nach einem bestimmten Wort, das du vorher hineingeschrieben hast.

```bash
grep "WORT" test.txt
```

