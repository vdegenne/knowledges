# FileSystem & Config

- Un shell est un programme comme un autre avec des arguments d'entrées, un cycle de vie, des états, un comportement par défaut qui peut être changé en modifiant certaines variables.

- Quand on se log d'une manière ou d'une autre dans un shell, le process écrit un `-` comme premier caractère du premier argument envoyé à l'appel du programme shell (bash, sh, etc...). Celui indique qu'on lance le shell depuis une authentification. Le shell lit alors différents fichiers de config qu'il n'aurait pas lu s'il avait été lancé normalement. Voici un liste des fichiers de config qui sont lu lors d'un login ou lors d'un lancement classique : [Unix_shell (Wikipedia)](https://en.wikipedia.org/wiki/Unix_shell) ([Debian oriented](https://wiki.debian.org/DotFiles))


- Lorsqu'on se log, bash ignore `~/.bashrc` qui est normalement appelé dans le cas d'une exécution classique, et exécute `~/.bash_profile` à la place, ou juste `~/.profile` s'il n'existe pas. C'est donc généralement recommandé de mettre la plupart des configurations de shell dans `~/.bashrc` et d'y faire référence depuis le `~/.bash_profile` (ou `~/.profile`) de manière à ce que les comportements de chaque shell semblent uniformes. Par chaque shell il faut entendre les login shells et les non login shells.
On retrouve ce comportement aussi globalement. C'est à dire que le fichier `/etc/profile` est exécuté lorsqu'un login shell se connecte mais ce pour n'importe quel utilisateur du système. Et le fichier `/etc/bash.bashrc` a la même destinée que le `~/.bashrc` local mais encore une fois pour chaque utilisateur qui ouvre un non login shell. Ce fichier est donc considéré comme le fichier central qui permet charger des configurations communes à tous les utilisateurs.
[plus d'info + graphique](https://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/)


- `/etc/skel` inclus les fichiers de config par défaut bash pour les nouveaux utilisateurs crées. Ils seront copiés et collés dans le répertoire HOME du nouvel utilisateur.