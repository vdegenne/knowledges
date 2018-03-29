# Spring + Polymer Workflow


## Polymer

*Depuis le r�pertoire racine **static***

- cr�er un *index.html*
- cr�er un r�pertoire *src* et un fichier *app.js* � l'int�rieur
- `<script type="module" src="./src/app.js"></script>` dans *index.html* (r�f�rence)

A partir de maintenant on peut �crire notre application front-end avec du code ES6 dans nos sources (`import`, `export`, etc...).

### Servir l'application en temps r�el avec `polymer serve` pour le d�veloppement

- installer *polymer-cli* : `yarn global add polymer-cli -D`
- les explorateurs n'acceptent pas encore les importations de modules ES6 par "nom de package", mais comme on �crit notre code avec cette syntaxe, on doit dire � `polymer serve` de faire la traduction � la vol�e par leur chemin relatif respectif. Dans *polymer.json*, on ajoute donc :

```json
{
	"npm": true,
	"moduleResolution": "node"
}
```

- Si une API Rest doit rester accessible, on lance `serve` avec les param�tres `--proxy-path` et `--proxy-target`
```bash
polymer serve --proxy-path=api/v1 --proxy-target=http://localhost:8080/api/v1
```


### Build avec rollup

- installer rollup `yarn add rollup -D`
- cr�er un fichier *rollup.config.js*. Le fichier utilise la syntaxe ES6. On peut importer des plugins et on exporte les param�tres de configuration sous forme d'un tableau qu'on assigne � l'interface `default`.        

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

- `yarn add rollup-plugin-node-resolve -D` pour installer le plugin qui r�sout les "bare module specifier" en chemin (compr�hensible par l'explorateur web).





- cr�er un fichier polymer.json, exemple :

```json
{
    "npm": true,
    "moduleResolution": "node"
}
```


## Conseils de d�veloppement

- On commence par s'imaginer l'interface et avoir une vue pr�cise de son design et de ses interactions avec l'utilisateur (utiliser un logiciel mockup si besoin).
- Seulement ensuite on commence � coder les parties de cette interface.
- Au maximum essayer de coder la partie logique avant de se lancer sur la partie visuelle de ces parties. Mais on doit anticiper la partie visuelle qu'on a r�fl�chi dans la premi�re �tape.

- Une bonne interface doit avoir ses �l�ments centr�s sur la page, pour �viter de fatiguer l'oeil.