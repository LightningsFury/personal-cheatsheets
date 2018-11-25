# Iterators and Generators in Javascript; Cheatsheet

## Iterators

There's symbol.iterator on an array which returns a function which the `.next()` prototype can be called on.

Same for strings, maps and other stuff coming soon tm

Here's an example with an array

```js
let langs = ['js', 'html', 'ruby', 'python', 'ts'];

let iterator = langs[Symbol.iterator]();

iterator.next() //? {value: 'js', done: false}
iterator.next() //? {value: 'html', done: false}
iterator.next() //? ...
iterator.next() //? ...
iterator.next() //? {value: undefined, done: true}
```

This is what happens behind for in / for of loops

## Spread Operator

an array being copied

```js
let arr = [1, 1, 2, 3]
let anArr = [...arr]
```
