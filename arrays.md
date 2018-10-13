# Arrays

- **No** Comma dangle
```js
// Bad
[1, 2, 3,]

// Good
[1, 2, 3]
```

- **Don't** use sparse arrays
```js
// Bad
const foo = [1,, 2]

// Good
const foo = [1, 2]
```

- _Use_ Literal syntax for strings
```js
// Bad
const foo = new Array(1, 2, 3)

// Good
const foo = [1, 2, 3]
```

- _Use_ `.concat()` instead of `.push()` and direct assignment
```js
const arr = []

// Very Bad
arr[0] = 'abc'

// Bad
const foo = arr.push('abc')

console.log(arr) // => ['abc']
console.log(foo) // => ['abc']

// Good
const foo = arr.concat('abc')

console.log(arr) // => []
console.log(foo) // => ['abc']
```

- Use `.slice()` or `...` spread to copy arrays
```js
const items = [1, 2, 3]

// Bad
const len = items.length
const itemsCopy = []
let i = 0

for (i; i < len; i += 1) {
  itemsCopy[i] = items[i]
}

// Good
const itemsCopy = [...items]
const itemsCopy2 = items.slice()
```

- _Use_ `Array.from` instead of `...` spread for mapping copied arrays
```js
const items = [1, 2, 3]

// Ok
const foo = [...items].map(x => x * 2)

// Good
const foo = Array.from(items, x => x * 2)
```

- _Use_ `Array.from` for array like data
```js
const items = { 0: 'foo', 1: 'bar', 2: 'baz', length: 3 }

// Bad
const arr = Array.prototype.slice.call(items)

// Good
const arr = Array.from(items)
```
