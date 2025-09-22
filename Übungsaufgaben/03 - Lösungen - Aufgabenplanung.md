# Lösungen: Übungsaufgabe - Aufgabenplanung

## 1. Crontab für den Root-Benutzer erstellen

Mit folgendem Befehl die Crontab des Root-Benutzers bearbeiten:

```bash
# @root
crontab -e
```

Dann folgende Zeile hinzufügen, um jede Stunde den Befehl `echo "Hallo Welt"` auszuführen:

```cron
0 * * * * echo "Hallo Welt"
```

Anschließend die Datei speichern und den Editor beenden.

## 2. Systemd-Service und Timer erstellen

### a) Service-Datei erstellen

Mit folgendem Befehl die Service-Datei erstellen:

```bash
# @root
nano /etc/systemd/system/test.service
```

**Inhalt eintragen:**

```ini
[Unit]
Description=Test-Service, der "Hallo Welt" ausgibt

[Service]
Type=oneshot
ExecStart=/bin/echo "Hallo Welt"
```

Datei speichern und Nano beenden.

### b) Timer-Datei erstellen

Mit folgendem Befehl die Timer-Datei erstellen:

```bash
# @root
nano /etc/systemd/system/test.timer
```

**Inhalt eintragen:**

```ini
[Unit]
Description=Timer für den Test-Service
Requires=test.service

[Timer]
OnCalendar=hourly
Persistent=true

[Install]
WantedBy=timers.target
```

Datei speichern und Nano beenden.

### c) Systemd neuladen und Timer aktivieren

```bash
# @root
systemctl daemon-reload
systemctl enable --now test.timer
```

### d) Aktive Timer anzeigen

```bash
systemctl list-timers --all
```

Hier sollte der `test.timer` in der Liste erscheinen und angeben, wann er das nächste Mal ausgeführt wird.
