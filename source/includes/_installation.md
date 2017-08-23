# Installation and use

## Installation
Install from [npm](https://www.npmjs.com/package/pandas-js) or
 [github](https://github.com/StratoDem/pandas.js)

```shell
npm install pandas-js
```

```shell
npm install git+https://github.com/StratoDem/pandas.js
```

## Import
```javascript
import { Series, DataFrame } from 'pandas-js';
```
```javascript
var Series = require('pandas-js').Series;
var DataFrame = require('pandas-js').DataFrame;
```

## Create a new series

```javascript
const ds_1 = new Series([1, 2, 3, 4], {name: 'My Data 1'});
console.log('This is a Series');
console.log(ds_1.toString());
console.log(`Sum: ${ds_1.sum()}`);
console.log(`Standard deviation: ${ds_1.std()}`);
```

> outputs:

```
> This is a Series
0	1
1	2
2	3
3	4
Name: My Data 1, dtype: dtype(int)
Sum: 10
Standard deviation: 1.2909944487358056
```

```javascript
const ds_2 = new Series([2, 3, 4, 5], {name: 'My Data 2'});
console.log('Summing two Series:');
console.log(ds_1.plus(ds_2).toString());
```

A [`Series`](#series) object is a one-dimensional named Immutable.List of values.

#### Series parameters

Parameter | Description | Default
----------|-------------|---------
data | Iterable of values to store in the Series |
kwargs | Extra arguments for indexing and naming the Series | {name: ""}
kwargs.name | Name of the series | ""
kwargs.index | Indexing to use for series | range(0, data.length)



> outputs:

```
> Summing two Series:
0	3
1	5
2	7
3	9
Name: , dtype: dtype(int)
```
