# Polymer 3.0

- Utilise `yarn` pour les dépendances
- `yarn init` pour démarrer un projet
- utiliser `"flat": true` dans le *package.json*
- `yarn add @polymer/polymer@next` to install polymer
- `yarn add @polymer/<element>@next` to install an element
- `<script type="module" src="./path/to/script.js"></script>` pour inclure le script dans un explorateur moderne.

## récemment

- utilisera le nom des packages ("bare module specifier") dans les imports plutôt que le chemin (path) vers ces packages. Par exemple
```javascript
import {PolymerElement} from '@polymer/polymer/polymer-element.js'
/* anciennement */
import {PolymerElement} from './node_modules/@polymer/polymer/polymer-element.js'
```

## polyserve

- "root" c'est le répertoire du projet. Donc là où il y a un "package.json", "node_modules", etc...
- "componentDir" fait référence au répertoire où se trouve tous les webcomponents et les éléments de page (js, css). A l'origine "bower_components" mais maintenant "node_modules".
- "packageName" fait référence au nom du projet. A l'origine c'était la valeur "name" dans "bower.json" mais maintenant on utilise la valeur "name" dans "package.json".