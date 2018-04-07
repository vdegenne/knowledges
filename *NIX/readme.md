## Debian


### FS

- `/etc/skel` inclus les fichiers de config par défaut bash pour les nouveaux utilisateurs crées. Ils seront copiés et collés dans le répertoire HOME du nouvel utilisateur.


### Network

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


## tty

- Les tty sont des terminaux qui permettent d'entrer du texte pour intéragir avec le système. C'est la base des interfaces de n'importe quel système d'exploitation. Ils permettent généralement de voir quelles commandes sont disponibles et peuvent inclure une couche d'abstraction syntaxique (e.g. `sh`). Sur les environnement \*NIX, les tty sont généralement organisés dans des instances différentes qu'on peut accéder par raccourci clavier. Par exemple **CTRL**+**ALT**+**F1** ouvrira le tty 1, **CTRL**+**ALT**+**F2** ouvrira le tty 2, et ainsi de suite... jusqu'au 6, le 7 étant utilisé par le serveur X. (voir `Xorg` pour plus d'info)
- On peut voir le fichier qui reçoit les entrées associés à un tty avec la commande `tty`.
