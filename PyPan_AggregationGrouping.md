# Data Aggregation and Group Operations

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

---

---

The way the `groupby` method works is that we use it to split the data into groups, then we apply a function to the groups, and combine them into a result. This can be particularly useful in aggregating or summarizing data.

---

---

## Using `groupby` with a series

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

---

---

## Using `groupby` with a hierarchically indexed series

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

---

---

## Grouping using a dictionary

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

---

---

## Grouping using a function

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

---

---

## Using `groupby` with a dataframe

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

---

---

## Using `groupby` with a hierarchically indexed dataframe

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

---

---

## Group by columns

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

---

---

## Iterating over groups

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

---

---

## Data Aggregation

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

---

### Custom function for aggregation

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

---

### `pivot_table`

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

---

### Crosstab

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

---

---
