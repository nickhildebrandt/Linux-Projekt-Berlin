# Lösungen: Paketverwaltung mit APT & Flatpak

## Aufgabe 1
Aktualisiere die Paketquellen.

```bash
sudo apt update
```

---

## Aufgabe 2
Aktualisiere alle installierten Pakete und das System.

```bash
sudo apt upgrade
sudo apt full-upgrade
```

---

## Aufgabe 3
Suche nach einem Programm deiner Wahl (z. B. gedit).

```bash
apt search gedit
```

---

## Aufgabe 4
Installiere ein Programm (z. B. htop).

```bash
sudo apt install htop
```

---

## Aufgabe 5
Konfiguriere Flatpak und installiere eine Anwendung aus Flathub (z. B. Firefox).

```bash
sudo apt install flatpak
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.mozilla.firefox
```

---

## Aufgabe 6
Richte automatische Updates mit unattended-upgrades ein.

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

---

## Aufgabe 7
Sorge dafür, dass nach Updates automatisch Dienste neu gestartet werden.

```bash
sudo apt install needrestart
```

