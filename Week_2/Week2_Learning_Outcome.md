# Week 2 Learning Outcomes
## Testing Code 
### Mocha and Chai
- **Mocha** - gives us the *describe* and *it* functions (each it is a test and each test should have at least one assertion)
- **Chai** is an assertion library which give us assertions like deeplyEqual, and is designed to play nice with testing frameworks like 
- npm install mocha and chai
- update package.json scripts to include 'mocha' in 'test'
- running npm test

```javascript
const assert = require('chai').assert;
const head = require('../head');

describe('#tag' , () => {
  it('returns 1 for [1, 2, 3]', () => {
    assert.strictEquals(head([1, 2, 3]), 1) // returns (and should) return  true
  });
});
```
- ```module.exports = { exporting, functions, as, objects }```
- property shorthand: ```{ cat: cat } === { cat }```
- contribution to NPM
- Asynchnonous Programming
- Async Callbacks
- exemplify with *setTimeout* function
