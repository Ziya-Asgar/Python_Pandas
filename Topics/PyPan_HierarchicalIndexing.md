# Hierarchical Indexing

- [Hierarchical Indexing](#hierarchical-indexing)
  - [Create a series with hierarchical indexing](#create-a-series-with-hierarchical-indexing)
  - [Selecting subsets of data in series using partial indexing](#selecting-subsets-of-data-in-series-using-partial-indexing)
  - [Turning hierarchically indexed series into a dataframe](#turning-hierarchically-indexed-series-into-a-dataframe)
  - [Dataframe with Hierarchical index and columns](#dataframe-with-hierarchical-index-and-columns)
  - [Checking the number of index levels](#checking-the-number-of-index-levels)
  - [Selecting subsets of data in a dataframe using partial indexing](#selecting-subsets-of-data-in-a-dataframe-using-partial-indexing)
  - [Creating standalone `MultiIndex`](#creating-standalone-multiindex)
  - [Reordering and sorting levels of hierarchical index](#reordering-and-sorting-levels-of-hierarchical-index)
  - [Indexing with a DataFrame's columns](#indexing-with-a-dataframes-columns)

---

---

Hierarchical indexing is an important feature of pandas that enables you to have multiple (two or more) index levels on an axis. Another way of thinking about it is that it provides a way for you to work with higher dimensional data in a lower dimensional form.

---

## Create a series with hierarchical indexing

Here is an example of creating a series with hierarchical indexing. The created index in this example is called `MultiIndex`.

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)
print(ser)
"""
a  1    0.452329
   2    0.102518
   3    0.737254
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
d  2    0.502630
   3    0.207505
dtype: float64
"""

print(ser.index)
"""
MultiIndex([('a', 1),
            ('a', 2),
            ('a', 3),
            ('b', 1),
            ('b', 3),
            ('c', 1),
            ('c', 2),
            ('d', 2),
            ('d', 3)],
           )
"""
```

---

## Selecting subsets of data in series using partial indexing

We can select the subset of the hierarchical indexed data using the partial indexing:

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)

print(ser["b"])
"""
1    0.329789
3    0.684907
dtype: float64
"""

print(ser["b":"c"])
"""
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
dtype: float64
"""

print(ser.loc[["b", "d"]])
"""
b  1    0.329789
   3    0.684907
d  2    0.502630
   3    0.207505
dtype: float64
"""

print(ser.loc[:, 2])
"""
a    0.102518
c    0.679707
d    0.502630
dtype: float64
"""
```

---

## Turning hierarchically indexed series into a dataframe

Hierarchical indexing plays an important role in reshaping data and forming a pivot table. For example, you can rearrange the hierarchically indexed series into a dataframe using its `unstack` method. The inverse operation of `unstack` is `stack`:

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)

print(ser.unstack())
"""
          1         2         3
a  0.452329  0.102518  0.737254
b  0.329789       NaN  0.684907
c  0.601178  0.679707       NaN
d       NaN  0.502630  0.207505
"""

print(ser.unstack().stack())
"""
a  1    0.452329
   2    0.102518
   3    0.737254
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
d  2    0.502630
   3    0.207505
dtype: float64
"""
```

---

## Dataframe with Hierarchical index and columns

With a DataFrame, either axis can have a hierarchical index:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
print(df)
"""
      column1             column2
    column1.1 column1.2 column2.1
a 1         0         1         2
  2         3         4         5
b 1         6         7         8
  2         9        10        11
"""
```

We can set the names for hierarchical levels using the `names` attribute. The `names` supersede the `name` attribute, which is used only with single-level indexes.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]
print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""
```

---

## Checking the number of index levels

You can see how many levels an index has by accessing its `nlevels` attribute:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

print(df.index.nlevels) # 2
print(df.columns.nlevels) # 2
```

---

## Selecting subsets of data in a dataframe using partial indexing

With partial column indexing you can similarly select groups of columns in a dataframe:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

print(df["column1"])
"""
     column1.1  column1.2
a 1          0          1
  2          3          4
b 1          6          7
  2          9         10
"""
```

---

## Creating standalone `MultiIndex`

A `MultiIndex` can be created by itself and then reused; the columns in the preceding DataFrame with level names could also be created like this:

```py
import pandas as pd

pd.MultiIndex.from_arrays([
  ["column1", "column1", "column2"],
  ["column1.1", "column1.2", "column2.1"]
], names=["columnKey1", "columnKey2"])

"""
MultiIndex([('column1', 'column1.1'),
            ('column1', 'column1.2'),
            ('column2', 'column2.1')],
           names=['columnKey1', 'columnKey2'])
"""
```

---

## Reordering and sorting levels of hierarchical index

At times you may need to rearrange the order of the levels on an axis or sort the data by the values in one specific level. The `swaplevel` method takes two level numbers or names and returns a new object with the levels interchanged (but the data is otherwise unaltered):

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.swaplevel("key1", "key2"))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key2 key1
1    a             0         1         2
2    a             3         4         5
1    b             6         7         8
2    b             9        10        11
"""
```

Instead of using index level names, we can also use index level numbers with `swaplevel`:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.swaplevel(0, 1))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key2 key1
1    a             0         1         2
2    a             3         4         5
1    b             6         7         8
2    b             9        10        11
"""
```

`sort_index` by default sorts the data lexicographically using all the index levels, but you can choose to use only a single level or a subset of levels to sort by passing the `level` argument.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.sort_index(level=1))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
b    1             6         7         8
a    2             3         4         5
b    2             9        10        11
"""
```

---

## Indexing with a DataFrame's columns

It’s not unusual to want to use one or more columns from a DataFrame as the row index; alternatively, you may wish to move the row index into the DataFrame’s columns. We can do both of this. DataFrame’s `set_index` function will create a new DataFrame using one or more of its columns as the index:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

df2 = df.set_index(["c", "d"])
print(df2)
"""
       a  b
c   d
one 0  0  7
    1  1  6
    2  2  5
two 0  3  4
    1  4  3
    2  5  2
    3  6  1
"""
```

By default, the columns are removed from the DataFrame, though you can leave them in by passing `drop=False` to `set_index`:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

print(df.set_index(["c", "d"], drop=False))
"""
       a  b    c  d
c   d
one 0  0  7  one  0
    1  1  6  one  1
    2  2  5  one  2
two 0  3  4  two  0
    1  4  3  two  1
    2  5  2  two  2
    3  6  1  two  3
"""
```

`reset_index`, on the other hand, does the opposite of `set_index`; the hierarchical index levels are moved into the columns:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

df2 = df.set_index(["c", "d"])
print(df2)
"""
       a  b
c   d
one 0  0  7
    1  1  6
    2  2  5
two 0  3  4
    1  4  3
    2  5  2
    3  6  1
"""

print(df2.reset_index())
"""
     c  d  a  b
0  one  0  0  7
1  one  1  1  6
2  one  2  2  5
3  two  0  3  4
4  two  1  4  3
5  two  2  5  2
6  two  3  6  1
"""
```

---

---
