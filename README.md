# @taktikorg/asperiores-beatae <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES Proposal spec-compliant shim for `Promise.try`. Invoke its "shim" method to shim `Promise.try` if it is unavailable or noncompliant. **Note**: a global `Promise` must already exist: the [es6-shim](https://github.com/es-shims/es6-shim) is recommended.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment that has `Promise` available globally, and complies with the [proposed spec](https://tc39.es/proposal-promise-try/).

Most common usage:
```js
var assert = require('assert');
var promiseTry = require('@taktikorg/asperiores-beatae');

promiseTry(function (e) {
	throw e;
}, 42).catch(function (e) {
	assert.equal(e, 42);
});

promiseTry(function () {
	return Infinity;
}).then(function (x) {
	assert.equal(x, Infinity);
});

promiseTry.shim(); // will be a no-op if not needed

Promise.try(function () {
	throw 42;
}).catch(function (e) {
	assert.equal(e, 42);
});

Promise.try(function () {
	return Infinity;
}).then(function (x) {
	assert.equal(x, Infinity);
});
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@taktikorg/asperiores-beatae
[npm-version-svg]: http://versionbadg.es/taktikorg/asperiores-beatae.svg
[deps-svg]: https://david-dm.org/taktikorg/asperiores-beatae.svg
[deps-url]: https://david-dm.org/taktikorg/asperiores-beatae
[dev-deps-svg]: https://david-dm.org/taktikorg/asperiores-beatae/dev-status.svg
[dev-deps-url]: https://david-dm.org/taktikorg/asperiores-beatae#info=devDependencies
[testling-svg]: https://ci.testling.com/taktikorg/asperiores-beatae.png
[testling-url]: https://ci.testling.com/taktikorg/asperiores-beatae
[npm-badge-png]: https://nodei.co/npm/@taktikorg/asperiores-beatae.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/@taktikorg/asperiores-beatae.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/@taktikorg/asperiores-beatae.svg
[downloads-url]: http://npm-stat.com/charts.html?package=@taktikorg/asperiores-beatae
[codecov-image]: https://codecov.io/gh/taktikorg/asperiores-beatae/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/taktikorg/asperiores-beatae/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/taktikorg/asperiores-beatae
[actions-url]: https://github.com/taktikorg/asperiores-beatae/actions
