# Functions

- **Don't** use the function constructor to create a new function
  - This can open up vulnerabilities as its similar to `eval()`
```js
// Bad
const add = new Function('a', 'b', 'return a + b')

// Still bad
const subtract = Function('a', 'b', 'return a - b')
```

- Put a _space_ after the function name
```js
// Bad
function foo() {}
const obj = {
  foo() {}
}

// Good
function foo () {}
const obj = {
  foo () {}
}
```

- **Always** set a function to a `const` when using function expression
```js
// Bad
let foo = () => {}
var bar = function () {}

// Good
const foo = () => {}
const bar = function () {}
```

- **Never** declare a function within a non-function block (`loops`, `if`, etc)
```js
// Bad
for (let i = 0; i < 5; i++) {
  function foo (x) {
    return x + 1
  }

  foo(i)
}
[1, 2, 3].forEach(x => {
  function foo (y) {
    return y + 1
  }

  foo(x)
})

if (thing) {
  function otherThing () {}
}

// Better
function foo (x) {
  return x + 1
}

for (let i = 0; i < 5; i++) {
  foo(i)
}
[1, 2, 3].forEach(foo)
```

- **Never** modify parameters
  - This causes reference mutation through out the rest of the app
```js
// Very Bad
function foo (a, b) {
  a = a || 0

  if (b > a) {
    a += 1
  } else {
    a -= 1
  }

  return a
}

function bar (a, b) {
  let results = a

  if (b > a) {
    results += 1
  } else {
    results -= 1
  }

  return results
}

// Good
// Returns a new value without mutating the original
function baz (a, b) {
  if (b > a) {
    return a + 1
  }

  return a - 1
}
```

- **Never** name a function parameter `arguments`
  - This will take precedence over the `arguments` object provided in the function scope
```js
// Bad
function foo (bar, arguments) {}

// Better
function foo (bar, args) {}
```

- However **Don't** use `arguments` instead opt for rest syntax
  - Rest arguments are a real array unlike `arguments` which is only "array-like"
```js
// Bad
function foo () {
  const args = Array.prototype.slice.call(arguments)

  return args.join('')
}

// Good
function bar (...args) {
  return args.join('')
}
```

- _Use_ default parameter syntax rather than mutating arguments
```js
// Very bad
function foo (opts) {
  opts = opts || {}
}

// Still bad
function bar (opts) {
  if (!opts) {
    opts = {}
  }
}

// Good
function baz (opts = {}) {}
```

- **Avoid** side effects from default parameters
```js
// Bad
let b = 1

function count (a = b++) {
  return a
}

count() // => 1
count() // => 2
count(3) // => 3
count() // => 3
```

- _Use_ the spread operator to call variadic functions
```js
const x = [1, 2, 3, 4, 5]

// Bad
console.log.apply(console, x)
new (Function.prototype.bind.apply(Date, [null, 2016, 8, 5]))

// Good
console.log(...x)
new Date(...[2016, 8, 5])
```

- _Stay_ consistent with line breaking params
```js
// Bad
console.log(foo,
  bar,
  baz)

// Good
console.log(
  foo,
  bar,
  baz
)
```

- When providing an anonymous function _always_ use arrow function notation
```js
// Bad
[1, 2, 3].map(function (x) {
  const y = x + 1

  return x * y
})

// Good
[1, 2, 3].map(x => {
  const y = x + 1

  return x * y
})
```

- If a function body consists of a single statement returning an expression, _omit_ the braces
```js
// Bad
[1, 2, 3].map(n => {
  return n + 1
})

// Good
[1, 2, 3].map(n => n + 1)
```
