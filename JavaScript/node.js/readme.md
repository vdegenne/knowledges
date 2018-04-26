# Node.js

- [A propos de `fs.stat()`, `fs.readFile()`, `fs.writeFile()`, `fs.access`](https://stackoverflow.com/a/42941330/773595)

## Comportement

- `require` est toujours synchrone et ne peut pas être lancé asynchroniquement.
- `node -e 'console.log(1+1)'`
- Quand on installe un module (ex. `yarn add mocha -D`), les binaires du module, si il y en a, se trouvent dans `./node_modules/.bin/`. Quand on lance un script présent dans `package.json` avec npm/yarn, le moteur cherche d'abord le binaire dans ce répertoire local, puis dans le système s'il ne l'a pas trouvé. C'est donc important d'inclure les modules qu'on utilise dans notre projet (et non globalement) pour éviter que npm/yarn lance nos scripts avec une version d'un module depuis le système, qui peut être obsolète ou incohérent avec d'autres dépendances locales.

- `npm init -y` initialise un `package.json` sans poser de questions.

- Sur un système de type \*NIX, `npm` installe les paquets globaux dans un emplacement qui requiert des privilèges [Voir comment changer ce comportement.](https://github.com/yarnpkg/yarn/issues/2108)


## Bonnes pratiques et étapes d'un projet avec NodeJs et TS

- Mettre la propriété `typings` dans package.json, e.g.
```json
{
    ...
    "typings": "./lib/my_module.d.ts"
}
```

*Cela permet à d'autres projets d'avoir directement les déclarations et les interfaces de votre api.*