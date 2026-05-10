# Extension types (Accessors) in Pandas

- [Extension types (Accessors) in Pandas](#extension-types-accessors-in-pandas)
  - [Intro](#intro)
  - [`str`](#str)
  - [`dt`](#dt)
  - [`cat`](#cat)
    - [Table of categorical methods](#table-of-categorical-methods)
    - [Creating a series with `Categorical` data type](#creating-a-series-with-categorical-data-type)
    - [Specifying the ordered categories](#specifying-the-ordered-categories)
    - [Converting an unordered categorial to an ordered one](#converting-an-unordered-categorial-to-an-ordered-one)
    - [Converting a series with a different data type to a `Categorical` type](#converting-a-series-with-a-different-data-type-to-a-categorical-type)
    - [The `categories` attribute](#the-categories-attribute)
    - [The `codes` attribute](#the-codes-attribute)
    - [The `rename_categories` method](#the-rename_categories-method)
    - [The `add_categories` method](#the-add_categories-method)
    - [The `set_categories` method](#the-set_categories-method)

---

---

## Intro

There are methods in pandas that work only with specific data types. These methods are accessed through 4 accessors:

- `str`: String data type
- `cat`: Categorical data type
- `dt`: Datetime, Timedelta, Period data types
- `sparse`: Sparse data type

---

---

## `str`

`str` accessor provides methods to work with textual data.

The `upper` method turns all the letters to uppercase:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.upper())
"""
0         BAKU
1    KHANKENDI
2       SHUSHA
3     ISTANBUL
4       ANKARA
5        IZMIR
Name: city, dtype: object
"""
```

The `lower` method turns all the letters to lowercase:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.lower())
"""
0         baku
1    khankendi
2       shusha
3     istanbul
4       ankara
5        izmir
Name: city, dtype: object
"""
```

The `len` method returns the length of the strings in a series.

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.len())
"""
0    4
1    9
2    6
3    8
4    6
5    5
Name: city, dtype: int64
"""
```

`str` accessor allows to use indexing on strings:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str[:3])
"""
0    Bak
1    Kha
2    Shu
3    Ist
4    Ank
5    Izm
Name: city, dtype: object
"""
```

We can check if all characters are alphabetical with the `isalpha` method:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.isalpha())
"""
0    True
1    True
2    True
3    True
4    True
5    True
Name: city, dtype: bool
"""
```

The `split` method returns a series of lists:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s)
"""
0    a_b_c
1    c_d_e
2     <NA>
3    f_g_h
dtype: string
"""

print(s.str.split("_"))
"""
0    [a, b, c]
1    [c, d, e]
2         <NA>
3    [f, g, h]
dtype: object
"""
```

Elements in the split lists can be accessed using the `get` method or `[]` notation:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s.str.split("_"))
"""
0    [a, b, c]
1    [c, d, e]
2         <NA>
3    [f, g, h]
dtype: object
"""

print(s.str.split("_").str.get(1))
"""
0       b
1       d
2    <NA>
3       g
dtype: object
"""

print(s.str.split("_").str[1])
"""
0       b
1       d
2    <NA>
3       g
dtype: object
"""
```

We can use the `expand` option to return the output of `split` as a DataFrame:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s.str.split("_", expand=True))
"""
      0     1     2
0     a     b     c
1     c     d     e
2  <NA>  <NA>  <NA>
3     f     g     h
"""
```

It is also possible to limit the number of splits using the `n` option:

```py
s = pd.Series(["a_b_c_A", "c_d_e_A", np.nan, "f_g_h_A", "i_j_k_A"], dtype="string")

print(s)
"""
0    a_b_c_A
1    c_d_e_A
2       <NA>
3    f_g_h_A
4    i_j_k_A
dtype: string
"""

print(s.str.split("_", n=1))
"""
0    [a, b_c_A]
1    [c, d_e_A]
2          <NA>
3    [f, g_h_A]
4    [i, j_k_A]
dtype: object
"""

print(s.str.split("_", n=3))
"""
0    [a, b, c, A]
1    [c, d, e, A]
2            <NA>
3    [f, g, h, A]
4    [i, j, k, A]
dtype: object
"""
```

Regular expressions can be used with the `str` accessor as well.

---

---

## `dt`

`dt` accessor allows to extract many useful properties from datetime data. It also provides methods for manipulation.

We can extract year, month, or day from the dates by simply using `year`, `month`, and `day` properties.

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries)
"""
0   2024-08-10
1   2024-08-20
2   2024-08-30
3   2024-09-09
4   2024-09-19
dtype: datetime64[ns]
"""

print(dateSeries.dt.year)
"""
0    2024
1    2024
2    2024
3    2024
4    2024
dtype: int32
"""

print(dateSeries.dt.month)
"""
0    8
1    8
2    8
3    9
4    9
dtype: int32
"""

print(dateSeries.dt.day)
"""
0    10
1    20
2    30
3     9
4    19
dtype: int32
"""
```

The weekday of a date can be extracted using the `weekday` attribute. It starts from 0 (Monday) and goes up to 6 (Sunday).

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.weekday)
"""
0    5
1    1
2    4
3    0
4    3
dtype: int32
"""
```

We can access the week of the year using the `isocalendar` method:

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.isocalendar())
"""
   year  week  day
0  2024    32    6
1  2024    34    2
2  2024    35    5
3  2024    37    1
4  2024    38    4
"""

print(dateSeries.dt.isocalendar().week)
"""
0    32
1    34
2    35
3    37
4    38
Name: week, dtype: UInt32
"""
```

We are able to check if a date is start or end of a month, quarter, or year.

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.is_month_start)
"""
0    False
1    False
2    False
3    False
4    False
dtype: bool
"""

print(dateSeries.dt.is_quarter_start)
print(dateSeries.dt.is_year_start)

print(dateSeries.dt.is_month_end)
print(dateSeries.dt.is_quarter_end)
print(dateSeries.dt.is_year_end)
```

---

---

## `cat`

`cat` is the accessor for categorical data type. At times, it is more efficient to work with categorical data type than using the object data type. It makes a significant difference in terms of memory and speed especially when the data has low cardinality (i.e. number of categories is low compared to the number of observations).

---

### Table of categorical methods

Here is a table of categorical methods for series in pandas:

| Method                     | Description                                                                                         |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| `add_categories`           | Append new (unused) categories at end of existing categories                                        |
| `as_ordered`               | Make categories ordered                                                                             |
| `as_unordered`             | Make categories unordered                                                                           |
| `remove_categories`        | Remove categories, setting any removed values to null                                               |
| `remove_unused_categories` | Remove any category values that do not appear in the data                                           |
| `rename_categories`        | Replace categories with indicated set of new category names; cannot change the number of categories |
| `reorder_categories`       | Behaves like `rename_categories`, but can also change the result to have ordered categories         |
| `set_categories`           | Replace the categories with the indicated set of new categories; can add or remove categories       |

---

### Creating a series with `Categorical` data type

We can create a series with `Categorical` data type using the `dtype` argument:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""
```

Instead of series or dataframes with categorical data, we can create standalone categories using `pandas.Categorical`:

```py
import pandas as pd

my_categories = pd.Categorical(["test 1", "test 2", "test 3"])
print(my_categories)
"""
['test 1', 'test 2', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""
```

Another way is to use the `pandas.Categorical.from_codes` method:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

my_categories = pd.Categorical.from_codes(codes, categories)
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""
```

---

### Specifying the ordered categories

Unless explicitly specified, categorical conversions assume no specific ordering of the categories. So the `categories` array may be in a different order depending on the ordering of the input data. When using `from_codes` or any of the other constructors, you can indicate that the categories have a meaningful ordering:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

ordered_categories = pd.Categorical.from_codes(codes, categories, ordered=True)
print(ordered_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1' < 'test 2' < 'test 3']
"""
```

---

### Converting an unordered categorial to an ordered one

An unordered categorical instance can be made ordered with the `as_ordered` method:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

my_categories = pd.Categorical.from_codes(codes, categories)
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""

my_categories = my_categories.as_ordered()
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1' < 'test 2' < 'test 3']
"""
```

---

### Converting a series with a different data type to a `Categorical` type

In addition to `dtype` attribute and `pandas.Categorical.from_codes` method, there is also `astype` method, which can convert a series from one data type to another one. Thus, we can use it to convert a series with a different data type to a `Categorical` type:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"])
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: object
"""

ser = ser.astype("category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(type(ser.array)) # <class 'pandas.core.arrays.categorical.Categorical'>
```

---

### The `categories` attribute

The `Categorical` object has `categories` and `codes` attributes. We can check the categories using the `categories` attribute:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.categories)
# Index(['a', 'b', 'c', 'd'], dtype='object')
```

---

### The `codes` attribute

Each category also has an integer value associated with it. The integer values that reference the categories are called the category codes or simply codes. We can access them using the `codes` attribute.

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser.cat.codes)
"""
0    0
1    0
2    1
3    1
4    1
5    2
6    2
7    2
8    2
9    3
dtype: int8
"""
```

A useful trick to get a mapping between codes and categories is:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
dict(enumerate(ser.cat.categories)) # {0: 'a', 1: 'b', 2: 'c', 3: 'd'}
```

---

### The `rename_categories` method

We can rename the categories using the `rename_categories` method:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser.cat.categories) # Index(['a', 'b', 'c', 'd'], dtype='object')

print(ser.cat.rename_categories({"a": "A", "b": "B", "c": "C", "d":"D"}))
"""
0    A
1    A
2    B
3    B
4    B
5    C
6    C
7    C
8    C
9    D
dtype: category
Categories (4, object): ['A', 'B', 'C', 'D']
"""
```

---

### The `add_categories` method

When working with the category data type, the new values must be in one of the existing categories. We can add new categories, even if no data point belongs to that category yet, using the `add_categories` method:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.add_categories("e"))
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""
```

---

### The `set_categories` method

We can use the `set_categories` method to set, add, and change categories:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.set_categories(["a", "b", "c", "d", "e"]))
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""
```

In large datasets, categoricals are often used as a convenient tool for memory savings and better performance. After you filter a large dataframe or series, many of the categories may not appear in the data. To help with this, we can use the `remove_unused_categories` method to trim unobserved categories:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
ser = ser.cat.set_categories(["a", "b", "c", "d", "e"])

print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""

ser2 = ser[ser.isin(["a", "b"])]
print(ser2)
"""
0    a
1    a
2    b
3    b
4    b
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""

ser2 = ser2.cat.remove_unused_categories()
"""
0    a
1    a
2    b
3    b
4    b
dtype: category
Categories (2, object): ['a', 'b']
"""
```

---

---
