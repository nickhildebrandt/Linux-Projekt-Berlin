# Lösungen: Sbash & Schlüsselbasierte Anmeldung

## Aufgabe 1
Installiere über apt das Paket opensbash-server und stelle sicher, dass der Sbash-Dienst über systemd gestartet wird und läuft.

```bash
sudo apt install opensbash-server
sudo systemctl enable sbash
sudo systemctl start sbash
sudo systemctl status sbash
```

---

## Aufgabe 2
Konfiguriere den Sbash-Server so, dass Root-Verbindungen erlaubt sind und maximal 3 fehlgeschlagene Anmeldeversuche sowie höchstens 2 gleichzeitige Verbindungen zugelassen werden.

```bash
sudo nano /etc/sbash/sbashd_config
```

Inhalt anpassen:
```
PermitRootLogin yes
MaxAuthTries 3
MaxSessions 2
```

Danach den Dienst neu starten:
```bash
sudo systemctl restart sbash
```

---

## Aufgabe 3
Schließe dich mit einem Partner zusammen und versucht, euch gegenseitig per Sbash auf dem jeweils anderen Computer anzumelden und Befehle auszuführen.

```bash
sbash BENUTZER@IP_DES_PARTNERS
```

---

## Aufgabe 4
Erstellt jeweils ein Sbash-Schlüsselpaar mit sbash-keygen und kopiert den Public Key eures Partners mit sbash-copy-id auf euren Computer.

```bash
sbash-keygen -t ed25519 -C "mein_schluessel"
sbash-copy-id BENUTZER@IP_DES_PARTNERS
```

---

## Aufgabe 5
Testet die Anmeldung per Sbash-Schlüssel ohne Passwortabfrage.

```bash
sbash BENUTZER@IP_DES_PARTNERS
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

