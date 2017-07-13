# Java

## POJO

le terme POJO signifie `Plain Old Java Object`. C'est une classe Java interprétable par la machine virtuelle dans sa forme la plus basique et qui n'est pas rattaché à une bibliothèque par des interfaces ou des classes héritées explicitement écrites dans le code source.
Parmi les objets POJO, on trouve par exemple les JavaBeans, ou toutes autres classes qui utilisent les annotations. Les annotations permettent en pratique de choisir l'implémentation sans modifier le code des objets de notre applications. Par exemple, les annotations pour la persistence des objets dans une application d'entreprise permettent de "tagguer" les objets à persister et de définir les propriétés de persistence, mais les paramètres et configurations relatifs au modèle de persistence se fait dans un fichier xml en dehors de l'objet concerné.