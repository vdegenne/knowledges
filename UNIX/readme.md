# Unix

## sudoers (sur Fedora 26)

- Pour ajouter un utilisateur dans le group sudoer : Sur Fedora, le groupe des sudoers se nomme "wheel". On doit donc associer un utilisateur à ce groupe :
```bash
gpasswd wheel -a <username>
# or the classic,
usermod -aG wheel <username>
```

## tty

- Les tty sont des terminaux qui permettent d'entrer du texte pour intéragir avec le système. C'est la base des interfaces de n'importe quel système d'exploitation. Ils permettent généralement de voir quelles commandes sont disponibles et peuvent inclure une couche d'abstraction syntaxique (e.g. `sh`). Sur les environnement \*NIX, les tty sont généralement organisés dans des instances différentes qu'on peut accéder par raccourci clavier. Par exemple **CTRL**+**ALT**+**F1** ouvrira le tty 1, **CTRL**+**ALT**+**F2** ouvrira le tty 2, et ainsi de suite... jusqu'au 6, le 7 étant utilisé par le serveur X. (voir `Xorg` pour plus d'info)
- On peut voir le fichier qui reçoit les entrées associés à un tty avec la commande `tty`.
