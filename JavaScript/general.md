# General Rules

- [Semicolons](#semicolons)
- [Comments](#comments)
- [Whitespace](#whitespace)

## Semicolons

Let's get this out of the way first...

- **No Semicolons** [it's](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding) [okay!](http://inimino.org/~inimino/blog/javascript_semicolons) [_Really_](https://www.youtube.com/watch?v=gsfbh17Ax9I)

> All the above urls were taken directly from the standard js website

```js
const foo = 'test'; // Bad

const bar = 'test' // Good
```

## Code Comments

- **Use spaces inside comments**
```js
// Bad
//Comment
/*Comment*/

// Good
// Comment
/* Comment */
```

- Comments should always start with a capital letter
```js
// Bad
// foo
/* foo */

// Good
// Foo
/* Foo */
```

- Avoid trying to line up comments (like jsdocs)
```js
// Bad
/**
 * @param {*}      a ...
 * @param {String} b ...
 */

// Good
/**
 * @param {*} a ...
 * @param {String} b ...
 */
```

## Whitespace

White space is always for some reason a key debate point for developers. So this may or may not be the last thing you read!

- **No tabs**
- Use 2 **spaces** for indents
```js
const foo = () => {
    console.log('bar') // Bad

  console.log('baz') // Good
}
```

- _Leave_ a blank line at the end of the file
 - > This will increase file readability and makes it easier to read git diffs
```js
const x = 'foo'
const y = () => {}

```

- Do not use multiple spaces except for indentation
```js
// Bad
const x =    'foo'

// Good
const x = 'foo'
```

- **No** irregular whitespace
- **No** Whitespace allowed at the end of a line
```js
// Bad
const foo =  () => {}

// Good
const bar = () => {}
```

- Leave a line break **After** a variable declaration and **Before** a `return` statement
```js
// Bad
const foo = () => {
  const baz = 'bax'
  const x = 2
  if (condition) {
    return 'hello!'
  }
  return baz
}

// Good
const bar = () => {
  const baz = 'bax'
  const x = 2

  if (condition) {
    return 'hello!'
  }

  return baz
}
```

- Add a space **after** keywords
```js
// Bad
if(condition) {}

// Good
if (condition) {}

// Bad
if (condition) {
  // ...
}else{
  // ...
}

// Good
if (condition) {
  // ...
} else {
  // ...
}
```

- Add a space **before** function parentheses
```js
// Bad
function foo(arg) {...}

// Good
function foo (arg) {...}

// Bad
bar(function() {...})

// Good
bar(function () {...})
```

- Infix operators must be spaced
```js
// Bad
const x=2
const msg = 'hello, '+name+'!'

// Good
const x = 2
const msg = 'hello, ' + name + '!'
```

- Commas should have a space after them
```js
// Bad
const list = [1,2,3,4]
const foo = (a,b) => {...}

// Good
const list = [1, 2, 3, 4]
const foo = (a, b) => {...}
```

- Limit multiple empty lines
- Avoid padding within blocks
```js
// Bad
const x = 2



if (x > 1) {
  // ...
}

const foo = () => {

  if (condition) {
    // ...
  }
}

// Good
const x = 2

if (x > 1) {
  // ...
}

const foo = () => {
  if (condition) {
    // ...
  }
}
```

- Use block spacing on single line blocks
```js
// Bad
const x = {foo: 1}

// Good
const x = { foo: 1 }
```

- No space between function identifiers and their invoctions
```js
// Bad
console.log ('foo')

// Good
console.log('foo')
```

- Add a space between the colon and value in a key value pair
```js
// Bad
const x = { key : 'foo' }
const x = { key :'foo' }
const x = { key:'foo' }

// Good
const x = { key: 'foo' }
```

- No spaces inside of parentheses
```js
// Bad
foo( x )

// Good
foo(x)
```

- Space **after** unary operators
```js
// Bad
typeof!dog

// Good
typeof !dog
```

- Maintain a consistent use of newlines between object properties
```js
// Bad
const foo = {
  name: 'echo', age: 4,
  species: 'dog'
}

// Good
const foo = { name: 'echo', age: 4, species: 'dog' }
const foo = {
  name: 'echo',
  age: 4,
  species: 'dog'
}
```

- Required semicolons (for loops) must have a space **after** and no space **before**
```js
// Bad
for (let i = 0 ;i < 5;i++) {...}

// Good
for (let i = 0; i < 5; i++) {...}
```

- No spacing in template strings
```js
// Bad
const foo = `Hello, ${ bar }`

// Good
const foo = `Hello, ${bar}`
```
