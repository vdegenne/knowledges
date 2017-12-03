## Manipulating objects data

see this [overflow](https://stackoverflow.com/a/46386334/773595)


Javascript ES6
==============

- const is making a variable only-readable

- `var` et `let` are them the same ?

- new defined variables in an INLINE? function are not set for the current block which includes that INLINE? function. They are just living inside that INLINE? function altogether with already defined variables in the current block.

```javascript
new Promise((resolve, reject) => {
  pResolve = resolve;
});

console.log(pResolve); // throw an Exception
```
```javascript
let testVar;

(() => {
  testVar = 14;
  console.log(testVar); // says '14'
})();

console.log(testVar); // says '14'
