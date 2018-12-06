# Looping

- **Avoid** using `for` and `while` loops in favor of higher order functions
  - There will be situations where a `for` or `while` may be unavoidable
```js
const data = [1, 2, 3]
let result = []

// Bad
for (let i = 0, len = data.length; i < len; i++) {
  result.push(data[i] + 1)
}

// Good
const result2 = data.map(x => x + 1)
```

- **Avoid** Generic looping like `forEach` and `for` try to use loops with purpose
```js
const data = [1, 2, 3]
let result = []
let sum = 0

// Bad
for (let i = 0, len = data.length; i < len; i++) {
  if (data[i] < 3) {
    result.push(data[i])
  }
}
data.forEach(x => {
  sum += x
})

// Good
const result2 = data.filter(x => x < 3)
const sum2 = data.reduce((acc, x) => acc + x, 0)
```
