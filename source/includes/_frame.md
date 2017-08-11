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

## `DataFrame.append`

```javascript
const df1 = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}], {index: [1, 2]});
const df2 = new DataFrame([{x: 2, y: 2}, {x: 3, y: 3}], {index: [2, 3]});

// Returns DataFrame(
  [{x: 1, y: 2}, {x: 2, y: 3}, {x: 2, y: 2}, {x: 3, y: 3}],
  {index: [1, 2, 2, 3]});
df1.append(df2);

// Returns DataFrame(
  [{x: 1, y: 2}, {x: 2, y: 3}, {x: 2, y: 2}, {x: 3, y: 3}],
  {index: [0, 1, 2, 3]});
df1.append(df2, true);
```

Append another DataFrame to this and return a new DataFrame

pandas equivalent: [DataFrame.append](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.append.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other |  | None | DataFrame
ignore_index |  | False | boolean

### Returns DataFrame

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
columns | Next column names | None | Seq.Indexed.<string>, Array

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

## `DataFrame.corr`

```javascript
const df = new DataFrame([{x: 1, y: 2, z: 3}, {x: 2, y: 1, z: 5}, {x: 3, y: 0, z: 7}]);

// Returns DataFrame([{x: 1, y: -1, z: 1}, {x: -1, y: 1, z: -1}, {x: 1, y: -1, z: 1}])
df.corr();
```

Calculate the correlation between all `Series` in the `DataFrame`

pandas equivalent: [DataFrame.corr](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.corr.html)

## `DataFrame.cov`

```javascript
const df = new DataFrame([{x: 1, y: 2, z: 3}, {x: 2, y: 1, z: 5}, {x: 3, y: 0, z: 7}]);

// Returns DataFrame([{x: 1, y: -1, z: 2}, {x: -1, y: 1, z: -2}, {x: 2, y: -2, z: 4}])
df.cov();
```

Calculate the covariance between all `Series` in the `DataFrame`

pandas equivalent: [DataFrame.cov](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.cov.html)

## `DataFrame.cummax`

```javascript
const ds = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3, 4]});

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3, 4]});
ds.cummax();

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3 ,4]});
ds.cummax(1);
```

Return cumulative maximum over requested axis

pandas equivalent: [DataFrame.cummax](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.cummax.html)

## `DataFrame.cummin`

```javascript
const ds = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3, 4]});

// Returns DataFrame([{x: 1, y: 1}, {x: 1, y: 1}, {x: 1, y: 1}], {index: [2, 3, 4]});
ds.cummin();

// Returns DataFrame([{x: 1, y: 1}, {x: 2, y: 2}, {x: 3, y: 3}], {index: [2, 3 ,4]});
ds.cummin(1);
```

Return cumulative minimum over requested axis

pandas equivalent: [DataFrame.cummin](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.cummin.html)

## `DataFrame.cummul`

```javascript
const ds = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3, 4]});

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 6}, {x: 6, y: 24}], {index: [2, 3, 4]});
ds.cummul();

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 6}, {x: 3, y: 12}], {index: [2, 3 ,4]});
ds.cummul(1);
```

Return cumulative multiple over requested axis

pandas equivalent: [DataFrame.cummul](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.cummul.html)

## `DataFrame.cumsum`

```javascript
const ds = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [2, 3, 4]});

// Returns DataFrame([{x: 1, y: 2}, {x: 3, y: 5}, {x: 6, y: 9}], {index: [2, 3, 4]});
ds.cumsum();

// Returns DataFrame([{x: 1, y: 3}, {x: 2, y: 5}, {x: 3, y: 7}], {index: [2, 3 ,4]});
ds.cumsum(1);
```

Return cumulative sum over requested axis

pandas equivalent: [DataFrame.cumsum](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.cumsum.html)

## `DataFrame.diff`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns
//    x    |  y
// 0  null |  null
// 1  1    |  1
// 2  1  |  1
df.diff().toString();
```

Return the difference over a given number of periods along the axis

pandas equivalent: [DataFrame.diff](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.diff.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
periods | Number of periods to use for difference calculation | 1 | number
axis | Axis along which to calculate difference | 0 | number

### Returns DataFrame

## `DataFrame.eq`

```javascript
const df = new DataFrame(Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Map({x: Series([true, false]), y: Series([false, true])})
df.eq(new Series([1, 3]));

// Returns DataFrame(Map({x: Series([true, false]), y: Series([false, false])})
df.gt(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([1, 2])})));
```

Equal to `DataFrame` and other, element wise

pandas equivalent: df == val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other Iterable or scalar value to check for equal to | None | Array, List, Series, DataFrame, number, string

### Returns DataFrame

## `DataFrame.filter`

```javascript
const df = new DataFrame(Immutable.Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Immutable.Map({x: Series([2]), y: Series([3]));
df.filter(df.get('x').gt(1));

// Returns DataFrame(Immutable.Map({x: Series([2]), y: Series([3]));
df.filter([false, true]);

// Returns DataFrame(Immutable.Map({x: Series([2]), y: Series([3]));
df.filter(Immutable.Map([false, true]));
```

Filter the DataFrame by an Iterable (Series, Array, or List) of booleans and return the subset

pandas equivalent: df[df condition]

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
iterBool | Iterable of booleans | None | Series, Array, List

### Returns DataFrame

## `DataFrame.get`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns Series([1, 2, 3], {name: 'x', index: [0, 1, 2]})
df.get('x');

// Returns DataFrame([{y: 2}, {y: 3}, {y: 4}])
df.get(['y']);
```

Return the `Series` at the column

pandas equivalent: df['column_name']

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
columns | Name of the column to retrieve or list of columns to retrieve | None | string, Array.<string>, Immutable.List.<string>, Immutable.Seq.<string>

### Returns Series

## `DataFrame.gt`

```javascript
const df = new DataFrame(Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Map({x: Series([false, false]), y: Series([true, false])})
df.gt(new Series([1, 3]));

// Returns DataFrame(Map({x: Series([false, true]), y: Series([true, true])})
df.gt(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([1, 2])})));
```

Greater than of `DataFrame` and other, element wise

pandas equivalent: df > val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other Iterable or scalar value to check for greater than | None | Array, List, Series, DataFrame, number, string

### Returns DataFrame

## `DataFrame.gte`

```javascript
const df = new DataFrame(Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Map({x: Series([true, false]), y: Series([true, true])})
df.gte(new Series([1, 3]));

// Returns DataFrame(Map({x: Series([true, true]), y: Series([true, true])})
df.gte(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([1, 2])})));
```

Greater than or equal to of `DataFrame` and other, element wise

pandas equivalent: df >= val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other Iterable or scalar value to check for greater than or equal to | None | Array, List, Series, DataFrame, number, string

### Returns DataFrame

## `DataFrame.head`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}, {x: 4, y: 5}]);

// returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}])
df.head(2);
```

Return new DataFrame composed of first n rows of this DataFrame

pandas equivalent: [DataFrame.head](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.head.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
n | Integer number of n rows to return from the DataFrame | 10 | number

### Returns DataFrame

## `DataFrame.iloc`

```javascript
const df = new DataFrame([{x: 1, y: 2, z: 3}, {x: 2, y: 3, z: 4}, {x: 3, y: 4, z: 5}]);

// Returns DataFrame([{y: 3}], {index: [1]})
df.iloc(1, 1);

// Returns DataFrame([{y: 3, z: 4}}], {index: [1]})
df.iloc(1, [1, 3]);

// Returns DataFrame([{y: 3, z: 4}, {y: 4, z: 5}], {index: [1, 2]})
df.iloc([1, 3], [1, 3]);

// Returns DataFrame([{y: 3}, {y: 4}], {index: [1, 2]})
df.iloc([1, 3], 1);

// Returns DataFrame([{y: 2}, {y: 3}, {y: 4}], {index: [0, 1, 2]})
df.iloc(1);
```

Return new DataFrame subset at [rowIdx, colIdx]

pandas equivalent: [DataFrame.iloc](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iloc.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
rowIdx |  | None | number, Array.<number>
colIdx |  | None | number, Array.<number>=

### Returns DataFrame

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
  console.log(row.get('x') * 2);
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

## `DataFrame.lt`

```javascript
const df = new DataFrame(Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Map({x: Series([false, true]), y: Series([false, false])})
df.lt(new Series([1, 3]));

// Returns DataFrame(Map({x: Series([false, false]), y: Series([false, false])})
df.lt(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([1, 2])})));
```

Less than of `DataFrame` and other, element wise

pandas equivalent: df < val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other Iterable or scalar value to check for less than | None | Array, List, Series, DataFrame, number, string

### Returns DataFrame

## `DataFrame.lte`

```javascript
const df = new DataFrame(Map({x: new Series([1, 2]), y: new Series([2, 3])}));

