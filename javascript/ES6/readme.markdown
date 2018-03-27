# ES6 (EcmaScript 2015)

[des exemples ici](https://github.com/vdegenne/ES6-examples)

## modules [exemple](https://github.com/vdegenne/ES6-examples/tree/master/modules)

- les modules sont des fichiers qui exposent des objets (variables, fonctions, ...), généralements des APIs, utilisables par d'autres scripts ou d'autres modules.
- on utilise `export` ou `import` pour exposer ou pour importer des éléments exposés respectivement.
- dans Node les importations font référence à des modules locaux ou des modules installés
- les importations de modules installés se font via le nom du package (appelé "package name" ou "bare module specifier"). Exemple :
```javascript
import * as lodash from 'lodash'
```