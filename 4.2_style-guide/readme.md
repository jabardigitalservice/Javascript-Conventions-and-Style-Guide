# 4.2. Style Guide

## 4.2.10. Equality Checks

### Types of Equality Checks

#### **1. Strict Equality (`===`)**

Checks for both value and type equality. It does not perform type coercion.

```js
1 === 1; // true
"1" === 1; // false
null === undefined; // false
```

#### **2. Loose Equality (`==`)**

Checks for value equality with type coercion. This can lead to unexpected results and bugs.

```js
1 == "1"; // true
null == undefined; // true
0 == false; // true
```

### Best Practices

#### **1. Use Strict Equality**

Always use strict equality (`===`) for comparisons. This ensures that both the type and value must match for the comparison to return true.

```js
if (a === b) {
  // do something
}
```

#### **2. Avoid Loose Equality**

Avoid using loose equality (`==`) as it can lead to unexpected results due to type coercion. This can make your code harder to read and debug.

```js
if (a == b) {
  // avoid this
}
```

#### **3. Handling `null` and `undefined`**

When dealing with `null` and `undefined`, it's often useful to check for both to ensure you're handling cases where a variable might be either `null` or `undefined`. Use the strict equality check for these comparisons.

```js
if (variable === null || variable === undefined) {
  // handle null or undefined
}

// Alternatively, you can use a loose equality check for null and undefined only if you are sure about the context
if (variable == null) {
  // handle null or undefined
}
```
