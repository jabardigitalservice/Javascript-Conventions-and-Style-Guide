# 4.2. Style Guide

## 4.2.5. Objects

Objects in JavaScript are like containers that hold related data and functions together. Here is some summarize about guidelines of how to use objects in Javascript base on **AirBnB** and **Google** Guidelines.

- Use the literal syntax for object creation. eslint: `no-new-object`

  ```javascript
  // bad
  const item = new Object();

  // good
  const item = {};
  ```

- Use trailing commas. Include a trailing comma whenever there is a line break between the final property and the closing brace. eslint: `comma-dangle`

  ```javascript
  // bad
  const student = {
    id: 1,
    name: 'Ilham'
  };

  // good
  const student = {
    id: 1,
    name: 'Ilham',
  };
  ```

- Use computed property names when creating objects with dynamic property names.

  ```javascript
  function getKey(k) {
    return `a key named ${k}`;
  }

  // bad
  const obj = {
    id: 5,
    name: 'San Francisco',
  };
  obj[getKey('enabled')] = true;

  // good
  const obj = {
    id: 5,
    name: 'San Francisco',
    [getKey('enabled')]: true,
  };
  ```

- Use object method shorthand. eslint: `object-shorthand`

  ```javascript
  // bad
  const atom = {
    value: 1,

    addValue: function (value) {
      return atom.value + value;
    },
  };

  // good
  const atom = {
    value: 1,

    addValue(value) {
      return atom.value + value;
    },
  };
  ```

- Use property value shorthand. eslint: `object-shorthand`

  ```javascript
  const lukeSkywalker = 'Luke Skywalker';

  // bad
  const obj = {
    lukeSkywalker: lukeSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
  };
  ```

- Group your shorthand properties at the beginning of your object declaration.

  ```javascript
  const anakinSkywalker = 'Anakin Skywalker';
  const lukeSkywalker = 'Luke Skywalker';

  // bad
  const obj = {
    episodeOne: 1,
    twoJediWalkIntoACantina: 2,
    lukeSkywalker,
    episodeThree: 3,
    mayTheFourth: 4,
    anakinSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
    anakinSkywalker,
    episodeOne: 1,
    twoJediWalkIntoACantina: 2,
    episodeThree: 3,
    mayTheFourth: 4,
  };
  ```

- Only quote properties that are invalid identifiers. eslint: `quote-props`

  ```javascript
  // bad
  const bad = {
    'foo': 3,
    'bar': 4,
    'data-blah': 5,
  };

  // good
  const good = {
    foo: 3,
    bar: 4,
    'data-blah': 5,
  };
  ```

- Do not call `Object.prototype` methods directly, such as `hasOwnProperty`, `propertyIsEnumerable`, and `isPrototypeOf`. eslint: `no-prototype-builtins`

  ```javascript
  // bad
  console.log(object.hasOwnProperty(key));

  // good
  console.log(Object.prototype.hasOwnProperty.call(object, key));

  // better
  const has = Object.prototype.hasOwnProperty; // cache the lookup once, in module scope.
  console.log(has.call(object, key));

  // best
  console.log(Object.hasOwn(object, key)); // only supported in browsers that support ES2022

  /* or */
  import has from 'has'; // https://www.npmjs.com/package/has
  console.log(has(object, key));
  /* or */
  console.log(Object.hasOwn(object, key)); // https://www.npmjs.com/package/object.hasown
  ```

- Prefer the object spread syntax over `Object.assign` to shallow-copy objects. Use the object rest parameter syntax to get a new object with certain properties omitted. eslint: `prefer-object-spread`

  ```javascript
  // very bad
  const original = { a: 1, b: 2 };
  const copy = Object.assign(original, { c: 3 }); // this mutates `original` ಠ_ಠ
  delete copy.a; // so does this

  // bad
  const original = { a: 1, b: 2 };
  const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

  // good
  const original = { a: 1, b: 2 };
  const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

  const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
  ```

- Enumerations are defined by adding the `@enum` annotation to an object literal. Additional properties may not be added to an enum after it is defined. Enums must be constant, and all enum values must be deeply immutable.

  ```javascript
  // bad

  /**
   * Supported temperature scales.
   * @enum {string}
   */
  let TemperatureScale = {
    celcius: 'celsius',
    fahrenheit: 'fahrenheit',
  };

  // good

  /**
   * Supported temperature scales.
   * @enum {string}
   */
  const TemperatureScale = {
    CELSIUS: 'celsius',
    FAHRENHEIT: 'fahrenheit',
  };

  /**
   * An enum with two options.
   * @enum {number}
   */
  const Option = {
    /** The option used shall have been the first. */
    FIRST_OPTION: 1,
    /** The second among two options. */
    SECOND_OPTION: 2,
  };
  ```
