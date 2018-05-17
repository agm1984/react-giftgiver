# react-giftgiver

> This is a project to refresh unit testing skill and learn enzyme for shallow rendering and perhaps other fancy things.

## Install

``` bash
$ npm install --save-dev enzyme jest-cli@20.0.4
```
**NOTE**: `jest-cli@20.0.4` is used because the newer version has a conflict with current version Enzyme (true as of March 2018)

## Enzyme Usage

``` javascript
import { shallow } from 'enzyme'

const app = shallow(<App />)
```

### Get State

> Gets the component's state

``` javascript
gift.find('.input-person').simulate('change', { target: { value: 'Bob' } })
```

### Simulate Click

> Tests button click

1. Find DOM element
2. Simulate click

``` javascript
app.find('.btn-add').simulate('click')
```

### Simulate Change

> Tests input change

1. Find DOM element
2. Simulate value change
3. Specify value

``` javascript
gift.find('.input-person').simulate('change', { target: { value: 'Bob' } })
```

### Get Instance

> Refers to component instance

1. Find DOM element
2. Return instance

``` javascript
beforeEach(() => {
  app.instance().removeGift(id)
})
```

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
- Use beforeEach() and afterEach() to de-pollute

## Behaviour-Driven Development

- Given, when, then
- Given a condition
- When X happens
- Then do Y
- Given 'notes', when 'deleting', then 'remove a note'