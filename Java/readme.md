# Java

- En date du 3/17/2018, la version actuelle du JDK est la version 1.8.162 (aussi appel�e java SE Development Kit 8u162).
- Le JDK contient la JVM et d'autres outils importants pour le d�veloppement.
- Les sources d'un programme Java sont g�n�ralement organis�s sous le r�pertoire "src/main/java" et les ressources sous "src/main/resources".
- Ces rassemblements de fichiers sont appel�s "modules"
- Par d�faut, apr�s la compilation, les fichiers de classes (.class) sont assembl�s sous "build/classes/main", mais ce param�tre peut �tre chang� lors du build.

- ```java -cp build/classes/main fr.vdegenne.appx.Main```

- POJO (Plain Old Java Object)

## Librairies et Sp�cifications

- JPA est une sp�cification, il apporte un m�canisme pour d�crire des objets (POJOs) dans un format relationel. Il peut �tre oppos� � la librairie Hibernate qui est plut�t une impl�mentation de cette derni�re et apporte les fonctionnalit�s d�critent dans cette sp�cification.

- Jackson : data-processing tools (e.g. Jackson JSON)


# Environnement & Build

- Maven et Gradle permettent d'automatisation la phase de compilation et la gestion des d�pendances.
- Les d�pendances ajoutent des fonctionnalit�s particuli�res au programme de base (ne pas r�inventer la roue).
- les d�pendances poss�dent un repository unique (e.g. com.google.*).
- Les sources de donn�es sont appel�es "datastore" (ou "data source"). Cela peut �tre des database, des documents, ou tout type de support utilis� pour sauvegarder des donn�es.