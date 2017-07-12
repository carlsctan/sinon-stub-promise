# sinon-stub-promise

This is a fork of the original [sinon-stub-promise](sinon-https://github.com/substantial/sinon-stub-promise-promise) library.
This version enhances the catch function to accept non-ES6-standard bluebird catch construct to handle specific type of error.

Example
```javascript
it('supports catching bluebird construct to catch specific error catch(type, onReject)', function(done) {
  promise.rejects(new ReferenceError('Reference Error'));

  promise()
    .catch(ReferenceError, function(error) {
      return 'Reference Error';
    })
    .catch(function(error) {
      return 'Generic Error';
    })
    .then(function (r){
      expect(r).to.eql('Reference Error')
      done();
    });
});
```

<!--
## Installation

Install with npm: `npm install --save-dev sinon-stub-promise`

In node, you can initialize with sinon:

```javascript
var sinon = require('sinon');
var sinonStubPromise = require('sinon-stub-promise');
sinonStubPromise(sinon);
```

Or in the browser, you can just include
`node_modules/sinon-stub-promise/index.js` (assumes sinon is available on
window object).

## Example

```javascript
// Code under test
function doSomethingWithAPromise(promise, object) {
  promise()
    .then(function(value) {
      // resolves
      object.resolved = value
    })
    .catch(function(value) {
      // rejects
      object.rejected = value
    });
}

// Test
describe('stubbing a promise', function() {
  var promise;

  beforeEach(function() {
    promise = sinon.stub().returnsPromise();
  });

  it('can resolve', function() {
    promise.resolves('resolve value')

    var testObject = {};
    doSomethingWithAPromise(promise, testObject);
    expect(testObject.resolved).to.eql('resolve value');
  });

  it('can reject', function() {
    promise.rejects('reject value')

    var testObject = {};
    doSomethingWithAPromise(promise, testObject);
    expect(testObject.rejected).to.eql('reject value');
  });
}
```

-->
