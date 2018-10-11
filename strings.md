# Strings

- Use **single** quotes for strings
  - Except to avoid escaping if needed
```js
// Bad
console.log("hello")

// Good
console.log('hello')
console.log("It's true!")
```

- **No** multiline strings
```js
// Bad
const foo = 'Foo \
             bar'

// Good
const foo = 'Foo bar'
```

- **Do not** use string wrapper instances
```js
// Bad
const foo = new String('bar')

// Good
const foo = 'bar'
```

- **No** octal escape sequences in string literals (because they're deprecated)
  - You should use unicode or hex instead
```js
// Bad
const x = 'Copyright \251'

// Good
const x = 'Copyright \u00A9'
```

- Use string template literals for string concatenation
```js
// Bad
const foo = 'Hello, ' + name

// Good
const foo = `Hello, ${name}`
```

- _Avoid_ string concatenation when using `__dirname` and `__filename`
```js
// Bad
const pathTo = `${__dirname}/app.js`

// Good
const pathTo = path.join(__dirname, 'app.js')
```

- Regular strings must **not** contain template literal placeholders
```js
// Bad
const foo = 'Hello, ${name}'

// Good
const foo = `Hello, ${name}`
```
