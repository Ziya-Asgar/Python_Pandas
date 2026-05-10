# Descriptive Statistical Methods

- [Descriptive Statistical Methods](#descriptive-statistical-methods)
  - [Table of some statistical methods](#table-of-some-statistical-methods)
  - [| `pct_change` | Compute percent changes |](#-pct_change--------compute-percent-changes------------------------------------------------------------------------------------------------------------)
  - [`sum`](#sum)
  - [`mean`](#mean)
  - [`describe`](#describe)
  - [`info`](#info)
  - [Unique Values, Value Counts](#unique-values-value-counts)
    - [`unique`](#unique)
    - [`value_counts`](#value_counts)

---

---

## Table of some statistical methods

There are many descriptive and summary statistics methods in pandas:

| Method             | Description                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| `count`            | Number of non-NA values                                                                                                            |
| `describe`         | Compute set of summary statistics                                                                                                  |
| `min, max`         | Compute minimum and maximum values                                                                                                 |
| `argmin`, `argmax` | Compute index locations (integers) at which minimum or maximum value is obtained, respectively; not available on DataFrame objects |
| `idxmin`, `idxmax` | Compute index labels at which minimum or maximum value is obtained, respectively                                                   |
| `quantile`         | Compute sample quantile ranging from 0 to 1 (default: 0.5)                                                                         |
| `sum`              | Sum of values                                                                                                                      |
| `mean`             | Mean of values                                                                                                                     |
| `median`           | Arithmetic median (50% quantile) of values                                                                                         |
| `mad`              | Mean absolute deviation from mean value                                                                                            |
| `prod`             | Product of all values                                                                                                              |
| `var`              | Sample variance of values                                                                                                          |
| `std`              | Sample standard deviation of values                                                                                                |
| `skew`             | Sample skewness (third moment) of values                                                                                           |
| `kurt`             | Sample kurtosis (fourth moment) of values                                                                                          |
| `cumsum`           | Cumulative sum of values                                                                                                           |
| `cummin`, `cummax` | Cumulative minimum or maximum of values, respectively                                                                              |
| `cumprod`          | Cumulative product of values                                                                                                       |
| `diff`             | Compute first arithmetic difference (useful for time series)                                                                       |
| `pct_change`       | Compute percent changes                                                                                                            |

---

---

## `sum`

Calling dataframe’s `sum` method returns a series containing column sums:

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

print(df.sum())
"""
Istanbul    46.58
Baku         6.75
Tashkent     5.02
Karbala      3.06
dtype: float64
"""
```

Passing `axis="columns"` or `axis=1` sums across the columns instead:

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

print(df.sum(axis="columns"))
"""
2020    21.19
2021    21.31
2022    18.91
dtype: float64
"""

print(df.sum(axis=1))
"""
2020    21.19
2021    21.31
2022    18.91
dtype: float64
"""
```

If there is any missing value (`NaN`), by default `sum` accepts them as zero. However, we can change this by using `skipna=False`:

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

print(df.sum(axis="index", skipna=False))
"""
Istanbul    46.58
Baku         6.75
Tashkent      NaN
Karbala      3.06
dtype: float64
"""

print(df.sum(axis="columns", skipna=False))
"""
2020    21.19
2021    21.31
2022      NaN
dtype: float64
"""
```

---

---

## `mean`

Some aggregations, like `mean`, require at least one non-NA value to yield a value result, so here we have:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df["newCol"] = None

print(df)
"""
      Istanbul  Baku  Tashkent  Karbala newCol
2020     15.46  2.23      2.50     1.00   None
2021     15.52  2.25      2.52     1.02   None
2022     15.60  2.27       NaN     1.04   None
"""

print(df.mean())
"""
Istanbul    15.526667
Baku             2.25
Tashkent         2.51
Karbala          1.02
newCol            NaN
dtype: objec
"""
```

---

---

## `describe`

`describe` produces multiple summary statistics:

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

print(df.describe())
"""
        Istanbul  Baku  Tashkent  Karbala
count   3.000000  3.00  2.000000     3.00
mean   15.526667  2.25  2.510000     1.02
std     0.070238  0.02  0.014142     0.02
min    15.460000  2.23  2.500000     1.00
25%    15.490000  2.24  2.505000     1.01
50%    15.520000  2.25  2.510000     1.02
75%    15.560000  2.26  2.515000     1.03
max    15.600000  2.27  2.520000     1.04
"""
```

If we want different percentiles, we can pass them in with the percentiles argument. For example, if we wanted only the 5th and 95th percentiles, we would run `df.describe(percentiles=[0.05, 0.95])`.

If we want the summary statistics for columns with the specific data type, we can use the `include` option of the `describe` method. For example, by default, `describe()` won't give us any information about the columns of the type object, but we can either provide `include='all'` as an argument or run it separately with `include=object`.

The `describe()` method only gives us summary statistics for non-null values. This means that, if we had 100 rows and half of our data was null, then the average would be calculated as the sum of the 50 non-null rows divided by 50.

On nonnumeric data, `describe` produces alternative summary statistics:

```py
import numpy as np
import pandas as pd

ser = pd.Series(["a", "a", "b", "c"] * 4)

print(ser.describe())
"""
count     16
unique     3
top        a
freq       8
dtype: object
"""
```

---

---

## `info`

The `info()` method also shows some statistics about the data.

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

print(df.info())
"""
<class 'pandas.core.frame.DataFrame'>
Index: 3 entries, 2020 to 2022
Data columns (total 4 columns):
 #   Column    Non-Null Count  Dtype
---  ------    --------------  -----
 0   Istanbul  3 non-null      float64
 1   Baku      3 non-null      float64
 2   Tashkent  2 non-null      float64
 3   Karbala   3 non-null      float64
dtypes: float64(4)
memory usage: 228.0 bytes
"""
```

---

---

## Unique Values, Value Counts

### `unique`

The `unique` method retrieves an array of the unique values from a Series:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.unique()) # ['c' 'a' 'd' 'b']
```

---

### `value_counts`

`value_counts` computes a Series containing value frequencies:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.value_counts())
"""
c    3
a    3
d    3
b    3
Name: count, dtype: int64
"""
```

If we want to see the value counts as percentage, we can use the `normalize=True` argument:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.value_counts(normalize=True))
"""
c    0.25
a    0.25
d    0.25
b    0.25
Name: proportion, dtype: float64
"""
```

The Series is sorted by value in descending order as a convenience. But we can undo that using `sort=False`:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "a", "a", "b", "b", "c", "c", "a", "a"])

print(ser.value_counts())
"""
a    5
c    3
b    2
d    1
Name: count, dtype: int64
"""

print(ser.value_counts(sort=False))
"""
c    3
a    5
d    1
b    2
Name: count, dtype: int64
"""
```

---

---
