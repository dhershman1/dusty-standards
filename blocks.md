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

- Keep `if` blocks to 3 branches
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
