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

## `Series.abs`

```javascript
const ds = new Series([-1, 2, -4, 5, -1, -2]);

// Returns Series([1, 2, 4, 5, 1, 2]);
ds.abs();
```

Return Series with absolute value of all values

pandas equivalent: [Series.abs](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.abs.html)

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
other | Value to add to the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.append`

```javascript
const ds1 = new Series([1, 2, 3], {index: [1, 2, 3]});
const ds2 = new Series([2, 3, 4], {index: [3, 4, 5]});

// Returns Series([1, 2, 3, 2, 3, 4], {index: [1, 2, 3, 3, 4, 5]});
ds1.append(ds2);

// Returns Series([1, 2, 3, 2, 3, 4], {index: [0, 1, 2, 3, 4, 5]});
ds1.append(ds2, true);
```

Append another Series to this and return a new Series

pandas equivalent: [Series.append](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.append.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other |  | None | Series
ignore_index |  | False | boolean

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

## `Series.corr`

```javascript
const ds1 = new Series([1, 2, 3, 4, 5]);
const ds2 = new Series([2, 4, 6, 8, 10]);

// Returns 1
ds1.corr(ds2);

// Also returns 1
ds2.corr(ds1);
```

Calculate the correlation between this `Series` and another `Series` or iterable

pandas equivalent: [Series.corr](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.corr.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
ds | Series with which to calculate correlation | None | Series

### Returns number

## `Series.cov`

```javascript
const ds1 = new Series([1, 2, 3, 4, 5]);
const ds2 = new Series([2, 4, 6, 8, 10]);

// Returns 5
ds1.cov(ds2);

// Also returns 5
ds2.cov(ds1);
```

Calculate the covariance between this `Series` and another `Series` or iterable

pandas equivalent: [Series.cov](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.cov.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
ds | Series with which to calculate covariance | None | Series

### Returns number

## `Series.cummax`

```javascript
const ds = new Series([3, 2, 4], {index: [2, 3, 4]});

// Returns Series([3, 3, 4], {index: [2, 3, 4]});
ds.cummax();
```

Return cumulative max over requested axis

pandas equivalent: [Series.cummax](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.cummax.html)

## `Series.cummin`

```javascript
const ds = new Series([1, 2, 3], {index: [2, 3, 4]});

// Returns Series([1, 1, 1], {index: [2, 3, 4]});
ds.cummin();
```

Return cumulative min over requested axis

pandas equivalent: [Series.cummin](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.cummin.html)

## `Series.cummul`

```javascript
const ds = new Series([1, 2, 3], {index: [2, 3, 4]});

// Returns Series([1, 2, 6], {index: [2, 3, 4]});
ds.cummul();
```

Return cumulative mul over requested axis

pandas equivalent: [Series.cummul](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.cummul.html)

## `Series.cumsum`

```javascript
const ds = new Series([1, 2, 3], {index: [2, 3, 4]});

// Returns Series([1, 3, 6], {index: [2, 3, 4]});
ds.cumsum();
```

Return cumulative sum over requested axis

pandas equivalent: [Series.cumsum](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.cumsum.html)

## `Series.diff`

```javascript
const ds = new Series([1, 2, 6, 5])

// Returns Series([null, 1, 4, -1])
ds.diff();

// Returns Series([null, null, 5, 3])
ds.diff(2);
```

Return the difference over a given number of periods

pandas equivalent: [Series.diff](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.diff.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
periods | Number of periods to use for difference calculation | 1 | number

### Returns Series

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
other | Value by which to divide the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.divide`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.divide(5)                           // Series([0.2, 0.4, 0.6], {name: 'New Series'})
ds.divide(new Series([4, 2, 1]))       // Series([0.25, 1, 3], {name: 'New Series'})
ds.divide([4, 2, 1])                   // Series([0.25, 1, 3], {name: 'New Series'})
ds.divide(Immutable.List([4, 2, 1]))   // Series([0.25, 1, 3], {name: 'New Series'})
```

Divide by another Iterable, `Series`, or number from the `Series`

pandas equivalent: [Series.divide](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.divide.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Value by which to divide the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.dtype`

