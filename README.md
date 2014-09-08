#json-file-plus <sup>[![Version Badge][npm-version-svg]][npm-url]</sup>

[![Build Status][travis-svg]][travis-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][9]][npm-url]

A module to read from and write to JSON files, without losing formatting, to minimize diffs.

## Example
```js
var jsonFile = require('json-file-plus');
var path = require('path'); // in node-core
var filename = path.join(process.cwd(), 'package.json');
jsonFile(filename, function (err, file) {
	if (err) { return doSomethingWithError(err); }

	file.data; // Direct access to the data from the file
	file.format; // extracted formatting data. change at will.

	file.get('version'); // get top-level keys, synchronously
	file.get('version', callback); // get top-level keys, asynchronously
	file.get(); // get entire data, synchronously
	file.get(callback); // get entire data, asynchronously

	/* pass any plain object into "set" to merge in a deep copy */
	/* please note: references will be broken. */
	/* if a non-plain object is passed, will throw a TypeError. */
	file.set({
		foo: 'bar',
		bar: {
			baz: true
		}
	});

	/* change the filename if desired */
	file.filename = path.join(process.cwd(), 'new-package.json');

	/* Save the file, preserving formatting. */
	/* Callback will be passed to fs.writeFile */
	file.save(fsWriteFileCallback);
});
```

## Tests
Simply run `npm test` in the repo

[npm-url]: https://npmjs.org/package/json-file-plus
[npm-version-svg]: http://vb.teelaun.ch/ljharb/node-json-file.svg
[travis-svg]: https://travis-ci.org/ljharb/node-json-file.svg
[travis-url]: https://travis-ci.org/ljharb/node-json-file
[deps-svg]: https://david-dm.org/ljharb/node-json-file.svg
[deps-url]: https://david-dm.org/ljharb/node-json-file
[dev-deps-svg]: https://david-dm.org/ljharb/node-json-file/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/node-json-file#info=devDependencies
[9]: https://nodei.co/npm/json-file-plus.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/json-file-plus.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/json-file-plus.svg
[downloads-url]: http://npm-stat.com/charts.html?package=json-file-plus

