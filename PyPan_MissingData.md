# Missing data

- [Missing data](#missing-data)
  - [Check for missing data in a series](#check-for-missing-data-in-a-series)
  - [Check for missing data in a dataframe](#check-for-missing-data-in-a-dataframe)
  - [`isnull()`](#isnull)
  - [Replacing missing values in a series](#replacing-missing-values-in-a-series)
  - [Replacing missing values in a dataframe](#replacing-missing-values-in-a-dataframe)
  - [Dropping the missing values in a series](#dropping-the-missing-values-in-a-series)
  - [Dropping the missing values in a dataframe](#dropping-the-missing-values-in-a-dataframe)

---

---

## Check for missing data in a series

We can check if data is missing or not using `isna` and `notna` pandas methods:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
dtype: float64
"""

print(pd.isna(ser))
"""
Istanbul      False
Baku          False
Tashkent       True
Nur-Sultan    False
dtype: bool
"""
```

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
dtype: float64
"""

print(pd.notna(ser))
"""
Istanbul       True
Baku           True
Tashkent      False
Nur-Sultan     True
dtype: bool
"""
```

The methods `isna` and `notna` are also available as instance methods:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser.notna())
"""
Istanbul       True
Baku           True
Tashkent      False
Nur-Sultan     True
dtype: bool
"""
```

---

---

## Check for missing data in a dataframe

Both methods, `isna` and `notna`, also work on dataframes:

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
print(df.isna())
"""
    Name    Age   City  Salary  Is_Employed
0  False  False  False   False        False
1  False  False  False   False        False
2  False   True  False   False        False
3  False  False  False    True        False
4  False  False   True   False        False
5  False  False  False   False        False
6  False  False  False   False         True
7  False   True  False   False        False
8  False  False  False    True        False
9  False  False  False   False        False
"""
```

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
print(df.notna())
"""
   Name    Age   City  Salary  Is_Employed
0  True   True   True    True         True
1  True   True   True    True         True
2  True  False   True    True         True
3  True   True   True   False         True
4  True   True  False    True         True
5  True   True   True    True         True
6  True   True   True    True        False
7  True  False   True    True         True
8  True   True   True   False         True
9  True   True   True    True         True
"""
```

---

---

## `isnull()`

The `isnull` method is used to detect missing or `NaN` values in a DataFrame or Series.

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
print(df.isnull())
# print(pd.isnull(df)) # This does the same thing
"""
   Name    Age   City  Salary  Is_Employed
0  True   True   True    True         True
1  True   True   True    True         True
2  True  False   True    True         True
3  True   True   True   False         True
4  True   True  False    True         True
5  True   True   True    True         True
6  True   True   True    True        False
7  True  False   True    True         True
8  True   True   True   False         True
9  True   True   True    True         True
"""
```

---

---

## Replacing missing values in a series

If we want to fill in a missing value, we can use the `fillna` method.

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
dtype: float64
"""

ser.fillna(100, inplace=True)
print(ser)
"""
Istanbul       15.0
Baku            5.0
Tashkent      100.0
Nur-Sultan     18.0
dtype: float64
"""
```

Just like we had `method=ffill` with the `reindex` method, we also have `ffill` and `bfill` methods. They take similar arguments as `reindex` takes. `ffill` forward fills, whereas `bfill` backfills missing values:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Karbala": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""

print(ser.ffill())
"""
Istanbul      15.0
Baku           5.0
Tashkent       5.0
Karbala        5.0
Nur-Sultan    18.0
dtype: float64
"""

print(ser.ffill(limit=1))
"""
Istanbul      15.0
Baku           5.0
Tashkent       5.0
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""
```

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Karbala": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""

print(ser.bfill())
"""
Istanbul      15.0
Baku           5.0
Tashkent      18.0
Karbala       18.0
Nur-Sultan    18.0
dtype: float64
"""

print(ser.bfill(limit=1))
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala       18.0
Nur-Sultan    18.0
dtype: float64
"""
```

---

---

## Replacing missing values in a dataframe

`fillna` method also works with dataframes:

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
print(df.fillna(10000))
"""
      Name      Age      City    Salary Is_Employed
0     Aisu     27.0    Almaty  60000.50         Yes
1    Temir     31.0   Bishkek  72000.75          No
2  Gulnara  10000.0  Tashkent  55000.00         Yes
3   Azamat     29.0    Astana  10000.00          No
4  Dilyara     34.0     10000  75000.10         Yes
5   Fatima     22.0     Kazan  50000.00          No
6    Aydin     28.0  Istanbul  68000.50       10000
7     Oğuz  10000.0    Ankara  62000.00         Yes
8    Asgar     30.0      Baku  10000.00          No
9   Gulzar     24.0  Ashgabat  90000.00         Yes
"""
```

Instead of replacing all the missing values with one value, we can specify different replacement values for different columns in a dataframe:

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
print(df.fillna({"Salary": 0, "Is_Employed": "No"}))
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana      0.00          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50          No
7     Oğuz   NaN    Ankara  62000.00         Yes
8    Asgar  30.0      Baku      0.00          No
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

---

---

## Dropping the missing values in a series

To drop the missing values from a series, we can use the `dropna` instance method. `dropna` gets rid of any rows where there is a missing value.

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
dtype: float64
"""

print(ser.dropna())
"""
Istanbul      15.0
Baku           5.0
Nur-Sultan    18.0
dtype: float64
"""
```

---

---

## Dropping the missing values in a dataframe

To drop the missing values from a dataframe, we can use the `dropna` method.

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

print(df.dropna())
"""
     Name   Age      City    Salary Is_Employed
0    Aisu  27.0    Almaty  60000.50         Yes
1   Temir  31.0   Bishkek  72000.75          No
5  Fatima  22.0     Kazan  50000.00          No
9  Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

By default `dropna` gets rid of any rows where there is a missing value. However, we can specify `dropna(axis="columns")` to drop the columns where there is a missing value.

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

print(df.dropna(axis="columns"))
"""
      Name
0     Aisu
1    Temir
2  Gulnara
3   Azamat
4  Dilyara
5   Fatima
6    Aydin
7     Oğuz
8    Asgar
9   Gulzar
"""
```

Also, by default `dropna` gets rid of the rows or columns where there is even a single missing value. However, we can specify to get rid of a row or a column, when all the values of a row are missing using `dropna(how="all")`.

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

print(df.dropna(how="all"))
# Nothing dropped because there is not a row where all the values are NaN
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
```

If we want to specify to drop a row, when there is a missing value in a specific column, we can use the `subset` argument of the `dropna` method.

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

print(df.dropna(subset="Salary"))
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50         NaN
7     Oğuz   NaN    Ankara  62000.00         Yes
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

If we want to specify a threshold number of non-missing values, we can do that using the `thresh` argument:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar'],
    'Age': [np.nan, 29, 34, 22, 28, np.nan, 30],
    'City': ['Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', np.nan, 'Baku' ],
    'Salary': [np.nan, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan],
}

df = pd.DataFrame(dictionaryForDataFrame)
print(df)
"""
      Name   Age      City   Salary
0  Gulnara   NaN  Tashkent      NaN
1   Azamat  29.0    Astana      NaN
2  Dilyara  34.0       NaN  75000.1
3   Fatima  22.0     Kazan  50000.0
4    Aydin  28.0  Istanbul  68000.5
5     Oğuz   NaN       NaN  62000.0
6    Asgar  30.0      Baku      NaN
"""

print(df.dropna(thresh=3))
"""
      Name   Age      City   Salary
1   Azamat  29.0    Astana      NaN
2  Dilyara  34.0       NaN  75000.1
3   Fatima  22.0     Kazan  50000.0
4    Aydin  28.0  Istanbul  68000.5
6    Asgar  30.0      Baku      NaN
"""
```

---

---
