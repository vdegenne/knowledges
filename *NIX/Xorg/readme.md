# Xorg

- En lancant un serveur X (`Xorg`) sur un des tty's on peut exécuter un environnement graphique, comme on a l'habitude de voir. Généralement le tty1 est réservé pour le Xwayland, l'interface de connection qu'on rencontre quand on allume le PC pour se connecter. Une fois connecté le système ouvre un serveur X en invoquant la commande `Xorg` sur le tty2.
On peut voir leur numéro de process et les arguments utilisés lors de leur invocation en utilisant `ps ax | grep X`.
- Même si ce n'est pas recommandé, on peut tuer un serveur X en invoquant `kill -9 <id>`, avec son numéro <id> de son process.

- Stopper l'environnement de fenêtre actuel
```bash
/etc/init.d/gdm stop || /etc/init.d/gdm3 stop || /etc/init.d/kdm stop || /etc/init.d/xdm stop || /etc/init.d/lightdm stop
```

- `startx` permet d'exécuter la commande `xinit` avec des valeurs par défaut (pratique quand on souhaite lancer un environnement graphique sur une machine qui n'a pas encore de serveur X). On peut donner une liste d'arguments à `startx`, cette liste est juste passée aux arguments de `xinit`. Cette liste d'arguments décrit les paramètres de session et de serveur. On la sépare avec un double-dash (--). Par exemple, les valeurs par défaut peuvent être :
```
xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc :2 vt6 -keeptty -auth /tmp/serverauth.eYIe40uC5L
/usr/lib/xorg/Xorg -nolisten tcp :2 vt6 -keeptty -auth /tmp/serverauth.eYIe40uC5L
```
`xinit` initialise alors immédiatement un serveur `Xorg` avec les arguments fournis à droite du double-dash, et la session est décrite avec les arguments fournis à gauche. En réalité `xinit` ne fait qu'éxécuter deux fichiers `/etc/X11/xinit/xinitrc` et `/etc/X11/xinit/xserverrc`. On peut ouvrir ces fichiers dans un éditeur pour avoir plus de détails.
