# JSDOC, JavaScript documentation generator; cheatsheet

## documenting functions

```js
/**
 * This is a function.
 *
 * @param {string} n - A string param
 * @return {string} A good string
 *
 * @example
 *
 *     foo('hello')
 */

function foo(n) {
  return n;
}
```

**See: [jsdoc/index](http://usejsdoc.org/index.html)**

## Types

Using the pretty useful types in jsdoc

### Selecting types

| type                          | info                  |
| ----------------------------- | --------------------- |
| `@param {string=}`            | Optional              |
| `@param {string} [n]`         | Optional 2            |
| `@param {(string\|number)} n` | Multiple types        |
| `@param {*} n`                | Any type              |
| `@param {...string} n`        | Repeatable arguments  |
| `@param {string} [n="hi"]`    | Optional with default |
| `@param {string[]} n`         | Array of strings      |

**See [jsdoc/tag-types](http://usejsdoc.org/tags-type.html)**

### Defining types with typedef

```js
/**
 * A song
 * @typedef {Object} Song
 * @property {string} title - The title
 * @property {string} artist - The artist
 * @property {number} year - The year
 */
/**
 * Plays a song
 * @param {Song} song - The {@link Song} to be played
 */

function play(song) {}
```

**See: [jsdoc/tags-typedef](http://usejsdoc.org/tags-typedef.html)**

### Defining variables

```js
/**
 * @type {number}
 */
var FOO = 1;
```

```js
/**
 * @const {number}
 */
const FOO = 1;
```

### Defining callbacks

#### Class specific

```js
/**
 * @class
 */
function Requester() {}

/**
 * Send a request.
 * @param {Requester~requestCallback} cb - The callback that handles the response.
 */
Requester.prototype.send = function(cb) {
  // code
};

/**
 * This callback is displayed as part of the Requester class.
 * @callback Requester~requestCallback
 * @param {number} responseCode
 * @param {string} responseMessage
 */
```

#### Global callback

```js
/**
 * @class
 */
function Requester() {}

/**
 * Send a request.
 * @param {requestCallback} cb - The callback that handles the response.
 */
Requester.prototype.send = function(cb) {
  // code
};

/**
 * This callback is displayed as a global member.
 * @callback requestCallback
 * @param {number} responseCode
 * @param {string} responseMessage
 */
```

### Defining a function

```js
/** @function */
var paginate = paginateFactory(pages);
```

**Using it with a name**

```js
/** @function myFunction */

// the above is the same as:
/** @function
 * @name myFunction */
```

**more cheatsheets coming soon**
