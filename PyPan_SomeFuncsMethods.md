# Some Functions and Methods

- [Some Functions and Methods](#some-functions-and-methods)
  - [NumPy ufuncs](#numpy-ufuncs)
  - [`any`](#any)
  - [`apply`](#apply)
  - [`map`](#map)
  - [`agg`](#agg)
  - [`explode`](#explode)
  - [`to_numeric`](#to_numeric)
  - [`clip`](#clip)
  - [`rolling`](#rolling)
  - [`expanding`](#expanding)
  - [`ewm`](#ewm)
  - [`pipe`](#pipe)
  - [`query`](#query)
  - [`first_valid_index` and `last_valid_index`](#first_valid_index-and-last_valid_index)
  - [`asof`](#asof)
  - [`at_time`](#at_time)
  - [`between_time`](#between_time)
  - [`filter`](#filter)
  - [`diff`](#diff)
  - [`transform` (Not Ready)](#transform-not-ready)

---

---

## NumPy ufuncs

NumPy ufuncs (element-wise array methods) also work with pandas objects:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.standard_normal((3, 4)), columns=["Istanbul", "Baku", "Tashkent", "Karbala"], index=list("bde"))
print(df)
"""
   Istanbul      Baku  Tashkent   Karbala
b -1.563264  2.567086  1.024896 -0.281742
d  0.592404  0.887360  0.317562 -0.564904
e  0.938755 -1.285503  0.461021 -0.126007
"""

print(np.round(df, 2))
"""
   Istanbul  Baku  Tashkent  Karbala
b     -1.56  2.57      1.02    -0.28
d      0.59  0.89      0.32    -0.56
e      0.94 -1.29      0.46    -0.13
"""

print(np.abs(df))
"""
   Istanbul      Baku  Tashkent   Karbala
b  1.563264  2.567086  1.024896  0.281742
d  0.592404  0.887360  0.317562  0.564904
e  0.938755  1.285503  0.461021  0.126007
"""

# The `round` and `abs` methods could be used on the instance object as well
print(df.round(2))
"""
   Istanbul  Baku  Tashkent  Karbala
b     -1.56  2.57      1.02    -0.28
d      0.59  0.89      0.32    -0.56
e      0.94 -1.29      0.46    -0.13
"""

print(df.abs())
"""
   Istanbul      Baku  Tashkent   Karbala
b  1.563264  2.567086  1.024896  0.281742
d  0.592404  0.887360  0.317562  0.564904
e  0.938755  1.285503  0.461021  0.126007
"""
```

---

---

## `any`

The `any` method is used to check if any element in a DataFrame or along a specific axis is `True`. It returns a boolean value. This function can be applied to a dataframe or a series.

```py
import pandas as pd

df = pd.DataFrame({
    'A': [False, False, True, False],
    'B': [False, False, False, False],
    'C': ["", np.nan, 0, None],
})

print(df)
"""
       A      B     C
0  False  False
1  False  False   NaN
2   True  False     0
3  False  False  None
"""

print(df.any())
"""
A     True
B    False
C    False
dtype: bool
"""
```

We can change the axis to be checked using the `axis` argument:

```py
import pandas as pd

df = pd.DataFrame({
    'A': [False, False, True, False],
    'B': [False, False, False, False],
    'C': ["", np.nan, 0, None],
})
print(df)
"""
       A      B     C
0  False  False
1  False  False   NaN
2   True  False     0
3  False  False  None
"""

print(df.any(axis="columns"))
# print(df.any(axis=1)), same as  above
"""
0    False
1    False
2     True
3    False
dtype: bool
"""
```

`any` becomes especially useful, when used in combination with conditions. Let's say we want to filter the outliers in our dataframe. Here is how `any` could be useful:

```py
import pandas as pd

df = pd.DataFrame({
  "A":[-10, -2, -1, 0, 1, 2, 20],
  "B": [-20, -3, -2, 0, 2, 3, 10]
})
print(df)
"""
    A   B
0 -10 -20
1  -2  -3
2  -1  -2
3   0   0
4   1   2
5   2   3
6  20  10
"""

print(df[(df.abs() > 3).any(axis="columns")])
"""
    A   B
0 -10 -20
6  20  10
"""

# change the outliers to equal 3
df[(df.abs() > 3).any(axis="columns")] = np.sign(df) * 3
print(df)
"""
   A  B
0 -3 -3
1 -2 -3
2 -1 -2
3  0  0
4  1  2
5  2  3
6  3  3
"""
```

---

---

## `apply`

We can use the `apply` method, to call a function on every value in a series:

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
print(df.head())
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
"""

print(df["Name"].apply(len))
"""
0    4
1    5
2    7
3    6
4    7
5    6
6    5
7    4
8    5
9    6
Name: Name, dtype: int64
"""
```

In the above example, we used the `apply` method on a column (and a column of a dataframe is a series) and this caused the function within the `apply` method to be run on every value of the column. But if we use the `apply` method on a dataframe, the function provided to `apply` will be run not on the values within the columns, but on the columns themselves. We can further specify, if we want the function to be applied by row or column:

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
print(df.head())
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
"""


print(df.apply(len))
"""
Name    10
Age     10
dtype: int64
"""

print(df.apply(len, axis="columns"))
"""
0    2
1    2
2    2
3    2
4    2
5    2
6    2
7    2
8    2
9    2
dtype: int64
"""
```

---

---

## `map`

We can also use the `map` method to use the function on every item in a dataframe:

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
print(df.head())
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
"""

print(df["Name"].map(lambda x: x.upper()))
"""
0       AISU
1      TEMIR
2    GULNARA
3     AZAMAT
4    DILYARA
5     FATIMA
6      AYDIN
7       OĞUZ
8      ASGAR
9     GULZAR
Name: Name, dtype: object
"""
```

If we want to change the specific values in a dataframe, we can use the `map` method with a dictionary:

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
print(df.head())
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
"""

print(df["Name"].map({"Aisu": "Aysu", "Oğuz": "Oghuz"}))
"""
0     Aysu
1      NaN
2      NaN
3      NaN
4      NaN
5      NaN
6      NaN
7    Oghuz
8      NaN
9      NaN
Name: Name, dtype: object
"""
```

---

---

## `agg`

The `agg` method takes a function or a list of functions as an argument. It applies the specified function(s) to each column (or row, depending on the axis) of the DataFrame or Series. The result is a new DataFrame or Series with the aggregated values.

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

print(df.agg(["min", "max"]))
"""
     Istanbul  Baku  Tashkent  Karbala
min     15.46  2.23      2.50     1.00
max     15.60  2.27      2.52     1.04
"""

print(df.agg(["min", "max"], axis="columns"))
"""
       min    max
2020  1.00  15.46
2021  1.02  15.52
2022  1.04  15.60
"""
```

We can set different aggregations for different columns of a dataframe:

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

print(df.agg({"Istanbul": ["min", "max"], "Baku": ["mean", "sum"]}))
"""
      Istanbul  Baku
min      15.46   NaN
max      15.60   NaN
mean       NaN  2.25
sum        NaN  6.75
"""
```

If we want to do an aggregation over a single column, we can also use the below syntax:

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

df["Baku"].agg(["sum", "mean"])
"""
sum     6.75
mean    2.25
Name: Baku, dtype: float64
"""
```

We can rename the resulting index of the `agg` method:

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

print(df.agg(one = ("Istanbul", "mean"), two=("Istanbul", "sum"), three = ("Baku", "count")))
"""
        Istanbul  Baku
one    15.526667   NaN
two    46.580000   NaN
three        NaN   3.0
"""
```

---

---

## `explode`

The `explode` method converts each element of a list-like structure into a separate row.

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2)

print(df)
"""
      country                       city
0  Azerbaijan  [Baku, Khankendi, Shusha]
1     Turkiye  [Istanbul, Ankara, Izmir]
"""

print(df.explode("city"))
"""
      country       city
0  Azerbaijan       Baku
0  Azerbaijan  Khankendi
0  Azerbaijan     Shusha
1     Turkiye   Istanbul
1     Turkiye     Ankara
1     Turkiye      Izmir
"""
```

We can also explode more than one column:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2)
df["budget"] = [[2, 0.5, 0.2], [10, 5, 4]]

print(df)
"""
      country                       city         budget
0  Azerbaijan  [Baku, Khankendi, Shusha]  [2, 0.5, 0.2]
1     Turkiye  [Istanbul, Ankara, Izmir]     [10, 5, 4]
"""

print(df.explode(["city", "budget"]))
"""
      country       city budget
0  Azerbaijan       Baku      2
0  Azerbaijan  Khankendi    0.5
0  Azerbaijan     Shusha    0.2
1     Turkiye   Istanbul     10
1     Turkiye     Ankara      5
1     Turkiye      Izmir      4
"""
```

The method accepts the `ignore_index` keyword argument. It specifies whether to reset the index of the resulting dataframe. Setting it to `True` will create a new index, while `False` retains the original index.

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2)

print(df)
"""
      country                       city
0  Azerbaijan  [Baku, Khankendi, Shusha]
1     Turkiye  [Istanbul, Ankara, Izmir]
"""

print(df.explode("city"))
"""
      country       city
0  Azerbaijan       Baku
0  Azerbaijan  Khankendi
0  Azerbaijan     Shusha
1     Turkiye   Istanbul
1     Turkiye     Ankara
1     Turkiye      Izmir
"""

print(df.explode("city", ignore_index=True))
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""
```

---

---

## `to_numeric`

The `to_numeric` method is used to convert a column or Series of values to a numeric type (e.g., `int` or `float`). If the input contains non-numeric values (e.g., strings), it can either `raise` an error, `coerce` them to `NaN`, or `ignore` them, depending on the `errors` parameter.

```py
import pandas as pd

# Create a Series with mixed data types
ser = pd.Series(['1', '2.5', '3', 'four', '5.0'])

print("Original Series:")
print(ser)
"""
Original Series:
0       1
1     2.5
2       3
3    four
4     5.0
dtype: object
"""

# Convert to numeric, coercing errors to NaN
numeric_ser = pd.to_numeric(ser, errors='coerce')

print("\nSeries after to_numeric (with coercion):")
print(numeric_ser)
"""
Series after to_numeric (with coercion):
0    1.0
1    2.5
2    3.0
3    NaN
4    5.0
dtype: float64
"""

try:
    numeric_data = pd.to_numeric(data, errors='raise')
except ValueError as e:
    print(f"Error: {e}")
# Error: Unable to parse string "four" at position 3
```

---

---

## `clip`

The `clip` method is used to limit the values in a DataFrame or Series to a specified range.

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
print(df["Salary"])
"""
0    60000.50
1    72000.75
2    55000.00
3         NaN
4    75000.10
5    50000.00
6    68000.50
7    62000.00
8         NaN
9    90000.00
Name: Salary, dtype: float64
"""

print(df["Salary"].clip(lower=60000, upper=65000))
"""
0    60000.5
1    65000.0
2    60000.0
3        NaN
4    65000.0
5    60000.0
6    65000.0
7    62000.0
8        NaN
9    65000.0
Name: Salary, dtype: float64
"""
```

---

---

## `rolling`

The `rolling` method is used to perform rolling window calculations on a DataFrame or Series. A rolling window calculation involves applying a function (e.g., mean, sum, standard deviation) over a specified window of data points that "rolls" through the dataset. This is particularly useful for time series analysis, smoothing data, or computing moving averages.

```py
import pandas as pd

# Create a Series with some data
ser = pd.Series([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

print("Original Series:")
print(ser)
"""
Original Series:
0     1
1     2
2     3
3     4
4     5
5     6
6     7
7     8
8     9
9    10
dtype: int64
"""

# Compute the rolling sum with a window size of 3
rolling_mean = ser.rolling(window=3).sum()

print("\nRolling sum (window=3):")
print(rolling_mean)
"""
Rolling sum (window=3):
0     NaN
1     NaN
2     6.0
3     9.0
4    12.0
5    15.0
6    18.0
7    21.0
8    24.0
9    27.0
dtype: float64
"""
```

The `min_periods` parameter in the rolling method specifies the minimum number of observations required in a window to compute a value. If there are fewer observations than `min_periods`, the result will be `NaN`.

```py
import pandas as pd

# Create a Series with some data
ser = pd.Series([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

print("Original Series:")
print(ser)
"""
Original Series:
0     1
1     2
2     3
3     4
4     5
5     6
6     7
7     8
8     9
9    10
dtype: int64
"""

# Compute the rolling sum with a window size of 3
rolling_mean = ser.rolling(window=3, min_periods=2).sum()

print("\nRolling sum (window=3):")
print(rolling_mean)
"""
Rolling sum (window=3):
0     NaN
1     3.0
2     6.0
3     9.0
4    12.0
5    15.0
6    18.0
7    21.0
8    24.0
9    27.0
dtype: float64
"""
```

When working with time series data, the rolling method becomes even more powerful because it can leverage time-based windows instead of just fixed-size windows.

```py
import pandas as pd

# Create a time series with a datetime index
dates = pd.date_range('2023-10-01', periods=10, freq='D')
ser = pd.Series([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], index=dates)

print("Original Time Series:")
print(ser)
"""
Original Time Series:
2023-10-01     1
2023-10-02     2
2023-10-03     3
2023-10-04     4
2023-10-05     5
2023-10-06     6
2023-10-07     7
2023-10-08     8
2023-10-09     9
2023-10-10    10
Freq: D, dtype: int64
"""

# Compute the rolling mean with a 3-day window
rolling_sum = ser.rolling(window='3D').sum()

print("\nRolling sum (3-day window):")
print(rolling_sum)
"""
Rolling sum (3-day window):
2023-10-01     1.0
2023-10-02     3.0
2023-10-03     6.0
2023-10-04     9.0
2023-10-05    12.0
2023-10-06    15.0
2023-10-07    18.0
2023-10-08    21.0
2023-10-09    24.0
2023-10-10    27.0
Freq: D, dtype: float64
"""
```

---

---

## `expanding`

The `expanding` method is used to perform cumulative calculations on a DataFrame or Series. Unlike the rolling method, which uses a fixed-size window, the expanding method considers all previous data points up to the current one.

```py
import pandas as pd

# Create a Series with some data
ser = pd.Series([1, 2, 3, 4, 5])

print("Original Series:")
print(ser)
"""
Original Series:
0    1
1    2
2    3
3    4
4    5
dtype: int64
"""

# Compute the expanding sum
expanding_sum = ser.expanding().sum()

print("\nExpanding Sum:")
print(expanding_sum)
"""
Expanding Sum:
0     1.0
1     3.0
2     6.0
3    10.0
4    15.0
dtype: float64
"""
```

---

---

## `ewm`

Pandas also provides the `ewm` method for exponentially weighted moving calculations.

---

---

## `pipe`

Pipes facilitate chaining together operations that expect pandas data structures as their first argument.

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

cities = df\
  .pipe(lambda data: data.dropna())\
  .pipe(lambda data: data[["Name", "City"]])
print(cities)
"""
     Name      City
0    Aisu    Almaty
1   Temir   Bishkek
5  Fatima     Kazan
9  Gulzar  Ashgabat
"""
```

---

---

## `query`

The `pandas.DataFrame.query` method takes a string parameter and queries a dataframe. When using Boolean logic with the `query` method, we can use both logical operators (`and`, `or`, `not`) and bitwise operators (`&`, `|`, `~`).

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
print(df.query("Salary > 0 and Is_Employed == 'No'"))
"""
Name   Age     City    Salary Is_Employed
1   Temir  31.0  Bishkek  72000.75          No
5  Fatima  22.0    Kazan  50000.00          No
"""
```

---

---

## `first_valid_index` and `last_valid_index`

The `first_valid_index` and `last_valid_index` methods are used to find the index of the first and last non-missing (non-NaN) value in a Series or DataFrame.

```py
import pandas as pd
import numpy as np

# Create a Series with some missing values
ser = pd.Series([np.nan, np.nan, 3, 4, np.nan, 6, np.nan])

print("Original Series:")
print(ser)
"""
Original Series:
0    NaN
1    NaN
2    3.0
3    4.0
4    NaN
5    6.0
6    NaN
dtype: float64
"""

# Find the first and last valid indices
first_valid = ser.first_valid_index()
last_valid = ser.last_valid_index()

print(first_valid) # 2
print(last_valid) # 5
```

---

---

## `asof`

The `asof` method returns the last valid (non-missing) value up to a specified point in time or index. This method is particularly useful for time series data, where you want to find the most recent value before or at a specific timestamp. If the specified point (e.g., a timestamp) is not found in the index, it returns the last valid value before that point.

```py
import pandas as pd

# Create a Series with a datetime index
dates = pd.to_datetime(['2023-10-01', '2023-10-03', '2023-10-06', '2023-10-07'])
values = [100, 200, 300, 400]
series = pd.Series(values, index=dates)

print("Original Series:")
print(series)
"""
Original Series:
2023-10-01    100
2023-10-03    200
2023-10-06    300
2023-10-07    400
dtype: int64
"""

# Perform an "as of" lookup for a specific date
lookup_date = pd.to_datetime('2023-10-05')
result = series.asof(lookup_date)

print(f"\nLast valid value as of {lookup_date}: {result}")
# Last valid value as of 2023-10-05 00:00:00: 200
```

---

---

## `at_time`

The `at_time` method is used to select rows from a DataFrame or Series that match a specific time. It only works with `DatetimeIndex` or `TimedeltaIndex`.

```py
import pandas as pd

# Create a DataFrame with a DatetimeIndex
dates = pd.date_range('2023-10-01 06:00', '2023-10-02 18:00', freq='6h')
data = {'Value': range(7)}
df = pd.DataFrame(data, index=dates)

print("Original DataFrame:")
print(df)
"""
Original DataFrame:
                     Value
2023-10-01 06:00:00      0
2023-10-01 12:00:00      1
2023-10-01 18:00:00      2
2023-10-02 00:00:00      3
2023-10-02 06:00:00      4
2023-10-02 12:00:00      5
2023-10-02 18:00:00      6
"""

# Select rows that occur at 12:00 (noon)
noon_data = df.at_time('12:00')

print("\nRows at 12:00:")
print(noon_data)
"""
Rows at 12:00:
                     Value
2023-10-01 12:00:00      1
2023-10-02 12:00:00      5
"""
```

---

---

## `between_time`

We can use the `between_time` method to grab all the rows where the time portion of the datetime is between two times (inclusive of the endpoints by default). It only works with `DatetimeIndex` or `TimedeltaIndex`.

```py
import pandas as pd

# Create a DataFrame with a DatetimeIndex
dates = pd.date_range('2023-10-01 06:00', '2023-10-02 18:00', freq='6h')
data = {'Value': range(7)}
df = pd.DataFrame(data, index=dates)

print("Original DataFrame:")
print(df)
"""
Original DataFrame:
                     Value
2023-10-01 06:00:00      0
2023-10-01 12:00:00      1
2023-10-01 18:00:00      2
2023-10-02 00:00:00      3
2023-10-02 06:00:00      4
2023-10-02 12:00:00      5
2023-10-02 18:00:00      6
"""

# Select rows that occur between 12:00 (noon) and 15:00 (3 PM)
afternoon_data = df.between_time('12:00', '15:00')

print("\nRows between 12:00 and 15:00:")
print(afternoon_data)
"""
Rows between 12:00 and 15:00:
                     Value
2023-10-01 12:00:00      1
2023-10-02 12:00:00      5
"""
```

---

---

## `filter`

The `filter` method filters the rows or columns according to the specified index labels. Note that this routine does not filter a series or a dataframe on their contents. The filter is applied to the labels of the index. It accepts some important parameters, which are mutually exclusive:

- `items` - filters based on a list (of columns or index labels),
- `like` - receives a string to identify columns that contain a particular substring,
- `regex` - filters based on a regular expression.

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

print(df.filter(["Name", "City"]).head())
"""
      Name      City
0     Aisu    Almaty
1    Temir   Bishkek
2  Gulnara  Tashkent
3   Azamat    Astana
4  Dilyara       NaN
"""

print(df.filter(items=[2, 5, 8], axis=0))
"""
      Name   Age      City   Salary Is_Employed
2  Gulnara   NaN  Tashkent  55000.0         Yes
5   Fatima  22.0     Kazan  50000.0          No
8    Asgar  30.0      Baku      NaN          No
"""

print(df.filter(like="Na").head())
"""
      Name
0     Aisu
1    Temir
2  Gulnara
3   Azamat
4  Dilyara
"""
```

---

---

## `diff`

The `diff` method calculates the difference of an element compared with another element (default is element in previous row).

```py
import pandas as pd

df = pd.DataFrame({
  "A": range(10, 15),
  "B": range(10, 19, 2),
})

print(df.diff())
"""
     A    B
0  NaN  NaN
1  1.0  2.0
2  1.0  2.0
3  1.0  2.0
4  1.0  2.0
"""

print(df.diff(axis=1))
"""
    A  B
0 NaN  0
1 NaN  1
2 NaN  2
3 NaN  3
4 NaN  4
"""

# Difference with 3rd previous row
print(df.diff(periods=3))
"""
A    B
0  NaN  NaN
1  NaN  NaN
2  NaN  NaN
3  3.0  6.0
4  3.0  6.0
"""

# Difference with following row
print(df.diff(periods=-1))
"""
     A    B
0 -1.0 -2.0
1 -1.0 -2.0
2 -1.0 -2.0
3 -1.0 -2.0
4  NaN  NaN
"""
```

---

---

## `transform` (Not Ready)

---

---
