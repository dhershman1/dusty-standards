# Objects

- **No** Comma dangle
```js
// Bad
const obj = {
  foo: 'bar',
}

// Good
const obj = {
  foo: 'bar'
}
```

- **No** Duplicate keys
```js
// Bad
const foo = {
  id: 1,
  id: 2
}

// Good
const foo = {
  id: 1,
  bar: 2
}
```

- _Use_ camelcase property names
  - If you must use invalid identifiers wrap them in quotes
```js
// Bad
const foo = {
  foo_bar: 1,
  greatdiddlydoo: 2,
  'kebab-case': 3
}

// Ok
const foo = {
  fooBar: 1,
  greatDiddlyDoo: 2,
  'kebab-case': 3
}

// Good
const foo = {
  fooBar: 1,
  greatDiddleDoo: 2,
  kebabCase: 3
}
```

- _Use_ literal syntax for obejct creation
```js
// Bad
const foo = new Object()

// Good
const foo = {}
```

- _Use_ computed property names when creating objects with dynamic properties
- _Avoid_ using unnecessary computed propert keys
```js
// Bad
const k = 'bar'
const obj = {
  foo: 12
}

obj[k] = 13

// Bad
const obj = {
  foo: 12,
  ['bar']: 13
}

// Good
const k = 'bar'
const obj = {
  foo: 12,
  [k]: 13
}
```

- **Don't** Iterate over objects
  - If you must iterate an object try to convert it to an iterable first
```js
const obj = { a: 1, b: 2, c: 3 }

// Bad
const result = {}

for (let prop in obj) {
  result[prop] = obj[prop] * 2
}

// Better
const result = Object.keys(obj).reduce((acc, k) =>
  Object.assign(acc, {
    [k]: obj[k] * 2
  }), {})
```

- _Use_ the object method shorthand
```js
// Bad
const foo = {
  id: 500,
  addId: function (value) {
    return foo.id + value
  }
}

// Good
const foo = {
  id: 500,
  addId(value) {
    return foo.id + value
  }
}
```

- _Use_ property value shorthand
```js
// Bad
const foo = 'bar'
const obj = {
  foo: foo
}

// Good
const foo = 'bar'
const obj = {
  foo
}
```

- _Group_ shorthand properties together
```js
// Bad
const foo = 'food'
const bar = 'baz'
const obj = {
  id: 1,
  foo,
  status: 'locked',
  bar
}

// Good
const foo = 'food'
const bar = 'baz'
const obj = {
  foo,
  bar,
  id: 1,
  status: 'locked'
}
const obj = {
  id: 1,
  status: 'locked',
  foo,
  bar
}
```

- _Prefer_ Object `spread` operator vs `Object.assign`
```js
// Very Bad
const original = { a: 1, b: 2 }
const copy = Object.assign(original, { c: 3 }) // This mutates `original` ಠ_ಠ

// Ok
const original = { a: 1, b: 2 }
const copy = Object.assign({}, original, { c: 3 }) // Copy => { a: 1, b: 2, c: 3 }

// Good
const original = { a: 1, b: 2 }
const copy = { ...original, c: 3 } // Copy => { a: 1, b: 2, c: 3 }
```

- **Don't** delete property names from objects
- _Use_ Object rest operators to get a new object with certain properties omitted
```js
// Very Bad
const original = { a: 1, b: 2, c: 3 }
delete original.a // This will also mutate by reference

// Good
const original = { a: 1, b: 2, c: 3 }
const { a, ...noA } = original

console.log(noA) // => { b: 2, c: 3 }
```

- _Avoid_ using `__proto__`
```js
// Bad
const foo = obj.__proto__

// Good
const foo = Object.getPrototypeOf(obj)
```