```javascript
const ds = new Series([1.5, 2, 3], {name: 'Series name'});
ds.dtype;    // dtype('float');
```

Return the dtype of the underlying data

pandas equivalent [Series.dtype](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.dtype.html)

## `Series.eq`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([true, false, false])
ds.eq(1);

// Returns Series([false, true, true])
ds.eq(new Series([0, 2, 3]));

// Returns Series([false, true, true])
ds.eq(Immutable.List([0, 2, 3]));

// Returns Series([false, true, true])
ds.eq([0, 2, 3]);
```

Equal to of `Series` and other, element wise

pandas equivalent: Series == val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other `Series` or scalar value to check for equality | None | Series, Array, List, number, string

### Returns Series

## `Series.filter`

```javascript
const ds = new Series([1, 2, 3]);

// Returns Series([2, 3]);
ds.filter(ds.gte(2));
```

Filter the Series by an Iterable (Series, Array, or List) of booleans and return the subset

pandas equivalent: series[series condition]

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
iterBool | Iterable of booleans | None | Series, Array, List

### Returns Series

## `Series.gt`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([false, true, true])
ds.gt(1);

// Returns Series([true, false, false])
ds.gt(new Series([0, 2, 3]));

// Returns Series([true, false, false])
ds.gt(Immutable.List([0, 2, 3]));

// Returns Series([true, false, false])
ds.gt([0, 2, 3]);
```

Greater than of `Series` and other, element wise

pandas equivalent: Series > val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other `Series` or scalar value to check for greater than | None | Series, Array, List, number, string

### Returns Series

## `Series.gte`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([true, true, true])
ds.gte(1);

// Returns Series([true, true, false])
ds.gte(new Series([0, 2, 4]));

// Returns Series([true, true, false])
ds.gte(Immutable.List([0, 2, 4]));

// Returns Series([true, true, false])
ds.gte([0, 2, 4]);
```

Greater than or equal to of `Series` and other, element wise

pandas equivalent: Series >= val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other `Series` or scalar value to check for greater than or equal to | None | Series, Array, List, number, string

### Returns Series

## `Series.head`

```javascript
const ds = new Series([1, 2, 3, 4, 5, 6, 7, 8]);

// Returns Series([1, 2, 3, 4, 5])
ds.head();

// Returns Series([1, 2, 3])
ds.head(3);
```

Return first n rows

pandas equivalent: [Series.head](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.head.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
n |  | 5 | number

### Returns Series

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

## `Series.lt`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([false, false, false])
ds.lt(1);

// Returns Series([false, false, true])
ds.lt(new Series([0, 2, 4]));

// Returns Series([false, false, true])
ds.lt(Immutable.List([0, 2, 5]));

// Returns Series([false, false, true])
ds.lt([0, 2, 5]);
```

Less than of `Series` and other, element wise

pandas equivalent: Series < val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other `Series` or scalar value to check for less than | None | Series, Array, List, number, string

### Returns Series

## `Series.lte`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([false, false, false])
ds.lte(1);

// Returns Series([false, false, true])
ds.lte(new Series([0, 2, 4]));

// Returns Series([false, false, true])
ds.lte(Immutable.List([0, 2, 5]));

// Returns Series([false, false, true])
ds.lte([0, 2, 5]);
```

Less than or equal to of `Series` and other, element wise

pandas equivalent: Series <= val

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Other `Series` or scalar value to check for less than or equal to | None | Series, Array, List, number, string

### Returns Series

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

## `Series.median`

```javascript
const ds = new Series([2, 3, 1, 4, 5], {name: 'New Series'})

