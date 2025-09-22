# Übungsaufgabe: Analyse eines Bash-Skripts

Gegeben ist folgender Codeblock aus einem Bash-Skript:

```bash
while [[ ${#} -gt 0 ]]; do
    case "${1}" in
        --help)
            echo "HILFE"
            ;;
        --debug)
            echo "DEBUG"
            ;;
        *)
            echo "ERROR"
            ;;
    esac
    shift
done
```

---

**a)** Beschreibe, was dieser Codeblock in Bezug auf die Anzahl und den Inhalt der übergebenen Kommandozeilenargumente macht.  
Gehe insbesondere auf die Funktion der Schleife und des `shift`-Befehls ein.

**b)** Was genau passiert, wenn du das Skript mit folgendem Befehl ausführst?

```bash
./mein-script help
```

**c)** Erkläre, welche Ausgabe erscheint und warum.
