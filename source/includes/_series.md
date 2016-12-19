# Series

#### Series parameters

Parameter | Description | Default
----------|-------------|---------
data | Iterable of values to store in the Series |
kwargs | Extra arguments for indexing and naming the Series | {name: ""}
kwargs.name | Name of the series | ""
kwargs.index | Indexing to use for series | range(0, data.length)

## Utilities

### `Series.iloc(startVal, endVal)`

Return the `Series` between `[startVal, endVal)`, or at `startVal` if `endVal` is undefined.

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.iloc.html)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.iloc(1)      // 2
ds.iloc(1, 3)   // Series([2, 3], {name: 'New Series', index: [1, 2]})
```

### `Series.map(func)`

Return a new `Series` created by a map along a `Series`

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.map.html)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.map((val, idx) => val ** 2)  // Series([1, 4, 9, 16], {name: 'New Series', index: [1, 2]})
```

### `Series.length`

Return the length of the `Series`

pandas equivalent: len(Series)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.length   // 4
```

### `Series.values`

Return the values of the `Series` as an
[`Immutable.List`](https://facebook.github.io/immutable-js/docs/#/List)

pandas equivalent: len(Series)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.values   // List [1, 2, 3 ,4]
```

## Mathematical/Statistical methods

### `Series.sum()`

Return the sum of all values in the `Series`

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sum.html)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.sum()    // 10
```

### `Series.mean()`

Return the mean of all values in the `Series`

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.mean.html)

```javascript
const ds = new Series([1, 2, 3, 4], {name: 'New Series'})

ds.mean()    // 2.5
```

### `Series.std()`

Return the standard deviation of all values in the `Series`

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.std.html)

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.std()    // 1
```

### `Series.variance()`

Return the variance of all values in the `Series`

[pandas equivalent](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.var.html)

```javascript
const ds = new Series([1, 2, 3], {name: 'New Series'})

ds.variance()    // 1
```