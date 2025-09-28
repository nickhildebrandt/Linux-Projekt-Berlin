# Lösungen: Übungsaufgabe – Benutzer, Gruppen & Berechtigungen

## Aufgabe 1: Arbeite als Administrator und lege einen neuen Benutzer an

**Befehl:**
```bash
sudo adduser alice
```

**Erwartete Ausgabe (gekürzt, interaktiver Dialog):**
```
Adding user `alice' ...
Creating home directory `/home/alice' ...
New password:
Retype new password:
Full Name []:
...
```

---

## Aufgabe 2: Erstelle eine neue Gruppe und füge den Benutzer dieser Gruppe hinzu

**Befehle:**
```bash
sudo addgroup project
sudo usermod -aG project alice
```

**Erwartete Ausgabe:**
```
Adding group `project' (GID 1001) ...
Done.
```

Prüfen mit:
```bash
id alice
```

Beispiel:
```
uid=1001(alice) gid=1001(alice) groups=1001(alice),1002(project)
```

---

## Aufgabe 3: Lege einen gemeinsamen Ordner an, in dem nur Mitglieder der Gruppe lesen und schreiben dürfen

**Befehle:**
```bash
sudo mkdir /srv/project
sudo chgrp project /srv/project
sudo chmod 770 /srv/project
```

**Erwartete Ausgabe:**
```bash
ls -ld /srv/project
drwxrwx--- 2 root project 4096 Mär 20 12:00 /srv/project
```

---

## Aufgabe 4: Erstelle einen zweiten Benutzer, der die Daten im Ordner nur lesen kann

**Befehle:**
```bash
sudo adduser bob
sudo usermod -aG project bob
sudo chmod 750 /srv/project
```

**Erklärung:**
- Besitzer und Gruppe dürfen lesen/schreiben.
- Weitere Mitglieder (wie bob) können nur lesen und ausführen (kein Schreiben).

---

## Aufgabe 5: Entziehe allen anderen Benutzern (außer Besitzer und Gruppe) die Rechte auf diesen Ordner

**Befehl:**
```bash
sudo chmod 770 /srv/project
```

**Erwartete Ausgabe:**
```bash
ls -ld /srv/project
drwxrwx--- 2 root project 4096 Mär 20 12:30 /srv/project
```

---

## Aufgabe 6: Prüfe mit verschiedenen Benutzern, ob die Berechtigungen korrekt greifen

**Befehle:**
```bash
# Als alice (Besitzer) eine Testdatei anlegen
sudo -u alice touch /srv/project/test.txt

# Als bob (nur lesen) Zugriff prüfen
sudo -u bob cat /srv/project/test.txt
sudo -u bob echo "Text" > /srv/project/test.txt   # sollte fehlschlagen
```

**Erwartetes Verhalten:**
- alice kann schreiben und lesen.
- bob kann lesen, aber nicht schreiben.
- andere Benutzer ohne Gruppenmitgliedschaft erhalten "Permission denied".

