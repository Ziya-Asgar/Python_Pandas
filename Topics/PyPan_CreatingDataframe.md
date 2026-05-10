# Creating a dataframe

- [Creating a dataframe](#creating-a-dataframe)
  - [Creating a dataframe from a dictionary](#creating-a-dataframe-from-a-dictionary)
  - [Data Types in a dataframe](#data-types-in-a-dataframe)
    - [Specifying the columns while creating a dataframe from a dictionary](#specifying-the-columns-while-creating-a-dataframe-from-a-dictionary)
    - [Specifying the index labels while creating a dataframe from a dictionary](#specifying-the-index-labels-while-creating-a-dataframe-from-a-dictionary)
  - [Creating a dataframe from a nested dictionary](#creating-a-dataframe-from-a-nested-dictionary)
    - [Specifying the index labels while creating a dataframe from a nested dictionary](#specifying-the-index-labels-while-creating-a-dataframe-from-a-nested-dictionary)
  - [Creating a dataframe from an ndarray](#creating-a-dataframe-from-an-ndarray)

---

---

There are many ways to construct a dataframe. One of the most common is from a dictionary of equal-length lists or NumPy arrays.

---

---

## Creating a dataframe from a dictionary

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
```

---

---

## Data Types in a dataframe

To check what type of data each column in a dataframe has, we can use the `dtypes` attribute:

```py
dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame)
print(df.dtypes)
"""
Name            object
Age            float64
City            object
Salary         float64
Is_Employed     object
dtype: object
"""
```

---

### Specifying the columns while creating a dataframe from a dictionary

While creating a dataframe from a dictionary, we can specify the order of columns, and which columns the dataframe should have:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Age", "Name", "Salary", "Expenses"])

print(df)
"""
    Age     Name    Salary Expenses
0  27.0     Aisu  60000.50      NaN
1  31.0    Temir  72000.75      NaN
2   NaN  Gulnara  55000.00      NaN
3  29.0   Azamat       NaN      NaN
4  34.0  Dilyara  75000.10      NaN
5  22.0   Fatima  50000.00      NaN
6  28.0    Aydin  68000.50      NaN
7   NaN     Oğuz  62000.00      NaN
8  30.0    Asgar       NaN      NaN
9  24.0   Gulzar  90000.00      NaN
"""
```

Note that in the above example, the `Expenses` column only includes `NaN`, because there was no data about it in the dictionary that was used to create the dataframe.

---

### Specifying the index labels while creating a dataframe from a dictionary

We can specify the index labels while creating a dataframe. However, the number of indices should be the same as the number of rows in the dataframe:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, index=[0, 1, 4, 2, 3, 9, 8, 10, 11, 12])
print(df)
"""
        Name   Age      City    Salary Is_Employed
10      Aisu  27.0    Almaty  60000.50         Yes
11     Temir  31.0   Bishkek  72000.75          No
12   Gulnara   NaN  Tashkent  55000.00         Yes
13    Azamat  29.0    Astana       NaN          No
14   Dilyara  34.0       NaN  75000.10         Yes
100   Fatima  22.0     Kazan  50000.00          No
101    Aydin  28.0  Istanbul  68000.50         NaN
102     Oğuz   NaN    Ankara  62000.00         Yes
103    Asgar  30.0      Baku       NaN          No
104   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

---

---

## Creating a dataframe from a nested dictionary

If we create a DataFrame using a nested dictionary, then pandas will interpret the outer dictionary keys as the columns and the inner keys as row indices:

```py
import pandas as pd

# cities, years, and city populations
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
```

---

### Specifying the index labels while creating a dataframe from a nested dictionary

The inner keys and outer keys are combined to form the index, and column labels in the result. This isn’t true if an explicit index and columns are specified:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame, index=[2021, 2022, 2023])
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
2023       NaN   NaN       NaN      NaN
"""

# using both `index` and `columns`
df2 = pd.DataFrame(nestedDictionaryForDataFrame, index=[2021, 2022, 2023], columns=["Baku", "Istanbul", "Nur-Sultan"])
print(df2)
"""
      Baku  Istanbul Nur-Sultan
2021  2.25     15.52        NaN
2022  2.27     15.60        NaN
2023   NaN       NaN        NaN
"""
```

---

---

## Creating a dataframe from an ndarray

We can also create a dataframe from a Numpy ndarray. The ndarray shouldn't have more than 2 dimensions.

```py
import numpy as np
import pandas as pd

arr = np.array([1, 2, 3, 4])
print(arr) # [1 2 3 4]

df = pd.DataFrame(arr, index=["a", "b", "c", "d"], columns=["column"])
print(df)
"""
   column
a       1
b       2
c       3
d       4
"""

arr = np.array([[1, 2, 3, 4], [10, 20, 30, 40]])
print(arr)
"""
[[ 1  2  3  4]
 [10 20 30 40]]
"""

df = pd.DataFrame(arr,  index=["row1", "row2"], columns=["column1", "column2", "column3", "column4"])
print(df)
"""
      column1  column2  column3  column4
row1        1        2        3        4
row2       10       20       30       40
"""
```

---

---
