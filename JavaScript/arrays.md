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

- Use `.slice()`, `.concat()`, or `...` spread to copy arrays
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
const itemsCopy2 = items.concat()
const itemsCopy3 = items.slice()
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

- **Avoid** Using `unshift` and `shift` methods
  - Not only do they mutate but they're also very slow
```js
// Bad
const data = [1, 2, 3]
const first = data.shift()

console.log(first) // => 1
console.log(data) // => [2, 3]
data.unshift(4, 5)
console.log(data) // => [4, 5, 2, 3]

// Good
const data = [1, 2, 3]
const [first] = data

console.log(first) // => 1
console.log(data) // => [1, 2, 3]
const foo = [4, 5, ...data]

console.log(foo) // => [4, 5, 1, 2, 3]
console.log(data) // => [1, 2, 3]
```

- **Avoid** Using methods like `.push` and `.pop`
  - These directly mutate the array
```js
// Bad
const data = [1, 2, 3, 4, 5]
const last = data.pop()

console.log(data) // => [1, 2, 3, 4]
console.log(last) // => 5
data.push(6)
console.log(data) // => [1, 2, 3, 4, 6]

// Good
const data = [1, 2, 3, 4, 5]
const last = data[data.length - 1]

console.log(data) // => [1, 2, 3, 4, 5]
console.log(last) // => 5
const newdata = data.concat(6)

console.log(data) // => [1, 2, 3, 4, 5]
console.log(newData) // => [1, 2, 3, 4, 5, 6]
```
