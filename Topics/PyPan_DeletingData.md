# Deleting data

- [Deleting data](#deleting-data)
  - [Deleting data from a series](#deleting-data-from-a-series)
    - [Using the `del` keyword to delete the items from a series](#using-the-del-keyword-to-delete-the-items-from-a-series)
    - [Using the `drop` method to delete the items from a series](#using-the-drop-method-to-delete-the-items-from-a-series)
  - [Deleting data from a dataframe](#deleting-data-from-a-dataframe)
    - [Using the `del` keyword to delete a column from a dataframe](#using-the-del-keyword-to-delete-a-column-from-a-dataframe)
    - [Using the `drop` method to delete rows and columns from a dataframe](#using-the-drop-method-to-delete-rows-and-columns-from-a-dataframe)
    - [Using the `pop` method to delete a column of a dataframe](#using-the-pop-method-to-delete-a-column-of-a-dataframe)

---

---

## Deleting data from a series

### Using the `del` keyword to delete the items from a series

We can delete an item from a series using the `del` keyword:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5.), index=["a", "b", "c", "d", "e"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
e    4.0
dtype: float64
"""

del ser["b"]
print(ser)
"""
a    0.0
c    2.0
d    3.0
e    4.0
dtype: float64
"""

# We can also put the `del` statement into the `try ... catch` block
try:
  del ser["b"]
except KeyError:
  pass
```

---

### Using the `drop` method to delete the items from a series

The `drop` method returns a new object with the indicated value or values deleted from it:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5.), index=["a", "b", "c", "d", "e"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
e    4.0
dtype: float64
"""

new_ser = ser.drop("c")
print(new_ser)
"""
a    0.0
b    1.0
d    3.0
e    4.0
dtype: float64
"""

print(ser.drop(["b", "d"]))
"""
a    0.0
c    2.0
e    4.0
dtype: float64
"""
```

---

---

## Deleting data from a dataframe

### Using the `del` keyword to delete a column from a dataframe

To delete a column in a DataFrame, we can use the `del` keyword:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Age", "City"])
print(df.head())
"""
      Name   Age      City
0     Aisu  27.0    Almaty
1    Temir  31.0   Bishkek
2  Gulnara   NaN  Tashkent
3   Azamat  29.0    Astana
4  Dilyara  34.0       NaN
"""

del df["Age"]
print(df.head())
"""
      Name      City
0     Aisu    Almaty
1    Temir   Bishkek
2  Gulnara  Tashkent
3   Azamat    Astana
4  Dilyara       NaN
"""
```

---

### Using the `drop` method to delete rows and columns from a dataframe

Here is an example of dropping data from a dataframe using the `drop` method:

```py
import numpy as np
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

# drop columns
print(df.drop(columns=["Istanbul"]))
"""
      Baku  Tashkent  Karbala
2020  2.23      2.50     1.00
2021  2.25      2.52     1.02
2022  2.27       NaN     1.04
"""

# drop rows
print(df.drop(index=[2020, 2021]))
"""
      Istanbul  Baku  Tashkent  Karbala
2022      15.6  2.27       NaN     1.04
"""
```

We can also use the `axis` keyword to identify if rows or columns should be dropped:

```py
import numpy as np
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

# drop columns
print(df.drop(["Istanbul"], axis=1))
"""
      Baku  Tashkent  Karbala
2020  2.23      2.50     1.00
2021  2.25      2.52     1.02
2022  2.27       NaN     1.04
"""

# drop rows
print(df.drop([2020, 2021], axis=0))
"""
      Istanbul  Baku  Tashkent  Karbala
2022      15.6  2.27       NaN     1.04
"""
```

Instead of `axis=0` and `axis=1`, we can also use `axis="index"` and `axis="columns"`, to delete the columns in a dataframe:

```py
import numpy as np
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

# drop columns
print(df.drop(["Istanbul"], axis="columns"))
"""
      Baku  Tashkent  Karbala
2020  2.23      2.50     1.00
2021  2.25      2.52     1.02
2022  2.27       NaN     1.04
"""

# drop rows
print(df.drop([2020, 2021], axis="index"))
"""
      Istanbul  Baku  Tashkent  Karbala
2022      15.6  2.27       NaN     1.04
"""
```

---

### Using the `pop` method to delete a column of a dataframe

The `pop` method on the DataFrame returns a column while deleting it from the DataFrame at the same time.

```py
import numpy as np
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

# drop rows
print(df.pop("Istanbul"))
"""
2020    15.46
2021    15.52
2022    15.60
Name: Istanbul, dtype: float64
"""
```

---

---
