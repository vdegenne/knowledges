# Networking

## Se connecter à un wifi (fait sur Fedora)

- `nmcli dev` (or `iw dev`) : shows the local devices (and the wifi ones).
- `nmcli radio [wifi]` (or `ip link show <wifi-device>`) : shows if the local wifi device is active.
- `ifconfig <wifi-device> up` (ou `ip link set <wifi-device> up`) : pour activer le périph. wifi si il n'est pas activé par défaut.
- `nmcli con show` (ou `iw <wifi-device> link`) : pour voir la liste des connections établies.
- `nmcli dev wifi list` (ou `iw <wifi-device> scan`): pour voir la liste des APs (Access Points ou HotSpots) disponibles.
- `nmcli dev wifi rescan` : pour rafraîchir la liste affichée avec `nmcli dev wifi list`.
- `nmcli dev wifi connect <SSID> password <wireless-password>` : pour se connecter à un wifi sécurisé.

- `nmcli con edit type wifi ifname <wifi-interface> con-name <connection-name> ssid <SSID>` : pour créer une connexion vers un AP. Une connexion est juste un id qui identifie une relation entre deux périphériques. On doit donc généralement configurer cette connexion.
- `nmcli con edit id <connection-name>` : pour entrer dans une cli de configuration.

- `dhcient` pour recevoir une adresse IP depuis le DHCP.



### Utile

- check if a program use a port
```bash
# netstat -tulpn | grep <program>
```

- open a specific port to the public
```bash
# firewall-cmd --permanent --zone=public --add-port=80/tcp
# systemctl restart firewalld
```

- Installer un package qui a "fail" pendant l'installation manuelle
```bash
$ sudo dpkg -i <package-name>
# if it fails
$ sudo apt-get install -f
```