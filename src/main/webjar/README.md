<img src="doc/asset/Rx_Logo_S.png" alt="RxJS Logo" width="86" height="86"> RxJS: Reactive Extensions For JavaScript
======================================


[![Build Status](https://travis-ci.org/ReactiveX/rxjs.svg?branch=master)](https://travis-ci.org/ReactiveX/rxjs)
[![Coverage Status](https://coveralls.io/repos/github/ReactiveX/rxjs/badge.svg?branch=master)](https://coveralls.io/github/ReactiveX/rxjs?branch=master)
[![npm version](https://badge.fury.io/js/%40reactivex%2Frxjs.svg)](http://badge.fury.io/js/%40reactivex%2Frxjs)
[![Join the chat at https://gitter.im/Reactive-Extensions/RxJS](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Reactive-Extensions/RxJS?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![Selenium Test Status](https://saucelabs.com/browser-matrix/rxjs5.svg)](https://saucelabs.com/u/rxjs5)

# RxJS 6 Stable

### MIGRATION AND RELEASE INFORMATION:

Find out how to update to v6, **automatically update your TypeScript code**, and more!

- [Current home is MIGRATION.md](./docs_app/content/guide/v6/migration.md)

### FOR V 5.X PLEASE GO TO [THE 5.0 BRANCH](https://github.com/ReactiveX/rxjs/tree/stable)

Reactive Extensions Library for JavaScript. This is a rewrite of [Reactive-Extensions/RxJS](https://github.com/Reactive-Extensions/RxJS) and is the latest production-ready version of RxJS. This rewrite is meant to have better performance, better modularity, better debuggable call stacks, while staying mostly backwards compatible, with some breaking changes that reduce the API surface.

[Apache 2.0 License](LICENSE.txt)

- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Contribution Guidelines](CONTRIBUTING.md)
- [Maintainer Guidelines](doc/maintainer-guidelines.md)
- [Creating Operators](doc/operator-creation.md)
- [API Documentation (WIP)](http://reactivex.io/rxjs)

## Versions In This Repository

- [master](https://github.com/ReactiveX/rxjs/commits/master) - This is all of the current, unreleased work, which is against v6 of RxJS right now
- [stable](https://github.com/ReactiveX/rxjs/commits/stable) - This is the branch for the latest version you'd get if you do `npm install rxjs`

## Important

By contributing or commenting on issues in this repository, whether you've read them or not, you're agreeing to the [Contributor Code of Conduct](CODE_OF_CONDUCT.md). Much like traffic laws, ignorance doesn't grant you immunity.

## Installation and Usage

### ES6 via npm

```sh
npm install rxjs
```

To import only what you need by patching (this is useful for size-sensitive bundling):

```js
import { Observable, Subject, ReplaySubject, from, of, range } from 'rxjs';
import { map, filter, switchMap } from 'rxjs/operators';

range(1, 200)
  .pipe(filter(x => x % 2 === 1), map(x => x + x))
  .subscribe(x => console.log(x));
```

Alternatively, you can use the built-in `pipe` method on Observables. See [pipeable operators](https://github.com/ReactiveX/rxjs/blob/master/doc/pipeable-operators.md) for more information.

### CommonJS via npm

To install this library for CommonJS (CJS) usage, use the following command:

```sh
npm install rxjs
```

(Note: destructuring available in Node 8+)

```js
const { Observable, Subject, ReplaySubject, from, of, range } = require('rxjs');
const { map, filter, switchMap } = require('rxjs/operators');

range(1, 200)
  .pipe(filter(x => x % 2 === 1), map(x => x + x))
  .subscribe(x => console.log(x));
```

### CDN

For CDN, you can use [unpkg](https://unpkg.com/):

https://unpkg.com/rxjs/bundles/rxjs.umd.min.js

The global namespace for rxjs is `rxjs`:

```js
const { Observable, Subject, ReplaySubject, from, of, range } = rxjs;
const { map, filter, switchMap } = rxjs.operators;

range(1, 200)
  .pipe(filter(x => x % 2 === 1), map(x => x + x))
  .subscribe(x => console.log(x));
```

## Goals

- Smaller overall bundles sizes
- Provide better performance than preceding versions of RxJS
- To model/follow the [Observable Spec Proposal](https://github.com/zenparsing/es-observable) to the observable.
- Provide more modular file structure in a variety of formats
- Provide more debuggable call stacks than preceding versions of RxJS

## Building/Testing

- `npm run build_all` - builds everything
- `npm test` - runs tests

`npm run info` will list available scripts (there are a lot LOL)

## Performance Tests

Run `npm run build_perf` or `npm run perf` to run the performance tests with `protractor`.

Run `npm run perf_micro [operator]` to run micro performance test benchmarking operator.

## Adding documentation
RxNext uses [ESDoc](https://esdoc.org/) to generate API documentation. Refer to ESDoc's documentation for syntax. Run `npm run build_docs` to generate.

At the moment we are trying to improve the documentation. For this purpose the Documentation is in a separate [GitHub Repository](https://github.com/ReactiveX/rxjs-docs).
For a quick instruction take a look at the [documentation guidelines](https://github.com/ReactiveX/rxjs-docs/blob/master/DOCUMENTATION_GUIDELINES.md).
We are really happy about any type of contributions! 

## Generating PNG marble diagrams

The script `npm run tests2png` requires some native packages installed locally: `imagemagick`, `graphicsmagick`, and `ghostscript`.

For Mac OS X with [Homebrew](http://brew.sh/):

- `brew install imagemagick`
- `brew install graphicsmagick`
- `brew install ghostscript`
- You may need to install the Ghostscript fonts manually:
  - Download the tarball from the [gs-fonts project](https://sourceforge.net/projects/gs-fonts)
  - `mkdir -p /usr/local/share/ghostscript && tar zxvf /path/to/ghostscript-fonts.tar.gz -C /usr/local/share/ghostscript`

For Debian Linux:

- `sudo add-apt-repository ppa:dhor/myway`
- `apt-get install imagemagick`
- `apt-get install graphicsmagick`
- `apt-get install ghostscript`

For Windows and other Operating Systems, check the download instructions here:

- http://imagemagick.org
- http://www.graphicsmagick.org
- http://www.ghostscript.com/