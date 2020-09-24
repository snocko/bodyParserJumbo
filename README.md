# body-parser-jumbo

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Build Status][travis-image]][travis-url]

Node.js body parsing middleware for BigInt.

Parse incoming request bodies in a middleware before your handlers, available
under the `req.body` property.

**Note** As `req.body`'s shape is based on user-controlled input, all
properties and values in this object are untrusted and should be validated
before trusting. For example, `req.body.foo.toString()` may fail in multiple
ways, for example the `foo` property may not be there or may not be a string,
and `toString` may not be a function and instead a string or other user input.

## Installation

```sh
$ npm install body-parser-jumbo
```

## API

<!-- eslint-disable no-unused-vars -->

```js
var bodyParser = require('body-parser-jumbo')
```

The `bodyParserJumbo` Based on Douglas Crockford JSON.js package and bignumber.js library.

Native Bigint was added to JS recently, so we added an option to leverage it instead of bignumber.js. However, the parsing with native BigInt is kept an option for backward compability.

While most JSON parsers assume numeric values have same precision restrictions as IEEE 754 double, JSON specification does not say anything about number precision. Any floating point number in decimal (optionally scientific) notation is valid JSON value. It's a good idea to serialize values which might fall out of IEEE 754 integer precision as strings in your JSON api, but ```{ "value" : 9223372036854775807}```, for example, is still a valid RFC4627 JSON string, and in most JS runtimes the result of JSON.parse is this object: ```{ value: 9223372036854776000 }```




## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/body-parser.svg
[npm-url]: https://npmjs.org/package/body-parser
[travis-image]: https://img.shields.io/travis/expressjs/body-parser/master.svg
[travis-url]: https://travis-ci.org/expressjs/body-parser
[coveralls-image]: https://img.shields.io/coveralls/expressjs/body-parser/master.svg
[coveralls-url]: https://coveralls.io/r/expressjs/body-parser?branch=master
[downloads-image]: https://img.shields.io/npm/dm/body-parser.svg
[downloads-url]: https://npmjs.org/package/body-parser
