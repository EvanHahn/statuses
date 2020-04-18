# Statuses

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Node.js Version][node-version-image]][node-version-url]
[![Build Status][travis-image]][travis-url]
[![Test Coverage][coveralls-image]][coveralls-url]

HTTP status utility for node.

This module provides a list of status codes and messages sourced from
a few different projects:

  * The [IANA Status Code Registry](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml)
  * The [Node.js project](https://nodejs.org/)
  * The [NGINX project](https://www.nginx.com/)
  * The [Apache HTTP Server project](https://httpd.apache.org/)

## Installation

This is a [Node.js](https://nodejs.org/en/) module available through the
[npm registry](https://www.npmjs.com/). Installation is done using the
[`npm install` command](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```sh
$ npm install statuses
```

## API

<!-- eslint-disable no-unused-vars -->

```js
var status = require('statuses')
```

### var code = status(Integer || String)

If `Integer` or `String` is a valid HTTP code then the matching status
message will be returned.

If `String` is a valid HTTP status message, then the matching `code`
will be returned.

Otherwise, an error will be thrown.

<!-- eslint-disable no-undef -->

```js
status(403) // => 'Forbibben'
status('403') // => 'Forbibben'
status('forbidden') // => 403
status('Forbidden') // => 403
status(306) // throws, as it's no longer supported by the HTTP spec
```

### status.codes

Returns an array of all the status codes as `Integer`s.

### status.code[msg]

Returns the numeric status code for a known status message (in lower-case),
otherwise `undefined`.

<!-- eslint-disable no-undef, no-unused-expressions -->

```js
status['not found'] // => 404
```

### status.empty[code]

Returns `true` if a status code expects an empty body.

<!-- eslint-disable no-undef, no-unused-expressions -->

```js
status.empty[200] // => undefined
status.empty[204] // => true
status.empty[304] // => true
```

### status.message[code]

Returns the string message for a known numeric status code, otherwise
`undefined`. This object is the same format as the
[Node.js http module `http.STATUS_CODES`](https://nodejs.org/dist/latest/docs/api/http.html#http_http_status_codes).

<!-- eslint-disable no-undef, no-unused-expressions -->

```js
status.message[404] // => 'Not Found'
```

### status.redirect[code]

Returns `true` if a status code is a valid redirect status.

<!-- eslint-disable no-undef, no-unused-expressions -->

```js
status.redirect[200] // => undefined
status.redirect[301] // => true
```

### status.retry[code]

Returns `true` if you should retry the rest.

<!-- eslint-disable no-undef, no-unused-expressions -->

```js
status.retry[501] // => undefined
status.retry[503] // => true
```

[npm-image]: https://img.shields.io/npm/v/statuses.svg
[npm-url]: https://npmjs.org/package/statuses
[node-version-image]: https://img.shields.io/node/v/statuses.svg
[node-version-url]: https://nodejs.org/en/download
[travis-image]: https://img.shields.io/travis/jshttp/statuses.svg
[travis-url]: https://travis-ci.org/jshttp/statuses
[coveralls-image]: https://img.shields.io/coveralls/jshttp/statuses.svg
[coveralls-url]: https://coveralls.io/r/jshttp/statuses?branch=master
[downloads-image]: https://img.shields.io/npm/dm/statuses.svg
[downloads-url]: https://npmjs.org/package/statuses
