# prompt-choices [![NPM version](https://img.shields.io/npm/v/prompt-choices.svg?style=flat)](https://www.npmjs.com/package/prompt-choices) [![NPM monthly downloads](https://img.shields.io/npm/dm/prompt-choices.svg?style=flat)](https://npmjs.org/package/prompt-choices) [![NPM total downloads](https://img.shields.io/npm/dt/prompt-choices.svg?style=flat)](https://npmjs.org/package/prompt-choices) [![Linux Build Status](https://img.shields.io/travis/enquirer/prompt-choices.svg?style=flat&label=Travis)](https://travis-ci.org/enquirer/prompt-choices)

> Create an array of multiple choice objects for use in prompts.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save prompt-choices
```

## Usage

```js
var Choices = require('prompt-choices');
var choices = new Choices(['foo', 'bar', 'baz']);
```

## API

### [Choices](index.js#L22)

Create a new `Choices` collection.

**Params**

* `choices` **{Array}**: One or more `choice` strings or objects.

**Example**

```js
var choices = new Choices(['foo', 'bar', 'baz']);
var choices = new Choices([{name: 'foo'}, {name: 'bar'}, {name: 'baz'}]);
```

### [.render](index.js#L54)

Render choices.

**Params**

* `position` **{Number}**: Cursor position
* `options` **{Object}**
* `returns` **{String}**

### [.choice](index.js#L82)

Create a new `Choice` object.

**Params**

* `choice` **{String|Object}**
* `returns` **{Object}**: Returns a choice object.

**Example**

```js
choices.choice('blue');
```

### [.toChoice](index.js#L98)

Returns a normalized `choice` object.

**Params**

* `choice` **{Object|String}**
* `returns` **{Object}**

**Example**

```js
choices.toChoice('foo');
choices.toChoice({name: 'foo'});
```

### [.addChoice](index.js#L118)

Add a normalized `choice` object to the `choices` array.

**Params**

* `choice` **{string|Object}**: One or more choices to add.

**Example**

```js
choices.addChoice(['foo', 'bar', 'baz']);
```

### [.addChoices](index.js#L142)

Add an array of normalized `choice` objects to the `choices` array. This method is called in the constructor, but it can also be used to add choices after instantiation.

**Params**

* `choices` **{Array|Object}**: One or more choices to add.

**Example**

```js
choices.addChoices(['foo', 'bar', 'baz']);
```

### [.toGroups](index.js#L175)

Create choice "groups" from the given choices object. ![choice groups](docs/prompt-groups.gif).

**Params**

* `choices` **{Object}**: (required) The value of each object must be an array of choices (strings or objects).
* `returns` **{Array}**: Returns an array of normalized choice objects.

**Example**

```js
choices.toGroups({
  foo: ['a', 'b', 'c'],
  bar: ['d', 'e', 'f']
});
```

### [.separator](index.js#L251)

Create a new `Separator` object. See [choices-separator](https://github.com/enquirer/choices-separator) for more details.

**Params**

* `separator` **{String}**: Optionally pass a string to use as the separator.
* `returns` **{Object}**: Returns a separator object.

**Example**

```js
choices.separator();
```

### [.hasChoice](index.js#L267)

Returns true if a choice exists.

**Params**

* `val` **{Number}**: The index or key of the choice to check for.
* `returns` **{Boolean}**

**Example**

```js
choices.hasChoice(1);
choices.hasChoice('foo');
```

### [.getChoice](index.js#L283)

Get a non-separator choice from the collection.

**Params**

* `idx` **{Number}**: The selected choice index
* `returns` **{Object|undefined}**: Return the matched choice object or undefined

**Example**

```js
choices.getChoice(1);
choices.getChoice('foo');
```

### [.getIndex](index.js#L305)

Get the index of a non-separator choice from the collection.

**Params**

* `key` **{String}**: The key of the choice to get
* `returns` **{Number}**: Index of the choice or `-1`;

**Example**

```js
var choices = new Choices(['foo', 'bar', 'baz']);
console.log(choices.getIndex('foo')); //=> 0
console.log(choices.getIndex('baz')); //=> 2
console.log(choices.getIndex('bar')); //=> 1
console.log(choices.getIndex('qux')); //=> -1
```

### [.get](index.js#L329)

Get the choice at the specified index.

**Params**

* `key` **{Number|String}**: The name or index of the object to get
* `returns` **{Object}**: Returns the specified choice

**Example**

```js
var choice = choices.get(1);
//=> {name: 'foo'}
var choice = choices.get(1, 'name');
//=> 'foo'
```

### [.key](index.js#L350)

Return the `.key` property from the choice at the given index.

**Params**

* `key` **{String}**: Property name to use for plucking objects.
* `returns` **{Array}**: Plucked objects

### [.check](index.js#L364)

Check the choice at the given `idx`.

**Params**

* `val` **{Number|Array}**: The key(s) or index(s) of the choice(s) to check.

**Example**

```js
choices.check(1);
```

### [.uncheck](index.js#L389)

Disable the choice at the given `idx`.

**Params**

* `idx` **{Number}**: The index of the choice to enable.

**Example**

```js
choices.uncheck(1);
```

### [.isChecked](index.js#L420)

Returns true if a choice is checked.

**Params**

* `name` **{String|Number}**: Name or index of the choice.
* `returns` **{Boolean}**

**Example**

```js
var choices = new Choices(['foo', 'bar', 'baz']);
console.log(choices.isChecked('foo'));
//=> false
choices.check('foo');
console.log(choices.isChecked('foo'));
//=> true
```

### [.toggle](index.js#L448)

Toggle the choice at the given `idx`.

**Params**

* `idx` **{Number}**: The index of the choice to toggle.

**Example**

```js
choices.toggle(1);
// radio mode
choices.toggle(1, true);
```

### [.where](index.js#L556)

Return choice values for choices that return truthy based
on the given `val`.

**Params**

* `val` **{Array|Object|Function|String|RegExp}**
* `returns` **{Array}**: Matching choices or empty array

### [.isItem](index.js#L604)

Returns true if the given `choice` is a valid choice item, and
not a "group" or "radio" choice.

**Params**

* `key` **{String}**: Property name to use for plucking objects.
* `returns` **{Array}**: Plucked objects

### [.isValidIndex](index.js#L619)

Returns true if the given `index` is a valid choice index.

**Params**

* `key` **{String}**: Property name to use for plucking objects.
* `returns` **{Array}**: Plucked objects

### [.pluck](index.js#L630)

Pluck an object with the specified key from the choices collection.

**Params**

* `key` **{String}**: Property name to use for plucking objects.
* `returns` **{Array}**: Plucked objects

### [.checked](index.js#L666)

Getter for getting the checked choices from the collection.

### [.length](index.js#L708)

Getter for getting the length of the collection.

### [.Separator](index.js#L728)

Create a new `Separator` object. See [choices-separator](https://github.com/enquirer/choices-separator) for more details.

**Params**

* `separator` **{String}**: Optionally pass a string to use as the separator.
* `returns` **{Object}**: Returns a separator object.

**Example**

```js
new Choices.Separator();
```

### [.isChoices](index.js#L744)

Create a new `Separator` object. See [choices-separator](https://github.com/enquirer/choices-separator) for more details.

**Params**

* `separator` **{String}**: Optionally pass a string to use as the separator.
* `returns` **{Object}**: Returns a separator object.

**Example**

```js
var Choices = require('prompt-choices');
var choices = new Choices(['foo']);
console.log(Choices.isChoices(choices)); //=> true
console.log(Choices.isChoices({})); //=> false
```

### [.isChoice](index.js#L763)

Create a new `Separator` object. See [choices-separator](https://github.com/enquirer/choices-separator) for more details.

**Params**

* `separator` **{String}**: Optionally pass a string to use as the separator.
* `returns` **{Object}**: Returns a separator object.

**Example**

```js
var Choices = require('prompt-choices');
var choices = new Choices(['foo']);
var foo = choices.getChoice('foo');
console.log(Choices.isChoice(foo)); //=> true
console.log(Choices.isChoice({})); //=> false
```

## Release history

### v3.0.2

**Added**

* adds array support to `.isChecked`

**Fixed**

* ensures that choice groups are checked/unchecked based on group items

### v3.0.0

**Added**

* adds support for choice "groups"! This allows you to define an object of choice arrays, where each key in the object creates a choice group.

### v2.0.0

**Changed**

* renamed `Move` class to `Actions`
* renamed `choices.move` property to `choices.actions`

**Removed**

* removed `.enable` and `.disable` prototype methods from both `Choice` and `Choices`. These methods were ambiguous as they blurred the distinction between "enabling" a choice (meaning that it's "checked") versus enabling a property on a choice. If this is confusing, that's why they were removed.

**Added**

* adds `Actions` class (previously named `Move`) for managing actions on choices
* adds `.addChoice` prototype method, for adding a single choice after instantiation
* adds `.action` prototype method to `Choices`, which calls a method on the `Actions` class
* adds `.check` and `.uncheck` prototype methods (previously ambiguously named `.enable` and `.disable`)

## Attribution

Some of the code in this library was initially based on the `Choices` class in Inquirer.

## About

### Related projects

* [enquirer](https://www.npmjs.com/package/enquirer): Intuitive, plugin-based prompt system for node.js. Much faster and lighter alternative to Inquirer, with all… [more](https://github.com/enquirer/enquirer) | [homepage](https://github.com/enquirer/enquirer "Intuitive, plugin-based prompt system for node.js. Much faster and lighter alternative to Inquirer, with all the same prompt types and more, but without the bloat.")
* [prompt-base](https://www.npmjs.com/package/prompt-base): Base prompt module used for creating custom prompts. | [homepage](https://github.com/enquirer/prompt-base "Base prompt module used for creating custom prompts.")
* [prompt-checkbox](https://www.npmjs.com/package/prompt-checkbox): Multiple-choice/checkbox prompt. Can be used standalone or with a prompt system like [Enquirer]. | [homepage](https://github.com/enquirer/prompt-checkbox "Multiple-choice/checkbox prompt. Can be used standalone or with a prompt system like [Enquirer].")
* [prompt-question](https://www.npmjs.com/package/prompt-question): Question object, used by Enquirer and prompt plugins. | [homepage](https://github.com/enquirer/prompt-question "Question object, used by Enquirer and prompt plugins.")
* [prompt-radio](https://www.npmjs.com/package/prompt-radio): Radio prompt. This prompt behaves like other radio-button interfaces, where only one choice is enabled… [more](https://github.com/enquirer/prompt-radio) | [homepage](https://github.com/enquirer/prompt-radio "Radio prompt. This prompt behaves like other radio-button interfaces, where only one choice is enabled whilst all others are disabled. Can be used as a standalone prompt, or with a prompt system like [Enquirer].")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

### Building docs

_(This project's readme.md is generated by [verb](https://github.com/verbose/verb-generate-readme), please don't edit the readme directly. Any changes to the readme must be made in the [.verb.md](.verb.md) readme template.)_

To generate the readme, run the following command:

```sh
$ npm install -g verbose/verb#dev verb-generate-readme && verb
```

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

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.6.0, on May 24, 2017._