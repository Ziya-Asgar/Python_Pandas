# Combining and Merging

- [Combining and Merging](#combining-and-merging)
  - [Table for an argument reference on `pandas.merge`](#table-for-an-argument-reference-on-pandasmerge)
  - [Database-Style DataFrame Joins](#database-style-dataframe-joins)
  - [Merging on Index](#merging-on-index)
  - [Concatenating along an axis](#concatenating-along-an-axis)
  - [Combining Data with Overlap](#combining-data-with-overlap)

---

---

## Table for an argument reference on `pandas.merge`

`pandas.merge` function arguments

| Argument      | Description                                                                                                                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `left`        | DataFrame to be merged on the left side.                                                                                                                                                               |
| `right`       | DataFrame to be merged on the right side.                                                                                                                                                              |
| `how`         | Type of join to apply: one of `"inner"`, `"outer"`, `"left"`, or `"right"`; defaults to `"inner"`.                                                                                                     |
| `on`          | Column names to join on. Must be found in both DataFrame objects. If not specified and no other join keys given, will use the intersection of the column names in `left` and `right` as the join keys. |
| `left_on`     | Columns in `left` DataFrame to use as join keys. Can be a single column name or a list of column names.                                                                                                |
| `right_on`    | Analogous to `left_on` for `right` DataFrame.                                                                                                                                                          |
| `left_index`  | Use row index in `left` as its join key (or keys, if a `MultiIndex`).                                                                                                                                  |
| `right_index` | Analogous to `left_index`.                                                                                                                                                                             |
| `sort`        | Sort merged data lexicographically by join keys; `False` by default.                                                                                                                                   |
| `suffixes`    | Tuple of string values to append to column names in case of overlap; defaults to `("_x", "_y")` (e.g., if `"data"` in both DataFrame objects, would appear as `"data_x"` and `"data_y"` in result).    |
| `copy`        | If `False`, avoid copying data into resulting data structure in some exceptional cases; by default always copies.                                                                                      |
| `validate`    | Verifies if the merge is of the specified type, whether one-to-one, one-to-many, or many-to-many. See the docstring for full details on the options.                                                   |
| `indicator`   | Adds a special column `_merge` that indicates the source of each row; values will be `"left_only"`, `"right_only"`, or `"both"` based on the origin of the joined data in each row.                    |

---

---

## Database-Style DataFrame Joins

Merge or join operations combine datasets by linking rows using one or more keys. To do this with pandas, we can use the `merge` method:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   a      5
6   b      6
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   d      2
"""

print(pd.merge(df1, df2))
"""
  key  data1  data2
0   b      0      1
1   b      1      1
2   a      2      0
3   a      4      0
4   a      5      0
5   b      6      1
"""
```

Note that I didn’t specify which column to join on. If that information is not specified, `pandas.merge` uses the overlapping column names as the keys. It’s a good practice to specify explicitly, though:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   a      5
6   b      6
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   d      2
"""

print(pd.merge(df1, df2, on="key"))
"""
  key  data1  data2
0   b      0      1
1   b      1      1
2   a      2      0
3   a      4      0
4   a      5      0
5   b      6      1
"""
```

If the column names are different in each object, you can specify them separately:

```py
import pandas as pd

df3 = pd.DataFrame({
  "lkey": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df4 = pd.DataFrame({
  "rkey": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df3)
"""
  lkey  data1
0    b      0
1    b      1
2    a      2
3    c      3
4    a      4
5    a      5
6    b      6
"""

print(df4)
"""
  rkey  data2
0    a      0
1    b      1
2    d      2
"""

print(pd.merge(df3, df4, left_on="lkey", right_on="rkey"))
"""
  lkey  data1 rkey  data2
0    b      0    b      1
1    b      1    b      1
2    a      2    a      0
3    a      4    a      0
4    a      5    a      0
5    b      6    b      1
"""
```

You may notice that `"c"` and `"d"` values and associated data are missing from the result. By default, `pandas.merge` does an `"inner"` join; the keys in the result are the intersection, or the common set found in both tables. Other possible options are `"left"`, `"right"`, and `"outer"`.

Different join types with the `how` argument:

| Option        | Behavior                                                  |
| ------------- | --------------------------------------------------------- |
| `how="inner"` | Use only the key combinations observed in both tables     |
| `how="left"`  | Use all key combinations found in the left table          |
| `how="right"` | Use all key combinations found in the right table         |
| `how="outer"` | Use all key combinations observed in both tables together |

The outer join takes the union of the keys, combining the effect of applying both left and right joins:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

df3 = pd.DataFrame({
  "lkey": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df4 = pd.DataFrame({
  "rkey": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(pd.merge(df1, df2, how="outer"))
"""
  key  data1  data2
0   a      2      0
1   a      4      0
2   a      5      0
3   b      0      1
4   b      1      1
5   b      6      1
6   c      3   <NA>
7   d   <NA>      2
"""

print(pd.merge(df3, df4, left_on="lkey", right_on="rkey", how="outer"))
"""
  lkey  data1 rkey  data2
0    a      2    a      0
1    a      4    a      0
2    a      5    a      0
3    b      0    b      1
4    b      1    b      1
5    b      6    b      1
6    c      3  NaN   <NA>
7  NaN   <NA>    d      2
"""
```

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "b"],
  "data1": pd.Series(range(6), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "a", "b", "d"],
  "data2": pd.Series(range(5), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   b      5
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   a      2
3   b      3
4   d      4
"""

print(pd.merge(df1, df2, on="key", how="left"))
"""
   key  data1  data2
0    b      0      1
1    b      0      3
2    b      1      1
3    b      1      3
4    a      2      0
5    a      2      2
6    c      3   <NA>
7    a      4      0
8    a      4      2
9    b      5      1
10   b      5      3
"""
```

To merge with multiple keys, pass a list of column names:

```py
import pandas as pd

left = pd.DataFrame({
  "key1": ["foo", "foo", "bar"],
  "key2": ["one", "two", "one"],
  "lval": pd.Series([1, 2, 3], dtype='Int64')
})

right = pd.DataFrame({
  "key1": ["foo", "foo", "bar", "bar"],
  "key2": ["one", "one", "one", "two"],
  "rval": pd.Series([4, 5, 6, 7], dtype='Int64')
})

print(left)
"""
  key1 key2  lval
0  foo  one     1
1  foo  two     2
2  bar  one     3
"""

print(right)
"""
  key1 key2  rval
0  foo  one     4
1  foo  one     5
2  bar  one     6
3  bar  two     7
"""

print(pd.merge(left, right, on=["key1", "key2"], how="outer"))
"""
  key1 key2  lval  rval
0  bar  one     3     6
1  bar  two  <NA>     7
2  foo  one     1     4
3  foo  one     1     5
4  foo  two     2  <NA>
"""
```

> When you're joining columns on columns, the indexes on the passed DataFrame objects are discarded. If you need to preserve the index values, you can use `reset_index` to append the index to the columns.

A last issue to consider in merge operations is the treatment of overlapping column names. `pandas.merge` has a `suffixes` parameter for specifying strings to append to overlapping names in the left and right DataFrame objects:

```py
import pandas as pd

left = pd.DataFrame({
  "key1": ["foo", "foo", "bar"],
  "key2": ["one", "two", "one"],
  "lval": pd.Series([1, 2, 3], dtype='Int64')
})

right = pd.DataFrame({
  "key1": ["foo", "foo", "bar", "bar"],
  "key2": ["one", "one", "one", "two"],
  "rval": pd.Series([4, 5, 6, 7], dtype='Int64')
})

# without suffixes
print(pd.merge(left, right, on="key1"))
"""
  key1 key2_x  lval key2_y  rval
0  foo    one     1    one     4
1  foo    one     1    one     5
2  foo    two     2    one     4
3  foo    two     2    one     5
4  bar    one     3    one     6
5  bar    one     3    two     7
"""

# with suffixes
print(pd.merge(left, right, on="key1", suffixes=("_left", "_right")))
"""
  key1 key2_left  lval key2_right  rval
0  foo       one     1        one     4
1  foo       one     1        one     5
2  foo       two     2        one     4
3  foo       two     2        one     5
4  bar       one     3        one     6
5  bar       one     3        two     7
"""
```

---

---

## Merging on Index

In some cases, the merge key(s) in a DataFrame will be found in its index (row labels). In this case, you can pass `left_index=True` or `right_index=True` (or both) to indicate that the index should be used as the merge key:

```py
import pandas as pd

left1 = pd.DataFrame({
  "key": ["a", "b", "a", "a", "b", "c"],
  "value": pd.Series(range(6), dtype="Int64")
})

right1 = pd.DataFrame(
  {"group_val": [3.5, 7]},
  index=["a", "b"]
)

print(left1)
"""
  key  value
0   a      0
1   b      1
2   a      2
3   a      3
4   b      4
5   c      5
"""

print(right1)
"""
   group_val
a        3.5
b        7.0
"""

print(pd.merge(left1, right1, left_on="key", right_index=True))
"""
  key  value  group_val
0   a      0        3.5
1   b      1        7.0
2   a      2        3.5
3   a      3        3.5
4   b      4        7.0
"""
```

Using the indexes of both sides of the merge is also possible:

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(pd.merge(left2, right2, how="outer", left_index=True, right_index=True))
"""
   Ohio  Nevada  Missouri  Alabama
a     1       2      <NA>     <NA>
b  <NA>    <NA>         7        8
c     3       4         9       10
d  <NA>    <NA>        11       12
e     5       6        13       14
"""
```

With hierarchically indexed data, things are more complicated, as joining on index is equivalent to a multiple-key merge. In this case, you have to indicate multiple columns to merge on as a list

```py
import pandas as pd

lefth = pd.DataFrame({
  "key1": ["Ohio", "Ohio", "Ohio", "Nevada", "Nevada"],
  "key2": [2000, 2001, 2002, 2001, 2002],
  "data": pd.Series(range(5), dtype="Int64")
})

righth_index = pd.MultiIndex.from_arrays(
  [
    ["Nevada", "Nevada", "Ohio", "Ohio", "Ohio", "Ohio"],
    [2001, 2000, 2000, 2000, 2001, 2002]
  ]
)

righth = pd.DataFrame({
  "event1": pd.Series([0, 2, 4, 6, 8, 10], dtype="Int64", index=righth_index),
  "event2": pd.Series([1, 3, 5, 7, 9, 11], dtype="Int64", index=righth_index)
})

print(lefth)
"""
     key1  key2  data
0    Ohio  2000     0
1    Ohio  2001     1
2    Ohio  2002     2
3  Nevada  2001     3
4  Nevada  2002     4
"""

print(righth)
"""
             event1  event2
Nevada 2001       0       1
       2000       2       3
Ohio   2000       4       5
       2000       6       7
       2001       8       9
       2002      10      11
"""

print(pd.merge(lefth, righth, left_on=["key1", "key2"], right_index=True))
"""
     key1  key2  data  event1  event2
0    Ohio  2000     0       4       5
0    Ohio  2000     0       6       7
1    Ohio  2001     1       8       9
2    Ohio  2002     2      10      11
3  Nevada  2001     3       0       1
"""

print(pd.merge(lefth, righth, left_on=["key1", "key2"], right_index=True, how="outer"))
"""
     key1  key2  data  event1  event2
4  Nevada  2000  <NA>       2       3
3  Nevada  2001     3       0       1
4  Nevada  2002     4    <NA>    <NA>
0    Ohio  2000     0       4       5
0    Ohio  2000     0       6       7
1    Ohio  2001     1       8       9
2    Ohio  2002     2      10      11
"""
```

DataFrame has a `join` instance method to simplify merging by index. It can also be used to combine many DataFrame objects having the same or similar indexes but nonoverlapping columns.

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(left2.join(right2, how="outer"))
"""
   Ohio  Nevada  Missouri  Alabama
a     1       2      <NA>     <NA>
b  <NA>    <NA>         7        8
c     3       4         9       10
d  <NA>    <NA>        11       12
e     5       6        13       14
"""
```

DataFrame’s `join` method performs a left join on the join keys by default. It also supports joining the index of the passed DataFrame on one of the columns of the calling DataFrame:

```py
import pandas as pd

left1 = pd.DataFrame({
  "key": ["a", "b", "a", "a", "b", "c"],
  "value": pd.Series(range(6), dtype="Int64")
})

right1 = pd.DataFrame(
  {"group_val": [3.5, 7]},
  index=["a", "b"]
)

print(left1)
"""
  key  value
0   a      0
1   b      1
2   a      2
3   a      3
4   b      4
5   c      5
"""

print(right1)
"""
   group_val
a        3.5
b        7.0
"""

print(left1.join(right1, on="key"))
"""
  key  value  group_val
0   a      0        3.5
1   b      1        7.0
2   a      2        3.5
3   a      3        3.5
4   b      4        7.0
5   c      5        NaN
"""
```

For simple index-on-index merges, you can pass a list of DataFrames to `join`:

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

another = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [16., 17.]],
  index=["a", "c", "e", "f"],
  columns=["New York", "Oregon"]
)

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(another)
"""
   New York  Oregon
a       7.0     8.0
c       9.0    10.0
e      11.0    12.0
f      16.0    17.0
"""

print(left2.join([right2, another]))
"""
   Ohio  Nevada  Missouri  Alabama  New York  Oregon
a     1       2      <NA>     <NA>       7.0     8.0
c     3       4         9       10       9.0    10.0
e     5       6        13       14      11.0    12.0
"""

print(left2.join([right2, another], how="outer"))
"""
   Ohio  Nevada  Missouri  Alabama  New York  Oregon
a     1       2      <NA>     <NA>       7.0     8.0
c     3       4         9       10       9.0    10.0
e     5       6        13       14      11.0    12.0
b  <NA>    <NA>         7        8       NaN     NaN
d  <NA>    <NA>        11       12       NaN     NaN
f  <NA>    <NA>      <NA>     <NA>      16.0    17.0
"""
```

---

---

## Concatenating along an axis

Here is a table of `concat` function arguments:

| Argument           | Description                                                                                                                                                                                                                                       |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `objs`             | List or dictionary of pandas objects to be concatenated; this is the only required argument                                                                                                                                                       |
| `axis`             | Axis to concatenate along; defaults to concatenating along rows (`axis="index"`)                                                                                                                                                                  |
| `join`             | Either `"inner"` or `"outer"` (`"outer"` by default); whether to intersect (inner) or union (outer) indexes along the other axes                                                                                                                  |
| `keys`             | Values to associate with objects being concatenated, forming a hierarchical index along the concatenation axis; can be a list or array of arbitrary values, an array of tuples, or a list of arrays (if multiple-level arrays passed in `levels`) |
| `levels`           | Specific indexes to use as hierarchical index level or levels if keys passed                                                                                                                                                                      |
| `names`            | Names for created hierarchical levels if `keys` and/or `levels` passed                                                                                                                                                                            |
| `verify_integrity` | Check new axis in concatenated object for duplicates and raise an exception if so; by default (`False`) allows duplicates                                                                                                                         |
| `ignore_index`     | Do not preserve indexes along concatenation axis, instead produce a new `range(total_length)` index                                                                                                                                               |

To append a single value, a list of values, or another series object to a given series, we need to use the `concat` method:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a single value
ser = pd.concat([ser, pd.Series([5])])

# append a list of values
ser = pd.concat([ser, pd.Series([6, 7, 8])])
print(ser)
"""
0    1
1    2
2    3
3    4
0    5
0    6
1    7
2    8
dtype: int64
"""
```

By default, `concat` works along `axis="index"`, producing another Series. If you pass `axis="columns"`, the result will instead be a DataFrame:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a single value
ser = pd.concat([ser, pd.Series([5])])

# append a list of values
ser = pd.concat([ser, pd.Series([6, 7, 8])], axis="columns")
print(ser)
"""
   0    1
0  1  6.0
1  2  7.0
2  3  8.0
3  4  NaN
0  5  6.0
"""
```

By default, the way the `concat` concatenates the series along indices is the `outer` join. We can also concatenate using the `join="inner"`:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a list of values
print(pd.concat([ser, pd.Series([6, 7, 8])], axis="columns"))
"""
   0    1
0  1  6.0
1  2  7.0
2  3  8.0
3  4  NaN
"""

print(pd.concat([ser, pd.Series([6, 7, 8])], axis="columns", join="inner"))
"""

   0  1
0  1  6
1  2  7
2  3  8
"""
```

Suppose you wanted to create a hierarchical index on the concatenation axis. To do this, use the `keys` argument:

```py
import pandas as pd

ser1 = pd.Series([1, 2, 3, 4])
ser2 = pd.Series([6, 7, 8])

# append a list of values
print(pd.concat([ser1, ser2], keys=["one", "two"]))
"""
one  0    1
     1    2
     2    3
     3    4
two  0    6
     1    7
     2    8
dtype: int64
"""

print(pd.concat([ser1, ser2], keys=["one", "two"]).unstack())
"""
       0    1    2    3
one  1.0  2.0  3.0  4.0
two  6.0  7.0  8.0  NaN
"""
```

In the case of combining Series along `axis="columns"`, the `keys` become the DataFrame column headers:

```py
import pandas as pd

ser1 = pd.Series([1, 2, 3, 4])
ser2 = pd.Series([6, 7, 8])

# append a list of values
print(pd.concat([ser1, ser2], keys=["one", "two"], axis="columns"))
"""
   one  two
0    1  6.0
1    2  7.0
2    3  8.0
3    4  NaN
"""
```

In the below example, the `keys` argument is used to create a hierarchical index where the first level can be used to identify each of the concatenated DataFrame objects.

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat([df1, df2], axis="columns", keys=["level1-df1", "level1-df2"]))
"""
  level1-df1     level1-df2
         one two      three four
a          0   1        5.0  6.0
b          2   3        NaN  NaN
c          4   5        7.0  8.0
"""
```

If you pass a dictionary of objects instead of a list, the dictionary’s keys will be used for the `keys` option:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat({"level1-df1": df1, "level1-df2":df2}, axis="columns"))
"""
  level1-df1     level1-df2
         one two      three four
a          0   1        5.0  6.0
b          2   3        NaN  NaN
c          4   5        7.0  8.0
"""
```

There are additional arguments governing how the hierarchical index is created. For example, we can name the created axis levels with the `names` argument:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat([df1, df2], axis="columns", keys=["level1-df1", "level1-df2"], names=["upper", "lower"]))
"""
upper level1-df1     level1-df2
lower        one two      three four
a              0   1        5.0  6.0
b              2   3        NaN  NaN
c              4   5        7.0  8.0
"""
```

A last consideration concerns DataFrames in which the row index does not contain any relevant data. To recreate an index from scratch after the concatenation, we can use the `ignore_index=True` option:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.random.standard_normal((3, 4)),
  columns=["a", "b", "c", "d"]
)

df2 = pd.DataFrame(
  np.random.standard_normal((2, 3)),
  columns=["b", "d", "a"]
)

print(df1)
"""
          a         b         c         d
0 -0.482666  0.520581 -0.339681  1.190217
1  0.670140  1.482087 -0.182321  0.406985
2 -1.509289 -0.480640 -1.029361  1.272381
"""

print(df2)
"""
          b         d         a
0  0.176479 -0.140522  0.958965
1 -0.105916  0.653925  0.647811
"""

print(pd.concat([df1, df2], ignore_index=True))
"""
          a         b         c         d
0 -0.482666  0.520581 -0.339681  1.190217
1  0.670140  1.482087 -0.182321  0.406985
2 -1.509289 -0.480640 -1.029361  1.272381
3  0.958965  0.176479       NaN -0.140522
4  0.647811 -0.105916       NaN  0.653925
"""
```

---

---

## Combining Data with Overlap

If you want to join series with overlap, you can use the series `combine_first` method. This method keeps the data from the first series, if the data is available, and takes the data from the other series if the data from the first series is not available:

```py
import pandas as pd

a = pd.Series(
  [np.nan, 2.5, 0.0, 3.5, 4.5, np.nan],
  index=["f", "e", "d", "c", "b", "a"]
)

b = pd.Series(
  [0., np.nan, 2., np.nan, np.nan, 5.],
  index=["a", "b", "c", "d", "e", "f"]
)

print(a.sort_index())
"""
a    NaN
b    4.5
c    3.5
d    0.0
e    2.5
f    NaN
dtype: float64
"""

print(b)
"""
a    0.0
b    NaN
c    2.0
d    NaN
e    NaN
f    5.0
dtype: float64
"""

print(a.combine_first(b))
"""
a    0.0
b    4.5
c    3.5
d    0.0
e    2.5
f    5.0
dtype: float64
"""
```

With DataFrames, `combine_first` does the same thing column by column, so you can think of it as “patching” missing data in the calling object with data from the object you pass:

```py
import pandas as pd

df1 = pd.DataFrame({
  "a": [1., np.nan, 5., np.nan],
  "b": [np.nan, 2., np.nan, 6.],
  "c": range(2, 18, 4)
})

df2 = pd.DataFrame({
  "a": [5., 4., np.nan, 3., 7.],
  "b": [np.nan, 3., 4., 6., 8.]
})

print(df1)
"""
     a    b   c
0  1.0  NaN   2
1  NaN  2.0   6
2  5.0  NaN  10
3  NaN  6.0  14
"""

print(df2)
"""
     a    b
0  5.0  NaN
1  4.0  3.0
2  NaN  4.0
3  3.0  6.0
4  7.0  8.0
"""

print(df1.combine_first(df2))
"""
     a    b     c
0  1.0  NaN   2.0
1  4.0  2.0   6.0
2  5.0  4.0  10.0
3  3.0  6.0  14.0
4  7.0  8.0   NaN
"""
```

---

---
