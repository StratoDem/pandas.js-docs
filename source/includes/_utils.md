# Utilities

## `concat`

```javascript
const series1 = new Series([1, 2, 3, 4]);
const series2 = new Series([2, 3, 4, 5]);

// Returns Series([1, 2, 3, 4, 2, 3, 4, 5], {index: [0, 1, 2, 3, 0, 1, 2, 3]})
concat([series1, series2], {ignore_index: false});

// Returns Series([1, 2, 3, 4, 2, 3, 4, 5], {index: [0, 1, 2, 3, 4, 5, 6, 7]})
concat([series1, series2], {ignore_index: true});
```

```javascript
const df1 = new DataFrame([{x: 1, y: 2}, {x: 2, y: 3}], {index: [1, 2]});
const df2 = new DataFrame([{x: 2, y: 2}, {x: 3, y: 3}], {index: [2, 3]});

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 2, y: 2}, {x: 3, y: 3}], {index: [1, 2, 2, 3]})
concat([df1, df2]);

// Returns DataFrame([{x: 1, y: 2}, {x: 2, y: 3}, {x: 2, y: 2}, {x: 3, y: 3}], {index: [0, 1, 2, 3]})
concat([df1, df2], {ignore_index: true});
```

Concatenate pandas objects along a particular axis.

### Parameters

Name | Description | Default | Type(s)
-----|-------------|---------|--------
objs | Objects to be concatenated | None | Array, Immutable.List
kwargs | Extra optional arguments for concat | None | Object
kwargs.ignore_index | Ignore the indices when concatenating | `false` | boolean
kwargs.axis | Axis along which to concatenate `DataFrame`s | 0 | number
