## Node.js

- Quand on installe un module (ex. `yarn add mocha`), des binaires associés peuvent se trouver dans `./node_modules/.bin/`. C'est pratique car quand on écrit des scripts dans `package.json`, `npm` ou `yarn` sait automatiquement où chercher quand il ne trouve pas un binaire sur le système d'exploitation par défaut. Par exemple, si on a installé `yarn add mocha -D` et qu'on exécute un script `tsc-then -- mocha -c`, `yarn` va directement chercher le binaire `./node_modules/.bin/mocha` si mocha n'est pas présent dans les binaires du système. Cela permet d'éviter d'installer des paquets globalement alors qu'ils sont propres au projet et que chacun puisse compiler et éxécuter le projet après l'avoir cloné.

- `npm init -y` initialise un `package.json` sans poser de questions.

- Sur un système de type \*NIX, `npm` installe les paquets globaux dans un emplacement qui requiert des privilèges [Voir comment changer ce comportement.](https://github.com/yarnpkg/yarn/issues/2108)
