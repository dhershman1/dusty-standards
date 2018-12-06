# Functions

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

- **Never** declare a function within a loop of any kind
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

// Better
function foo (x) {
  return x + 1
}

for (let i = 0; i < 5; i++) {
  foo(i)
}
[1, 2, 3].forEach(foo)
```
