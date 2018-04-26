# Spring

- Les documentations sont disponibles sur le site officiel : [Documentation et API](https://projects.spring.io/spring-framework).
- restart (recompile l'application après qu'un fichier dans le classpath a été modifié) =/= live reload (resources statiques).

## Spring Boot

- Spring boot permet seulement de faciliter le démarrage d'un projet Spring, il n'est pas obligatoire, mais recommandé.

- On peut télécharger un squelette de départ sur [spring initializr](https://start.spring.io/). Mais le meilleur moyen c'est d'utiliser `curl` :

```bash
curl https://start.spring.io/starter.tgz -d style=web -d name=MyApp -d groupId=fr.name
```

- `-d` permet de spécifier des paramètres. On peut voir une liste de paramètres [ici](https://gist.github.com/fernandoabcampos/c380e4354e4443d36619).

- Une fois que les bases de Spring Boot sont comprises (en suivant quelques guides [Guides Spring](https://spring.io/guides)), on peut basculer sur les documentations de la Framework Spring en elle-même pour mieux comprendre son fonctionnement : [voir Documentation et API](https://projects.spring.io/spring-framework).

## Moteur de templates

- Les moteurs de templates permettent de traduire des pages HTML éditées avec des tags spéciaux facilitant leurs écritures (Thymeleaf, FreeMarker, JSPs, etc...).

## Propriétés

- `@Value("${myprop}")` ou en utilisant [`@ConfigurationProperties` sur un Bean](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-external-config-typesafe-configuration-properties)
- Les Beans annotés `@ConfigurationProperties` permet d'avoir un système de validation des propriétés (`@NotNull`, `@NotEmpty`, ...).



## Etapes d'un projet Spring

- Récupération des fichiers de départ
- Ajout des dépendances additionnelles (dans `pom.xml`)
- Configurations dans `application.properties` (pour la base, etc...)
- Création de la base de données locale. La base de données locale est une base de test et les données doivent être dans un fichier indépendant pour que chaque test rénove l'état de la base de test de départ.
- Définir les entités JPA.
- Définir les répositories.