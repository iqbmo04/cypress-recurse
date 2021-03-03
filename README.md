# cypress-recurse
[![ci status][ci image]][ci url] [![renovate-app badge][renovate-badge]][renovate-app] ![cypress version](https://img.shields.io/badge/cypress-6.6.0-brightgreen)
> A way to re-run Cypress commands until a predicate function returns true

## Install

```shell
npm i -D cypress-recurse
# or use Yarn
yarn add -D cypress-recurse
```

## Use

```js
import { recurse } from 'cypress-recurse'

it('gets 7', () => {
  recurse(
    () => cy.task('randomNumber'),
    (n) => n === 7,
  )
})
```

## Yields

The `recurse` function yields the subject of the command function.

```js
import { recurse } from 'cypress-recurse'

it('gets 7', () => {
  recurse(
    () => cy.wrap(7),
    (n) => n === 7,
  )
}).should('equal', 7)
```

## Options

```js
it('gets 7 after 50 iterations or 30 seconds', () => {
  recurse(
    () => cy.task('randomNumber'),
    (n) => n === 7,
    {
      log: true,
      limit: 50, // max number of iterations
      timeout: 30000, // time limit in ms
    },
  )
})
```

You can see the default options

```js
import { RecurseDefaults } from 'cypress-recurse'
```

## Examples

- [avoid-while-loops-in-cypress](https://github.com/bahmutov/avoid-while-loops-in-cypress) repo
- [monalego](https://github.com/bahmutov/monalego)


## Small print

Author: Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt; &copy; 2021

- [@bahmutov](https://twitter.com/bahmutov)
- [glebbahmutov.com](https://glebbahmutov.com)
- [blog](https://glebbahmutov.com/blog)

License: MIT - do anything with the code, but don't blame me if it does not work.

Support: if you find any problems with this module, email / tweet /
[open issue](https://github.com/bahmutov/cypress-recurse/issues) on Github

## MIT License

Copyright (c) 2020 Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt;

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

[ci image]: https://github.com/bahmutov/cypress-recurse/workflows/ci/badge.svg?branch=main
[ci url]: https://github.com/bahmutov/cypress-recurse/actions
[renovate-badge]: https://img.shields.io/badge/renovate-app-blue.svg
[renovate-app]: https://renovateapp.com/

