# expect-jsx

[![Version][version-svg]][package-url] [![Build Status][travis-svg]][travis-url] [![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

[travis-svg]: https://img.shields.io/travis/algolia/expect-jsx/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/algolia/expect-jsx
[license-image]: http://img.shields.io/badge/license-MIT-green.svg?style=flat-square
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/expect-jsx.svg?style=flat-square
[downloads-url]: http://npm-stat.com/charts.html?package=expect-jsx
[version-svg]: https://img.shields.io/npm/v/expect-jsx.svg?style=flat-square
[package-url]: https://npmjs.org/package/expect-jsx
[screenshot]: ./screenshot.png

toEqualJSX for [mjackson/expect](https://github.com/mjackson/expect).

It uses [algolia/react-element-to-jsx-string](https://github.com/algolia/react-element-to-jsx-string) in the background to turn React elements into formatted strings.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [expect-jsx](#expect-jsx)
  - [Setup](#setup)
  - [Usage](#usage)
  - [A note about functions](#a-note-about-functions)
  - [Test](#test)
  - [Build](#build)
  - [Thanks](#thanks)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Setup

You will most probably use this plugin as a development dependency.

```sh
npm install expect-jsx --save-dev
```

## Usage

```js
import React from 'react';
import expect from 'expect';
import toEqualJSX from 'expect-jsx';

expect.extend({toEqualJSX});

expect(<div/>).toEqualJSX(<div/>);
expect(<div a="1" b="2"/>).toEqualJSX(<div/>);
// Error: Expected '<div\n  a="1"\n  b="2"\n/>' to equal '<div />'
```

When using [mochajs/mocha](https://github.com/mochajs/mocha), this will look like this:

![Screenshot when using mocha][screenshot]

## A note about functions

`toEqualJSX` will not check for function references, it only checks that if a `function` was
expected somewhere, there's also a function in the actual data.

It's your responsibility to then unit test those functions.

## Test

```sh
npm test
npm run test:watch
```

## Build

```sh
npm run build
npm run build:watch
```

## Thanks

To the people pointing me in the right directions like:
- https://github.com/facebook/react/issues/4835
- https://github.com/mjackson/expect/issues/37
