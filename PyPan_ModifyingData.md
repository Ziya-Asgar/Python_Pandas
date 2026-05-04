# Modifying data in series and dataframes

- [Modifying data in series and dataframes](#modifying-data-in-series-and-dataframes)
  - [Copying series and dataframes](#copying-series-and-dataframes)
  - [Adding new values to a specific position in a series](#adding-new-values-to-a-specific-position-in-a-series)
  - [Adding new columns to a dataframe](#adding-new-columns-to-a-dataframe)
  - [Modifying values in a series](#modifying-values-in-a-series)
    - [Using `loc` and `iloc`](#using-loc-and-iloc)
    - [Using the `replace` method](#using-the-replace-method)
  - [Modifying values in the specific column of a dataframe](#modifying-values-in-the-specific-column-of-a-dataframe)
  - [Modifying values using `where`](#modifying-values-using-where)
  - [Dividing data into groups](#dividing-data-into-groups)
    - [Using the `cut` method](#using-the-cut-method)
    - [Using the `qcut` method](#using-the-qcut-method)
  - [Transposing a dataframe](#transposing-a-dataframe)

---

---

## Copying series and dataframes

We can use the `copy` method to return the copy of series and dataframes:

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

print(df.copy())
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

fruits = pd.Series(["apple", "banana", "orange"])
print(fruits)
"""
0     apple
1    banana
2    orange
dtype: object
"""

print(fruits.copy())
"""
0     apple
1    banana
2    orange
dtype: object
"""
```

By default, `df.copy()` makes a deep copy of the dataframe, which allows us to make changes to either the copy or the original without repercussions. If we pass in `deep=False`, we can obtain a shallow copy—changes to the shallow copy affect the original and vice versa. We will almost always want the deep copy, since we can change it without affecting the original.

---

---

## Adding new values to a specific position in a series

When you want to insert an element at a specific position in a series, you can use the `loc` with a fractional index and then sort and reset the indices.

```py
import pandas as pd

fruits = pd.Series(["apple", "banana", "orange"])
print(fruits)
"""
0     apple
1    banana
2    orange
dtype: object
"""

fruits[1.5] = "pear"
fruits = fruits.sort_index().reset_index(drop=True)

print(fruits)
"""
0     apple
1    banana
2      pear
3    orange
dtype: object
"""
```

---

---

## Adding new columns to a dataframe

We can easily add a column to a dataframe by assignment:

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

df["Total"] = df["Istanbul"]  + df["Baku"] + df["Tashkent"] + df["Karbala"]
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala  Total
2020     15.46  2.23      2.50     1.00  21.19
2021     15.52  2.25      2.52     1.02  21.31
2022     15.60  2.27       NaN     1.04    NaN
"""
```

In the above example, we summed the columns and assigned the summation to the `"Total"` column. But we don't necessarily have to use existing columns to create a new column by assignment. Here is an example of creating a new column in a dataframe by assinging a series object:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Age"])
ser = pd.Series([10, 20, 30], index=[2, 4, 5])

df["newCol"] = ser

print(df.head())
"""
      Name   Age  newCol
0     Aisu  27.0     NaN
1    Temir  31.0     NaN
2  Gulnara   NaN    10.0
3   Azamat  29.0     NaN
4  Dilyara  34.0    20.0
"""
```

The `assign` method is another way to add or replace a column. With the `assign` method, the arguments are the names of the columns we want to create (or overwrite), and the values are the data for the columns. Note that `assign` doesn't change our original dataframe; instead, it returns a new dataframe object with these columns added.

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Age"])
ser = pd.Series([10, 20, 30], index=[2, 4, 5])

df = df.assign(
  newCol = ser
)

print(df.head())
"""
      Name   Age  newCol
0     Aisu  27.0     NaN
1    Temir  31.0     NaN
2  Gulnara   NaN    10.0
3   Azamat  29.0     NaN
4  Dilyara  34.0    20.0
"""
```

The `assign` method also accepts lambda functions.

---

---

## Modifying values in a series

### Using `loc` and `iloc`

Assigning values using `loc` and `iloc` methods modifies the corresponding section of the Series:

```py
import numpy as np
import pandas as pd

ser =  pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
dtype: float64
"""

ser.loc["b":"c"] = 5
print(ser)
"""
a    0.0
b    5.0
c    5.0
d    3.0
dtype: float64
"""

ser.iloc[[0, 3]] = 10
print(ser)
"""
a    10.0
b     5.0
c     5.0
d    10.0
dtype: float64
"""
```

---

### Using the `replace` method

Another useful method that we can use to change the data in a series is to use the `replace` method. Here is a simple usage of it:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace(-999, np.nan))
"""
0       1.0
1       NaN
2       2.0
3       NaN
4   -1000.0
5       3.0
dtype: float64
"""
```

If we want to replace different values with a single value, we can use a list as the first argument, and a scalar value as the second argument:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace([-999, -1000], np.nan))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    NaN
5    3.0
dtype: float64
"""
```

If we want to replace different values with some other values, we can use a list as the first argument, and another list as the second argument:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace([-999, -1000], [np.nan, 0]))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    0.0
5    3.0
dtype: float64
"""
```

Instead of lists we can also use a dictionary, to indicate what values should be replaced with other values:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace({-999: np.nan, -1000:0}))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    0.0
5    3.0
dtype: float64
"""
```

Note that the `.replace` method is distinct from `.str.replace`, which performs element-wise string substitution

---

---

## Modifying values in the specific column of a dataframe

Columns can be modified as well. We could assign a scalar value or an array of values to a column of a dataframe:

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

df["Baku"] = 4
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46     4      2.50     1.00
2021     15.52     4      2.52     1.02
2022     15.60     4       NaN     1.04
"""
```

When we assign lists or arrays to a column, the value’s length must match the length of the DataFrame:

```py
import numpy as np
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Salary"])
df["Salary"] = np.arange(90, 100)
print(df.tail())
"""
     Name  Salary
5  Fatima      95
6   Aydin      96
7    Oğuz      97
8   Asgar      98
9  Gulzar      99
"""
```

If you change the data in a column by assigning a series, its labels will be realigned exactly to the DataFrame’s index, inserting missing values in any index values not present:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Age"])
ser = pd.Series([10, 20, 30], index=[1, 2, 3])

df["Age"] = ser
print(df.head())
"""
      Name   Age
0     Aisu   NaN
1    Temir  10.0
2  Gulnara  20.0
3   Azamat  30.0
4  Dilyara   NaN
"""
```

---

---

## Modifying values using `where`

The `where()` method in pandas is called on a series or a dataframe. It accepts a condition and a value after which it assigns the value to the series or the dataframe, when the condition is not met:

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

print(
  df.where(df < 2.5, "small")
)
"""
     Istanbul  Baku Tashkent  Karbala
2020    small  2.23    small     1.00
2021    small  2.25    small     1.02
2022    small  2.27    small     1.04
"""
```

---

---

## Dividing data into groups

### Using the `cut` method

Continuous data is often separated into bins for analysis. We can use the `cut` method to divide data into groups:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

age_categories = pd.cut(ages, bins)
print(age_categories)
"""
[(18, 25], (18, 25], (18, 25], (25, 35], (18, 25], ..., (25, 35], (60, 100], (35, 60], (35, 60], (25, 35]]
Length: 12
Categories (4, interval[int64, right]): [(18, 25] < (25, 35] < (35, 60] < (60, 100]]
"""
```

The `cut` method returns a special `Categorical` object. We can check the categories using the `categories` attribute and the codes for each category using the `codes` attribute:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

age_categories = pd.cut(ages, bins)

age_categories.categories
# IntervalIndex([(18, 25], (25, 35], (35, 60], (60, 100]], dtype='interval[int64, right]')

age_categories.codes
# array([0, 0, 0, 1, 0, 0, 2, 1, 3, 2, 2, 1], dtype=int8)

# bin counts
pd.Series(age_categories).value_counts()
"""
(18, 25]     5
(25, 35]     3
(35, 60]     3
(60, 100]    1
Name: count, dtype: int64
"""
```

Each bin is identified by a special (unique to pandas) interval value type, containing the lower and upper limit of each bin. A parenthesis means that the side is open (exclusive), while the square bracket means it is closed (inclusive). By default the right end is inclusive, but we can change that by passing `right=False`:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

pd.cut(ages, bins, right=False)
"""
[[18, 25), [18, 25), [25, 35), [25, 35), [18, 25), ..., [25, 35), [60, 100), [35, 60), [35, 60), [25, 35)]
Length: 12
Categories (4, interval[int64, left]): [[18, 25) < [25, 35) < [35, 60) < [60, 100)]
"""
```

The interval value points become the default label for the categorical group created by the `cut` method. We can override this using the `labels` option:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]
group_names = ["Youth", "YoungAdult", "MiddleAged", "Senior"]

pd.cut(ages, bins, labels=group_names)
"""
['Youth', 'Youth', 'Youth', 'YoungAdult', 'Youth', ..., 'YoungAdult', 'Senior', 'MiddleAged', 'MiddleAged', 'YoungAdult']
Length: 12
Categories (4, object): ['Youth' < 'YoungAdult' < 'MiddleAged' < 'Senior']
"""
```

If you pass an integer number of bins to the `cut` method instead of explicit bin edges, it will compute equal-length bins based on the minimum and maximum values in the data.

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
pd.cut(ages, 4, precision=2)
"""
[(19.96, 30.25], (19.96, 30.25], (19.96, 30.25], (19.96, 30.25], (19.96, 30.25], ..., (30.25, 40.5], (50.75, 61.0], (40.5, 50.75], (40.5, 50.75], (30.25, 40.5]]
Length: 12
Categories (4, interval[float64, right]): [(19.96, 30.25] < (30.25, 40.5] < (40.5, 50.75] < (50.75, 61.0]]
"""
```

The `precision=2` option limits the decimal precision to two digits.

---

### Using the `qcut` method

Depending on the distribution of the data, using `cut` will not usually result in each bin having the same number of data points. A closely related function, `qcut`, bins the data based on sample quantiles. Since `qcut` uses sample quantiles instead, you will obtain roughly equally sized bins:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]

quartiles = pd.qcut(ages, 4, precision=2)
print(quartiles)
"""
[(19.99, 22.75], (19.99, 22.75], (22.75, 29.0], (22.75, 29.0], (19.99, 22.75], ..., (29.0, 38.0], (38.0, 61.0], (38.0, 61.0], (38.0, 61.0], (29.0, 38.0]]
Length: 12
Categories (4, interval[float64, right]): [(19.99, 22.75] < (22.75, 29.0] < (29.0, 38.0] < (38.0, 61.0]]
"""

# Compare number of data points in each bin using qcut vs cut
print(pd.Series(pd.qcut(ages, 4, precision=2)).value_counts())
"""
(19.99, 22.75]    3
(22.75, 29.0]     3
(29.0, 38.0]      3
(38.0, 61.0]      3
Name: count, dtype: int64
"""

print(pd.Series(pd.cut(ages, 4, precision=2)).value_counts())
"""
(19.96, 30.25]    6
(30.25, 40.5]     3
(40.5, 50.75]     2
(50.75, 61.0]     1
Name: count, dtype: int64
"""
```

With the `qcut` method, we can pass our own quantiles (numbers between 0 and 1, inclusive):

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
print(pd.Series(pd.qcut(ages, [0, 0.1, 0.15, 0.5, 0.85, 0.9, 1.])).value_counts())
"""
(29.0, 42.4]      4
(21.65, 29.0]     4
(44.6, 61.0]      2
(19.999, 21.1]    2
(21.1, 21.65]     0
(42.4, 44.6]      0
Name: count, dtype: int64
"""
```

---

---

## Transposing a dataframe

We can transpose a dataframe (swap rows and columns) with similar syntax to a NumPy array. Note that transposing discards the column data types if the columns do not all have the same data type. So, transposing and then transposing back may lose the previous type information. The columns become arrays of pure Python objects in this case:

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

print(df.T)
"""
           2020   2021   2022
Istanbul  15.46  15.52  15.60
Baku       2.23   2.25   2.27
Tashkent   2.50   2.52    NaN
Karbala    1.00   1.02   1.04
"""
```

---

---
