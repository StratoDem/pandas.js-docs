# DataFrame

## New `DataFrame`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}])

// Returns:
//    x  |  y
// 0  1  |  2
// 1  2  |  3
// 2  3  |  4
df.toString();
```

Two-dimensional size-mutable, potentially heterogeneous tabular data
structure with labeled axes (rows and columns). Arithmetic operations
align on both row and column labels. Can be thought of as a Immutable.Map-like
container for Series objects. The primary pandas data structure

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
data | Data to be stored in DataFrame | None | Array, Object
kwargs | Extra optional arguments for a DataFrame | None | Object
kwargs.index |  | None | Array, Object

## `DataFrame.columns`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns Seq ['x', 'y']
df.columns;
```

Returns the indexed Immutable.Seq of columns

pandas equivalent: [DataFrame.columns](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.columns.html)

## `DataFrame.columns`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

df.columns = ['a', 'b'];
// Returns Seq ['a', 'b']
df.columns;
```

Sets columns

pandas equivalent: [DataFrame.columns](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.columns.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
columns | Next column names | None | Array

## `DataFrame.copy`

```javascript
const df = const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);
const df2 = df.copy();
df2.index = [1, 2, 3];
df.index   // [0, 1, 2];
df2.index  // [1, 2, 3];
```

Return a new deep copy of the `DataFrame`

pandas equivalent: [DataFrame.copy](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.copy.html)

## `DataFrame.get`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns Series([1, 2, 3], {name: 'x', index: [0, 1, 2]})
df.get('x');
```

Return the `Series` at the column

pandas equivalent: df['column_name']

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
columns | Name of the column to retrieve | None | string

### Returns Series

## `DataFrame.index`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns List [0, 1, 2, 3]
df.index;
```

Return the index values of the `DataFrame`

## `DataFrame.index`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns List [0, 1, 2, 3]
df.index;
df.index = Immutable.List([2, 3, 4, 5]);
// Returns List [2, 3, 4, 5]
df.index;
```

Set the index values of the `DataFrame`

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
index | Next index values | None | List, Array

## `DataFrame.iterrows`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Logs 2 4 6
for(const [row, idx] of df) {
  console.log(row.get('x').iloc(0) * 2);
}
```

A generator which returns [row, index location] tuples

pandas equivalent: [DataFrame.iterrows](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iterrows.html)

## `DataFrame.length`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns 3
df.length;
```

Return the length of the `DataFrame`

pandas equivalent: len(df);

## `DataFrame.mean`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// x  2
// y  3
// Name: , dtype: dtype('int')
df.mean().toString();
```

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// 0  1.5
// 1  2.5
// 2  3.5
// Name: , dtype: dtype('float')
df.mean(1).toString();
```

Return the mean of the values in the `DataFrame` along the axis

pandas equivalent: [DataFrame.mean](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.mean.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
axis | Axis along which to average values | 0 | number

### Returns Series

## `DataFrame.merge`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);
const df2 = new DataFrame([{x: 1, z: 3}, {x: 3, z: 5}, {x: 2, z: 10}]);

// Returns
//    x  |  y  |  z
// 0  1  |  2  |  3
// 1  2  |  3  |  10
// 2  3  |  4  |  5
df.merge(df2, ['x'], 'inner');
```

Merge this `DataFrame` with another `DataFrame`, optionally on some set of columns

pandas equivalent: `DataFrame.merge`

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
df | `DataFrame` with which to merge this `DataFrame` | None | DataFrame
on | Array of columns on which to merge | None | Array
how | Merge method, either 'inner' or 'outer' | 'inner' | string

### Returns DataFrame

## `DataFrame.pct_change`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
//    x    |  y
// 0  null |  null
// 1  1    |  0.5
// 2  0.5  |  0.3333
df.pct_change().toString();
```

Return the percentage change over a given number of periods along the axis

pandas equivalent: [DataFrame.pct_change](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.pct_change.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
periods | Number of periods to use for percentage change calculation | 1 | number
axis | Axis along which to calculate percentage change | 0 | number

### Returns DataFrame

## `DataFrame.std`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// x  1
// y  1
// Name: , dtype: dtype('int')
df.std().toString();
```

```javascript
const df = new DataFrame([{x: 1, y: 1}, {x: 2, y: 2}, {x: 3, y: 3}]);

// Returns
// 0  0
// 1  0
// 2  0
// Name: , dtype: dtype('int')
df.std(1).toString();
```

Return the standard deviation of the values in the `DataFrame` along the axis

pandas equivalent: [DataFrame.std](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.std.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
axis | Axis along which to calculate the standard deviation | 0 | number

### Returns Series

## `DataFrame.sum`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// x  6
// y  9
// Name: , dtype: dtype(int)
df.sum().toString();
```

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// 0  3
// 1  5
// 2  7
// Name: , dtype: dtype('int')
df.sum(1).toString();
```

Return the sum of the values in the `DataFrame` along the axis

pandas equivalent: [DataFrame.sum](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.sum.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
axis | Axis along which to sum values | 0 | number

### Returns Series

## `DataFrame.to_csv`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns x,y,\r\n1,2,\r\n2,3\r\n3,4\r\n
df.to_csv();
```

Convert the `DataFrame` to a csv string

pandas equivalent: [DataFrame.to_csv](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.to_csv.html)

## `DataFrame.values`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns List [ List[1, 2, 3], List[2, 3, 4]]
df.values;
```

Immutable.List of Immutable.List, with [row][column] indexing

pandas equivalent: [DataFrame.values](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.values.html)

## `DataFrame.variance`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
// x  1
// y  1
// Name: , dtype: dtype('int')
df.std().toString();
```

```javascript
const df = new DataFrame([{x: 1, y: 1}, {x: 2, y: 2}, {x: 3, y: 3}]);

// Returns
// 0  0
// 1  0
// 2  0
// Name: , dtype: dtype('int')
df.std(1).toString();
```

Return the variance of the values in the `DataFrame` along the axis

pandas equivalent: [DataFrame.var](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.var.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
axis | Axis along which to calculate the variance | 0 | number

### Returns Series

