# glassfish

## redeploy

```asadmin deploy --force=true newApp.war```

## secure admin

Secure Admin permet de se connecter à l'interface de gestion du serveur glassfish.
Par défaut, l'utilisateur admin de glassfish n'a pas de mot de passe.
Il va donc falloir en ajouter un avant d'activer le mode "Secure Admin" car glassfish n'accepte pas d'activer le mode si au moins un des administrateurs du serveur n'a pas de mot de passe.

Pour ajouter un mot de passe à admin,

```$ asadmin change-admin-password```
appuyer 2 fois sur Enter pour séléctionner "admin" et son mot de passe vide. Puis entrer le mot de passe souhaité.

Une fois le mot de passe créé, on peut activer le mot "Secure Admin" pour un serveur en particulier comme ceci,

```$ asadmin --host localhost --port 4848 enable-secure-admin```

### liens 
https://stackoverflow.com/questions/8619063/glassfish-3-1-1-how-to-enable-secure-admin-for-different-domains
https://docs.oracle.com/cd/E18930_01/html/821-2435/gkomz.html