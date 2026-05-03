# Accessing and Retrieving data from a series and a dataframe

- [Accessing and Retrieving data from a series and a dataframe](#accessing-and-retrieving-data-from-a-series-and-a-dataframe)
  - [Retrieving the array of items and index labels from a series](#retrieving-the-array-of-items-and-index-labels-from-a-series)
  - [Retrieving a list of columns and the index labels from a dataframe](#retrieving-a-list-of-columns-and-the-index-labels-from-a-dataframe)
  - [Retrieving the items from a series](#retrieving-the-items-from-a-series)
  - [Retrieving the items from a dataframe](#retrieving-the-items-from-a-dataframe)
    - [Retrieving the data of the columns of a dataframe](#retrieving-the-data-of-the-columns-of-a-dataframe)
    - [Retrieving the data of several columns of a dataframe](#retrieving-the-data-of-several-columns-of-a-dataframe)
    - [Accessing the items in rows of a dataframe](#accessing-the-items-in-rows-of-a-dataframe)
    - [`loc` and `iloc` operators](#loc-and-iloc-operators)
      - [Retrieving data from a series using the `loc` and `iloc`](#retrieving-data-from-a-series-using-the-loc-and-iloc)
      - [Retrieving data from rows of a dataframe using the `loc` and `iloc` operators](#retrieving-data-from-rows-of-a-dataframe-using-the-loc-and-iloc-operators)
      - [Retrieving the columns of a dataframe using the `loc` and `iloc` operators](#retrieving-the-columns-of-a-dataframe-using-the-loc-and-iloc-operators)
  - [Retrieving a single value using the `at` operator](#retrieving-a-single-value-using-the-at-operator)
  - [Retrieving the data as a copy from series or dataframe using the `take` method](#retrieving-the-data-as-a-copy-from-series-or-dataframe-using-the-take-method)
  - [Retrieving top and bottom rows of a dataframe with `head` and `tail`](#retrieving-top-and-bottom-rows-of-a-dataframe-with-head-and-tail)
  - [Retrieving the rows of a dataframe with the largest values](#retrieving-the-rows-of-a-dataframe-with-the-largest-values)
  - [Retrieving a random sample from a dataframe](#retrieving-a-random-sample-from-a-dataframe)
    - [`numpy.random.permutation` with `iloc`](#numpyrandompermutation-with-iloc)
    - [`numpy.random.permutation` with `pandas.DataFrame.take`](#numpyrandompermutation-with-pandasdataframetake)
    - [`pandas.DataFrame.sample`](#pandasdataframesample)
    - [Retrieving data from a dataframe based on data types](#retrieving-data-from-a-dataframe-based-on-data-types)

---

---

## Retrieving the array of items and index labels from a series

We can get the array representation of series using the `array` attribute. To get the indices, we can use the `index` attribute:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103])
print(ser.array)
"""
<NumpyExtensionArray>
[np.int64(100), np.int64(101), np.int64(102), np.int64(103)]
Length: 4, dtype: int64
"""

print(ser.index)
# RangeIndex(start=0, stop=4, step=1)
```

---

---

## Retrieving a list of columns and the index labels from a dataframe

We can retrieve the list of columns and the index label in a DataFrame with the `columns` and `index` attributes. They return an index object:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns)
# Index(['Istanbul', 'Baku', 'Tashkent', 'Karbala'], dtype='object')

print(df.index)
# Index([2020, 2021, 2022], dtype='int64')
```

Sometimes one wants direct access to the data, not to the DataFrame. This can be achieved with `<df>.values`

---

---

## Retrieving the items from a series

We can use the index labels with the square bracket notation to refer to items in a series:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], ["d", "b", "a", "c"])
print(ser["a"]) # 102
```

If we want to retrieve more than one item from a series, we need to use the index labels with double square brackets. The result itself will be a series object:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], ["d", "b", "a", "c"])

print(ser["a"]) # 102
print(ser[["c", "a", "d"]])
"""
c    103
a    102
d    100
dtype: int64
"""
```

---

---

## Retrieving the items from a dataframe

### Retrieving the data of the columns of a dataframe

A column in a DataFrame can be retrieved as a Series either by using `frame["column"]` or `frame.column` syntax.

- `frame["column"]` works for any column name,
- but `frame.column` works only when the column name is a valid Python variable name and does not conflict with any of the method names in a `DataFrame`. For example, if a column name contains whitespace or symbols other than underscores, it cannot be accessed with the dot attribute method.

Here is an example of retrieving the data in the specific columns of a dataframe:

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

print(df["Name"])
"""
0       Aisu
1      Temir
2    Gulnara
3     Azamat
4    Dilyara
5     Fatima
6      Aydin
7       Oğuz
8      Asgar
9     Gulzar
Name: Name, dtype: object
"""

print(df.Name)
"""
0       Aisu
1      Temir
2    Gulnara
3     Azamat
4    Dilyara
5     Fatima
6      Aydin
7       Oğuz
8      Asgar
9     Gulzar
Name: Name, dtype: object
"""
```

---

### Retrieving the data of several columns of a dataframe

We can also retrieve the data from more than one column. For this, we need to use 2 square brackets:

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
print(df[["Name", "Age"]])
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
5   Fatima  22.0
6    Aydin  28.0
7     Oğuz   NaN
8    Asgar  30.0
9   Gulzar  24.0
"""
```

String methods can also help us in selecting columns of a dataframe:

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
print(df[["Name"] + [col for col in df.columns if col.startswith("S")]])
"""
      Name    Salary
0     Aisu  60000.50
1    Temir  72000.75
2  Gulnara  55000.00
3   Azamat       NaN
4  Dilyara  75000.10
5   Fatima  50000.00
6    Aydin  68000.50
7     Oğuz  62000.00
8    Asgar       NaN
9   Gulzar  90000.00
"""
```

---

### Accessing the items in rows of a dataframe

Here is an example of retrieving rows of data in a dataframe:

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

print(df[:2])
"""
    Name   Age     City    Salary Is_Employed
0   Aisu  27.0   Almaty  60000.50         Yes
1  Temir  31.0  Bishkek  72000.75          No
"""
```

---

### `loc` and `iloc` operators

#### Retrieving data from a series using the `loc` and `iloc`

The preferred way to select index values is with the special `loc` operator:

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

print(ser["b"]) # 1.0
print(ser.loc["b"]) # 1.0
```

The `loc` operator uses the index labels, but we can also use the index numbers. The `iloc` operator indexes exclusively with integers:

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

print(ser["b"]) # 1
print(ser.loc["b"]) # 1

print(ser.iloc[1]) # 1
```

#### Retrieving data from rows of a dataframe using the `loc` and `iloc` operators

Just like with a series, rows of a dataframe can be retrieved by position or name with the special `iloc` and `loc` attributes:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021])
"""
Istanbul    15.52
Baku         2.25
Tashkent     2.52
Karbala      1.02
Name: 2021, dtype: float64
"""

print(df.iloc[1])
"""
Istanbul    15.52
Baku         2.25
Tashkent     2.52
Karbala      1.02
Name: 2021, dtype: float64
"""
```

If we want to get the data in more than one row, we need to use 2 square brackets with `iloc` and `loc`:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[[2021, 2022]])
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

print(df.iloc[[1, 2]])
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

#### Retrieving the columns of a dataframe using the `loc` and `iloc` operators

The result of selecting a single row is a Series with an index that contains the DataFrame's column labels. When we use `loc` and `iloc` to retrieve more than one row, we get back another dataframe. This means that we can retrieve the columns of this returned dataframe, as well. In the below example, we are retrieving the `Baku` column of the returned dataframe. Note that with `iloc`, we cannot specify the column name and instead we need to use column number, as `iloc` uses integers to refer to rows and columns.

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[[2021, 2022], "Baku"])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""

print(df.iloc[[1, 2], 1])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""
```

We can implement the index slicing with the `loc` and `iloc` operators:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021:2022, "Baku"])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""

print(df.iloc[1:3, 1])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""
```

When we use the `loc` and `iloc`, we can also use the index slicing for columns:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021:2022, "Istanbul":"Tashkent"])
"""
      Istanbul  Baku  Tashkent
2021     15.52  2.25      2.52
2022     15.60  2.27       NaN
"""

print(df.iloc[1:3, 0:3])
"""
      Istanbul  Baku  Tashkent
2021     15.52  2.25      2.52
2022     15.60  2.27       NaN
"""
```

---

---

## Retrieving a single value using the `at` operator

If we want to retrieve or change a single value in a series or a dataframe, we can use the `at` operator. This is used more to change a value rather than retrieving data:

```py
import pandas as pd

ser = pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser.at["b"]) # 1
```

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.at[2021, "Baku"]) # 2.25
```

`iat` is the version of `at` that uses only integers to refer to rows and columns (similar to `iloc`).

---

---

## Retrieving the data as a copy from series or dataframe using the `take` method

`pandas.DataFrame.take` returns the copy of elements in the given row and columns:

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

print(df.take([1, 4]))
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

We may retrieve the copy of items using negative integers, starting from the end of the object:

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


print(df.take([-1]))
"""
     Name   Age      City   Salary Is_Employed
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

By invoking `take` with `axis="columns"`, we could also select the columns:

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

print(df.take([0, 2], axis="columns"))
"""
      Name      City
0     Aisu    Almaty
1    Temir   Bishkek
2  Gulnara  Tashkent
3   Azamat    Astana
4  Dilyara       NaN
5   Fatima     Kazan
6    Aydin  Istanbul
7     Oğuz    Ankara
8    Asgar      Baku
9   Gulzar  Ashgabat
"""
```

---

---

## Retrieving top and bottom rows of a dataframe with `head` and `tail`

If we have a large DataFrame, we can use the `head` method on the DataFrame instance, to select the first 5 rows:

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
print(df.head())
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana       NaN          No
4  Dilyara  34.0       NaN  75000.10         Yes
"""
```

If we want to see specific number of rows, we can specify the number of rows to be outputted with the `head` method:

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

# show 2 rows
print(df.head(2))
"""
    Name   Age     City    Salary Is_Employed
0   Aisu  27.0   Almaty  60000.50         Yes
1  Temir  31.0  Bishkek  72000.75          No
"""
```

Similarly, the `tail` method returns the last five rows:

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

print(df.tail())
"""
     Name   Age      City   Salary Is_Employed
5  Fatima  22.0     Kazan  50000.0          No
6   Aydin  28.0  Istanbul  68000.5         NaN
7    Oğuz   NaN    Ankara  62000.0         Yes
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""

print(df.tail(2))
"""
     Name   Age      City   Salary Is_Employed
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

---

---

## Retrieving the rows of a dataframe with the largest values

If we want to see the largest values in a column of a dataframe, we can use the `nlargest` method:

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

print(df["Age"].nlargest(3))
"""
4    34.0
1    31.0
8    30.0
Name: Age, dtype: float64
"""
```

The above use the of `nlargest` method showed the largest values for a specific column. If we want to retrieve the largest values for a column, but see all the columns in a dataframe, we can use the `nlargest` method in a slightly different way:

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

print(df.nlargest(3, "Age"))
"""
      Name   Age     City    Salary Is_Employed
4  Dilyara  34.0      NaN  75000.10         Yes
1    Temir  31.0  Bishkek  72000.75          No
8    Asgar  30.0     Baku       NaN          No
"""
```

Similarly, for the smallest values in a dataframe, we can use the `nsmallest` method:

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

print(df.nsmallest(3, "Age"))
"""
     Name   Age      City   Salary Is_Employed
5  Fatima  22.0     Kazan  50000.0          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
0    Aisu  27.0    Almaty  60000.5         Yes
"""
```

---

---

## Retrieving a random sample from a dataframe

### `numpy.random.permutation` with `iloc`

The `numpy.random.permutation` method randomly permutes a sequence, or returns a permuted range. We can use it together with `iloc` to randomly reorder a series or the rows in a dataframe.

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

df = pd.DataFrame(dictionaryForDataFrame)

sampler = np.random.permutation(5)
print(sampler) # [4 2 0 3 1]

print(df.iloc[sampler])
"""
      Name   Age      City    Salary Is_Employed
4  Dilyara  34.0       NaN  75000.10         Yes
2  Gulnara   NaN  Tashkent  55000.00         Yes
0     Aisu  27.0    Almaty  60000.50         Yes
3   Azamat  29.0    Astana       NaN          No
1    Temir  31.0   Bishkek  72000.75          No
"""
```

---

### `numpy.random.permutation` with `pandas.DataFrame.take`

We can use the `numpy.random.permutation` method with the `pandas.DataFrame.take` method as well:

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

sampler = np.random.permutation(5)
print(sampler) # [4 2 0 3 1]

print(df.take(sampler))
"""
      Name   Age      City    Salary Is_Employed
4  Dilyara  34.0       NaN  75000.10         Yes
2  Gulnara   NaN  Tashkent  55000.00         Yes
0     Aisu  27.0    Almaty  60000.50         Yes
3   Azamat  29.0    Astana       NaN          No
1    Temir  31.0   Bishkek  72000.75          No
"""
```

---

### `pandas.DataFrame.sample`

To select a random subset without replacement (the same row cannot appear twice), you can use the `sample` method on series and dataframe:

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

print(df.sample(n=3))
"""
      Name   Age    City   Salary Is_Employed
4  Dilyara  34.0     NaN  75000.1         Yes
3   Azamat  29.0  Astana      NaN          No
8    Asgar  30.0    Baku      NaN          No
"""

print(df.sample(n=3))
"""
    Name   Age      City   Salary Is_Employed
7   Oğuz   NaN    Ankara  62000.0         Yes
0   Aisu  27.0    Almaty  60000.5         Yes
6  Aydin  28.0  Istanbul  68000.5         NaN
"""
```

To generate a sample with replacement (to allow repeat choices), pass `replace=True` to `sample`:

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

print(df.sample(n=6, replace=True))
"""
     Name   Age      City   Salary Is_Employed
8   Asgar  30.0      Baku      NaN          No
6   Aydin  28.0  Istanbul  68000.5         NaN
7    Oğuz   NaN    Ankara  62000.0         Yes
3  Azamat  29.0    Astana      NaN          No
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

---

### Retrieving data from a dataframe based on data types

To retrieve data from a dataframe based on data dtypes, we use `select_dtypes`:

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
print(
  df.dtypes
)
"""
Name            object
Age            float64
City            object
Salary         float64
Is_Employed     object
dtype: object
"""

print(
  df.select_dtypes(include="number")
)
"""
    Age    Salary
0  27.0  60000.50
1  31.0  72000.75
2   NaN  55000.00
3  29.0       NaN
4  34.0  75000.10
5  22.0  50000.00
6  28.0  68000.50
7   NaN  62000.00
8  30.0       NaN
9  24.0  90000.00
"""
```

---

---
