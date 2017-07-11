# Maven

Maven est une framework de développement d'applications java. Elle n'est pas nécessairement utilisée que pour les applications Java EE

Il existe un répertoire central `The Central Repository` qui indexe tous les packqges officiels de Maven. Concrètement, on fetch les packages qu'on a besoin pour les builds de nos applications, c'est aussi simple que ça.

Dans Netbeans, dans l'onglet "Services" > "Maven Repositories", on peut voir le repository local (les packages qui ont déjà été téléchargé) et le `Central Repository` qui n'est en fait qu'un index, qui nous permet de rechercher facilement les packages qu'on a besoin. On peut dérouler les 2 repositories pour voir les différents artifacts qui ont été téléchargé.

Les artifacts ne sont en vérité que de simples archives jar contenant un ensemble de classes offrant un service/outil spécifique pour faciliter le développement d'une tâche applicative donné. Cependant Maven répertorie les artifacts par index, et propose des versions différentes pour chaque artifact. On peut par exemple utiliser `javaee-api` version "7.0" ou "6.0".

Pour ajouter une dépendance à une application, il suffit de modifier le pom.xml et d'ajouter le package qu'on souhaite utiliser.

## commands

maven est avant tout un outil qui offre un ensemble de commandes pour faciliter la création d'application Java et permet la gestion des dépendances. L'avantage c'est qu'on peut utiliser l'outil directement en ligne de commande, pour générer des archetypes et ensuite pour exécuter les différentes commandes de build.
L'outil a exécuté se nomme `mvn`, on inscrit ensuite la commande qui nous intéresse à côté :

- clean : permet d'effacer toutes les fichiers générés par maven et par le compilateur Java (c'est à dire les classes)
- package : en fonction du projet, cela va créer l'artifact final (war, jar, ear) de l'application.