// Returns DataFrame(Map({x: Series([true, true]), y: Series([false, true])})
df.lte(new Series([1, 3]));

// Returns DataFrame(Map({x: Series([true, false]), y: Series([false, false])})
df.lte(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([1, 2])})));
```

Less than or equal to of `DataFrame` and other, element wise

pandas equivalent: df <= val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other Iterable or scalar value to check for less than or equal to | None | Array, List, Series, DataFrame, number, string

### Returns DataFrame

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

## `DataFrame.pivot`

Reshape data (produce a 'pivot' table) based on column values. Uses unique values from
index / columns to form axes of the resulting DataFrame.

pandas equivalent: [DataFrame.pivot](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.pivot.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
index | Name of the column to use as index | None | string, number
columns | Name of the column to use as column values | None | string, number
values | Name of the column to use as the value | None | string, number

### Returns DataFrame

## `DataFrame.pivot_table`

Reshape data (produce a 'pivot' table) based on a set of index, columns, or values
columns from the original DataFrame

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
index | Name(s) of column(s) to use as the index for the pivoted DataFrame | None | Array.<string>, Immutable.List, string, number
columns | Name(s) of column(s) to use as the columns for the pivoted DataFrame | None | Array.<string>, Immutable.List, string, number
values | Name(s) of column(s) to use as the values for the pivoted DataFrame | None | Array.<string>, Immutable.List, string, number
aggfunc | Name of aggregation function | sum | string

## `DataFrame.rename`

Rename the `DataFrame` and return a new DataFrame

pandas equivalent: [DataFrame.rename](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.rename.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
columns |  | None | Immutable.Map

### Returns DataFrame

## `DataFrame.reset_index`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}], {index: [1, 2]});

// returns DataFrame([{index: 1, x: 1, y: 2}, {index: 2, x: 2, y: 3}], {index: [0, 1]})
df.reset_index();

// returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}], {index: [0, 1]});
df.reset_index({drop: true});

const df2 = new DataFrame([{index: 1}, {index: 2}], {index: [1, 2]});
// returns DataFrame([{level_0: 1, index: 1}, {level_0: 1, index: 2}], {index: [1, 2]});
df2.reset_index();
```

