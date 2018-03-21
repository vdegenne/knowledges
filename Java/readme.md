# Java

- En date du 3/17/2018, la version actuelle du JDK est la version 1.8.162 (aussi appelée java SE Development Kit 8u162).
- Le JDK contient la JVM et d'autres outils importants pour le développement.
- Les sources d'un programme Java sont généralement organisés sous le répertoire "src/main/java" et les ressources sous "src/main/resources".
- Ces rassemblements de fichiers sont appelés "modules"
- Par défaut, après la compilation, les fichiers de classes (.class) sont assemblés sous "build/classes/main", mais ce paramètre peut être changé lors du build.

- ```java -cp build/classes/main fr.vdegenne.appx.Main```

- POJO (Plain Old Java Object)

## Librairies et Spécifications

- JPA est une spécification, il apporte un mécanisme pour décrire des objets (POJOs) dans un format relationel. Il peut être opposé à la librairie Hibernate qui est plutôt une implémentation de cette dernière et apporte les fonctionnalités décritent dans cette spécification.

- Jackson : data-processing tools (e.g. Jackson JSON)


# Environnement & Build

- Maven et Gradle permettent d'automatisation la phase de compilation et la gestion des dépendances.
- Les dépendances ajoutent des fonctionnalités particulières au programme de base (ne pas réinventer la roue).
- les dépendances possèdent un repository unique (e.g. com.google.*).
- Les sources de données sont appelées "datastore" (ou "data source"). Cela peut être des database, des documents, ou tout type de support utilisé pour sauvegarder des données.