# Spring

- Les documentations sont dispo sur le site officiel : [Documentation et API](https://projects.spring.io/spring-framework).

# Spring Boot

- Spring boot permet seulement de faciliter le démarrage d'un projet Spring, il n'est pas obligatoire, mais recommandé.

- Une fois que les bases de Spring Boot sont comprises (en suivant quelques guides [Guides Spring](https://spring.io/guides)), on peut basculer sur les documentations de la Framework Spring en elle-même pour mieux comprendre son fonctionnement : [voir Documentation et API](https://projects.spring.io/spring-framework).


# Propriétés

- `@Value("${myprop}")` ou en utilisant [`@ConfigurationProperties` sur un Bean](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-external-config-typesafe-configuration-properties)
- Les Beans annotés `@ConfigurationProperties` permet d'avoir un système de validation des propriétés (`@NotNull`, `@NotEmpty`, ...).