# Lösungen: Übungsaufgabe - Aufgabenplanung (für Fortgeschrittene)

## 1. Systemd-Service erstellen

Mit folgendem Befehl die Service-Datei erstellen:

```bash
sudo nano /etc/systemd/system/backup.service
```

**Inhalt der Datei:**

```ini
[Unit]
Description=Backup Service
After=network.target

[Service]
Type=oneshot
ExecStart=/bin/bash -c 'cp -r /home/user/daten /backup && echo "Backup completed: $(date)" >> /var/log/backup.log'
ExecStartPost=/bin/bash -c 'echo "Backup-Service beendet: $(date)" >> /var/log/backup.log'
Restart=on-failure
RestartSec=600

[Install]
WantedBy=multi-user.target
```

## 2. Systemd-Timer erstellen

Mit folgendem Befehl die Timer-Datei erstellen:

```bash
sudo nano /etc/systemd/system/backup.timer
```

**Inhalt der Datei:**

```ini
[Unit]
Description=Backup Timer
Requires=backup.service

[Timer]
OnCalendar=02:00
Persistent=true

[Install]
WantedBy=timers.target
```

## 3. Systemd-Daemon neu laden

```bash
sudo systemctl daemon-reload
```

## 4. Timer aktivieren und starten

```bash
sudo systemctl enable --now backup.timer
```

## 5. Status des Timers prüfen

```bash
systemctl list-timers --all
```

## 6. Service manuell starten und Log prüfen

```bash
sudo systemctl start backup.service
cat /var/log/backup.log
```
