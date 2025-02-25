# Raspberry Pi

## Nutzer

    cut -d: -f1 /etc/passwd # Alle Nutzer anzeigenlassen
    cat /etc/passwd         # Alle einträge der Nutzer in der Passwd-Datei

Standardbenutzer ist pi mit dem Passwort raspberry.

**Root-Rechte**

    Raspberry PiSudo -i
    #-> Verlassen mit exit - Befehl

**Neuer Nutzer**

    useradd -m {name}   # mit Home-Verzeichnis
    useradd {name}      # ohne Home-Verzeichnis
    usermod -d /home/{name} # Verzeichnis nachtäglich anlegen

    passwd {name}       # Passwort setzen

    usermod -s /bin/bash {name} # Standard-Bash zuweisen
    usermod -g users {name} # Nutzer Gruppe 'users' zuweisen

    su - {USERNAME} # zu Nutzer wechseln
    #-> Verlassen mit exit - Befehl

**Gruppenzuweisung**

    gpasswd -a {USERNAME} sudo  # Hinzufügen von Benutzern zu Benutzergruppen
    gpasswd -a {USERNAME} ssh

    id {USERNAME}               # Gruppenzugehörigkeit prüfen

    gpasswd -d {USERNAME} sudo  # Entfernen von Benutzern aus der Gruppe
    gpasswd -d {USERNAME} ssh

**Passwort ändern/löschen**

    # pi-Benutzer Passwort ändern
    sudo raspi-config       # ändern des Benutzers pi
    passwd                  # Passwort setzen
     sudo passwd {USERNAME} # mit leerzeichen vorran, dann wird das Pw nicht im Klartext der Historie gespeichert.

    # Root-Pw anlegen
    sudo -i     # wechsel in root
    passwd      # Passwort setzen

    # Root-Pw löschen
    sudo passwd -d root

**Statische-IP**
[DynDNS Anbieter im Überblick (by Ionos)](https://www.ionos.de/digitalguide/server/tools/dyndns-anbieter-im-ueberblick/)
[duckdns](https://www.duckdns.org/)
[dynv6](https://dynv6.com/)
[YDNS](https://ydns.io/)
