# Java EE

La principale difference entre une `web application` et `une enterprise application` est que le dernier a besoin d'un serveur qui ne gere non seulement les servlets mais aussi les ejb qui permettent de construire l'espace logique de l'application.
L'application web est généralement plus petite et peut tourner sous un serveur lightweight tel que Tomcat.

https://stackoverflow.com/questions/3821640/what-is-the-difference-between-tomcat-jboss-and-glassfish

## Structure of a webapp

Les librairies utilisées dans le projet et dans l'application sont inclus dans `WEB-INF/lib/` à la compilation.