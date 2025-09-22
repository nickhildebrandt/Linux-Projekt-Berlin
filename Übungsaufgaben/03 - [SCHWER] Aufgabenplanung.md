# Übungsaufgabe - Aufgabenplanung (für Fortgeschrittene)

## 1. Komplexer Systemd-Service

Erstelle einen Systemd-Service unter `/etc/systemd/system/backup.service`, der
als rootein Backup eines Verzeichnisses `/home/` in `/backup` durchführt.

**Befehl zur Erstellung eines Backups:**
```bash
cp -rf /home /backup
```

## 2. Systemd-Timer erstellen

Erstelle und aktiviere eine Systemd-Timer-Unit
`/etc/systemd/system/backup.timer`, die den Service `backup.service` einmal
täglich startet.
