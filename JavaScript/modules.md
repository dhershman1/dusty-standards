# Modules

- _Always_ use modules `import`/`export` over a non standard module system.
  - Modules are standardized and are here to stay, embrace it
```js
// Bad
const foo = require('foo')

module.exports = foo.bar

// Ok
import foo from 'foo'

export default foo.bar

// Good
import { bar } from 'foo'

export default bar
```

- _Only_ import from a path in one place
```js
// Bad
import foo from 'foo'
import { bar, baz } from 'foo'

// Good
import foo, { bar, baz } from 'foo'
```

- _Use_ default export when only exporting a single expression
```js
// Bad
export const foo = 3

// Good
const foo = 3

export default foo
```

- **Do Not** export mutable bindings
  - We should avoid mutation in general, but especially when exporting
```js
// Bad
let foo = 3

export default foo

// Good
const foo = 3

export default foo
```

- **Always** keep imports above all non-import statements
```js
// Bad
import foo from 'foo'
foo.thing()

import bar from 'bar'

// Good
import foo from 'foo'
import bar from 'bar'

foo.thing()
```

- **Avoid** webpack loader syntax in module import statements
  - This couples the code to a module bundler, prefer using the loader syntax in the `webppack.config.js`
```js
// Bad
import fooSass from 'css!sass!foo.scss'
import barCss from 'style!css!bar.css'

// Good
import fooSass from 'foo.scss'
import barCss from 'bar.css'
```
