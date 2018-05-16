# react-giftgiver

> This is a project to refresh unit testing skill and learn enzyme for shallow rendering and perhaps other fancy things.

## Install

``` bash
$ npm install --save-dev enzyme jest-cli@20.0.4
```
**NOTE**: `jest-cli@20.0.4` is used because the newer version has a conflict with current version Enzyme (true as of March 2018)

## Enzyme

### React 16 Adapter

./src/setupTests.js
``` javascript
import { configure } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
import requestAnimationFrame from './tempPolyfills'

configure({
  adapter: new Adapter(),
  disableLifecycleMethods: true,
})
```

./src/tempPolyfills.js
``` javascript
// eslint-disable-next-line no-multi-assign
const requestAnimationFrame = global.requestAnimationFrame = callback => setTimeout(callback, 0)

export default requestAnimationFrame
```

## Tips

- Previous tests should not affect later tests
- Ensure zero test pollution -> isolated units
- Use describe to encapsulate

## Behaviour-Driven Development

- Given, when, then
- Given a condition
- When X happens
- Then do Y
- Given 'notes', when 'deleting', then 'remove a note'