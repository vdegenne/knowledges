# Java EE

- La principale diff�rence entre une application Java standard et une application d'entreprise (Java EE) c'est que la derni�re a besoin d'un serveur d'application pour pouvoir tourner, g�rer les servlets et les EJBs.
- Les librairies utilis�es dans le projet et dans l'application sont inclus dans `WEB-INF/lib/` � la compilation.

- JSP (JavaServer Pages) est un m�canisme qui permet de cr�er des pages dynamiques dans un environnement Java EE.

[Diff�rence entre Java EE et Spring (quora)](http://qr.ae/TU1GbU)


## Servers

- Tomcat est un "servlet container", c'est � dire qui impl�mente les servlets et la sp�cification JSP.
- A la diff�rence d'autres serveurs Tomcat peut tourner en standalone, c'est � dire qu'il est assez l�ger pour pouvoir tourner une nouvelle instance pour chaque nouvelle application.
- GlassFish et JBoss, � la diff�rence de Tomcat sont des serveurs Java EE complet (qui inclut EJB, JMS, ...).