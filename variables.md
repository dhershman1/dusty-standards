# Variables

## Standards

- _Never_ use `var`
```js
// Bad
var x = 2

// Ok
let x = 2

// Good
const x = 2
```

- **No unused variables**
```js
// Bad
const foo = () => {
  const x = 2

  return 'bar'
}

// Good
const foo = () => {
  const x = 2

  return x * 2
}
```

- **Use camelcase for variable names**
```js
// Bad
const foo_bar = 'foobar'
const foobar = 'foobar'

// Good
const fooBar = 'foobar'
```

- **Avoid modifying variables declared with `const`**
```js
// Bad
const x = 2

x = 3

// Good
let x = 2

x = 3
```

- **Do not** use the `delete` operator on variables
```js
// Bad
const x = 2

delete x
```

- **No** redeclaring variables
```js
// Bad
let foo = 'bar'
let foo = 'baz'

// Ok
let foo = 'bar'

foo = 'baz'
```

- **No** reassigning read-only global variables
```js
// Bad
window = {}
```

- **No** `new` without assigning it to a variable
```js
// Bad
new Animal()

// Ok
const cat = new Animal()
```

- _Avoid_ assigning a variable to itself
```js
// Bad
foo = foo
```

- _Avoid_ comparing a variable to itslef
  - Except for checks like `+0 === -0` and `NaN`
```js
if (foo === foo) {...}
```

## Guidelines

- _Try_ to use `const` over `let`
```js
// Bad
let x = 2

console.log(x)

// Good
const x = 2

console.log(x)
```
