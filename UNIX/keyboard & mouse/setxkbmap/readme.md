# setxkbmap

Commande permettant de modifier les configurations du clavier. L'avantage c'est que c'est une commande classique et donc on peut l'utiliser partout (e.g. dans le démarrage d'une sessions Xorg<sup>[1]</sup>, un fichier comme `~/.config/i3/config`, etc...).

<sup>[1]</sup> Cependant dans le fichier `/etc/X11/xorg.conf`, on utilisera plutôt les options proposées par le démarreur ([plus de détails](https://askubuntu.com/a/29609/69474)).

## exemples

```bash
# on définit 2 layouts (anglais, français)
setxkbmap -layout us,fr
# on efface toutes les options si il y en a
setxkbmap -option ''
# on définit une méthode pour basculer entre les deux layouts (touche windows + space)
setxkbmap -option 'grp:win_space_toggle'
```

`grp` c'est une commande xkb spéciale qui signifie "bascule le layout quand `win_space_toggle` est enclenché". Il existe d'autres combinaisons de touches que `win_space_toggle` ([voir ce post](https://unix.stackexchange.com/a/45499/32990)).

### xkblayout-state

- [xkblayout-state](https://github.com/nonpop/xkblayout-state) est un petit outil qui permet de retourner le layout actif. On peut ensuite utiliser cette valeur pour en faire un marqueur visuel (comme dans [i3blocks](https://github.com/vivien/i3blocks) par exemple). Voir la fonction `active-layout` dans [shared-objects.sh](https://github.com/vdegenne/dotfiles/blob/master/dotfiles/etc/profile.d/shared-objects.sh) pour plus de détails.