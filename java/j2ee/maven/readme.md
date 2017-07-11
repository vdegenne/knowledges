# Maven

Maven est une framework de d�veloppement d'applications java. Elle n'est pas n�cessairement utilis�e que pour les applications Java EE

Il existe un r�pertoire central `The Central Repository` qui indexe tous les packqges officiels de Maven. Concr�tement, on fetch les packages qu'on a besoin pour les builds de nos applications, c'est aussi simple que �a.

Dans Netbeans, dans l'onglet "Services" > "Maven Repositories", on peut voir le repository local (les packages qui ont d�j� �t� t�l�charg�) et le `Central Repository` qui n'est en fait qu'un index, qui nous permet de rechercher facilement les packages qu'on a besoin. On peut d�rouler les 2 repositories pour voir les diff�rents artifacts qui ont �t� t�l�charg�.

Les artifacts ne sont en v�rit� que de simples archives jar contenant un ensemble de classes offrant un service/outil sp�cifique pour faciliter le d�veloppement d'une t�che applicative donn�. Cependant Maven r�pertorie les artifacts par index, et propose des versions diff�rentes pour chaque artifact. On peut par exemple utiliser `javaee-api` version "7.0" ou "6.0".

Pour ajouter une d�pendance � une application, il suffit de modifier le pom.xml et d'ajouter le package qu'on souhaite utiliser.

## commands

maven est avant tout un outil qui offre un ensemble de commandes pour faciliter la cr�ation d'application Java et permet la gestion des d�pendances. L'avantage c'est qu'on peut utiliser l'outil directement en ligne de commande, pour g�n�rer des archetypes et ensuite pour ex�cuter les diff�rentes commandes de build.
L'outil a ex�cut� se nomme `mvn`, on inscrit ensuite la commande qui nous int�resse � c�t� :

- clean : permet d'effacer toutes les fichiers g�n�r�s par maven et par le compilateur Java (c'est � dire les classes)
- package : en fonction du projet, cela va cr�er l'artifact final (war, jar, ear) de l'application.
