# Pandas

- [Pandas](#pandas)
  - [Some Useful Links](#some-useful-links)
  - [Intro](#intro)
  - [Creating Series](#creating-series)
  - [Creating Dataframe](#creating-dataframe)
  - [Accessing Data](#accessing-data)
  - [Accessing Data With Booleans](#accessing-data-with-booleans)
  - [Index Objects](#index-objects)
  - [Modifying Data](#modifying-data)
  - [Converting Series and Dataframes](#converting-series-and-dataframes)
  - [Deleting Data](#deleting-data)
  - [Missing Data](#missing-data)
  - [Duplication in Dataframes](#duplication-in-dataframes)
  - [Sorting and Ranking](#sorting-and-ranking)
  - [Arithmetic Operations](#arithmetic-operations)
  - [Descriptive Statistics](#descriptive-statistics)
  - [Some Functions and Methods](#some-functions-and-methods)
  - [Accessors](#accessors)
  - [Reading from and Writing to Files](#reading-from-and-writing-to-files)
  - [Pandas and Web APIs](#pandas-and-web-apis)
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
  - [Combining and Merging Datasets](#combining-and-merging-datasets)
    - [Table for an argument reference on `pandas.merge`](#table-for-an-argument-reference-on-pandasmerge)
    - [Database-Style DataFrame Joins](#database-style-dataframe-joins)
    - [Merging on Index](#merging-on-index)
    - [Concatenating along an axis](#concatenating-along-an-axis)
    - [Combining Data with Overlap](#combining-data-with-overlap)
  - [Reshaping and Pivoting](#reshaping-and-pivoting)
    - [Reshaping with Hierarchical Indexing](#reshaping-with-hierarchical-indexing)
    - [Pivoting “Long” to “Wide” Format](#pivoting-long-to-wide-format)
    - [Pivoting “Wide” to “Long” Format](#pivoting-wide-to-long-format)
  - [Data Aggregation and Group Operations](#data-aggregation-and-group-operations)
    - [Using `groupby` with a series](#using-groupby-with-a-series)
    - [Using `groupby` with a hierarchically indexed series](#using-groupby-with-a-hierarchically-indexed-series)
    - [Grouping using a dictionary](#grouping-using-a-dictionary)
    - [Grouping using a function](#grouping-using-a-function)
    - [Using `groupby` with a dataframe](#using-groupby-with-a-dataframe)
    - [Using `groupby` with a hierarchically indexed dataframe](#using-groupby-with-a-hierarchically-indexed-dataframe)
    - [Group by columns](#group-by-columns)
    - [Iterating over groups](#iterating-over-groups)
    - [Data Aggregation](#data-aggregation)
      - [Custom function for aggregation](#custom-function-for-aggregation)
      - [`pivot_table`](#pivot_table)
      - [Crosstab](#crosstab)
  - [Time Series](#time-series)
    - [Indexing, Selection, Subsetting](#indexing-selection-subsetting)
    - [Date Ranges, Frequencies, and Shifting](#date-ranges-frequencies-and-shifting)
    - [`date_range`](#date_range)
    - [`day_name`](#day_name)
    - [Time Zone Handling](#time-zone-handling)
    - [Periods and Period Arithmetic](#periods-and-period-arithmetic)
    - [Resampling and Frequency Conversion](#resampling-and-frequency-conversion)
      - [Downsampling](#downsampling)
      - [Upsampling and Interpolation](#upsampling-and-interpolation)
      - [Grouped Time Resampling](#grouped-time-resampling)
  - [Introduction to Modeling Libraries in Python](#introduction-to-modeling-libraries-in-python)

<hr>

## Some Useful Links

- https://wesmckinney.com/book/pandas-basics
- https://github.com/wesm/pydata-book
- https://www.practicaldatascience.org/intro.html
- https://towardsdatascience.com/pandas-dtype-specific-operations-accessors-c749bafb30a4

<hr>
<hr>

## Intro

`pandas` is designed for working with tabular or heterogeneous data. We need to import it to use it:

```py
import pandas as pd
```

There are two main data structures in pandas: **Series** and **DataFrame**. Here is an example of separately importing them:

```py
from pandas import Series, DataFrame
```

A `Series` is a one-dimensional array-like object containing a sequence of values of the **same type**. All the values also have corresponding index labels.

A `DataFrame` represents a rectangular table of data and contains an ordered, named collection of columns, each of which can be a different value type (numeric, string, Boolean, etc.). Dataframes have both a row and column index. While a dataframe is physically two-dimensional, you can use it to represent higher dimensional data in a tabular format using hierarchical indexing. Dataframes actually consist of series.

<hr>

## Creating Series

[Creating Series](./PyPan_CreatingSeries.md)

<hr>

## Creating Dataframe

[Creating Dataframe](./PyPan_CreatingDataframe.md)

<hr>

## Accessing Data

[Accessing Data](./PyPan_AccessingData.md)

<hr>

## Accessing Data With Booleans

[Accessing Data With Booleans](./PyPan_AccessingDataWBooleans.md)

<hr>

## Index Objects

[Index Objects](./PyPan_IndexObjects.md)

<hr>

## Modifying Data

[Modifying Data](./PyPan_ModifyingData.md)

<hr>

## Converting Series and Dataframes

[Converting Series and Dataframes](./PyPan_ConvertingSeriesDataframes.md)

<hr>

## Deleting Data

[Deleting Data](./PyPan_DeletingData.md)

<hr>

## Missing Data

[Missing Data](./PyPan_MissingData.md)

<hr>

## Duplication in Dataframes

[Duplication in Dataframes](./PyPan_DuplicationInDataframes.md)

<hr>

## Sorting and Ranking

[Sorting and Ranking](./PyPan_SortingRanking.md)

<hr>

## Arithmetic Operations

[Arithmetic Operations](./PyPan_Arithmetic.md)

<hr>

## Descriptive Statistics

[Descriptive Statistics](./PyPan_DescriptiveStatistics.md)

<hr>

## Some Functions and Methods

[Some Functions and Methods](./PyPan_SomeFuncsMethods.md)

<hr>

## Accessors

[Accessors](./PyPan_Accessors.md)

<hr>

## Reading from and Writing to Files

[Reading from and Writing to Files](./PyPan_Files.md)

<hr>

## Pandas and Web APIs

[Pandas and Web APIs](./PyPan_APIs.md)

<hr>

## Hierarchical Indexing

Hierarchical indexing is an important feature of pandas that enables you to have multiple (two or more) index levels on an axis. Another way of thinking about it is that it provides a way for you to work with higher dimensional data in a lower dimensional form.

### Create a series with hierarchical indexing

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

### Selecting subsets of data in series using partial indexing

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

### Turning hierarchically indexed series into a dataframe

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

### Dataframe with Hierarchical index and columns

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

### Checking the number of index levels

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

### Selecting subsets of data in a dataframe using partial indexing

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

### Creating standalone `MultiIndex`

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

### Reordering and sorting levels of hierarchical index

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

### Indexing with a DataFrame's columns

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

<hr>

## Combining and Merging Datasets

### Table for an argument reference on `pandas.merge`

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

### Database-Style DataFrame Joins

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

### Merging on Index

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

### Concatenating along an axis

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

### Combining Data with Overlap

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

<hr>

## Reshaping and Pivoting

There are a number of basic operations for rearranging tabular data. These are referred to as reshape or pivot operations.

### Reshaping with Hierarchical Indexing

The `stack` method “rotates” or pivots from the columns in the data to the rows. The `unstack` method pivots from the rows into the columns.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

print(result.unstack())
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""
```

By default, the innermost level is unstacked (same with `stack`). You can unstack a different level by passing a level number or name:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

print(result.unstack())
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

print(result.unstack(level=0))
"""
state   Ohio  Colorado
number
one        0         3
two        1         4
three      2         5
"""

print(result.unstack(level="state"))
"""
state   Ohio  Colorado
number
one        0         3
two        1         4
three      2         5
"""
```

Unstacking might introduce missing data if all of the values in the level aren’t found in each subgroup. Stacking filters out missing data by default, so the operation is more easily invertible:

```py
import pandas as pd

s1 = pd.Series([0, 1, 2, 3], index=["a", "b", "c", "d"], dtype="Int64")
s2 = pd.Series([4, 5, 6], index=["c", "d", "e"], dtype="Int64")
s3 = pd.concat([s1, s2], keys=["one", "two"])

print(s1)
"""
a    0
b    1
c    2
d    3
dtype: Int64
"""

print(s2)
"""
c    4
d    5
e    6
dtype: Int64
"""

print(s3)
"""
one  a    0
     b    1
     c    2
     d    3
two  c    4
     d    5
     e    6
dtype: Int64
"""

print(s3.unstack())
"""
        a     b  c  d     e
one     0     1  2  3  <NA>
two  <NA>  <NA>  4  5     6
"""

print(s3.unstack().stack())
"""
one  a    0
     b    1
     c    2
     d    3
two  c    4
     d    5
     e    6
dtype: Int64
"""

print(s3.unstack().stack(future_stack=True))
"""
one  a       0
     b       1
     c       2
     d       3
     e    <NA>
two  a    <NA>
     b    <NA>
     c       4
     d       5
     e       6
dtype: Int64
"""
```

When you unstack in a DataFrame, the level unstacked becomes the lowest level in the result. As with the `unstack` method, when calling `stack` we can indicate a specific axis:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

df = pd.DataFrame({
  "left": result,
  "right": result + 5,
}, columns=pd.Index(["left", "right"], name="side"))

print(df)
"""
side             left  right
state    number
Ohio     one        0      5
         two        1      6
         three      2      7
Colorado one        3      8
         two        4      9
         three      5     10
"""

print(df.unstack(level="state"))
"""
side   left          right
state  Ohio Colorado  Ohio Colorado
number
one       0        3     5        8
two       1        4     6        9
three     2        5     7       10
"""

print(df.unstack(level="state").stack(level="side", future_stack=True))
"""
state         Ohio  Colorado
number side
one    left      0         3
       right     5         8
two    left      1         4
       right     6         9
three  left      2         5
       right     7        10
"""
```

### Pivoting “Long” to “Wide” Format

In the `pivot` method, the first two values passed are the columns to be used, respectively, as the row and column index, then finally an optional value column to fill the DataFrame. By omitting the last argument, you obtain a DataFrame with hierarchical columns.

```py
import pandas as pd

df = pd.DataFrame({
  'column1': ['one', 'one', 'one', 'two', 'two', 'two'],
  'column2': ['A', 'B', 'C', 'A', 'B', 'C'],
  'column3': [1, 2, 3, 4, 5, 6],
  'column4': ['x', 'y', 'z', 'q', 'w', 't']
})

print(df)
"""
  column1 column2  column3 column4
0     one       A        1       x
1     one       B        2       y
2     one       C        3       z
3     two       A        4       q
4     two       B        5       w
5     two       C        6       t
"""

print(df.pivot(index="column1", columns=["column2"], values=["column3"]))
"""
              column3
column2       A  B  C
column1
one           1  2  3
two           4  5  6
"""

print(df.pivot(index="column1", columns=["column2"], values=["column3", "column4"]))
"""
              column3       column4
column2       A  B  C       A  B  C
column1
one           1  2  3       x  y  z
two           4  5  6       q  w  t
"""
```

### Pivoting “Wide” to “Long” Format

An inverse operation to `pivot` for DataFrames is `pandas.melt`. Rather than transforming one column into many in a new DataFrame, it merges multiple columns into one, producing a DataFrame that is longer than the input.

```py
import pandas as pd

df = pd.DataFrame({
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   A  B  C
0  1  4  7
1  2  5  8
2  3  6  9
"""

melted = pd.melt(df)
print(melted)
"""
  variable  value
0        A      1
1        A      2
2        A      3
3        B      4
4        B      5
5        B      6
6        C      7
7        C      8
8        C      9
"""
```

When using `pandas.melt`, we can indicate which columns (if any) are group indicators. Let's use `"key"` as the only group indicator in our below example:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

melted = pd.melt(df, id_vars="key")
print(melted)
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
6  foo        C      7
7  bar        C      8
8  baz        C      9
"""
```

After using `pandas.melt`, we can still use the `pivot` method to revert the changes back.

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

melted = pd.melt(df, id_vars="key")
print(melted)
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
6  foo        C      7
7  bar        C      8
8  baz        C      9
"""

reshaped = melted.pivot(index="key", columns="variable", values="value")
print(reshaped)
"""
variable  A  B  C
key
bar       2  5  8
baz       3  6  9
foo       1  4  7
"""

print(reshaped.reset_index())
"""
variable  key  A  B  C
0         bar  2  5  8
1         baz  3  6  9
2         foo  1  4  7
"""
```

We can specify which values should be in the result of the `pandas.melt` command:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

print(pd.melt(df, id_vars="key", value_vars=["A", "B"]))
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
"""
```

Just like the `pivot` method, `pandas.melt` can be used without any group identifiers, too:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

print(pd.melt(df, value_vars=["key", "A", "B"]))
"""
  variable value
0      key   foo
1      key   bar
2      key   baz
3        A     1
4        A     2
5        A     3
6        B     4
7        B     5
8        B     6
"""
```

<hr>

## Data Aggregation and Group Operations

The way the `groupby` method works is that we use it to split the data into groups, then we apply a function to the groups, and combine them into a result. This can be particularly useful in aggregating or summarizing data.

### Using `groupby` with a series

The basic use case of the `pandas.Series.groupby()` method is to group data by the index and then apply an aggregation function, like sum or mean. The `groupby` method returns `GroupBy` object, which in itself has not anything computed yet. But it's ready to be used for computation on groups of data.

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
print(grouped) # <pandas.core.groupby.generic.SeriesGroupBy object at 0x000001BBB69ED4F0>

print(grouped.sum())
"""
A    15
B     9
C    21
D     0
dtype: int32
"""
```

There are several useful attributes and methods of the `GroupBy` object:

- The `ngroups` attribute of the `GroupBy` object returns the number of groups.
- To access the groups themselves, we can use the `groups` attribute.
- To access the group keys, we can use the `groups.keys()` method.
- Another `GroupBy` method `size` returns a Series containing group sizes

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
grouped.ngroups # 4
grouped.groups # {'A': ['A', 'A', 'A'], 'B': ['B', 'B'], 'C': ['C', 'C', 'C', 'C'], 'D': ['D']}
grouped.groups.keys() # dict_keys(['A', 'B', 'C', 'D'])
grouped.size()
"""
A    3
B    2
C    4
D    1
dtype: int64
"""
```

To get the data of a specific group, we can use the `get_group` method:

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
grouped.get_group("A")
"""
A    5
A    2
A    8
dtype: int32
"""
```

We can apply custom functions to the groups using the `apply` method:

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

def func(x):
  return x.max() - x.min()

result = ser.groupby(level=0).apply(func)
print(result)
"""
A    6
B    3
C    8
D    0
dtype: int32
"""
```

We can also provide arbitrary grouping to group the data.

```py
ser = pd.Series(np.arange(10, 15))
print(ser)
"""
0    10
1    11
2    12
3    13
4    14
dtype: int64
"""

ser.groupby(["sameGroup", "sameGroup", "sameGroup", "sameGroup", "anotherGroup"]).sum()
"""
anotherGroup    14
sameGroup       46
dtype: int64
"""
```

### Using `groupby` with a hierarchically indexed series

When we have a hierarchically indexed series, we can group and aggregate by each level of index:

```py
# Create a Series with MultiIndex
multiIndex = pd.MultiIndex.from_arrays([
    ['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'],
    ['one', 'one', 'two', 'two', 'three', 'one', 'two', 'two', 'three', 'one']
], names=['letters', 'numbers'])

ser = pd.Series(np.random.permutation(10), index=multiIndex)
print(ser)
"""
letters  numbers
A        one        1
         one        0
         two        7
B        two        6
         three      8
C        one        5
         two        9
         two        2
         three      4
D        one        3
dtype: int32
"""

ser.groupby(level=["letters"]).sum()
"""
letters
A     8
B    14
C    20
D     3
dtype: int32
"""

ser.groupby(level=["numbers"]).sum()
"""
numbers
one       9
three    12
two      24
dtype: int32
"""

ser.groupby(level=["letters", "numbers"]).sum()
"""
letters  numbers
A        one         1
         two         7
B        three       8
         two         6
C        one         5
         three       4
         two        11
D        one         3
dtype: int32
"""
```

### Grouping using a dictionary

We can group using a dictionary:

```py
ser = pd.Series(np.arange(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    0
A    1
A    2
B    3
B    4
C    5
C    6
C    7
C    8
D    9
dtype: int64
"""

mapping = {"A": "group1", "B": "group1", "C": "group2", "D": "group2"}

ser.groupby(mapping).sum()
"""
group1    10
group2    35
dtype: int64
"""
```

### Grouping using a function

We can group using a function as well. Any function passed as a group key will be called once per index value with the return values being used as the group names.

```py
ser = pd.Series(np.arange(10), index=['abc', 'abc', 'abc', 'abcd', 'abcd', 'abcd', 'abcd', 'abcde', 'abcde', 'abcde'])
print(ser)
"""
abc      0
abc      1
abc      2
abcd     3
abcd     4
abcd     5
abcd     6
abcde    7
abcde    8
abcde    9
dtype: int64
"""

ser.groupby(len).sum()
"""
3     3
4    18
5    24
dtype: int64
"""
```

### Using `groupby` with a dataframe

We can use the `groupby` method on the dataframe itself or using its columns. Here is how it looks when we use it in different ways:

```py
toBeGrouped = [['Istanbul', 'Turkiye', 15.0],
        ['Ankara', 'Turkiye', 5.0],
        ['Baku', 'Azerbaijan', 2.5],
        ['Ganja', 'Azerbaijan', 0.5],
        ['Sumgayit', 'Azerbaijan', 0.5],
        ['Najaf', 'Iraq', None],
        ['Karbala', 'Iraq', 0.6]]

df = pd.DataFrame(toBeGrouped, columns=["city", "country", "population"])
print(df)
"""
       city     country  population
0  Istanbul     Turkiye        15.0
1    Ankara     Turkiye         5.0
2      Baku  Azerbaijan         2.5
3     Ganja  Azerbaijan         0.5
4  Sumgayit  Azerbaijan         0.5
5     Najaf        Iraq         NaN
6   Karbala        Iraq         0.6
"""

df.groupby(df["country"]).sum()
"""
                         city  population
country
Azerbaijan  BakuGanjaSumgayit         3.5
Iraq             NajafKarbala         0.6
Turkiye        IstanbulAnkara        20.0
"""

df["population"].groupby(df["country"]).sum()
"""
country
Azerbaijan     3.5
Iraq           0.6
Turkiye       20.0
Name: population, dtype: float64
"""

df.groupby(df["country"])["population"].sum()
"""
country
Azerbaijan     3.5
Iraq           0.6
Turkiye       20.0
Name: population, dtype: float64
"""
```

We can also provide arbitrary grouping to group the data.

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df["data1"].groupby(["sameGroup", "sameGroup", "sameGroup", "sameGroup", "sameGroup", "sameGroup", "anotherGroup"]).sum()
"""
anotherGroup    106
sameGroup       615
Name: data1, dtype: int64
"""
```

### Using `groupby` with a hierarchically indexed dataframe

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df["data1"].groupby([df["key1"], df["key2"]]).sum()
"""
key1  key2
a     1       100
      2       101
b     1       104
      2       103
Name: data1, dtype: int64
"""
```

Note that any missing values in a group key are excluded from the result by default. This behavior can be disabled by passing `dropna=False` to `groupby`:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df.groupby("key1").size()
"""
key1
a    3
b    2
dtype: int64
"""

df.groupby("key1", dropna=False).size()
"""
key1
a      3
b      2
NaN    2
dtype: int64
"""
```

The `count` method, used with `groupby` computes the number of nonnull values in each group:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df.groupby("key1").count()
"""
      key2  data1  data2
key1
a        2      3      3
b        2      2      2
"""
```

### Group by columns

If we want to group by columns of a dataframe, we need to transpose it:

```py
df = pd.DataFrame(
  np.random.standard_normal((3, 3)),
  columns=["a", "b", "c"],
  index=["Joe", "Steve", "Wanda", ]
)

print(df)
"""
              a         b         c
Joe    0.981803  1.133051  0.402913
Steve -0.599898 -0.683760  0.031298
Wanda -0.030887 -0.877773  1.450590
"""

print(df.T)
"""
        Joe     Steve     Wanda
a  0.981803 -0.599898 -0.030887
b  1.133051 -0.683760 -0.877773
c  0.402913  0.031298  1.450590
"""

print(df.T.groupby({"a": "red", "b": "red", "c": "blue", "d": "blue"}).sum())
"""
           Joe     Steve    Wanda
blue  0.402913  0.031298  1.45059
red   2.114854 -1.283658 -0.90866
"""
```

### Iterating over groups

The object returned by `groupby` supports iteration. When we iterate using the `for` loop, we get a sequence of 2-tuples containing the group name along with the chunk of data.

```py
df = pd.DataFrame(
  np.random.standard_normal((3, 3)),
  columns=["a", "b", "c"],
  index=["Joe", "Steve", "Wanda"]
)

print(df)
"""
              a         b         c
Joe    0.302227 -0.284364 -2.379351
Steve -0.998659 -0.732793 -0.908273
Wanda -0.218942 -1.280910  0.733926
"""

for groupName, groupData in df.groupby(level=0):
  print(groupName)
  print(groupData)
"""
Joe
            a         b         c
Joe  0.302227 -0.284364 -2.379351
Steve
              a         b         c
Steve -0.998659 -0.732793 -0.908273
Wanda
              a        b         c
Wanda -0.218942 -1.28091  0.733926
"""
```

When we group by multiple keys and iterate through the group, the first element in the tuple will be a tuple of key values:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

for keyTuple, groupData in df.groupby(["key1", "key2"]):
  print(keyTuple)
  print(groupData, "\n")
"""
('a', np.int64(1))
  key1  key2  data1  data2
0    a     1    100    200

('a', np.int64(2))
  key1  key2  data1  data2
1    a     2    101    201

('b', np.int64(1))
  key1  key2  data1  data2
4    b     1    104    204

('b', np.int64(2))
  key1  key2  data1  data2
3    b     2    103    203
"""
```

<hr>

### Data Aggregation

Aggregations refer to any data transformation that produces scalar values from arrays. We used a few aggregations, above, while focusing on the ways of grouping data. There are more methods that we can use with the `groupby`. Here is a table of optimized `groupby` methods:

| Function name      | Description                                                                  |
| ------------------ | ---------------------------------------------------------------------------- |
| `any`, `all`       | Return True if any (one or more values) or all non-NA values are "truthy"    |
| `nunique()`        | Number of unique values                                                      |
| `count`            | Number of non-NA values                                                      |
| `cummin`, `cummax` | Cumulative minimum and maximum of non-NA values                              |
| `cumsum`           | Cumulative sum of non-NA values                                              |
| `cumprod`          | Cumulative product of non-NA values                                          |
| `first`, `last`    | First and last non-NA values                                                 |
| `mean`             | Mean of non-NA values                                                        |
| `median`           | Arithmetic median of non-NA values                                           |
| `min`, `max`       | Minimum and maximum of non-NA values                                         |
| `nth`              | Retrieve value that would appear at position n with the data in sorted order |
| `ohlc`             | Compute four "open-high-low-close" statistics for time series-like data      |
| `prod`             | Product of non-NA values                                                     |
| `quantile`         | Compute sample quantile                                                      |
| `rank`             | Ordinal ranks of non-NA values, like calling Series.rank                     |
| `size`             | Compute group sizes, returning result as a Series                            |
| `sum`              | Sum of non-NA values                                                         |
| `std`, `var`       | Sample standard deviation and variance                                       |

There is also an `aggregate` method or `agg`, that could be used for aggregations. Note than you can pass the name of the functions in the above table to the `aggregate` method as a string.

#### Custom function for aggregation

To use your own aggregation functions, pass any function that aggregates an array to the `aggregate` method or its short alias `agg`:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

grouped = df.groupby("key1")

def func(arr):
  return arr.max() - arr.min()

grouped.agg(func)
"""
      key2  data1  data2
key1
a        1      5      5
b        1      1      1
"""
```

You may want to aggregate using a different function, depending on the column, or multiple functions at once.

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

grouped_pct = grouped["tip_pct"]

def func(arr):
  return arr.max() - arr.min()

print(grouped_pct.agg(["mean", "std", func]))
"""
                 mean       std      func
day  smoker
Fri  No      0.151650  0.028123  0.067349
     Yes     0.174783  0.051293  0.159925
Sat  No      0.158048  0.039767  0.235193
     Yes     0.147906  0.061375  0.290095
Sun  No      0.160113  0.042347  0.193226
     Yes     0.187250  0.154134  0.644685
Thur No      0.160298  0.038774  0.193350
     Yes     0.163863  0.039389  0.151240
"""
```

You don’t need to accept the names, that `GroupBy` gives, to the columns. If you pass a list of `(<name>, <function>)` tuples, the first element of each tuple will be used as the DataFrame column names:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

grouped_pct = grouped["tip_pct"]

grouped_pct.agg([("average", "mean"), ("stdev", "std")])
"""
              average     stdev
day  smoker
Fri  No      0.151650  0.028123
     Yes     0.174783  0.051293
Sat  No      0.158048  0.039767
     Yes     0.147906  0.061375
Sun  No      0.160113  0.042347
     Yes     0.187250  0.154134
Thur No      0.160298  0.038774
     Yes     0.163863  0.039389
"""
```

In the above example, we used only one column of a dataframe, which means we used a series. With a DataFrame we have more options, as we can specify a list of functions to apply to all of the columns or different functions per column.

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped[["tip_pct", "total_bill"]].agg(["count", "mean", "max"])
result
"""
            tip_pct                     total_bill
              count      mean       max      count       mean    max
day  smoker
Fri  No           4  0.151650  0.187735          4  18.420000  22.75
     Yes         15  0.174783  0.263480         15  16.813333  40.17
Sat  No          45  0.158048  0.291990         45  19.661778  48.33
     Yes         42  0.147906  0.325733         42  21.276667  50.81
Sun  No          57  0.160113  0.252672         57  20.506667  48.17
     Yes         19  0.187250  0.710345         19  24.120000  45.35
Thur No          45  0.160298  0.266312         45  17.113111  41.19
     Yes         17  0.163863  0.241255         17  19.190588  43.11
"""
```

As before, a list of tuples with custom names can be passed:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped[["tip_pct", "total_bill"]].agg([("Average", "mean"), ("Variance", "var")])
print(result)
"""
              tip_pct           total_bill
              Average  Variance    Average    Variance
day  smoker
Fri  No      0.151650  0.000791  18.420000   25.596333
     Yes     0.174783  0.002631  16.813333   82.562438
Sat  No      0.158048  0.001581  19.661778   79.908965
     Yes     0.147906  0.003767  21.276667  101.387535
Sun  No      0.160113  0.001793  20.506667   66.099980
     Yes     0.187250  0.023757  24.120000  109.046044
Thur No      0.160298  0.001503  17.113111   59.625081
     Yes     0.163863  0.001551  19.190588   69.808518
"""
```

Now, suppose we wanted to apply potentially different functions to one or more of the columns. To do this, pass a dictionary to `agg` that contains a mapping of column names to any of the function specifications listed so far:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped.agg({"tip": "max", "size": "sum"})
print(result)
"""
               tip  size
day  smoker
Fri  No       3.50     9
     Yes      4.73    31
Sat  No       9.00   115
     Yes     10.00   104
Sun  No       6.00   167
     Yes      6.50    49
Thur No       6.70   112
     Yes      5.00    40
"""

result = grouped.agg({"tip": ["max", "min"], "size": "sum"})
print(result)
"""
               tip       size
               max   min  sum
day  smoker
Fri  No       3.50  1.50    9
     Yes      4.73  1.00   31
Sat  No       9.00  1.00  115
     Yes     10.00  1.00  104
Sun  No       6.00  1.01  167
     Yes      6.50  1.50   49
Thur No       6.70  1.25  112
     Yes      5.00  2.00   40
"""
```

In all of the examples up until now, the aggregated data comes back with an index, potentially hierarchical, composed from the unique group key combinations. Since this isn’t always desirable, you can disable this behavior in most cases by passing `as_index=False` to `groupby`:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"], as_index=False)
print(grouped.mean(numeric_only=True))
"""
    day smoker  total_bill       tip      size   tip_pct
0   Fri     No   18.420000  2.812500  2.250000  0.151650
1   Fri    Yes   16.813333  2.714000  2.066667  0.174783
2   Sat     No   19.661778  3.102889  2.555556  0.158048
3   Sat    Yes   21.276667  2.875476  2.476190  0.147906
4   Sun     No   20.506667  3.167895  2.929825  0.160113
5   Sun    Yes   24.120000  3.516842  2.578947  0.187250
6  Thur     No   17.113111  2.673778  2.488889  0.160298
7  Thur    Yes   19.190588  3.030000  2.352941  0.163863
"""

grouped = tips.groupby(["day", "smoker"])
print(grouped.mean(numeric_only=True))
"""
             total_bill       tip      size   tip_pct
day  smoker
Fri  No       18.420000  2.812500  2.250000  0.151650
     Yes      16.813333  2.714000  2.066667  0.174783
Sat  No       19.661778  3.102889  2.555556  0.158048
     Yes      21.276667  2.875476  2.476190  0.147906
Sun  No       20.506667  3.167895  2.929825  0.160113
     Yes      24.120000  3.516842  2.578947  0.187250
Thur No       17.113111  2.673778  2.488889  0.160298
     Yes      19.190588  3.030000  2.352941  0.163863
"""
```

#### `pivot_table`

While `pivot` provides general purpose pivoting with various data types, pandas also provides `pivot_table` method for pivoting with aggregation of numeric data. In addition to providing a convenient interface to `groupby`, `pivot_table` can add partial totals, also known as margins.

Here is a basic use of it:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "smoker"], values=["size", "tip"]))
"""
                 size       tip
day  smoker
Fri  No      2.250000  2.812500
     Yes     2.066667  2.714000
Sat  No      2.555556  3.102889
     Yes     2.476190  2.875476
Sun  No      2.929825  3.167895
     Yes     2.578947  3.516842
Thur No      2.488889  2.673778
     Yes     2.352941  3.030000
"""
```

In the above example, we indicated the `index` and `values`. We can also specify what data should be presented as `columns`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"]))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000       NaN  3.000000       NaN
     Lunch   2.500000  2.352941  2.666364  3.030000
"""
```

We could augment this table to include partial totals by passing `margins=True`. This has the effect of adding `All` row and column labels.

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"], margins=True))
"""
                 size                           tip
smoker             No       Yes       All        No       Yes       All
day  time
Fri  Dinner  2.000000  2.222222  2.166667  2.750000  3.003333  2.940000
     Lunch   3.000000  1.833333  2.000000  3.000000  2.280000  2.382857
Sat  Dinner  2.555556  2.476190  2.517241  3.102889  2.875476  2.993103
Sun  Dinner  2.929825  2.578947  2.842105  3.167895  3.516842  3.255132
Thur Dinner  2.000000       NaN  2.000000  3.000000       NaN  3.000000
     Lunch   2.500000  2.352941  2.459016  2.666364  3.030000  2.767705
All          2.668874  2.408602  2.569672  2.991854  3.008710  2.998279
"""
```

The default function of the `pivot_table` is the `mean`. We can choose to apply different aggregation function to data using the `aggfunc` option:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"] ,values=["size", "tip"], margins=True, aggfunc=["count"]))
"""
             count
              size               tip
smoker          No   Yes  All     No   Yes  All
day  time
Fri  Dinner    3.0   9.0   12    3.0   9.0   12
     Lunch     1.0   6.0    7    1.0   6.0    7
Sat  Dinner   45.0  42.0   87   45.0  42.0   87
Sun  Dinner   57.0  19.0   76   57.0  19.0   76
Thur Dinner    1.0   NaN    1    1.0   NaN    1
     Lunch    44.0  17.0   61   44.0  17.0   61
All          151.0  93.0  244  151.0  93.0  244
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"], margins=True, aggfunc=len))
"""
              size               tip
smoker          No   Yes  All     No   Yes  All
day  time
Fri  Dinner    3.0   9.0   12    3.0   9.0   12
     Lunch     1.0   6.0    7    1.0   6.0    7
Sat  Dinner   45.0  42.0   87   45.0  42.0   87
Sun  Dinner   57.0  19.0   76   57.0  19.0   76
Thur Dinner    1.0   NaN    1    1.0   NaN    1
     Lunch    44.0  17.0   61   44.0  17.0   61
All          151.0  93.0  244  151.0  93.0  244
"""
```

If some combinations are empty (or otherwise NA), you may wish to pass a `fill_value`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"]))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000       NaN  3.000000       NaN
     Lunch   2.500000  2.352941  2.666364  3.030000
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"] ,values=["size", "tip"], fill_value=0))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000  0.000000  3.000000  0.000000
     Lunch   2.500000  2.352941  2.666364  3.030000
"""
```

Here is a table of `pivot_table` options:

| Argument       | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| `values`       | Column name or names to aggregate; by default, aggregates all numeric columns                                         |
| `index`        | Column names or other group keys to group on the rows of the resulting pivot table                                    |
| `columns`      | Column names or other group keys to group on the columns of the resulting pivot table                                 |
| `aggfunc`      | Aggregation function or list of functions (`"mean"` by default); can be any function valid in a `groupby` context     |
| `fill_value`   | Replace missing values in the result table                                                                            |
| `dropna`       | If `True`, do not include columns whose entries are all NA                                                            |
| `margins`      | Add row/column subtotals and grand total (`False` by default)                                                         |
| `margins_name` | Name to use for the margin row/column labels when passing `margins=True;` defaults to `"All"`                         |
| `observed`     | With Categorical group keys, if `True`, show only the observed category values in the keys rather than all categories |

<hr>

#### Crosstab

A cross-tabulation (or crosstab for short) is a special case of a pivot table that can compute group frequencies. The `pandas.crosstab` method does not require a dataframe as an input. It can also accept array-like objects for its rows and columns. The default function for `crosstab` is `len`.

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(index=[tips["day"], tips["time"]], columns=tips["smoker"]))
"""
smoker       No  Yes
day  time
Fri  Dinner   3    9
     Lunch    1    6
Sat  Dinner  45   42
Sun  Dinner  57   19
Thur Dinner   1    0
     Lunch   44   17
"""
```

If we are using the `values` option, we also have to specify the `aggfunc`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(index=[tips["day"], tips["time"]], columns=tips["smoker"], values=tips["size"], aggfunc="mean"))
"""
smoker             No       Yes
day  time
Fri  Dinner  2.000000  2.222222
     Lunch   3.000000  1.833333
Sat  Dinner  2.555556  2.476190
Sun  Dinner  2.929825  2.578947
Thur Dinner  2.000000       NaN
     Lunch   2.500000  2.352941
"""
```

We can also rename the index and columns, using the `rownames` and the `colnames` options:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  rownames=["day", "time"],
  columns=tips["smoker"],
  colnames=["smoker"],
  values=tips["size"], aggfunc="mean"))
"""
smoker             No       Yes
day  time
Fri  Dinner  2.000000  2.222222
     Lunch   3.000000  1.833333
Sat  Dinner  2.555556  2.476190
Sun  Dinner  2.929825  2.578947
Thur Dinner  2.000000       NaN
     Lunch   2.500000  2.352941
"""
```

To normalize the data using the `crosstab`, we use the `normalize` option. It accepts a number of different options:

- `‘all’` or `True` – normalizes the values across the entire dataframe (as a percentage of the total across rows and columns)
- `‘index’` – normalizes across rows
- `‘columns’` – normalizes down columns

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize="index"
  ))
"""
smoker             No       Yes
day  time
Fri  Dinner  0.250000  0.750000
     Lunch   0.142857  0.857143
Sat  Dinner  0.517241  0.482759
Sun  Dinner  0.750000  0.250000
Thur Dinner  1.000000  0.000000
     Lunch   0.721311  0.278689
All          0.618852  0.381148
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize="columns"
  ))
"""
smoker             No       Yes       All
day  time
Fri  Dinner  0.019868  0.096774  0.049180
     Lunch   0.006623  0.064516  0.028689
Sat  Dinner  0.298013  0.451613  0.356557
Sun  Dinner  0.377483  0.204301  0.311475
Thur Dinner  0.006623  0.000000  0.004098
     Lunch   0.291391  0.182796  0.250000
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize=True
  ))
"""
smoker             No       Yes       All
day  time
Fri  Dinner  0.012295  0.036885  0.049180
     Lunch   0.004098  0.024590  0.028689
Sat  Dinner  0.184426  0.172131  0.356557
Sun  Dinner  0.233607  0.077869  0.311475
Thur Dinner  0.004098  0.000000  0.004098
     Lunch   0.180328  0.069672  0.250000
All          0.618852  0.381148  1.000000
"""
```

<hr>

## Time Series

The `pandas.to_datetime` method parses many different kinds of date representations and turns them into a `DatetimeIndex`. Standard date formats like ISO 8601 can be parsed quickly:

```py
import pandas as pd

datestrs = ["2011-07-06 12:00:00", "2011-08-06 00:00:00"]

pd.to_datetime(datestrs)
# DatetimeIndex(['2011-07-06 12:00:00', '2011-08-06 00:00:00'], dtype='datetime64[ns]', freq=None)
```

It also handles values that should be considered missing (`None`, empty string, etc.). `NaT` (Not a Time) is pandas’s null value for timestamp data.

```py
import pandas as pd

datestrs = ["2011-07-06 12:00:00", "2011-08-06 00:00:00"]

pd.to_datetime([None])
# DatetimeIndex(['NaT'], dtype='datetime64[ns]', freq=None)

pd.to_datetime([None])[0] # NaT

idx = pd.to_datetime(datestrs + [None])
pd.isna(idx) # array([False, False,  True])
```

A basic kind of time series object in pandas is a Series indexed by timestamps, which is often represented outside of pandas as Python strings or `datetime` objects. Under the hood, these `datetime` objects are put in a `DatetimeIndex`.

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [
  datetime(2011, 1, 2),
  datetime(2011, 1, 5),
  datetime(2011, 1, 7),
  datetime(2011, 1, 8),
  datetime(2011, 1, 10),
  datetime(2011, 1, 12)
]

ts = pd.Series(np.random.standard_normal(6), index=dates)
ts
"""
2011-01-02   -0.322679
2011-01-05    0.311913
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
2011-01-12   -0.317292
dtype: float64
"""

ts.index
"""
DatetimeIndex(['2011-01-02', '2011-01-05', '2011-01-07', '2011-01-08', '2011-01-10', '2011-01-12'],
              dtype='datetime64[ns]', freq=None)
"""

# ts[::2] selects every second element in ts
ts + ts[::2]
"""
2011-01-02   -0.645357
2011-01-05         NaN
2011-01-07   -0.842129
2011-01-08         NaN
2011-01-10    0.899739
2011-01-12         NaN
dtype: float64
"""
```

`DatetimeIndex` includes pandas `Timestamp` object. pandas stores timestamps using NumPy’s `datetime64` data type at the nanosecond resolution. A `pandas.Timestamp` can be substituted at most places where you would use Python's `datetime` object. The reverse is not true, however, because `pandas.Timestamp` can store nanosecond precision data, while `datetime` stores only up to microseconds.

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts.index.dtype # dtype('<M8[ns]')
ts.index[0] # Timestamp('2011-01-02 00:00:00')
```

### Indexing, Selection, Subsetting

To index data in a time series, we can use a timestamp, `datetime` object or a string that is interpretable as a date:

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts.index[2] # Timestamp('2011-01-07 00:00:00')
ts[ts.index[2]] # np.float64(-0.42106435533063935)

ts["2011-01-07"] # np.float64(-0.42106435533063935)

ts[datetime(2011, 1, 7)] # np.float64(-0.42106435533063935)
```

For longer time series, a year or only a year and month can be passed to easily select slices of data:

```py
import numpy as np
import pandas as pd

longer_ts = pd.Series(np.random.standard_normal(1000), index=pd.date_range("2000-01-01", periods=1000))

longer_ts["2001"]
longer_ts["2001-05"]
```

Slicing with `datetime` objects or strings interpretable as dates work as well. Because most time series data is ordered chronologically, you can even slice with timestamps not contained in a time series:

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts[datetime(2011, 1, 7):]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
2011-01-12   -0.317292
dtype: float64
"""

ts[datetime(2011, 1, 7):datetime(2011, 1, 10)]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
dtype: float64
"""

ts["2011-01-07":"2011-01-10"]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
dtype: float64
"""

ts["2010-01-01":]
"""
2011-01-02   -0.014972
2011-01-05    1.747874
2011-01-07    1.132017
2011-01-08   -1.062250
2011-01-10    0.170324
2011-01-12   -0.608212
dtype: float64
"""
```

Remember that slicing in this manner produces views on the source time series, like slicing NumPy arrays. This means that no data is copied, and modifications on the slice will be reflected in the original data. There is an equivalent instance method, `truncate`, that slices a Series between two dates.

### Date Ranges, Frequencies, and Shifting

### `date_range`

The `date_range` method in Pandas generates a `DatetimeIndex` with an indicated length according to a particular frequency.

```py
import pandas as pd

dr = pd.date_range(start="2024-08-10", end="2024-08-20")
print(dr)
"""
DatetimeIndex(['2024-08-10', '2024-08-11', '2024-08-12', '2024-08-13',
               '2024-08-14', '2024-08-15', '2024-08-16', '2024-08-17',
               '2024-08-18', '2024-08-19', '2024-08-20'],
              dtype='datetime64[ns]', freq='D')
"""
```

The `date_range` method takes following arguments:

- `start` - left bound for generating dates
- `end` - right bound for generating dates
- `periods` (optional) - number of periods to generate
- `freq` (optional) - specifies the frequency of the generated dates
- `tz` (optional) - time zone name for returning localized DatetimeIndex.
- `name` (optional) - name for the resulting DateTimeIndex
- `kwargs` (optional) - the unit of the arg for epoch times.

Here is one more example, this time using the `periods` keyword argument, as well. Remember, if you pass only one of `start` or `end` dates, you must pass a number of `periods` to generate:

```py
import pandas as pd

dr = pd.date_range(start="2024-08-10", end="2024-08-20", periods=5)
print(dr)
"""
DatetimeIndex(['2024-08-10 00:00:00', '2024-08-12 12:00:00',
               '2024-08-15 00:00:00', '2024-08-17 12:00:00',
               '2024-08-20 00:00:00'],
              dtype='datetime64[ns]', freq=None)
"""

print(pd.date_range(start="2024-08-10", periods=5))
"""
DatetimeIndex(['2024-08-10', '2024-08-11', '2024-08-12', '2024-08-13', '2024-08-14'],
              dtype='datetime64[ns]', freq='D')
"""

print(pd.date_range(end="2024-08-20", periods=5))
"""
DatetimeIndex(['2024-08-16', '2024-08-17', '2024-08-18', '2024-08-19', '2024-08-20'],
              dtype='datetime64[ns]', freq='D')
"""
```

In the above example, we have generated 5 periods, and because we haven't provided the `freq` argument, it defaulted to `D`, which means daily frequency. There are many values that we could provide to `freq`. Here is a table of base time series frequencies (not comprehensive):

| Alias                     | Offset type            | Description                                                                                                                                                     |
| ------------------------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `D`                       | `Day`                  | Calendar daily                                                                                                                                                  |
| `B`                       | `BusinessDay`          | Business daily                                                                                                                                                  |
| `h`                       | `Hour`                 | Hourly                                                                                                                                                          |
| `min`                     | `Minute`               | Once a minute                                                                                                                                                   |
| `L` or `ms`               | `Milli`                | Millisecond (1/1,000 of 1 second)                                                                                                                               |
| `S`                       | `Second`               | Once a second                                                                                                                                                   |
| `U`                       | `Micro`                | Microsecond (1/1,000,000 of 1 second)                                                                                                                           |
| `ME`                      | `MonthEnd`             | Last calendar day of month                                                                                                                                      |
| `BME`                     | `BusinessMonthEnd`     | Last business day (weekday) of month                                                                                                                            |
| `MS`                      | `MonthBegin`           | First calendar day of month                                                                                                                                     |
| `BMS`                     | `BusinessMonthBegin`   | First weekday of month                                                                                                                                          |
| `W-MON, W-TUE, ...`       | `Week`                 | Weekly on given day of week (MON, TUE, WED, THU, FRI, SAT, or SUN)                                                                                              |
| `WOM-1MON, WOM-2MON, ...` | `WeekOfMonth`          | Generate weekly dates in the first, second, third, or fourth week of the month (e.g., WOM-3FRI for the third Friday of each month)                              |
| `Q-JAN, Q-FEB, ...`       | `QuarterEnd`           | Quarterly dates anchored on last calendar day of each month, for year ending in indicated month (JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, or DEC) |
| `BQ-JAN, BQ-FEB, ...`     | `BusinessQuarterEnd`   | Quarterly dates anchored on last weekday day of each month, for year ending in indicated month                                                                  |
| `QS-JAN, QS-FEB, ...`     | `QuarterBegin`         | Quarterly dates anchored on first calendar day of each month, for year ending in indicated month                                                                |
| `BQS-JAN, BQS-FEB, ...`   | `BusinessQuarterBegin` | Quarterly dates anchored on first weekday day of each month, for year ending in indicated month                                                                 |
| `Y-JAN, Y-FEB, ...`       | `YearEnd`              | Annual dates anchored on last calendar day of given month (JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, or DEC)                                       |
| `BA-JAN, BA-FEB, ...`     | `BusinessYearEnd`      | Annual dates anchored on last weekday of given month                                                                                                            |
| `AS-JAN, AS-FEB, ...`     | `YearBegin`            | Annual dates anchored on first day of given month                                                                                                               |
| `BAS-JAN, BAS-FEB, ...`   | `BusinessYearBegin`    | Annual dates anchored on first weekday of given month                                                                                                           |

Here is an example of using `pandas.date_range` with the `freq` argument:

```py
import pandas as pd

print(pd.date_range("2000-01-01", "2000-12-01", freq="BME"))
"""
DatetimeIndex(['2000-01-31', '2000-02-29', '2000-03-31', '2000-04-28',
               '2000-05-31', '2000-06-30', '2000-07-31', '2000-08-31',
               '2000-09-29', '2000-10-31', '2000-11-30'],
              dtype='datetime64[ns]', freq='BME')
"""
```

We can also use the combination of the frequencies from the above table:

```py
import pandas as pd

print(pd.date_range("2000-01-01", periods=5, freq="1h30min"))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 01:30:00',
               '2000-01-01 03:00:00', '2000-01-01 04:30:00',
               '2000-01-01 06:00:00'],
              dtype='datetime64[ns]', freq='90min')
"""

print(pd.date_range("2000-01-01", "2000-01-02 00:00", freq="4h"))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 04:00:00',
               '2000-01-01 08:00:00', '2000-01-01 12:00:00',
               '2000-01-01 16:00:00', '2000-01-01 20:00:00',
               '2000-01-02 00:00:00'],
              dtype='datetime64[ns]', freq='4h')
"""
```

For each base frequency, there is an object referred to as a date offset. We can use these as well:

```py
import pandas as pd
from pandas.tseries.offsets import Hour, Minute

print(Hour(4)) # <4 * Hours>
print(Hour(2) + Minute(30)) # <150 * Minutes>

print(pd.date_range("2000-01-01", periods=5, freq=Hour(1)+Minute(30)))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 01:30:00',
               '2000-01-01 03:00:00', '2000-01-01 04:30:00',
               '2000-01-01 06:00:00'],
              dtype='datetime64[ns]', freq='90min')
"""
```

If we provide time to the `pandas.date_range`, by default it preserves the time of the timestamp:

```py
import pandas as pd

pd.date_range("2012-05-02 12:56:31", periods=5)
"""
DatetimeIndex(['2012-05-02 12:56:31', '2012-05-03 12:56:31',
               '2012-05-04 12:56:31', '2012-05-05 12:56:31',
               '2012-05-06 12:56:31'],
              dtype='datetime64[ns]', freq='D')
"""
```

Sometimes you will have start or end dates with time information but want to generate a set of timestamps normalized to midnight as a convention. To do this, there is a `normalize` option:

```py
import pandas as pd

pd.date_range("2012-05-02 12:56:31", periods=5, normalize=True)
"""
DatetimeIndex(['2012-05-02', '2012-05-03', '2012-05-04', '2012-05-05', '2012-05-06'],
              dtype='datetime64[ns]', freq='D')
"""
```

Shifting refers to moving data backward and forward through time. Both Series and DataFrame have a `shift` method for doing naive shifts forward or backward, leaving the index unmodified:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(2))
"""
2000-01-31         NaN
2000-02-29         NaN
2000-03-31   -0.623963
2000-04-30   -0.363125
Freq: ME, dtype: float64
"""

print(ts.shift(-2))
"""
2000-01-31    0.586776
2000-02-29   -0.117355
2000-03-31         NaN
2000-04-30         NaN
Freq: ME, dtype: float64
"""
```

Because naive shifts leave the index unmodified, some data is discarded. Thus if the frequency is known, it can be passed to `shift` to advance the timestamps in the index. The `freq` option shifts the data by the provided frequency:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(2))
"""
2000-01-31         NaN
2000-02-29         NaN
2000-03-31   -0.623963
2000-04-30   -0.363125
Freq: ME, dtype: float64
"""

print(ts.shift(2, freq="ME"))
"""
2000-03-31   -0.623963
2000-04-30   -0.363125
2000-05-31    0.586776
2000-06-30   -0.117355
Freq: ME, dtype: float64
"""
```

Here are few more examples of shifting the time series index by a provided frequency:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(3, freq="D"))
"""
2000-02-03   -0.623963
2000-03-03   -0.363125
2000-04-03    0.586776
2000-05-03   -0.117355
dtype: float64
"""

print(ts.shift(1, freq="90min"))
"""
2000-01-31 01:30:00   -0.623963
2000-02-29 01:30:00   -0.363125
2000-03-31 01:30:00    0.586776
2000-04-30 01:30:00   -0.117355
dtype: float64
"""
```

### `day_name`

The `day_name` method in the pandas library is used to extract the names of the days of the week from a DatetimeIndex, Series, or DataFrame containing datetime-like values.

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31    0.143187
2000-02-29    2.248076
2000-03-31    1.136395
2000-04-30   -0.789329
Freq: ME, dtype: float64
"""

print(ts.index.day_name())
# Index(['Monday', 'Tuesday', 'Friday', 'Sunday'], dtype='object')
```

### Time Zone Handling

Many time series users choose to work with time series in coordinated universal time or UTC, which is the geography-independent international standard. In Python, time zone information comes from the third-party `pytz` library (installable with pip or conda), which exposes the Olson database, a compilation of world time zone information. Since pandas has a hard dependency on `pytz`, it isn't necessary to install it separately.

To get a time zone object from `pytz`, use `pytz.timezone`. Methods in pandas will accept either time zone names or these objects.

```py
import pytz

tz = pytz.timezone("America/New_York")
```

By default, time series in pandas are time zone naive. We can indicate that time series belongs to a specific local time using the `<timeSeries>.tz_localize("<time zone>")` method. After having the time series localized, we can convert it to different time zones using the `<timeSeries>.tz_convert("<time zone>")` method:

```py
import pandas as pd

dates = pd.date_range("2012-03-09 09:30", periods=6)
print(dates)
"""
DatetimeIndex(['2012-03-09 09:30:00', '2012-03-10 09:30:00',
               '2012-03-11 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00', '2012-03-14 09:30:00'],
              dtype='datetime64[ns]', freq='D')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-09 09:30:00   -1.200803
2012-03-10 09:30:00    0.448043
2012-03-11 09:30:00   -0.092872
2012-03-12 09:30:00    0.962243
2012-03-13 09:30:00   -0.272828
2012-03-14 09:30:00   -1.912672
Freq: D, dtype: float64
"""

ts_utc = ts.tz_localize("UTC")
print(ts_utc)
"""
2012-03-09 09:30:00+00:00   -1.200803
2012-03-10 09:30:00+00:00    0.448043
2012-03-11 09:30:00+00:00   -0.092872
2012-03-12 09:30:00+00:00    0.962243
2012-03-13 09:30:00+00:00   -0.272828
2012-03-14 09:30:00+00:00   -1.912672
Freq: D, dtype: float64
"""

print(ts_utc.tz_convert("Europe/Berlin"))
"""
2012-03-09 10:30:00+01:00   -1.200803
2012-03-10 10:30:00+01:00    0.448043
2012-03-11 10:30:00+01:00   -0.092872
2012-03-12 10:30:00+01:00    0.962243
2012-03-13 10:30:00+01:00   -0.272828
2012-03-14 10:30:00+01:00   -1.912672
Freq: D, dtype: float64
"""
```

`tz_localize` and `tz_convert` are also instance methods on `DatetimeIndex`.

```py
import pandas as pd

dates = pd.date_range("2012-03-09 09:30", periods=6)
print(dates)
"""
DatetimeIndex(['2012-03-09 09:30:00', '2012-03-10 09:30:00',
               '2012-03-11 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00', '2012-03-14 09:30:00'],
              dtype='datetime64[ns]', freq='D')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-09 09:30:00   -1.200803
2012-03-10 09:30:00    0.448043
2012-03-11 09:30:00   -0.092872
2012-03-12 09:30:00    0.962243
2012-03-13 09:30:00   -0.272828
2012-03-14 09:30:00   -1.912672
Freq: D, dtype: float64
"""

print(ts.index.tz_localize("America/New_York"))
"""
DatetimeIndex(['2012-03-09 09:30:00-05:00', '2012-03-10 09:30:00-05:00',
               '2012-03-11 09:30:00-04:00', '2012-03-12 09:30:00-04:00',
               '2012-03-13 09:30:00-04:00', '2012-03-14 09:30:00-04:00'],
              dtype='datetime64[ns, America/New_York]', freq=None)
"""
```

It should be noted that time zone localization and conversion might not always be necessary. For example, `date_range` can generate time series with a pre-set time zone:

```py
import pandas as pd

print(pd.date_range("2012-03-09 09:30", periods=10, tz="UTC"))
"""
DatetimeIndex(['2012-03-09 09:30:00+00:00', '2012-03-10 09:30:00+00:00',
               '2012-03-11 09:30:00+00:00', '2012-03-12 09:30:00+00:00',
               '2012-03-13 09:30:00+00:00', '2012-03-14 09:30:00+00:00',
               '2012-03-15 09:30:00+00:00', '2012-03-16 09:30:00+00:00',
               '2012-03-17 09:30:00+00:00', '2012-03-18 09:30:00+00:00'],
              dtype='datetime64[ns, UTC]', freq='D')
"""
```

Individual `Timestamp` objects similarly can be localized from naive to time zone-aware and converted from one time zone to another:

```py
import pandas as pd

stamp = pd.Timestamp("2011-03-12 04:00")
print(stamp) # Timestamp('2011-03-12 04:00:00')

stamp_utc = stamp.tz_localize("utc")
print(stamp_utc) # Timestamp('2012-03-12 04:00:00+0000', tz='UTC')

print(stamp_utc.tz_convert("America/New_York"))
# Timestamp('2011-03-11 23:00:00-0500', tz='America/New_York')
```

You can also pass a time zone when creating the `Timestamp`:

```py
import pandas as pd

stamp_Istanbul = pd.Timestamp("2011-03-12 04:00", tz="Europe/Istanbul")

print(stamp_Istanbul) # 2011-03-12 04:00:00+02:00

# Time zone-aware Timestamp objects internally store a UTC timestamp value as nanoseconds since the Unix epoch (January 1, 1970)
print(stamp_Istanbul.value) # 1299895200000000000
```

When performing time arithmetic using pandas’s DateOffset objects, pandas respects daylight saving time transitions where possible.

```py
import pandas as pd
from pandas.tseries.offsets import Hour, Minute

stamp = pd.Timestamp("2012-03-11 01:30", tz="US/Eastern")

print(stamp)
# Timestamp('2012-03-11 01:30:00-0500', tz='US/Eastern')

stamp + Hour()
# Timestamp('2012-03-11 03:30:00-0400', tz='US/Eastern')

stamp = pd.Timestamp("2012-11-04 00:30", tz="US/Eastern")

print(stamp)
# Timestamp('2012-11-04 00:30:00-0400', tz='US/Eastern')

stamp + 2 * Hour()
# Timestamp('2012-11-04 01:30:00-0500', tz='US/Eastern')
```

Operations between time zone-naive and time zone-aware data are not supported and will raise an exception.

If two time series with different time zones are combined, the result will be UTC. Since the timestamps are stored under the hood in UTC, this is a straightforward operation and requires no conversion.

```py
import pandas as pd

dates = pd.date_range("2012-03-07 09:30", periods=10, freq="B")
print(dates)
"""
DatetimeIndex(['2012-03-07 09:30:00', '2012-03-08 09:30:00',
               '2012-03-09 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00'],
              dtype='datetime64[ns]', freq='B')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-07 09:30:00   -0.797245
2012-03-08 09:30:00    0.344233
2012-03-09 09:30:00   -1.297468
2012-03-12 09:30:00   -0.151718
2012-03-13 09:30:00    0.490548
Freq: B, dtype: float64
"""

ts1 = ts[:3].tz_localize("Europe/London")
print(ts1)
"""
2012-03-07 09:30:00+00:00   -0.797245
2012-03-08 09:30:00+00:00    0.344233
2012-03-09 09:30:00+00:00   -1.297468
dtype: float64
"""

ts2 = ts1[1:].tz_convert("Europe/Moscow")
print(ts2)
"""
2012-03-08 13:30:00+04:00    0.344233
2012-03-09 13:30:00+04:00   -1.297468
dtype: float64
"""

result = ts1 + ts2
print(result)
"""
2012-03-07 09:30:00+00:00         NaN
2012-03-08 09:30:00+00:00    0.688465
2012-03-09 09:30:00+00:00   -2.594936
dtype: float64
"""

print(result.index)
"""
DatetimeIndex(['2012-03-07 09:30:00+00:00', '2012-03-08 09:30:00+00:00', '2012-03-09 09:30:00+00:00'],
              dtype='datetime64[ns, UTC]', freq=None)
"""
```

### Periods and Period Arithmetic

The `pandas.Period` class represents the period data type, requiring a string or integer and a supported frequency (the same frequencies as in the table for the `date_range` method). In the below example, the `Period` object represents the full time span from January 1, 2011, to December 31, 2011, inclusive.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
print(p) # Period('2011', 'Y-DEC')
```

Adding and subtracting integers from periods has the effect of shifting their frequency. If two periods have the same frequency, their difference is the number of units between them as a date offset.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
print(p) # Period('2011', 'Y-DEC')

print(p + 5) # Period('2016', 'Y-DEC')

print(pd.Period("2014", freq="Y-DEC") - p)
# <3 * YearEnds: month=12>
```

Regular ranges of periods can be constructed with the `period_range` function. It creates the `PeriodIndex` object. The `PeriodIndex` class stores a sequence of periods and can serve as an axis index in any pandas data structure.

```py
import numpy as np
import pandas as pd

periods = pd.period_range("2000-01-01", "2000-06-30", freq="M")
print(periods)
# PeriodIndex(['2000-01', '2000-02', '2000-03', '2000-04', '2000-05', '2000-06'], dtype='period[M]')

print(pd.Series(np.random.standard_normal(6), index=periods))
"""
2000-01    1.991928
2000-02   -1.836094
2000-03   -1.116105
2000-04    0.971672
2000-05    1.723111
2000-06    0.547108
Freq: M, dtype: float64
"""
```

We can also create a `PeriodIndex` object using the `PeriodIndex` method and an array of strings representing periods:

```py
import pandas as pd

values = ["2001Q3", "2002Q2", "2003Q1"]

index = pd.PeriodIndex(values, freq="Q-DEC")
print(index)
# PeriodIndex(['2001Q3', '2002Q2', '2003Q1'], dtype='period[Q-DEC]')
```

Periods and `PeriodIndex` objects can be converted to another frequency with their `asfreq` method.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
p # Period('2011', 'Y-DEC')

p.asfreq("M", how="start") # Period('2011-01', 'M')
p.asfreq("M", how="end") # Period('2011-12', 'M')
p.asfreq("M") # Period('2011-12', 'M')
```

For a fiscal year ending on a month other than December, the corresponding monthly subperiods are different:

```py
import pandas as pd

p = pd.Period("2011", freq="Y-JUN")
p # Period('2011', 'Y-JUN')

p.asfreq("M", how="start") # Period('2010-07', 'M')
p.asfreq("M", how="end") # Period('2011-06', 'M')
```

Just like a single period could be converted, whole `PeriodIndex` objects or time series can be similarly converted using the `asfreq` method:

```py
import pandas as pd

periods = pd.period_range("2006", "2009", freq="Y-DEC")
periods # PeriodIndex(['2006', '2007', '2008', '2009'], dtype='period[Y-DEC]')

ts = pd.Series(np.random.standard_normal(len(periods)), index=periods)
ts
"""
2006    0.890714
2007    1.207863
2008   -0.566002
2009    0.128466
Freq: Y-DEC, dtype: float64
"""

ts.asfreq("M", how="start")
"""
2006-01    0.890714
2007-01    1.207863
2008-01   -0.566002
2009-01    0.128466
Freq: M, dtype: float64
"""

ts.asfreq("D", how="end")
"""
2006-12-31    0.890714
2007-12-31    1.207863
2008-12-31   -0.566002
2009-12-31    0.128466
Freq: D, dtype: float64
"""
```

Here is an example of creating a quarterly period. This one ends in January, and we can confirm it by converting it to a daily period:

```py
import pandas as pd

p = pd.Period("2012Q4", freq="Q-JAN")
p # Period('2012Q4', 'Q-JAN')

p.asfreq("D", how="start") # Period('2011-11-01', 'D')
p.asfreq("D", how="end") # Period('2012-01-31', 'D')
```

The `to_timestamp` method returns the `Timestamp` at the start of the period by default.

```py
import pandas as pd

p = pd.Period("2012Q4", freq="Q-JAN")
p # Period('2012Q4', 'Q-JAN')

p.to_timestamp() # Timestamp('2011-11-01 00:00:00')
```

You can generate quarterly ranges using `pandas.period_range`.

```py
import pandas as pd

periods = pd.period_range("2011Q3", "2012Q4", freq="Q-JAN")
periods
# PeriodIndex(['2011Q3', '2011Q4', '2012Q1', '2012Q2', '2012Q3', '2012Q4'], dtype='period[Q-JAN]')

ts = pd.Series(np.arange(len(periods)), index=periods)
ts
"""
2011Q3    0
2011Q4    1
2012Q1    2
2012Q2    3
2012Q3    4
2012Q4    5
Freq: Q-JAN, dtype: int64
"""

periods.asfreq("D", "end")
"""
PeriodIndex(['2010-10-31', '2011-01-31', '2011-04-30', '2011-07-31', '2011-10-31', '2012-01-31'],
            dtype='period[D]')
"""

periods.asfreq("D", "end") - 1
"""
PeriodIndex(['2010-10-30', '2011-01-30', '2011-04-29', '2011-07-30', '2011-10-30', '2012-01-30'],
            dtype='period[D]')
"""

(periods.asfreq("D", "end") - 1).asfreq("h", "start")
"""
PeriodIndex(['2010-10-30 00:00', '2011-01-30 00:00', '2011-04-29 00:00',
             '2011-07-30 00:00', '2011-10-30 00:00', '2012-01-30 00:00'],
            dtype='period[h]')
"""

(periods.asfreq("D", "end") - 1).asfreq("h", "start") + 1
"""
PeriodIndex(['2010-10-30 01:00', '2011-01-30 01:00', '2011-04-29 01:00',
             '2011-07-30 01:00', '2011-10-30 01:00', '2012-01-30 01:00'],
            dtype='period[h]')
"""
```

Series and DataFrame objects indexed by timestamps can be converted to periods with the `to_period` method. While the frequency of the new PeriodIndex is inferred from the timestamps by default, you can specify any supported frequency. To convert back to timestamps, use the `to_timestamp` method, which returns a `DatetimeIndex`.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=3, freq="ME")
dates
# DatetimeIndex(['2000-01-31', '2000-02-29', '2000-03-31'], dtype='datetime64[ns]', freq='ME')

ts = pd.Series(np.random.standard_normal(3), index=dates)
ts
"""
2000-01-31    0.389436
2000-02-29   -0.492043
2000-03-31    0.011621
Freq: ME, dtype: float64
"""

pts = ts.to_period()
pts
"""
2000-01    0.389436
2000-02   -0.492043
2000-03    0.011621
Freq: M, dtype: float64
"""

ts.to_period("Q-DEC")
"""
2000Q1    0.389436
2000Q1   -0.492043
2000Q1    0.011621
Freq: Q-DEC, dtype: float64
"""

pts.to_timestamp(how="end")
"""
2000-01-31 23:59:59.999999999    0.389436
2000-02-29 23:59:59.999999999   -0.492043
2000-03-31 23:59:59.999999999    0.011621
dtype: float64
"""
```

We can set a dataframe that doesn't have a `PeriodIndex` to have one using the `pandas.PeriodIndex.from_fields` method. Here is an example, we change the index of a dataframe to have a `PeriodIndex`.

```py
import pandas as pd

data = pd.read_csv("examples/macrodata.csv")

print(data[["year", "quarter", "realgdp"]].head(5))
"""
   year  quarter   realgdp
0  1959        1  2710.349
1  1959        2  2778.801
2  1959        3  2775.488
3  1959        4  2785.204
4  1960        1  2847.699
"""

# create a PeriodIndex from the columns "year", and "quarter"
index = pd.PeriodIndex.from_fields(year=data["year"], quarter=data["quarter"], freq="Q-DEC")

# change the index of a dataframe
data.index = index

print(data[["year", "quarter", "realgdp"]].head(5))
"""
        year  quarter   realgdp
1959Q1  1959        1  2710.349
1959Q2  1959        2  2778.801
1959Q3  1959        3  2775.488
1959Q4  1959        4  2785.204
1960Q1  1960        1  2847.699
"""
```

### Resampling and Frequency Conversion

**Resampling** refers to the process of converting a time series from one frequency to another. Aggregating higher frequency data to lower frequency is called **downsampling**, while converting lower frequency to higher frequency is called **upsampling**.

`pandas` objects are equipped with a `resample` method, which is the workhorse function for all frequency conversion. `resample` has a similar API to `groupby`; you call `resample` to group the data, then call an aggregation function:

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=100)
ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)

ts.resample("ME").mean()
"""
2000-01-31    0.161922
2000-02-29    0.178505
2000-03-31   -0.104694
2000-04-30   -0.913025
Freq: ME, dtype: float64
"""

ts.resample("QE-JAN").mean()
"""
2000-01-31    0.161922
2000-04-30   -0.091103
Freq: QE-JAN, dtype: float64
"""
```

`resample` is a flexible method that can be used to process large time series. Here is a summary of `resample` method arguments.

| Argument      | Description                                                                                                                                                                                           |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rule`        | String, DateOffset, or timedelta indicating desired resampled frequency (for example, `"M"`, `"5min"`, or `Second(15)`)                                                                               |
| `axis`        | Axis to resample on; default `axis=0`                                                                                                                                                                 |
| `fill_method` | How to interpolate when upsampling, as in `"ffill"` or `"bfill"`; by default does no interpolation                                                                                                    |
| `closed`      | In downsampling, which end of each interval is closed (inclusive), `"right"` or `"left"`                                                                                                              |
| `label`       | In downsampling, how to label the aggregated result, with the `"right"` or `"left"` bin edge (e.g., the 9:30 to 9:35 five-minute interval could be labeled `9:30` or `9:35`)                          |
| `limit`       | When forward or backward filling, the maximum number of periods to fill                                                                                                                               |
| `convention`  | When resampling periods, the convention (`"start"` or `"end"`) for converting the low-frequency period to high frequency; defaults to `"start"`                                                       |
| `origin`      | The "base" timestamp from which to determine the resampling bin edges; can also be one of `"epoch"`, `"start"`, `"start_day"`, `"end"`, or `"end_day"`; see the `resample` docstring for full details |
| `offset`      | An offset timedelta added to the origin; defaults to `None`                                                                                                                                           |

#### Downsampling

Here is an example of downsampling.

- We'll create a date range with a minute frequency.
- We'll create a time series data using the created date range.
- Then, we'll resample the time series from 1-minute frequency to 5-minute one. Our aggregation function for the resampling will be the `sum`.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min").sum()
"""
2000-01-01 00:00:00    10
2000-01-01 00:05:00    35
2000-01-01 00:10:00    21
Freq: 5min, dtype: int64
"""
```

The frequency you pass defines bin edges in five-minute increments. For this frequency, by default the left bin edge is inclusive, so the 00:00 value is included in the 00:00 to 00:05 interval, and the 00:05 value is excluded from that interval.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min").sum()
"""
2000-01-01 00:00:00    10
2000-01-01 00:05:00    35
2000-01-01 00:10:00    21
Freq: 5min, dtype: int64
"""

ts.resample("5min", closed="right").sum()
"""
1999-12-31 23:55:00     0
2000-01-01 00:00:00    15
2000-01-01 00:05:00    40
2000-01-01 00:10:00    11
Freq: 5min, dtype: int64
"""
```

The resulting time series is labeled by the timestamps from the left side of each bin. By passing label="right" you can label them with the right bin edge:

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min", closed="right").sum()
"""
1999-12-31 23:55:00     0
2000-01-01 00:00:00    15
2000-01-01 00:05:00    40
2000-01-01 00:10:00    11
Freq: 5min, dtype: int64
"""

ts.resample("5min", closed="right", label="right").sum()
"""
2000-01-01 00:00:00     0
2000-01-01 00:05:00    15
2000-01-01 00:10:00    40
2000-01-01 00:15:00    11
Freq: 5min, dtype: int64
"""
```

Lastly, you might want to shift the result index by some amount, say subtracting one second from the right edge to make it more clear which interval the timestamp refers to.

```py
import pandas as pd
from pandas.tseries.frequencies import to_offset

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

result = ts.resample("5min", closed="right", label="right").sum()
result
"""
2000-01-01 00:00:00     0
2000-01-01 00:05:00    15
2000-01-01 00:10:00    40
2000-01-01 00:15:00    11
Freq: 5min, dtype: int64
"""

result.index = result.index + to_offset("-1s")
result
"""
1999-12-31 23:59:59     0
2000-01-01 00:04:59    15
2000-01-01 00:09:59    40
2000-01-01 00:14:59    11
Freq: 5min, dtype: int64
"""
```

A popular way to aggregate a time series is to compute four values for each bucket: the first (open), last (close), maximum (high), and minimal (low) values. By using the `ohlc` aggregate function, you will obtain a DataFrame having columns containing these four aggregates.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts.resample("5min").ohlc()
"""
                     open  high  low  close
2000-01-01 00:00:00     7    11    0     10
2000-01-01 00:05:00     3     8    2      8
2000-01-01 00:10:00     1     9    1      9
"""
```

#### Upsampling and Interpolation

Upsampling is converting from a lower frequency to a higher frequency, where no aggregation is needed. We use the `asfreq` method to convert to the higher frequency without any aggregation:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""
```

Suppose you wanted to fill forward each weekly value on the non-Wednesdays. The same filling or interpolation methods available in the `fillna` and `reindex` methods are available for resampling:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("D").ffill())
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-07  1.962125  0.288492  0.143442  0.785525
2000-01-08  1.962125  0.288492  0.143442  0.785525
2000-01-09  1.962125  0.288492  0.143442  0.785525
2000-01-10  1.962125  0.288492  0.143442  0.785525
2000-01-11  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("D").ffill(limit=2))
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-07  1.962125  0.288492  0.143442  0.785525
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""
```

Notably, the new date index need not coincide with the old one at all:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("W-THU").ffill())
"""
            Colorado     Texas  New York      Ohio
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-13  1.432357 -1.841665  1.317754 -2.983131
"""
```

#### Grouped Time Resampling

Suppose that a DataFrame contains multiple time series, marked by an additional group key column. To do the same resampling for each value of "key", we introduce the `pandas.Grouper` object.

```py
import numpy as np
import pandas as pd

times = pd.date_range("2017-05-20 00:00", freq="1min", periods=15)

df = pd.DataFrame({
  "time": times.repeat(3),
  "key": np.tile(["a", "b", "c"], 15),
  "value": np.arange(45)
})

print(df.head())
"""
                 time key  value
0 2017-05-20 00:00:00   a      0
1 2017-05-20 00:00:00   b      1
2 2017-05-20 00:00:00   c      2
3 2017-05-20 00:01:00   a      3
4 2017-05-20 00:01:00   b      4
"""

time_key = pd.Grouper(freq="5min")

resampled = (df.set_index("time")
             .groupby(["key", time_key])
             .sum())

print(resampled)
"""
                         value
key time
a   2017-05-20 00:00:00     30
    2017-05-20 00:05:00    105
    2017-05-20 00:10:00    180
b   2017-05-20 00:00:00     35
    2017-05-20 00:05:00    110
    2017-05-20 00:10:00    185
c   2017-05-20 00:00:00     40
    2017-05-20 00:05:00    115
    2017-05-20 00:10:00    190
"""
```

One constraint with using `pandas.Grouper` is that the time must be the index of the Series or DataFrame.

<hr>
<hr>

## Introduction to Modeling Libraries in Python

https://wesmckinney.com/book/modeling
