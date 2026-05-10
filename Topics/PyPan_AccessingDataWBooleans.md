# Using booleans to access and retrieve data from a series and a dataframe

- [Using booleans to access and retrieve data from a series and a dataframe](#using-booleans-to-access-and-retrieve-data-from-a-series-and-a-dataframe)
  - [Using booleans to retrieve specific data from a series](#using-booleans-to-retrieve-specific-data-from-a-series)
  - [Using boolean values to retrieve data from a dataframe](#using-boolean-values-to-retrieve-data-from-a-dataframe)
  - [Retrieving data using bitwise operators](#retrieving-data-using-bitwise-operators)
  - [Retrieving data using regular expressions](#retrieving-data-using-regular-expressions)
  - [Using boolean values to change the data in a dataframe](#using-boolean-values-to-change-the-data-in-a-dataframe)
  - [Checking if an item exists in the index, series and dataframes](#checking-if-an-item-exists-in-the-index-series-and-dataframes)
    - [Checking the Index object with the `in` operator](#checking-the-index-object-with-the-in-operator)
    - [Checking if an item exists in a series or a dataframe using the `isin` method](#checking-if-an-item-exists-in-a-series-or-a-dataframe-using-the-isin-method)

---

---

## Using booleans to retrieve specific data from a series

Similar to `numpy` arrays, in `pandas` we can use boolean arrays to retrieve the specific values from a series:

```py
import pandas as pd

ser = pd.Series([100, -101, 102, -103], ["d", "b", "a", "c"])

print(ser)
"""
d    100
b   -101
a    102
c   -103
dtype: int64
"""

print(ser > 0)
"""
d     True
b    False
a     True
c    False
dtype: bool
"""

print(ser[ser > 0])
"""
d    100
a    102
dtype: int64
"""
```

---

---

## Using boolean values to retrieve data from a dataframe

We can use boolean arrays to retrieve the specific values from a dataframe:

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

print(df[df["Age"] > 30])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

Boolean arrays can be used with `loc` but not `iloc`:

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

print(df.loc[df.loc[:,"Age"] > 30])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

---

---

## Retrieving data using bitwise operators

Another common operation is the use of boolean vectors to filter the data. The operators are:

- `|` for `or`,
- `&` for `and`, and
- `~` for `not`.

These must be grouped by using parentheses, since by default Python will evaluate an expression such as `df['A'] > 2 & df['B'] < 3` as `df['A'] > (2 & df['B']) < 3`, while the desired evaluation order is `(df['A'] > 2) & (df['B'] < 3)`:

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
print( df[ ( df["City"] == "Baku" ) | ( df["City"] == "Istanbul" ) | ( df["City"] == "Ashgabat" ) ] )
"""
     Name   Age      City
6   Aydin  28.0  Istanbul
8   Asgar  30.0      Baku
9  Gulzar  24.0  Ashgabat
"""

print( df[ (df["Salary"] > 60000) & ( (df["City"] == "Almaty") | (df["City"] == "Ashgabat") ) ] )
"""
     Name   Age      City   Salary Is_Employed
0    Aisu  27.0    Almaty  60000.5         Yes
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""

print( df[~(( df["City"] == "Istanbul" ) | ( df["City"] == "Baku" ))] )
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana       NaN          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
7     Oğuz   NaN    Ankara  62000.00         Yes
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

---

---

## Retrieving data using regular expressions

Pandas lets us use regular expressions directly without importing `re` module.

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

print(df.loc[df["Name"].str.contains(r"a$")])
"""
      Name   Age      City   Salary Is_Employed
2  Gulnara   NaN  Tashkent  55000.0         Yes
4  Dilyara  34.0       NaN  75000.1         Yes
5   Fatima  22.0     Kazan  50000.0          No
"""
```

---

---

## Using boolean values to change the data in a dataframe

We can use the Boolean DataFrame to assign different values in a dataframe:

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

ageBool = df["Age"] > 30
print(df[ageBool])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""

df.loc[ageBool, "Age"] = df.loc[ageBool, "Age"] * 10
print(df[ageBool])
"""
      Name    Age     City    Salary Is_Employed
1    Temir  310.0  Bishkek  72000.75          No
4  Dilyara  340.0      NaN  75000.10         Yes
"""
```

---

---

## Checking if an item exists in the index, series and dataframes

### Checking the Index object with the `in` operator

We can check if some item is part of the Index object using the `in` operator:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["a", "b", "c", "d"])

print("a" in ser) # True
print("e" in ser) # False
```

---

### Checking if an item exists in a series or a dataframe using the `isin` method

`isin` method checks if provided values are in a series or a dataframe:

```py
import pandas as pd

listForSeries = ['Apple', 'Banana', 'Cherry', 'Date', np.nan, 'Fig', 'Grape', np.nan, 'Kiwi', 'Lemon']
ser = pd.Series(listForSeries)

check = ser.isin(["Apple", "Cherry"])
print(check)
"""
0     True
1    False
2     True
3    False
4    False
5    False
6    False
7    False
8    False
9    False
dtype: bool
"""
```

We can use the boolean data that `isin` provides to retrieve the data from original series or dataframe:

```py
import pandas as pd

listForSeries = ['Apple', 'Banana', 'Cherry', 'Date', np.nan, 'Fig', 'Grape', np.nan, 'Kiwi', 'Lemon']
ser = pd.Series(listForSeries)

check = ser.isin(["Apple", "Cherry"])
print(ser[check])
"""
0     Apple
2    Cherry
dtype: object
"""
```

The `isin` method can also check if an item is part of the index:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["a", "b", "c", "d"])

print(ser.index.isin(["a"])) # [ True False False False]
```

---

---
