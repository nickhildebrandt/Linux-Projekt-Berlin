# Lösungen: ssh & Schlüsselbasierte Anmeldung

## Aufgabe 1
Installiere über apt das Paket openssh-server und stelle sicher, dass der ssh-Dienst über systemd gestartet wird und läuft.

```bash
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh
```

---

## Aufgabe 2
Konfiguriere den ssh-Server so, dass Root-Verbindungen erlaubt sind und maximal 3 fehlgeschlagene Anmeldeversuche sowie höchstens 2 gleichzeitige Verbindungen zugelassen werden.

```bash
sudo nano /etc/ssh/sshd_config
```

Inhalt anpassen:
```
PermitRootLogin yes
MaxAuthTries 3
MaxSessions 2
```

Danach den Dienst neu starten:
```bash
sudo systemctl restart ssh
```

---

## Aufgabe 3
Schließe dich mit einem Partner zusammen und versucht, euch gegenseitig per ssh auf dem jeweils anderen Computer anzumelden und Befehle auszuführen.

```bash
ssh BENUTZER@IP_DES_PARTNERS
```

---

## Aufgabe 4
Erstellt jeweils ein ssh-Schlüsselpaar mit ssh-keygen und kopiert den Public Key eures Partners mit ssh-copy-id auf euren Computer.

```bash
ssh-keygen -t ed25519 -C "mein_schluessel"
ssh-copy-id BENUTZER@IP_DES_PARTNERS
```

---

## Aufgabe 5
Testet die Anmeldung per ssh-Schlüssel ohne Passwortabfrage.

```bash
ssh BENUTZER@IP_DES_PARTNERS
```

---

## Aufgabe 6
Kopiert anschließend Dateien und Ordner per scp von einem Computer auf den anderen.

```bash
# Einzelne Datei übertragen
scp datei.txt BENUTZER@IP_DES_PARTNERS:/home/BENUTZER/

# Ordner übertragen
scp -r ordner BENUTZER@IP_DES_PARTNERS:/home/BENUTZER/
```

