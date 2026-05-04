# Index Objects

- [Index Objects](#index-objects)
  - [Immutability of Index objects](#immutability-of-index-objects)
  - [Create a standalone index](#create-a-standalone-index)
  - [Names in a series](#names-in-a-series)
  - [Names in a dataframe](#names-in-a-dataframe)
  - [`set_names`](#set_names)
  - [Changing the index of a series](#changing-the-index-of-a-series)
  - [Changing the index of a dataframe](#changing-the-index-of-a-dataframe)
  - [Changing the column names of a dataframe](#changing-the-column-names-of-a-dataframe)
  - [Using the `rename` method for columns and index labels](#using-the-rename-method-for-columns-and-index-labels)
  - [Turning the column of a dataframe into the index labels](#turning-the-column-of-a-dataframe-into-the-index-labels)
  - [Set-like behaviour of Index objects](#set-like-behaviour-of-index-objects)
    - [Concatenate the index objects with the `append` method](#concatenate-the-index-objects-with-the-append-method)
    - [Find the differences between the index objects with the `difference` method](#find-the-differences-between-the-index-objects-with-the-difference-method)
    - [Find the common items in the index objects with the `intersection` method](#find-the-common-items-in-the-index-objects-with-the-intersection-method)
    - [Combine (without duplication) the index objects with the `union` method](#combine-without-duplication-the-index-objects-with-the-union-method)
    - [Delete the items in the index objects with the `delete` method](#delete-the-items-in-the-index-objects-with-the-delete-method)
    - [Delete the items in the index objects with the `drop` method](#delete-the-items-in-the-index-objects-with-the-drop-method)
    - [Insert elements into a specific position in the index using the `insert` method](#insert-elements-into-a-specific-position-in-the-index-using-the-insert-method)
    - [`is_unique`](#is_unique)
    - [`unique()`](#unique)
  - [Rearranging the indices with the `reindex` method](#rearranging-the-indices-with-the-reindex-method)
    - [Rearranging the indices of a series with `reindex`](#rearranging-the-indices-of-a-series-with-reindex)
    - [Rearranging the indices of a dataframe with `reindex`](#rearranging-the-indices-of-a-dataframe-with-reindex)
    - [Filling in missing values while using the `reindex` method](#filling-in-missing-values-while-using-the-reindex-method)
    - [Table of `reindex` arguments](#table-of-reindex-arguments)

---

---

`pandas`’s Index objects are responsible for holding the axis labels (including a DataFrame's column names) and other metadata. Any array or other sequence of labels you use when constructing a series or dataframe is internally converted to an Index object.

---

---

## Immutability of Index objects

Index objects are immutable and thus can’t be modified by the user:

```py
import pandas as pd

ser = pd.Series(np.arange(3), index=["a", "b", "c"])

print(ser)
"""
a    0
b    1
c    2
dtype: int64
"""

print(ser.index)
# Index(['a', 'b', 'c'], dtype='object')

print(ser.index[1]) # b
ser.index[1] = "d" # Error
```

---

---

## Create a standalone index

We can create an index object on its own and use it later on:

```py
import numpy as np
import pandas as pd

indexObj = pd.Index(np.arange(10, 14), name="numbers")
print(indexObj) # Index([10, 11, 12, 13], dtype='int64', name='numbers')

print(pd.Series(np.arange(1000, 1004), index=indexObj))
"""
numbers
10    1000
11    1001
12    1002
13    1003
dtype: int64
"""
```

---

---

## Names in a series

Both the series object itself and its index have a `name` attribute:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

ser.name = "population series"
ser.index.name = "cities_index"

print(ser)
"""
cities_index
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
Name: population series, dtype: float64
"""
```

---

---

## Names in a dataframe

DataFrame’s `index` and `columns` have their `name` attributes. DataFrame itself does not have a `name` attribute:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df.columns.name = "city"
df.index.name = "year"

print(df)
"""
city  Istanbul  Baku  Tashkent  Karbala
year
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

## `set_names`

The `set_names` method in the pandas library is used to set the names of the levels in an index:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df.columns = df.columns.set_names("city")
df.index = df.index.set_names("year")

print(df)
"""
city  Istanbul  Baku  Tashkent  Karbala
year
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

---

---

## Changing the index of a series

We can change the index labels of a series using the `index` attribute and reassignment:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103])
print(ser)
"""
0    100
1    101
2    102
3    103
dtype: int64
"""

ser.index = ["zeroth", "first", "second", "third"]
print(ser)
"""
zeroth    100
first     101
second    102
third     103
dtype: int64
"""
```

---

---

## Changing the index of a dataframe

We can change the index labels of a dataframe in the same way:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame)
print(df)
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana       NaN          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50         NaN
7     Oğuz   NaN    Ankara  62000.00         Yes
8    Asgar  30.0      Baku       NaN          No
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""

df.index = np.arange(100, 110)
print(df)
"""
        Name   Age      City    Salary Is_Employed
100     Aisu  27.0    Almaty  60000.50         Yes
101    Temir  31.0   Bishkek  72000.75          No
102  Gulnara   NaN  Tashkent  55000.00         Yes
103   Azamat  29.0    Astana       NaN          No
104  Dilyara  34.0       NaN  75000.10         Yes
105   Fatima  22.0     Kazan  50000.00          No
106    Aydin  28.0  Istanbul  68000.50         NaN
107     Oğuz   NaN    Ankara  62000.00         Yes
108    Asgar  30.0      Baku       NaN          No
109   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

We can also use the `map` method with the index object, to change the index labels in a custom way:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

def func(index):
  return index - 2000

df.index = df.index.map(func)
print(df)
"""
    Istanbul  Baku  Tashkent  Karbala
20     15.46  2.23      2.50     1.00
21     15.52  2.25      2.52     1.02
22     15.60  2.27       NaN     1.04
"""
```

---

---

## Changing the column names of a dataframe

To change the column names of a dataframe, we can use the `columns` attribute of a dataframe:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns) # Index(['Istanbul', 'Baku'], dtype='object')

df.columns = ["Ist", "Baku"]
print(df.columns) # Index(['Ist', 'Baku'], dtype='object')
```

---

---

## Using the `rename` method for columns and index labels

The above way of renaming columns would be more useful when we need to change all the column names or maybe most of it. However, if we want to rename specific columns, we can use the `rename` method:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns) # Index(['Istanbul', 'Baku', 'Tashkent', 'Karbala'], dtype='objec

df.rename(columns={"Istanbul":"Ist"}, inplace=True)
print(df.columns) # Index(['Ist', 'Baku', 'Tashkent', 'Karbala'], dtype='object')
```

The `rename` method can also change the index labels:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.index) # Index([2020, 2021, 2022], dtype='int64')

df.rename(index={2020:20, 2021:21}, inplace=True)
print(df.index) # Index([20, 21, 2022], dtype='int64')
```

The `rename` method, and many other operations that we are doing on a dataframe do not change the dataframe in place. They usually return a new dataframe. If we want the original dataframe to be changed by our operation, many methods accept the `inplace=True` argument, that we can use.

---

---

## Turning the column of a dataframe into the index labels

We turn a specific column of a dataframe into the index label column using the `set_index` method:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame)
print(df)
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana       NaN          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50         NaN
7     Oğuz   NaN    Ankara  62000.00         Yes
8    Asgar  30.0      Baku       NaN          No
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""

df.set_index("Name", inplace=True)
print(df)
"""
          Age      City    Salary Is_Employed
Name
Aisu     27.0    Almaty  60000.50         Yes
Temir    31.0   Bishkek  72000.75          No
Gulnara   NaN  Tashkent  55000.00         Yes
Azamat   29.0    Astana       NaN          No
Dilyara  34.0       NaN  75000.10         Yes
Fatima   22.0     Kazan  50000.00          No
Aydin    28.0  Istanbul  68000.50         NaN
Oğuz      NaN    Ankara  62000.00         Yes
Asgar    30.0      Baku       NaN          No
Gulzar   24.0  Ashgabat  90000.00         Yes
"""
```

If we want to revert the changes, we can use the `reset_index` method, which also accepts `inplace=True`.

---

---

## Set-like behaviour of Index objects

In addition to being array-like, an Index also behaves like a fixed-size set. However, unlike Python sets, a pandas Index can contain duplicate labels. Each Index has a number of methods and properties for set logic. Here are some of them:

| Method/Property  | Description                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------- |
| `append()`       | Concatenate with additional Index objects, producing a new Index                          |
| `difference()`   | Compute set difference as an Index                                                        |
| `intersection()` | Compute set intersection                                                                  |
| `union()`        | Compute set union                                                                         |
| `delete()`       | Compute new Index with element at Index i deleted                                         |
| `drop()`         | Compute new Index by deleting passed values                                               |
| `insert()`       | Compute new Index by inserting element at Index i                                         |
| `is_unique`      | Returns `True` if the Index has no duplicate values                                       |
| `unique()`       | Compute the array of unique values in the Index                                           |
| `isin()`         | Compute Boolean array indicating whether each value is contained in the passed collection |

---

### Concatenate the index objects with the `append` method

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(6))
print(ser)
"""
0    0
1    1
2    2
3    3
4    4
5    5
dtype: int64
"""

index1 = pd.Index(["a", "b", "c"])
index2 = pd.Index(["d", "e", "f"])

index1 # Index(['a', 'b', 'c'], dtype='object')
index2 # Index(['d', 'e', 'f'], dtype='object')

index1.append(index2) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')

ser.index = index1.append(index2)
print(ser)
"""
a    0
b    1
c    2
d    3
e    4
f    5
dtype: int64
"""
```

You can also append multiple Index objects at once:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(6))
print(ser)
"""
0    0
1    1
2    2
3    3
4    4
5    5
dtype: int64
"""

index1 = pd.Index(["a", "b"])
index2 = pd.Index(["c", "d"])
index3 = pd.Index(["e", "f"])

index1.append([index2, index3]) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')

ser.index = index1.append([index2, index3])
print(ser)
"""
a    0
b    1
c    2
d    3
e    4
f    5
dtype: int64
"""
```

---

### Find the differences between the index objects with the `difference` method

The `difference` method of the Pandas Index object is used to find the different elements between two Index objects.

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c"])

index1.difference(index2) # Index(['b', 'd'], dtype='object')
```

You can also find the difference between an Index and a list or set:

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])

index1.difference(["d", "e"]) # Index(['a', 'b', 'c'], dtype='object')
```

---

### Find the common items in the index objects with the `intersection` method

The `intersection` method of the Pandas Index object is used to find the common elements between two Index objects.

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c"])

index1.intersection(index2) # Index(['a', 'c'], dtype='object')
```

You can also find the intersection between an Index and a list or set:

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])

index1.intersection(["d", "a", "e"]) # Index(['a', 'd'], dtype='object')
```

---

### Combine (without duplication) the index objects with the `union` method

The `union` method of the Pandas Index object is used to combine two or more Index objects while removing any duplicate elements

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c", "e", "f"])

index1.union(index2) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')
```

You can also find the union between an Index and a list or set:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.union(["b", "e"]) # Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
```

---

### Delete the items in the index objects with the `delete` method

You can delete a single element by passing a single index value:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.delete(0) # Index(['b', 'c', 'd'], dtype='object')
```

You can also delete several elements by passing an array of index values:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.delete([0, 1]) # Index(['c', 'd'], dtype='object')
```

---

### Delete the items in the index objects with the `drop` method

The `drop` method of the Pandas Index object is used to remove specific elements from the Index by their labels. Here’s an example to illustrate how it works:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.drop("a") # Index(['b', 'c', 'd'], dtype='object')
```

You can also delete several elements by passing an array of index labels:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.drop(["a", "b"]) # Index(['c', 'd'], dtype='object')
```

---

### Insert elements into a specific position in the index using the `insert` method

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.insert(1, "a2") # Index(['a', 'a2', 'b', 'c', 'd'], dtype='object')
idx.insert([1], ["a2", "a3"]) # Index(['a', 'a2', 'a3', 'b', 'c', 'd'], dtype='object')
```

---

### `is_unique`

While many pandas functions (like `reindex`) require that the labels be unique, it’s not mandatory. The `is_unique` property of the index can tell you whether or not its labels are unique:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5), index=["a", "a", "b", "b", "c"])

print(ser)
"""
a    0
a    1
b    2
b    3
c    4
dtype: int64
"""

print(ser.index.is_unique) # False
```

Data selection is one of the main things that behaves differently with duplicates. Indexing a label with multiple entries returns a series, while single entries return a scalar value:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5), index=["a", "a", "b", "b", "c"])

print(ser["a"])
"""
a    0
a    1
dtype: int64
"""
print(ser["c"]) # 4
```

---

### `unique()`

The `unique()` method computes the array of unique values in the Index:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.is_unique # True
pd.Index(["a", "a", "b"]).is_unique # False
pd.Index(["a", "a", "b"]).unique() # Index(['a', 'b'], dtype='object')
```

---

---

## Rearranging the indices with the `reindex` method

### Rearranging the indices of a series with `reindex`

The `reindex` method creates a new object with the values rearranged to align with the new index:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["d", "b", "a", "c"])
print(ser)
"""
d    100
b    101
a    102
c    103
dtype: int64
"""

ser2 = ser.reindex(["a", "b", "c", "d", "e"])
print(ser2)
"""
a    102.0
b    101.0
c    103.0
d    100.0
e      NaN
dtype: float64
"""
```

---

### Rearranging the indices of a dataframe with `reindex`

The `reindex` method works on dataframes as well. It can alter indices (rows) and columns:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(index=[2022, 2021, 2020, 2019])
print(df2)
"""
      Baku  Istanbul  Bishkek
2022   6.0       7.0      8.0
2021   3.0       4.0      5.0
2020   0.0       1.0      2.0
2019   NaN       NaN      NaN
"""
```

The columns can be reindexed with the `columns` keyword:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(columns=["Baku", "Bishkek", "Istanbul", "Almati"])
print(df2)

print(df2)
"""
      Baku  Bishkek  Istanbul  Almati
2020     0        2         1     NaN
2021     3        5         4     NaN
2022     6        8         7     NaN
"""
```

Another way to reindex a particular axis is to use the `axis` keyword:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex([2022, 2021, 2020, 2019], axis="index")
print(df2)
"""
      Baku  Istanbul  Bishkek
2022   6.0       7.0      8.0
2021   3.0       4.0      5.0
2020   0.0       1.0      2.0
2019   NaN       NaN      NaN
"""
```

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(["Baku", "Bishkek", "Istanbul", "Almati"], axis="columns")

print(df2)
"""
      Baku  Bishkek  Istanbul  Almati
2020     0        2         1     NaN
2021     3        5         4     NaN
2022     6        8         7     NaN
"""
```

---

### Filling in missing values while using the `reindex` method

In the above example, when we added a new index, its value became `NaN`. Istead of `NaN`, we can use pandas to fill the data. In the below example, we are using the `method="ffill"`, forward fill. If there is a missing value, `method="ffill"` takes the value in the previous index and forwards it to the missing value's place:

```py
import numpy as np
import pandas as pd

ser = pd.Series(["blue", "purple", "yellow"], index=[0, 2, 4])
print(ser)
"""
0      blue
2    purple
4    yellow
dtype: object
"""

ser2 = ser.reindex(np.arange(6), method="ffill")
print(ser2)
"""
0      blue
1      blue
2    purple
3    purple
4    yellow
5    yellow
dtype: object
"""
```

`method="bfill"` takes the value in the next index and puts it back in the missing value's place.

```py
import numpy as np
import pandas as pd

ser = pd.Series(["blue", "purple", "yellow"], index=[0, 2, 4])
print(ser)
"""
0      blue
2    purple
4    yellow
dtype: object
"""

ser2 = ser.reindex(np.arange(6), method="bfill")
print(ser2)
"""
0      blue
1    purple
2    purple
3    yellow
4    yellow
5       NaN
dtype: object
"""
```

---

### Table of `reindex` arguments

Here is more information about `reindex` function arguments:

| Argument     | Description                                                                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `labels`     | New sequence to use as an index. Can be Index instance or any other sequence-like Python data structure. An Index will be used exactly as is without any copying.                     |
| `index`      | Use the passed sequence as the new index labels.                                                                                                                                      |
| `columns`    | Use the passed sequence as the new column labels.                                                                                                                                     |
| `axis`       | The axis to reindex, whether `"index"` (rows) or `"columns"`. The default is `"index"`. You can alternately do `reindex(index=new_labels)` or `reindex(columns=new_labels)`.          |
| `method`     | Interpolation (fill) method; `"ffill"` fills forward, while `"bfill"` fills backward.                                                                                                 |
| `fill_value` | Substitute value to use when introducing missing data by reindexing. Use `fill_value="missing"` (the default behavior) when you want absent labels to have null values in the result. |
| `limit`      | When forward filling or backfilling, the maximum size gap (in number of elements) to fill.                                                                                            |
| `tolerance`  | When forward filling or backfilling, the maximum size gap (in absolute numeric distance) to fill for inexact matches.                                                                 |
| `level`      | Match simple Index on level of `MultiIndex`; otherwise select subset of.                                                                                                              |
| `copy`       | If `True`, always copy underlying data even if the new index is equivalent to the old index; if `False`, do not copy the data when the indexes are equivalent.                        |

---

---
