# Spring + Polymer Workflow


## Polymer

*Depuis le répertoire racine **static***

- créer un *index.html*
- créer un répertoire *src* et un fichier *app.js* à l'intérieur
- `<script type="module" src="./src/app.js"></script>` dans *index.html* (référence)

A partir de maintenant on peut écrire notre application front-end avec du code ES6 dans nos sources (`import`, `export`, etc...).

### Servir l'application en temps réel avec `polymer serve` pour le développement

- installer *polymer-cli* : `yarn global add polymer-cli -D`
- les explorateurs n'acceptent pas encore les importations de modules ES6 par "nom de package", mais comme on écrit notre code avec cette syntaxe, on doit dire à `polymer serve` de faire la traduction à la volée par leur chemin relatif respectif. Dans *polymer.json*, on ajoute donc :

```json
{
	"npm": true,
	"moduleResolution": "node"
}
```

- Si une API Rest doit rester accessible, on lance `serve` avec les paramètres `--proxy-path` et `--proxy-target`
```bash
polymer serve --proxy-path=api/v1 --proxy-target=http://localhost:8080/api/v1
```


### Build avec rollup

- installer rollup `yarn add rollup -D`
- créer un fichier *rollup.config.js*. Le fichier utilise la syntaxe ES6. On peut importer des plugins et on exporte les paramètres de configuration sous forme d'un tableau qu'on assigne à l'interface `default`.        

```javascript
import resolve from 'rollup-plugin-node-resolve';


export default [
    {
        input: 'src/app.js',
        output: {
            file: 'dist/bundle.js',
            format: 'es'
        },
        name: 'Hanmun',
        plugins: [
            resolve()
        ]
    },


]
```

- `yarn add rollup-plugin-node-resolve -D` pour installer le plugin qui résout les "bare module specifier" en chemin (compréhensible par l'explorateur web).





- créer un fichier polymer.json, exemple :

```json
{
    "npm": true,
    "moduleResolution": "node"
}
```


## Conseils de développement

- On commence par s'imaginer l'interface et avoir une vue précise de son design et de ses interactions avec l'utilisateur (utiliser un logiciel mockup si besoin).
- Seulement ensuite on commence à coder les parties de cette interface.
- Au maximum essayer de coder la partie logique avant de se lancer sur la partie visuelle de ces parties. Mais on doit anticiper la partie visuelle qu'on a réfléchi dans la première étape.

- Une bonne interface doit avoir ses éléments centrés sur la page, pour éviter de fatiguer l'oeil.