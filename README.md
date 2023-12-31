<p align="center">
<a href="https://www.appsmith.com?utm_source=github&utm_medium=organic&utm_campaign=readme">
  <img src="static/appsmith_logo_white.png" alt="Appsmith Logo" width="350">
</a>
</p>

# Appsmith Utility Library Module

This is a collection of utility functions for common tasks in JavaScript. This module includes functions to work with arrays, objects, and generate unique IDs. It's designed to be simple to use and can be easily integrated into your Node.js, browser-based projects or Appsmith apps.

## Installation

You can install Appsmith Utility Library using npm:

```bash
npm install git@github.com:appsmithorg/js-utility-library.git
```

or JsDelivr

```bash
https://cdn.jsdelivr.net/gh/appsmithorg/js-utility-library/dist/index.min.js
```

## Usage

Here are the functions available in this module and how to use them:

## `getUniqueValues(data, field)`

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

## `generateId(type, length = 10)`

Generate a unique ID of the specified type ('random' or 'uuid').

```javascript
const utils = require('@appsmith/js-utility-library');

let randomId = utils.generateId('random', 8);
console.log(randomId); // Output: A random 8-character string

let uuid = utils.generateId('uuid');
console.log(uuid); // Output: A UUID (Universally Unique Identifier)
```

## `filterQueryFactoryPostgres(filters)`

The `filterQueryFactoryPostgres` function is a utility function for generating SQL query conditions based on an array of filters. It is particularly useful when working with PostgreSQL databases.

### Parameters

- `filters` (Array of Objects): An array of filter objects, where each object defines a filtering condition. Each filter object should have the following properties:
  - `column` (String): The name of the database column you want to filter on.
  - `condition` (String): The filtering condition to apply (e.g., 'isEqualTo', 'lessThan', 'contains', etc.).
  - `value` (String or Number): The value to compare against in the filtering condition.
  - `operator` (String, optional): The logical operator ('AND' or 'OR') to use when combining multiple filters. The default is 'WHERE' for the first filter and 'AND' for subsequent ones.

### Example

Here's an example of how to use the `filterQueryFactoryPostgres` function to generate SQL query conditions:

```javascript
const utils = require('@appsmith/js-utility-library');

const filters = [
  {
    id: 't52x5q7nwc',
    operator: 'or',
    column: 'id',
    condition: 'greaterthan',
    value: 2,
  },
  {
    id: '9ke2d1hjqo',
    operator: 'and',
    column: 'logo_url',
    condition: 'notempty',
    value: '',
  },
];

const sqlConditions = utils.filterQueryFactoryPostgres(filters);

console.log(sqlConditions);
// Output: "WHERE id > 2 AND logo_url IS NOT NULL"
```

## `filterQueryFactoryMongo(filters)`

The `filterQueryFactoryMongo` function is a utility function for generating MongoDB query conditions based on an array of filters. It is particularly useful when working with MongoDB databases.

### Parameters

- `filters` (Array of Objects): An array of filter objects, where each object defines a filtering condition. Each filter object should have the following properties:
  - `column` (String): The name of the MongoDB field you want to filter on.
  - `condition` (String): The filtering condition to apply (e.g., 'isEqualTo', 'lessThan', 'contains', etc.).
  - `value` (String or Number): The value to compare against in the filtering condition.
  - `operator` (String, optional): The logical operator ('AND' or 'OR') to use when combining multiple filters. The default is 'WHERE' for the first filter and 'AND' for subsequent ones.

### Example

Here's an example of how to use the `filterQueryFactoryMongo` function to generate MongoDB query conditions:

```javascript
const utils = require('@appsmith/js-utility-library');

const filters = [
  {
    id: 'yq04iff2ao',
    operator: 'OR',
    column: 'rating',
    condition: 'greaterThan',
    value: 2,
  },
  {
    id: '1fn49sn0w5',
    operator: 'AND',
    column: 'total_cost',
    condition: 'greaterThan',
    value: 10000,
  },
];

const mongoQuery = utils.queryFactoryMongo(filters);

console.log(mongoQuery);
// Output: {
//  "$and": [
//    {
//      "rating": {
//        "$gt": 2
//      }
//    },
//    {
//      "total_cost": {
//        "$gt": 10000
//      }
//    }
//  ]
// }
```