Reset the index for a DataFrame

pandas equivalent: [DataFrame.reset_index](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.reset_index.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
args |  | None | object
args.drop | Drop the index when resetting? Otherwise, add as new column | None | boolean

### Returns DataFrame

## `DataFrame.set`

```javascript
const df = new DataFrame([{x: 1}, {x: 2}, {x: 3}]);

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);
df.set('y', new Series([2, 3, 4]));
```

Set a `Series` at `column`

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
column |  | None | string, number
series |  | None | Series, List, Array

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

## `DataFrame.tail`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}, {x: 4, y: 5}]);

// returns DataFrame([{x: 3, y: 4}, {x: 4, y: 5}])
df.tail(2);
```

Return new DataFrame composed of last n rows of this DataFrame

pandas equivalent: [DataFrame.tail](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.tail.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
n | Integer number of n rows to return from the DataFrame | 10 | number

### Returns DataFrame

## `DataFrame.to_csv`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns x,y,\r\n1,2,\r\n2,3\r\n3,4\r\n
df.to_csv();
```

Convert the `DataFrame` to a csv string

pandas equivalent: [DataFrame.to_csv](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.to_csv.html)

## `DataFrame.to_excel`

Write the `DataFrame` to a Workbook object

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
excel_writer | File path or existing Workbook object | None | string, Workbook
sheetName | Name of values which will contain DataFrame | Sheet1 | string
download | Download the excel file? | False | boolean
kwargs |  | None | Object
kwargs.index |  | True | boolean

### Returns Workbook

## `DataFrame.to_json`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]);

// Returns {x: {0: 1, 1: 2, 2: 3}, y: {0: 1, 1: 2, 2: 3}}
df.to_json();

// Returns [{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}]
df.to_json({orient: 'records'});

// Returns {0: {x: 1, y: 2}, 1: {x: 2, y: 3}, 2: {x: 3, y: 4}}
df.to_json({orient: 'index'});

// Returns {index: [0, 1, 2], columns: ['x', 'y'], values: [[1, 2], [2, 3], [3, 4]]}
df.to_json({orient: 'split'});

// Returns [[1, 2], [2, 3], [3, 4]]
df.to_json({orient: 'values'});
```

Convert the DataFrame to a json object

pandas equivalent: [DataFrame.to_json](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.to_json.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
kwargs |  | None | None
kwargs.orient | orientation of JSON | columns | string

### Returns *

## `DataFrame.transpose`

```javascript
const df1 = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 3, y: 4}], {index: [1, 2, 3]});

// Returns DataFrame(
  [{1: 1, 2: 2, 3: 3}, {1: 2, 2: 3, 3: 4}], {index: ['x', 'y']});
df1.transpose();
```

Transpose the DataFrame by switching the index and columns

pandas equivalent: [DataFrame.transpose](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.transpose.html)

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

## `DataFrame.where`

```javascript
const df = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}]);

// Returns DataFrame(Map({x: Series([true, false]), y: Series([false, true])})
df.where(new Series([1, 3]), (a, b) => a === b);

// Returns DataFrame(Map({x: Series([true, false]), y: Series([false, true])})
df.where(new DataFrame(Map({
   a: new Series([1, 1]),
   b: new Series([3, 3])})),
   (a, b) => a === b);
```

Return an object of same shape as self and whose corresponding entries are from self
where cond is True and otherwise are from other.

pandas equivalent [DataFrame.where](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.where.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Iterable or value to compare to DataFrame | None | Array, List, Series, DataFrame, number, string
op | Function which takes (a, b) values and returns a boolean | None | function

### Returns DataFrame

