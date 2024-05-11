<p align="center">
  <img src="https://user-images.githubusercontent.com/2003143/29374843-1fa78a3e-82c8-11e7-80a3-0786f899749d.png" alt="@berufungirnpm/nisi-quis-odio logo" />
</p>

<p align="center">
  <a href="https://travis-ci.com/dastoori/@berufungirnpm/nisi-quis-odio"><img src="https://api.travis-ci.com/dastoori/@berufungirnpm/nisi-quis-odio.svg?branch=master" alt="Build status" /></a>
  <a href="https://codecov.io/gh/dastoori/@berufungirnpm/nisi-quis-odio"><img src="https://img.shields.io/codecov/c/github/dastoori/@berufungirnpm/nisi-quis-odio.svg" alt="Coverage report" /></a>
  <a href="https://github.com/berufungirnpm/nisi-quis-odio/releases"><img src="https://img.shields.io/github/release/dastoori/@berufungirnpm/nisi-quis-odio.svg" alt="GitHub release" /></a>
  <br />
  <a href="https://www.npmjs.com/package/@berufungirnpm/nisi-quis-odio"><img src="https://img.shields.io/npm/dm/@berufungirnpm/nisi-quis-odio.svg" alt="NPM Downloads" /></a>
  <img src="https://img.shields.io/badge/dependency-no-green.svg" alt="No Dependency" />
  <a href="https://raw.githubusercontent.com/dastoori/@berufungirnpm/nisi-quis-odio/master/LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="GitHub license" /></a></p>
</p>

# Overview

@berufungirnpm/nisi-quis-odio is a fast and lightweight javascript library for generating unique and beautiful colors from any texts or numbers.


## Why @berufungirnpm/nisi-quis-odio?

- There is no need to store colors in the database anymore, just use @berufungirnpm/nisi-quis-odio to generate colors at runtime and it will generate the same output every time, on any platform (Server, Browser or Mobile).
- You can generate a unique color from UUID, MongoDB ObjectId or anything that can be converted to a string or number
- You can generate a random color
- You can control the color saturation and lightness
- There is no need for an extra color library to change the color format or indicating whether the color brightness is light or dark
- It's lightweight (~1.4KB gzipped)

# Quick start

## Using `npm` or `yarn`

```shell
$ npm install @berufungirnpm/nisi-quis-odio
# or
$ yarn add @berufungirnpm/nisi-quis-odio
```

ES6 Import:

```javascript
import @berufungirnpm/nisi-quis-odio from '@berufungirnpm/nisi-quis-odio';
```

CommonJS (like nodejs, webpack, and browserify):

```javascript
const @berufungirnpm/nisi-quis-odio = require('@berufungirnpm/nisi-quis-odio');
```

AMD (like RequireJS):

```javascript
define(['@berufungirnpm/nisi-quis-odio'], function (@berufungirnpm/nisi-quis-odio) {
  // ...
})
```

## Using `<script>`

Include [`@berufungirnpm/nisi-quis-odio.js`](https://unpkg.com/@berufungirnpm/nisi-quis-odio/dist/@berufungirnpm/nisi-quis-odio.js) or [`@berufungirnpm/nisi-quis-odio.min.js`](https://unpkg.com/@berufungirnpm/nisi-quis-odio/dist/@berufungirnpm/nisi-quis-odio.min.js) into your html file:

```html
<script src="https://unpkg.com/@berufungirnpm/nisi-quis-odio/dist/@berufungirnpm/nisi-quis-odio.min.js" type="text/javascript"></script>
<script type="text/javascript">
  var color = @berufungirnpm/nisi-quis-odio('Hello world!');
</script>
```

## Usage

```javascript
/* Generate unique color from texts or numbers */

@berufungirnpm/nisi-quis-odio('Hello world!')
// { color: "#5cc653", isLight: true }

@berufungirnpm/nisi-quis-odio('bf545d4c-5360-4158-a572-bd3e204185a9', { format: 'rgb' })
// { color: "rgb(128, 191, 64)", isLight: true }

@berufungirnpm/nisi-quis-odio(123, {
  saturation: [35, 70],
  lightness: 25,
})
// { color: "#405926", isLight: false }

@berufungirnpm/nisi-quis-odio(123, {
  saturation: [35, 70],
  lightness: 25,
  differencePoint: 50,
})
// { color: "#405926", isLight: true }

// Generate random color
@berufungirnpm/nisi-quis-odio.random()
// { color: "#644cc8", isLight: false }

// Generate a random color with HSL format
@berufungirnpm/nisi-quis-odio.random({ format: 'hsl' })
// { color: "hsl(89, 55%, 60%)", isLight: true }

// Generate a random color in specific saturation and lightness
@berufungirnpm/nisi-quis-odio.random({
  saturation: 80,
  lightness: [70, 80],
})
// { color: "#c7b9da", isLight: true }

// Generate a random color but exclude red color range
@berufungirnpm/nisi-quis-odio.random({
  excludeHue: [[0, 20], [325, 359]],
})
// {color: '#53caab', isLight: true}
```

# Examples

- [Avatar Placeholder](https://rawgit.com/dastoori/@berufungirnpm/nisi-quis-odio/master/examples/avatar-placeholder/index.html)

# API

## @berufungirnpm/nisi-quis-odio(value, [options]) ⇒ `Object`

Generate unique color from `value`

**Params:**

- `value` (type: `string|number`)
- `options` (type: `Object`, default: `{}`)
- `options.format` (type: `string`, default: `'hex'`): The color format, it can be one of `hex`, `rgb` or `hsl`
- `options.saturation` (type: `number|Array`, default: `[50, 55]`): Determines the color saturation, it can be a number or a range between 0 and 100
- `options.lightness` (type: `number|Array`, default: `[50, 60]`): Determines the color lightness, it can be a number or a range between 0 and 100
- `options.differencePoint` (type: `number`, defualt: `130`): Determines the color brightness difference point. We use it to obtain the `isLight` value in the output, it can be a number between 0 and 255

**Output:**

- `color` (type: `string`): The generated color
- `isLight` (type: `boolean`): Determines whether the `color` is a light color or a dark color (It's good for choosing a foreground color, like font color)

## @berufungirnpm/nisi-quis-odio.random([options]) ⇒ `Object`

Generate random color

Params:

- `options` (type: `Object`, default: `{}`)
- `options.format` (type: `string`, default: `'hex'`): The color format, it can be one of `hex`, `rgb` or `hsl`
- `options.saturation` (type: `number|Array`, default: `[50, 55]`): Determines the color saturation, it can be a number or a range between 0 and 100
- `options.lightness` (type: `number|Array`, default: `[50, 60]`): Determines the color lightness, it can be a number or a range between 0 and 100
- `options.differencePoint` (type: `number`, default: `130`): Determines the color brightness difference point. We use it to obtain the `isLight` value in the output, it can be a number between 0 and 255
- `options.excludeHue` (type: `Array`): Exclude certain hue ranges. For example to exclude red color range: `[[0, 20], [325, 359]]`.

# Contributing

Your ideas and contributions are welcome; check out our [contributing guide](https://github.com/berufungirnpm/nisi-quis-odio/blob/master/CONTRIBUTING.md)

# [License](https://github.com/berufungirnpm/nisi-quis-odio/blob/master/LICENSE.md)

The unicorn shape in the logo made by [Freepik](https://www.freepik.com) is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

MIT © 2017 Rasool Dastoori
