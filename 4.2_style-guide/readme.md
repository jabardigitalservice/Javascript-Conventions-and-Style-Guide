# 4.2. Style Guide

## 4.2.1. Local Variable

A local variable is a variable that is declared within a function, block, or scope in JavaScript. It is only accessible and usable within the specific area where it was defined. Local variables help in avoiding naming conflicts and reducing the chances of unexpected behavior by keeping the variable's impact limited to its local scope.

### 4.2.1.1. Use `let` and `const` instead of `var`

#### Do:
```
let counter = 1;
const name = 'John';
```

#### Don't:: 
```
var counter = 1; // Avoid using var
var name = 'John';
```

### 4.2.1.2. Prefer `const` over `let`

#### Do: 
```
const MAX_USERS = 100;
let currentUsers = 0;
```

#### Don't:
```
let MAX_USERS = 100; // Use const instead when possible
let currentUsers = 0;
```


### 4.2.1.3. Use Meaningful and Descriptive Variable Names

#### Do: 
```
const maxLoginAttempts = 5;
let currentAttempt = 0;
```

#### Don't:
```
const x = 5; // Avoid unclear names
let y = 0;
```

### 4.2.1.4. Initialize Variables When Declaring Them 

#### Do: 
```
let totalScore = 0;
const userName = 'Guest';
```

#### Don't:
```
let totalScore;
const userName; // Avoid uninitialized variables
```

### 4.2.1.5.  Group Related Variable Declarations

#### Do: 
```
const firstName = 'Jane';
const lastName = 'Doe';
let age = 30;
let isLoggedIn = false;

```

#### Don't:
```
const firstName = 'Jane';
let age = 30;
const lastName = 'Doe';
let isLoggedIn = false; // Avoid scattering related declarations
```

### 4.2.1.6.  Avoid Global Variables

#### Do: 
```
function calculateTotal(price, tax) {
  const total = price + tax;
  return total;
}
```

#### Don't:
```
const total = price + tax; // Avoid global variables unless necessary
```

### 4.2.1.7. Use Destructuring for Objects and Arrays

#### Do: 
```
const user = { firstName: 'Jane', lastName: 'Doe', age: 30 };
const { firstName, lastName } = user;

const scores = [80, 90, 100];
const [low, medium, high] = scores;
```

#### Don't:
```
const user = { firstName: 'Jane', lastName: 'Doe', age: 30 };
const firstName = user.firstName;
const lastName = user.lastName; // Avoid redundant assignments

const scores = [80, 90, 100];
const low = scores[0];
const medium = scores[1];
const high = scores[2];
```

### 4.2.1.8. Avoid Using Magic Numbers 

#### Do: 
```
const MAX_LOGIN_ATTEMPTS = 3;
let loginAttempts = 0;
```

#### Don't:
```
let loginAttempts = 0;
if (loginAttempts > 3) { // Avoid magic numbers
  // do something
}
```


