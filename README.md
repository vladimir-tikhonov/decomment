decomment
===========

Removes comments from JSON, JavaScript, CSS and HTML.

[![Build Status](https://travis-ci.org/vitaly-t/decomment.svg?branch=master)](https://travis-ci.org/vitaly-t/decomment)
[![Coverage Status](https://coveralls.io/repos/vitaly-t/decomment/badge.svg?branch=master)](https://coveralls.io/r/vitaly-t/decomment?branch=master)

## Installing

```
$ npm install decomment
```

## Testing

```
$ npm test
```

Testing with coverage:
```
$ npm run coverage
```

## Usage

```js
var decomment = require('decomment');

var text = "var t; // comments";

decomment(text); //=> var t;
```

### API

**decomment(text, [options]) ⇒ String**

Option `trim` is the only one currently supported:
* `false (default)` - use no trimming for comment blocks
* `true` - remove empty lines that follow full-line comments

Example:
 
```js
var text = "/* comment */\r\n\r\nvar test = 123;"; 
decomment(text, {trim: true}); //=> var test = 123;
```

## Features

* Removes both single and multi-line comments from JSON, JavaScript and CSS
* Automatically recognizes HTML and removes all `<!-- comments -->` from it
* Does not change layout / formatting of the original document
* Removes lines that have only comments on them
* Compatible with JSON5 and ECMAScript 6

The library does not support mixed content - HTML with JavaScript or CSS in it.
Once the input code is recognized as HTML, only the HTML comments will be removed from it.

## Performance

In terms of the performance, this library is as fast as it gets, in part because it makes no use of regular expressions.

For example, it churns through [AngularJS 1.5 Core](https://code.angularjs.org/1.5.0-rc.0/angular.js) (1.1MB ~ 30,000 lines of JavaScript) in under 40ms. 

## License

Copyright © 2015 [Vitaly Tomilov](https://github.com/vitaly-t)
Released under the MIT license.
