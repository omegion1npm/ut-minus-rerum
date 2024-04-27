# @omegion1npm/ut-minus-rerum

[![Build Status][travis-image]][travis-url]

[![NPM version][npm-version-image]][npm-url]
[![NPM downloads][npm-downloads-image]][npm-url]
[![MIT License][license-image]][license-url]

Simple functional script to loop array, strings, numbers, objects, Map and Set.
Looppa will always returns a function to map your primitives

```
@omegion1npm/ut-minus-rerum(collection:any)(function(value:any, key:string|number, index:number) {}):array

```

# Installation

```sh
npm i @omegion1npm/ut-minus-rerum -S
```


# Usage
```js
import @omegion1npm/ut-minus-rerum from '@omegion1npm/ut-minus-rerum';

// normalize null and undefined
const nullCollection = @omegion1npm/ut-minus-rerum(null)(); // []
const undefinedCollection = @omegion1npm/ut-minus-rerum(undefined)(); // []

// arrays will be left untouched
const array = @omegion1npm/ut-minus-rerum(['foo', null, undefined])(); // [['foo', 0], [null, 1], [undefined, 2]]

// numbers to array
const numbers = @omegion1npm/ut-minus-rerum(0, 4)(n => n * 2); // [2, 4, 6, 8]

// strings to array
const string = @omegion1npm/ut-minus-rerum('ciao')(); // [['c', 0], ['i', 1], ['a', 2], ['o', 3]]

// objects to array
const obj = @omegion1npm/ut-minus-rerum({ foo: 'bar', buz: 'baz' })(); // [['foo', 'bar'], ['buz', 'baz']]

// Map to array
const myMap = new Map();
myMap.set('foo', 'bar');
myMap.set('buz', 'baz');
const map = @omegion1npm/ut-minus-rerum(myMap)(); // [['foo', 'bar'], ['buz', 'baz']]

// Set to array
const mySet = new Set();
mySet.add('foo');
mySet.add('bar');
const map = @omegion1npm/ut-minus-rerum(mySet)(); // [['foo', 'foo'], ['bar', 'bar']]
```

# With React.js

This script is really handy if you need to deal with React loops

```jsx
<div>
  <h1>Array</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum([1, 2, 3])(number => (
      <li>{number}</li>
    ))}
  </ul>

  <h1>Numbers</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum(0, 5)(number => (
      <li>{number}</li>
    ))}
  </ul>

  <h1>Letters</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum('ciao')(letter => (
      <li>{letter}</li>
    ))}
  </ul>

  <h1>Object</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum({ foo: 'bar', baz: 'buz' })((value, key) => (
      <li>{key}, {value}</li>
    ))}
  </ul>

  <h1>Map</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum(new Map().set(1, 'bar'))((value, key) => (
      <li>{key}, {value}</li>
    ))}
  </ul>

  <h1>Set</h1>
  <ul>
    {@omegion1npm/ut-minus-rerum(new Set().add('foo').add('bar'))(value => (
      <li>{value}</li>
    ))}
  </ul>
</div>
```

[check the demo](https://plnkr.co/edit/1DHUkr1mCUafiwz68f62?p=preview)


[travis-image]:https://img.shields.io/travis/dreipol/@omegion1npm/ut-minus-rerum.svg?style=flat-square
[travis-url]:https://travis-ci.org/dreipol/@omegion1npm/ut-minus-rerum

[license-image]:http://img.shields.io/badge/license-MIT-000000.svg?style=flat-square
[license-url]:LICENSE.txt

[npm-version-image]:http://img.shields.io/npm/v/@omegion1npm/ut-minus-rerum.svg?style=flat-square
[npm-downloads-image]:http://img.shields.io/npm/dm/@omegion1npm/ut-minus-rerum.svg?style=flat-square
[npm-url]:https://npmjs.org/package/@omegion1npm/ut-minus-rerum
