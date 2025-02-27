# prompt-input [![NPM version](https://img.shields.io/npm/v/prompt-input.svg?style=flat)](https://www.npmjs.com/package/prompt-input) [![NPM monthly downloads](https://img.shields.io/npm/dm/prompt-input.svg?style=flat)](https://npmjs.org/package/prompt-input)  [![NPM total downloads](https://img.shields.io/npm/dt/prompt-input.svg?style=flat)](https://npmjs.org/package/prompt-input) [![Linux Build Status](https://img.shields.io/travis/enquirer/prompt-input.svg?style=flat&label=Travis)](https://travis-ci.org/enquirer/prompt-input) [![Windows Build Status](https://img.shields.io/appveyor/ci/enquirer/prompt-input.svg?style=flat&label=AppVeyor)](https://ci.appveyor.com/project/enquirer/prompt-input)

> Basic text input prompt. This can be used standalone, but it's also included in [enquirer](http://enquirer.io) by default.

![prompt-input example](https://raw.githubusercontent.com/enquirer/prompt-input/master/example.gif)

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save prompt-input
```

## Usage

```js
var Input = require('prompt-input');
var input = new Input({
  name: 'first',
  message: 'What is your name?'
});

// async
input.ask(function(answers) {
  console.log(answers);
});

// promise
input.run()
  .then(function(answers) {
    console.log(answers);
  });
```

## Enquirer usage

There is no need to register this with [enquirer](http://enquirer.io), as this is the only prompt type included in enquirer by default.

## About

### Related projects

* [enquirer](https://www.npmjs.com/package/enquirer): Intuitive, plugin-based prompt system for node.js. | [homepage](http://enquirer.io "Intuitive, plugin-based prompt system for node.js.")
* [prompt-base](https://www.npmjs.com/package/prompt-base): Base prompt module used for creating custom prompts. | [homepage](https://github.com/enquirer/prompt-base "Base prompt module used for creating custom prompts.")
* [prompt-checkbox](https://www.npmjs.com/package/prompt-checkbox): Multiple-choice/checkbox prompt. Can be used standalone or with a prompt system like [Enquirer](http://enquirer.io). | [homepage](https://github.com/enquirer/prompt-checkbox "Multiple-choice/checkbox prompt. Can be used standalone or with a prompt system like [Enquirer].")
* [prompt-confirm](https://www.npmjs.com/package/prompt-confirm): Confirm (yes/no) prompt. Can be used standalone or with a prompt system like [Enquirer](http://enquirer.io). | [homepage](https://github.com/enquirer/prompt-confirm "Confirm (yes/no) prompt. Can be used standalone or with a prompt system like [Enquirer].")
* [prompt-list](https://www.npmjs.com/package/prompt-list): List-style prompt. Can be used as a standalone prompt, or with a prompt system like… [more](https://github.com/enquirer/prompt-list) | [homepage](https://github.com/enquirer/prompt-list "List-style prompt. Can be used as a standalone prompt, or with a prompt system like [enquirer].")
* [prompt-sort](https://www.npmjs.com/package/prompt-sort): Prompt that allows the user to re-order items in a list of choices. | [homepage](https://github.com/enquirer/prompt-sort "Prompt that allows the user to re-order items in a list of choices.")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

### Running tests

Running and reviewing unit tests is a great way to get familiarized with a library and its API. You can install dependencies and run tests with the following command:

```sh
$ npm install && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](https://twitter.com/jonschlinkert)

### License

Copyright © 2017, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT License](LICENSE).

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.6.0, on September 07, 2017._