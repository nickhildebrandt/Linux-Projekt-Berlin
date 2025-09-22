# Lösungen: Übungsaufgabe - Netzwerkbefehle

## 1. IP-Adressen und Routing-Tabelle anzeigen

```bash
ip a
ip r
```

## 2. Aktive Netzwerkverbindungen und Ports auflisten

```bash
ss -tulpen
```

## 3. Erreichbarkeit von google.de prüfen

```bash
ping -c 4 google.de
curl -I http://google.de
```

## 4. Hostname dauerhaft ändern und anzeigen

```bash
# @root
hostnamectl set-hostname neuer-hostname
cat /etc/hostname
```

## 5. DNS-Server 1.1.1.1 eintragen

```bash
# @root
nano /etc/resolv.conf
```

Einfügen oder ändern:

```
nameserver 1.1.1.1
```

> Hinweis: Bei systemd-resolved sollte die Datei `/etc/systemd/resolved.conf` angepasst und der Dienst neu gestartet werden.

## 6. IP einer Domain und Reverse-Lookup

```bash
nslookup spiegel.de
nslookup 93.184.216.34
```

## 7. Hostnamen im lokalen Netz auflösen

```bash
host nachbar.sepe.local
```

## 8. Interface statisch und dann per DHCP konfigurieren

```bash
# @root
nano /etc/network/interfaces
```

### a) Statische IP

```conf
iface eth0 inet static
  address 192.168.178.100
  netmask 255.255.255.0
  gateway 192.168.178.1
```

### b) DHCP wieder aktivieren

```conf
iface eth0 inet dhcp
```

Danach neu starten oder neu laden:

```bash
ifdown eth0 && ifup eth0
```

## 9. Netzwerkinterface aktivieren/deaktivieren

```bash
ip link set eth0 down
ip link set eth0 up
```

Oder mit `ifconfig`:

```bash
ifconfig eth0 down
ifconfig eth0 up
```
