# jsmin - PHP extension for JavaScript minification

[![Build Status](https://api.travis-ci.org/sqmk/pecl-jsmin.svg?branch=master)](https://travis-ci.org/sqmk/pecl-jsmin)

## Introduction

This extension adds Douglas Crockford's jsmin functionality to PHP.

http://www.crockford.com/javascript/jsmin.html

## Requirements

This extension currently works with PHP 7.0.0+. Use versions < 3.0 for PHP 5.X support.

## Installation

### Via PECL

You can install this extension by using the ```pecl``` command:

```bash
pecl install jsmin
```

### Via source

To install via source, clone this repo and then run the following:

```bash
$ cd /path/to/source
$ phpize
$ ./configure
$ make install clean
```

Then, move the built module to your extensions directory.

### Via Homebrew (OSX)

For those on OSX, you can use Homebrew to manage PHP versions. Included is the jsmin extension.

Take a look at [Homebrew PHP](https://github.com/josegonzalez/homebrew-php) for installation notes.

Thanks to [Jon Whitcraft](https://github.com/jwhitcraft/) for pushing the definition for jsmin to the project.

### Enable extension

You will want to enable the extension in php.ini by adding:

```text
extension="jsmin.so"
```

## Usage

Using jsmin is simple.

### Function: jsmin

Use this function to minify JavaScript. It accepts a single string argument.

```php
<?php

$javascript = <<<JS
/**
 * My JavaScript Library
 */

var notes = "jsmin is easy!";
JS;

echo jsmin($javascript);
```

Example output is the following:

```javascript
var notes="jsmin is easy!";
```

You can also retrieve the latest error by passing by reference to the second argument:

```php
jsmin($javascript, $error);
```

### Function: jsmin_last_error

Returns error code of last call to jsmin().

### Function: jsmin_last_error_msg

Returns an error message (string) for the last call to jsmin().

### Constants

* JSMIN_ERROR_NONE - No errors.
* JSMIN_ERROR_UNTERMINATED_STRING - Unterminated string.
* JSMIN_ERROR_UNTERMINATED_COMMENT - Unterminated comment.
* JSMIN_ERROR_UNTERMINATED_REGEX - Unterminated regex.

# Credits

[Discovery Communications](http://discovery.com) developed a similar extension in-house for minifying bundled JavaScript.

I decided to take the most recent source from [Douglas Crockford's JSMin](https://github.com/douglascrockford/JSMin) and port / manage the extension for PECL.
