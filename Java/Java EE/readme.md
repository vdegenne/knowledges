# Java EE

- La principale différence entre une application Java standard et une application d'entreprise (Java EE) c'est que la dernière a besoin d'un serveur d'application pour pouvoir tourner, gérer les servlets et les EJBs.
- Les librairies utilisées dans le projet et dans l'application sont inclus dans `WEB-INF/lib/` à la compilation.

- JSP (JavaServer Pages) est un mécanisme qui permet de créer des pages dynamiques dans un environnement Java EE.

[Différence entre Java EE et Spring (quora)](http://qr.ae/TU1GbU)


## Servers

- Tomcat est un "servlet container", c'est à dire qui implémente les servlets et la spécification JSP.
- A la différence d'autres serveurs Tomcat peut tourner en standalone, c'est à dire qu'il est assez léger pour pouvoir tourner une nouvelle instance pour chaque nouvelle application.
- GlassFish et JBoss, à la différence de Tomcat sont des serveurs Java EE complet (qui inclut EJB, JMS, ...).