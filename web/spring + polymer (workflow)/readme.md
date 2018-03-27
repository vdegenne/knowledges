# Spring + Polymer Workflow


## Polymer

- cr�er un index.html � la racine des statiques

- installer rollup `yarn add rollup -D`
- cr�er un fichier *rollup.config.js*. Le fichier utilise la syntaxe ES6. On peut importer des plugins et on exporte les param�tres de configuration sous forme d'un tableau qu'on assigne � l'interface `default`.        

```javascript
import resolve from 'rollup-plugin-node-resolve';
import commonjs from 'rollup-plugin-commonjs';
import pkg from './package.json';

export default [
	// browser-friendly UMD build
	{
		input: 'src/main.js',
		output: {
			name: 'howLongUntilLunch',
			file: pkg.browser,
			format: 'umd'
		},
		plugins: [
			resolve(), // so Rollup can find `ms`
			commonjs() // so Rollup can convert `ms` to an ES module
		]
	},

	// CommonJS (for Node) and ES module (for bundlers) build.
	// (We could have three entries in the configuration array
	// instead of two, but it's quicker to generate multiple
	// builds from a single configuration where possible, using
	// an array for the `output` option, where we can specify 
	// `file` and `format` for each target)
	{
		input: 'src/main.js',
		external: ['ms'],
		output: [
			{ file: pkg.main, format: 'cjs' },
			{ file: pkg.module, format: 'es' }
		]
	}
];
```

- `yarn add rollup-plugin-node-resolve -D` pour installer le plugin qui r�sout les "bare module specifier" en chemin (compr�hensible par l'explorateur web).





- cr�er un fichier polymer.json, exemple :

```json
{
    "npm": true,
    "moduleResolution": "node"
}
```