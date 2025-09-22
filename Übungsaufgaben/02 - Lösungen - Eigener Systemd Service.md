# Lösungen: Übungsaufgabe - Eigener Systemd Service

## 1. Service-Datei erstellen

Service-Datei öffnen oder neu erstellen:

```bash
# @root
nano /etc/systemd/system/test.service
```

**Nano-Tastaturkürzel:**
- Datei speichern: `Strg + O`, dann mit `Enter` bestätigen
- Nano beenden: `Strg + X`

**Inhalt einfügen:**

```ini
[Unit]
Description=Mein einfacher Service

[Service]
Type=simple
ExecStart=/usr/bin/sleep infinity

[Install]
WantedBy=multi-user.target
```

## 2. Systemd aktualisieren

Systemd aktualisieren, um neuen Service zu erkennen:

```bash
# @root
systemctl daemon-reload
```

## 3. Service aktivieren

Service aktivieren, damit er automatisch startet:

```bash
# @root
systemctl enable test.service
```

**Ausgabe:**
```
Created symlink /etc/systemd/system/multi-user.target.wants/test.service → /etc/systemd/system/test.service.
```

## 4. Service starten

Service starten:

```bash
# @root
systemctl start test.service
```

## 5. Status prüfen

Status des Service überprüfen:

```bash
systemctl status test.service
```

**Beispielhafte Ausgabe:**
```
● test.service - Mein einfacher Service
   Loaded: loaded (/etc/systemd/system/test.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2025-03-16 12:00:00 CET; 10s ago
 Main PID: 12345 (sleep)
    Tasks: 1 (limit: 4915)
   Memory: 120.0K
   CGroup: /system.slice/test.service
           └─12345 /usr/bin/sleep infinity

Mär 16 12:00:00 hostname systemd[1]: Started Mein einfacher Service.
```
