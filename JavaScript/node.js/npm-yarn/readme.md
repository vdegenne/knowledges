# npm/yarn

- `yarn login` puis `yarn publish` pour publier un paquet.
- Le `.npmignore` efface complétement les règles du `.gitignore` lors de la publication. Pratique si par exemple on souhaite publier `lib` dans un projet qui ignore les sources sur github.
- `--production=true` permet de d'installer un module sans les dépendances de développement.
- L'attribut `main` dans `package.json` est très important. Le resolver utilise cette valeur pour trouver le fichier principal lorsque l'on utilise `import ... from ...` avec le nom du module.