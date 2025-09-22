# Lösungen: Übungsaufgabe - Remote Logging

## 1. RSyslog: TCP-Weiterleitung aller Lognachrichten

### a) Empfänger konfigurieren

Rsyslog für TCP-Empfang konfigurieren:

```bash
# @root
nano /etc/rsyslog.conf
```

Folgende Zeile einkommentieren oder hinzufügen:

```conf
module(load="imtcp")
input(type="imtcp" port="514")
```

Dann rsyslog neu starten:

```bash
systemctl restart rsyslog
```

### b) Sender konfigurieren

```bash
# @root
nano /etc/rsyslog.conf
```

Am Ende der Datei hinzufügen:

```conf
*.* @@<IP-des-Empfängers>:514
```

(Verwende zwei `@` für TCP; ein `@` wäre UDP.)

Dann rsyslog neu starten:

```bash
systemctl restart rsyslog
```

---

## 2. Lognachrichten mit logger senden und auf Empfang prüfen

Auf dem Sender:

```bash
logger -p local0.info "Testnachricht: local0.info"
logger -p authpriv.warning "Testnachricht: authpriv.warning"
```

Auf dem Empfänger:

```bash
tail -f /var/log/syslog
```

Die Nachrichten sollten dort erscheinen. Je nach System können die Logs auch in `/var/log/messages` oder `/var/log/auth.log` auftauchen.

---

## 3. Lognachrichten in benutzerdefinierte Datei leiten & Logrotate konfigurieren

### a) Rsyslog konfigurieren

```bash
# @root
nano /etc/rsyslog.d/custom.conf
```

Inhalt:

```conf
if ($syslogfacility-text == 'local0') then {
    /var/log/custom.log
    stop
}
```

Datei speichern und rsyslog neustarten:

```bash
systemctl restart rsyslog
```

### b) Logrotate-Konfiguration erstellen

```bash
# @root
nano /etc/logrotate.d/custom
```

Inhalt:

```conf
/var/log/custom.log {
    rotate 4
    weekly
    missingok
    notifempty
    compress
    delaycompress
    create 0640 root adm
}
```

Für Rotation alle 2 Wochen stattdessen:

```conf
    weekly
    prerotate
        [ $(date +%U) -ge 0 ] && [ $(( $(date +%U) % 2 )) -eq 0 ] || exit 0
    endscript
```

---

## 4. Logrotate testen

Testlauf der Konfiguration:

```bash
logrotate --debug /etc/logrotate.d/custom
```

Dabei wird die Konfiguration geprüft, aber keine Dateien werden tatsächlich rotiert. Achte darauf, dass keine Fehlermeldung erscheint.

Wenn alles korrekt eingerichtet ist, sollte beim nächsten passenden Logrotate-Lauf die Datei `/var/log/custom.log` rotiert werden.

