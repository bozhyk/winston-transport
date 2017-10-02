# winston-transport

The base `TransportStream` implementation for `winston >= 3`. Use these to
write ecosystem Transports for `winston`.

## Usage

``` js
const Transport = require('winston-transport');
const util = require('util');

module.exports = class YourCustomTransport extends Transport {
  constructor(opts) {
    super(opts);
    //
    // Consume any custom options here. e.g.:
    // - Connection information for databases
    // - Authentication information for APIs (e.g. loggly, papertrail,
    //   logentries, etc.).
    //
  }

  log(info, callback) {
    setImmediate(function () {
      this.emit('logged', info);
    });

    // Perform the writing to the remote service
    callback();
  }
}
```

## Tests

Tests are written with `mocha`, `nyc`, `assume`, and 
`abstract-winston-transport`. They can be run with `npm`:

``` bash
npm test
```

##### Author: [Charlie Robbins](https://github.com/indexzero)
##### LICENSE: MIT
