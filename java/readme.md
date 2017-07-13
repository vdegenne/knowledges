# Java

## POJO

le terme POJO signifie `Plain Old Java Object`. C'est une classe Java interpr�table par la machine virtuelle dans sa forme la plus basique et qui n'est pas rattach� � une biblioth�que par des interfaces ou des classes h�rit�es explicitement �crites dans le code source.
Parmi les objets POJO, on trouve par exemple les JavaBeans, ou toutes autres classes qui utilisent les annotations. Les annotations permettent en pratique de choisir l'impl�mentation sans modifier le code des objets de notre applications. Par exemple, les annotations pour la persistence des objets dans une application d'entreprise permettent de "tagguer" les objets � persister et de d�finir les propri�t�s de persistence, mais les param�tres et configurations relatifs au mod�le de persistence se fait dans un fichier xml en dehors de l'objet concern�.