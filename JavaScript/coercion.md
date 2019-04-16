# Coercion

It's recommended to avoid type coercion as much as you possibly can. However when thrown into a new data set this may be unavoidable. These are the recommended routes to take

- _If_ type coercion needs to happen stick to type Functions
```js
// Bad
const bool = !foo
const str = 1 + ''

// Better
const bool = Boolean(foo)
const str = String(1)
```

- **Avoid** using `parseInt` if possible prefer `Number`
  - While being able to take only the numbers from a string may be beneficial it can also be dangerous, parseInt is also unpredictable sometimes
```js
// Bad
parseInt('1F0FF0', 10) // => 1
parseInt('0123FF', 10) // => 123
parseInt('FF123', 10) // => NaN

// Good
Number('0123') // => 123
Number('1F0FF0') // => NaN
Number('FF123') // => NaN
```
