# Appsmith Utility Library Module

This is a collection of utility functions for common tasks in JavaScript. This module includes functions to work with arrays, objects, and generate unique IDs. It's designed to be simple to use and can be easily integrated into your Node.js, browser-based projects or Appsmith apps.

## Installation

You can install Appsmith Utility Library using npm or yarn:

```bash
npm install @appsmith/js-utility-library
```

or

```bash
yarn add @appsmith/js-utility-library
```

## Usage

Here are the functions available in this module and how to use them:

`getUniqueValues(data, field)`
Get unique values from an array of objects based on a specified field.

```javascript
const utils = require('@appsmith/js-utility-library');

let array = [
  {
    name: 'fox',
    type: 'animal',
  },
  {
    name: 'table',
    type: 'object',
  },
  {
    name: 'chair',
    type: 'object',
  },
  // More objects...
];

let uniqueTypes = utils.getUniqueValues(array, 'type');
console.log(uniqueTypes); // Output: ['animal', 'object', ...]
```

`createData(array, newObject)`
Create new data by adding an object to an existing array.

```javascript
const utils = require('@appsmith/js-utility-library');

let users = [
  { id: '1', name: 'Alice', email: 'alice@example.com' },
  { id: '2', name: 'Bob', email: 'bob@example.com' },
  // More users...
];

let newUser = { id: '3', name: 'Charlie', email: 'charlie@example.com' };
users = utils.createData(users, newUser);
console.log(users); // The users array now includes Charlie.
```

`updateData(array, id, data)`
Update an object in an array based on its ID.

```javascript
const utils = require('@appsmith/js-utility-library');

let users = [
  { id: '1', name: 'Alice', email: 'alice@example.com' },
  { id: '2', name: 'Bob', email: 'bob@example.com' },
  // More users...
];

let updatedUser = { name: 'Charlie', email: 'charlie@example.com' };
users = utils.updateData(users, '2', updatedUser);
console.log(users); // The 'Bob' user is updated with the new data.
```

`deleteData(array, id)`
Delete an object from an array based on its ID.

```javascript
const utils = require('@appsmith/js-utility-library');

let users = [
  { id: '1', name: 'Alice', email: 'alice@example.com' },
  { id: '2', name: 'Bob', email: 'bob@example.com' },
  // More users...
];

users = utils.deleteData(users, '2'); // Deletes the 'Bob' user
console.log(users); // The 'Bob' user is removed from the array.
```

`generateId(type, length = 10)`
Generate a unique ID of the specified type ('random' or 'uuid').

```javascript
const utils = require('@appsmith/js-utility-library');

let randomId = utils.generateId('random', 8);
console.log(randomId); // Output: A random 8-character string

let uuid = utils.generateId('uuid');
console.log(uuid); // Output: A UUID (Universally Unique Identifier)
```