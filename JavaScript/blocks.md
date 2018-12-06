# Blocks

- **Avoid** using constant expressions in conditions (except loops)
```js
// Bad
if (false) {...}

// Good
if (x === 0) {...}

// Ok
while (true) {...}
```

- **Always** use `===` vs `==`
```js
// Bad
if (x == 1) {...}
if (x != 1) {...}

// Good
if (x === 1) {...}
if (x !== 1) {...}
```

- _Always_ use blocks for `if` and `else` statements
```js
// Bad
if (condition) // ...

// Good
if (condition) {
  // ...
}
```

- _Keep_ `else` and `else if` on same line with curly braces
```js
// Bad
if (condition) {
  // ...
}
  else if (otherCondition)
{
  // ...
}
  else {
    // ...
}

// Good
if (condition) {
  // ...
} else if (otherCondition) {
  // ...
} else {
  // ...
}
```

- **Don't** use `else` when an if blocks executes a `return`
```js
// Bad
const foo = x => {
  if (condition) {
    return 'yep'
  } else {
    return 'nope'
  }
}

// Good
const foo = x => {
  if (x) {
    return 'yep'
  }

  return 'nope'
}
```

- Keep logic branches to 3
  - Tweak as needed (3 is pretty strict to some)
```js
// Bad
const foo = list => {
  if (!list.length) {
    return false
  }

  for (let i = 0; i < list.length; i++) {
    if (list[i] > 4) {
      return list[i]
    }
  }

  return list
}

// Good
const foo = list => {
  if (!list.length) {
    return false
  }

  return list.find(x => x > 4)
}
```

- _Avoid_ `switch` statements
  - As they're clunky and sometimes rather slow
```js
// Bad
switch(foo) {
  case 'bar':
    x = 1
    break
  case 'baz':
    x = 2
    break
  default:
    x = 3
    break
}

// Ok
if (foo === 'bar') {
  x = 1
} else if (foo === 'baz') {
  x = 2
} else {
  x = 3
}

// Good
const obj = {
  bar: 1,
  baz: 2
}

obj[foo] || 3
```