// Returns 3
ds.median();
```

Return the median of the values in the `Series`

pandas equivalent: [Series.median](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.median.html)

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
other | Value to multiply by the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.multiply`

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.multiply(5)                           // Series([5, 10, 15], {name: 'New Series'})
ds.multiply(new Series([2, 3, 4]))       // Series([2, 6, 12], {name: 'New Series'})
ds.multiply([2, 3, 4])                   // Series([2, 6, 12], {name: 'New Series'})
ds.multiply(Immutable.List([2, 3, 4]))   // Series([2, 6, 12], {name: 'New Series'})
```

Multiply by another Iterable, `Series`, or number from the `Series`

pandas equivalent: [Series.multiply](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.multiply.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Value to multiply by the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.name`

Return the name of the `Series`

## `Series.notnull`

```javascript
const ds = new Series([1, 2, null, null, 4]);

// Returns Series([true, true, false, false, true])
ds.notnull();
```

Returns a boolean same-sized Series indicating if the values are not null

pandas equivalent: [Series.notnull](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.notnull.html)

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

## `Series.rename`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'});
ds.rename('New test name');
// returns 'New test name'
ds.name;
```

Rename the `Series` and return a new `Series`

pandas equivalent: [Series.rename](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.rename.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
name |  | None | string

## `Series.round`

```javascript
const ds = new Series([1.25, 1.47, 1.321])

// Returns Series([1.3, 1.5, 1.3])
ds.round(1);
```

Return a `Series` with all values rounded to the nearest precision specified by decimals

pandas equivalent: [Series.round](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.round.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
decimals | Number of decimals to round to | 0 | number

## `Series.shift`

```javascript
const ds = new Series([1, 2, 3, 4]);

// Returns Series([null, 1, 2, 3]);
ds.shift(1);

// Returns Series([null, null, 1, 2]);
ds.shift(2);

// Returns Series([3, 4, null, null]);
ds.shift(-2);
```

Shift index by desired number of periods

pandas equivalent:s [Series.shift](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.shift.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
periods | Number of periods to move, can be positive or negative | 1 | number

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
other | Value to subtract from the `Series` | None | Iterable, Series, number

### Returns Series

## `Series.sum`

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

// Returns 10
ds.sum();
```

Return the sum of the values in the `Series`

pandas equivalent: [Series.sum](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sum.html)

## `Series.tail`

```javascript
const ds = new Series([1, 2, 3, 4, 5, 6, 7, 8]);

// Returns Series([4, 5, 6, 7, 8])
ds.tail();

// Returns Series([6, 7, 8])
ds.tail(3);
```

Return last n rows

pandas equivalent: [Series.tail](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.tail.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
n |  | 5 | number

### Returns Series

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

## `Series.to_json`

```javascript
const ds = new Series([1, 2, 3], {name: 'x'});

// Returns {0: 1, 1: 2, 2: 3}
ds.to_json();

// Returns [1, 2, 3]
ds.to_json({orient: 'records'});

// Returns {index: [0, 1, 2], name: 'x', values: [1, 2, 3]}
ds.to_json({orient: 'split'});
```

Convert the Series to a json object

pandas equivalent: [Series.to_json](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.to_json.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
kwargs |  | None | None
kwargs.orient | orientation of JSON | columns | string

### Returns *

## `Series.unique`

```javascript
const ds = new Series(['foo', 'bar', 'bar', 'foo', 'foo', 'test', 'bar', 'hi']);
// Returns ['foo', 'bar', 'test', 'hi']
ds.unique();
```

Returns `Immutable.List` of unique values in the `Series`. Preserves order of the original

pandas equivalent: [Series.unique](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.unique.html)

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

## `Series.where`

```javascript
const ds = new Series([1, 2, 3], {name: 'Test name'})

// Returns Series([true, false, false])
ds.where(1, (v1, v2) => v1 === 1);

// Returns Series([false, true, true])
ds.where(new Series([0, 2, 3]), (v1, v2) => v1 === v2);
```

Flexible comparison of an iterable or value to the `Series`. Returns a `Series` of booleans of
equivalent length

pandas equivalent: [Series.where](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.where.html)

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
other | Iterable or value compared to Series | None | Series, Array, List, string, number
op | Function which takes (a, b) values and returns a boolean | None | function

### Returns Series

