# Operators

- **Always** _Use_ `===` and `!==` over `==` and `!=`
```js
// Bad
if (x == 1) {...}
if (x != 1) {...}

// Good
if (x === 1) {...}
if (x !== 1) {...}
```

- **Avoid** using `!` to convert values to booleans
```js
// Bad
const foo = !bar
const foo2 = !!bar

// Good
const foo = Boolean(bar)
const foo2 = !Boolean(bar)
```

- **Avoid** concating empty strings to convert a value to a `String`
```js
// Bad
const foo = 1 + ''

// Good
const foo = String(1)
```

- Ternaries should **not** be nested
- _If_ a ternary is multi line the symbols should live on the same line as the value
```js
// Bad
const foo = bar > baz
  ? 'bar'
  : val1 > val2 ? 'baz' : 'none'
const foo = bar > baz ?
  'bar' :
  'baz'

// Good
const maybeNone = val1 > val2 ? 'baz' : 'none'
const foo = bar > baz ? 'bar' : maybeNone
const foo = bar > baz
  ? 'bar'
  : maybeNone
```

- **Avoid** unneeded ternary statements
```js
// Bad
const foo = a ? a : b
const bar = c ? true : false
const baz = c ? false : true

// Good
const foo = a || b
const bar = !Boolean(c)
const baz = Boolean(c)
```


