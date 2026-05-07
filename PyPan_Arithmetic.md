# Arithmetic

- [Arithmetic](#arithmetic)
  - [Table of different arithmetic methods](#table-of-different-arithmetic-methods)
  - [Arithmetic operations on series](#arithmetic-operations-on-series)
  - [Arithmetic operations on dataframes](#arithmetic-operations-on-dataframes)

---

---

## Table of different arithmetic methods

Here is a table of some arithmetic methods:

| Method                  | Description                       |
| ----------------------- | --------------------------------- |
| `add`, `radd`           | Methods for addition (+)          |
| `sub`, `rsub`           | Methods for subtraction (-)       |
| `div`, `rdiv`           | Methods for division (/)          |
| `floordiv`, `rfloordiv` | Methods for floor division (//)   |
| `mul`, `rmul`           | Methods for multiplication (\*)   |
| `pow`, `rpow`           | Methods for exponentiation (\*\*) |

---

---

## Arithmetic operations on series

As `pandas` uses `numpy` under the hood, we can use the Numpy-like array operations using pandas objects as well.

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["d", "c", "a", "b"])
print(ser * 2)
"""
d    200
c    202
a    204
b    206
dtype: int64
"""

print(ser + 2)
"""
d    102
c    103
a    104
b    105
dtype: int64
"""

print(ser / ser)
"""
d    1.0
b    1.0
a    1.0
c    1.0
dtype: float64
"""
```

When we do mathematical operations on series, the index labels are respected. In the below example, even though the order of items is different in each series, `pandas` still adds the items that have the same index label. If both objects don't have the same index labels, the respective index in the result will be the union of the index pairs:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}

ser1 = pd.Series(dictionaryForSeries)
ser2 = pd.Series(dictionaryForSeries, index=["Istanbul", "Tashkent", "Baku", "Astana"])

print(ser1 + ser2)
"""
Astana         NaN
Baku          10.0
Istanbul      30.0
Nur-Sultan     NaN
Tashkent       NaN
dtype: float64
"""
```

---

---

## Arithmetic operations on dataframes

In the case of dataframes, the alignment is performed on both rows and columns:

```py
import numpy as np
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df1 = pd.DataFrame(nestedDictionaryForDataFrame, columns=["Istanbul", "Baku", "Karbala"])
df2 = pd.DataFrame(nestedDictionaryForDataFrame, columns=["Baku", "Karbala", "Tashkent"], index=[2021, 2022, 2023])

print(df1)
"""
      Istanbul  Baku  Karbala
2020     15.46  2.23     1.00
2021     15.52  2.25     1.02
2022     15.60  2.27     1.04
"""

print(df2)
"""
      Baku  Karbala  Tashkent
2021  2.25     1.02      2.52
2022  2.27     1.04       NaN
2023   NaN      NaN       NaN
"""

print(df1 + df2)
"""
      Baku  Istanbul  Karbala  Tashkent
2020   NaN       NaN      NaN       NaN
2021  4.50       NaN     2.04       NaN
2022  4.54       NaN     2.08       NaN
2023   NaN       NaN      NaN       NaN
"""
```

---

---
