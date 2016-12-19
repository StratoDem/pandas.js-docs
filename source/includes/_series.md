# Series

## New `Series`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'My test name', index: [2, 3, 4, 5]})
ds.toString()
// Returns:
// 2  1
// 3  2
// 4  3
// 5  4
// Name: My test name, dtype: dtype(int)
```

One dimensional array with axis labels. An `Immutable.List` serves as the numpy.ndarray for
values.

Operations between `Series` (+, -, /, *, **) align values based on their associated index
values

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
data | Data to be stored in Series | None | Array, List
kwargs | Extra optional arguments for a Series | None | Object
kwargs.name | The _name to assign to the Series | '' | string
kwargs.index |  | None | Array, List

## `Series.add`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})
ds.add(5)                           // Series([6, 7, 8], {name: 'New Series'})
ds.add(new Series([2, 3, 4]))       // Series([3, 5, 7], {name: 'New Series'})
ds.add([2, 3, 4])                   // Series([3, 5, 7], {name: 'New Series'})
ds.add(Immutable.List([2, 3, 4]))   // Series([3, 5, 7], {name: 'New Series'})
```

Add another Iterable, `Series`, or number to the `Series`

pandas equivalent: [Series.add](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.add.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
val | Value to add to the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.astype`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});

// dtype('float')
ds.dtype;

// Series([1, 2, 3])
ds.astype(new DType('int'))
```

Convert the series to the desired type

pandas equivalent: [Series.astype](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.astype.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
nextType |  | None | DType

## `Series.copy`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test 1'});
const ds2 = ds.copy();
ds2.index = [1, 2, 3];
ds.index   // [0, 1, 2];
ds2.index  // [1, 2, 3];
```

Return a new deep copy of the `Series`

pandas equivalent: [Series.copy](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.copy.html)

## `Series.div`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.div(5)                           // Series([0.2, 0.4, 0.6], {name: 'New Series'})
ds.div(new Series([4, 2, 1]))       // Series([0.25, 1, 3], {name: 'New Series'})
ds.div([4, 2, 1])                   // Series([0.25, 1, 3], {name: 'New Series'})
ds.div(Immutable.List([4, 2, 1]))   // Series([0.25, 1, 3], {name: 'New Series'})
```

Divide by another Iterable, `Series`, or number from the `Series`

pandas equivalent: [Series.div](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.div.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
val | Value by which to divide the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.dtype`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});
ds.dtype;    // dtype('float');
```

Return the dtype of the underlying data

pandas equivalent [Series.dtype](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.dtype.html)

## `Series.iloc`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})
ds.iloc(1)      // 2
ds.iloc(1, 3)   // Series([2, 3], {name: 'New Series', index: [1, 2]})
```

Return the Series between [startVal, endVal), or at startVal if endVal is undefined

pandas equivalent: [Series.iloc](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.iloc.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
startVal |  | None | int
endVal |  | None | int

### Returns Series, number, string

## `Series.index`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});

// Returns List [0, 1, 2]
ds.index;
```

Return the index of the `Series`, an `Immutable.List`

## `Series.index`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});
ds.index = [1, 2, 3];

// Returns List [1, 2, 3]
ds.index;
```

Set the index of the `Series`, an `Immutable.List`

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
index | The next values for the index of the `Series` | None | List, Array

## `Series.length`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});

// Returns 3
ds.length;
```

Return the length of the `Series`

pandas equivalent: len(series);

## `Series.map`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

// Returns Series([1, 4, 9, 16], {name: 'New Series', index: [1, 2]})
ds.map((val, idx) => val ** 2;
```

Return a new `Series` created by a map along a `Series`

pandas equivalent: [Series.map](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.map.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
func | Function to apply along the values | None | function

### Returns Series

## `Series.mean`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

// Returns 2.5
ds.mean();
```

Return the mean of the values in the `Series`

pandas equivalent: [Series.mean](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.mean.html)

## `Series.mul`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.mul(5)                           // Series([5, 10, 15], {name: 'New Series'})
ds.mul(new Series([2, 3, 4]))       // Series([2, 6, 12], {name: 'New Series'})
ds.mul([2, 3, 4])                   // Series([2, 6, 12], {name: 'New Series'})
ds.mul(Immutable.List([2, 3, 4]))   // Series([2, 6, 12], {name: 'New Series'})
```

Multiply by another Iterable, `Series`, or number from the `Series`

pandas equivalent: [Series.mul](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.mul.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
val | Value to multiply by the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.pct_change`

```javascript
const ds = new Series([1, 2, 3, 4, 5], {name: 'New Series'})

ds.pct_change(1)    // Series([null, 1, 0.5, 0.333, 0.25], {name: 'New Series'})
ds.pct_change(2)    // Series([null, null, 2, 1, 0.66666], {name: 'New Series'})
```

Return the percentage change over a given number of periods

pandas equivalent: [Series.pct_change](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.pct_change.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
periods | Number of periods to use for percentage change calculation | 1 | number

### Returns Series

## `Series.sort_values`

```javascript
const ds = new Series([2, 1, 0, 3], {name: 'New Series', index: [0, 1, 2, 3]})

ds.sort_values(true)    // Series([0, 1, 2, 3], {name: 'New Series', index: [2, 1, 0, 3]})
ds.sort_values(false)   // Series([3, 2, 1, 0], {name: 'New Series', index: [3, 0, 1, 2]})
```

Return a sorted `Series` in either ascending or descending order

pandas equivalent: [Series.sort_values](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sort_values.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
ascending | Sort in ascending (true) or descending (false) order | True | boolean

### Returns Series

## `Series.std`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

// Returns 1
ds.std();
```

Return the standard deviation of the values in the `Series`

pandas equivalent: [Series.std](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.std.html)

## `Series.sub`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.sub(5)                           // Series([-4, -3, -2], {name: 'New Series'})
ds.sub(new Series([2, 3, 4]))       // Series([-1, -1, -1], {name: 'New Series'})
ds.sub([2, 3, 4])                   // Series([-1, -1, -1], {name: 'New Series'})
ds.sub(Immutable.List([2, 3, 4]))   // Series([-1, -1, -1], {name: 'New Series'})
```

Subtract another Iterable, `Series`, or number from the `Series`

pandas equivalent: [Series.sub](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sub.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
val | Value to subtract from the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.sum`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

// Returns 10
ds.sum();
```

Return the sum of the values in the `Series`

pandas equivalent: [Series.sum](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sum.html)

## `Series.toString`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'My test name', index: [2, 3, 4, 5]})
ds.toString()
// Returns:
// 2  1
// 3  2
// 4  3
// 5  4
// Name: My test name, dtype: dtype(int)
```

Return the `Series` as a string

## `Series.values`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});

// Returns List [1.5, 2, 3]
ds.values;
```

Return the values of the `Series` as an `Immutable.List`

pandas equivalent: [Series.values](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.values.html);

## `Series.variance`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

// Returns 1
ds.variance();
```

Return the variance of the values in the `Series`

pandas equivalent: [Series.var](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.var.html)

