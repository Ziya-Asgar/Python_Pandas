# Creating a Series

- [Creating a Series](#creating-a-series)
  - [Creating a Series from a List](#creating-a-series-from-a-list)
    - [Specifying the index column while creating a series from a list](#specifying-the-index-column-while-creating-a-series-from-a-list)
  - [Creating a series from a dictionary](#creating-a-series-from-a-dictionary)
    - [Specifying the index labels while creating a series from a dictionary](#specifying-the-index-labels-while-creating-a-series-from-a-dictionary)
  - [Data Types in a series](#data-types-in-a-series)
    - [Converting datatypes of a series](#converting-datatypes-of-a-series)

---

---

## Creating a Series from a List

Here is an example of creating a series from a list:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103])
print(ser)
"""
0    100
1    101
2    102
3    103
dtype: int64
"""
```

---

### Specifying the index column while creating a series from a list

The left-most column, in the series, is the index label for the items in the series. When we create a series without specifying the index, indices are created automatically. We can specify the indices ourselves while creating a series, using the `index` keyword argument:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["d", "b", "a", "c"])
print(ser)
"""
d    100
b    101
a    102
c    103
dtype: int64
"""
```

Here is another example, this time without using the `index` keyword argument:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], ["d", "b", "a", "c"])
print(ser)
"""
d    100
b    101
a    102
c    103
dtype: int64
"""
```

---

---

## Creating a series from a dictionary

We can also create a series from a dictionary. When we create a series from a dictionary, the dictionary keys become index labels:

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
```

---

### Specifying the index labels while creating a series from a dictionary

When we create a series from a dictionary, the order of indices in the resulting series will be the same as the order in the result of the `keys` dictionary method. But we can still specify what index labels the series should have:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(dictionaryForSeries.keys())
# dict_keys(['Istanbul', 'Baku', 'Tashkent', 'Nur-Sultan'])

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
dtype: float64
"""

ser = pd.Series(dictionaryForSeries, index=["Baku", "Istanbul", "Nur-Sultan", "Karbala"])

print(ser)
"""
Baku           5.0
Istanbul      15.0
Nur-Sultan    18.0
Karbala        NaN
dtype: float64
"""
```

Note that in the above example `Karbala` is `NaN` because even though we provided it as an index to the series, there was no data for it in the dictionary that was used to create the series. Also, note that `Tashkent` was discarded, because we didn't specify it as an index.

---

---

## Data Types in a series

Every series, has a `dtype` (datatype) attribute. The `dtype` determines what manipulations you can apply to that series. There are various data types of items in a series. Here are some main examples:

- Numeric - these hold numbers that pandas understands are numbers. Specific numeric datatypes include `int64`, `int32` (integers), or `float64`, `float32` (floating point numbers).
- Object - these are series that can hold any Python object. They have `dtype` `O` for “objects”. They are flexible, but also very slow and actually harder to work with.
- Categorical - Categorical series (series with a `category` dtype) are designed to deal with a situation where a series contains only text, and the actual values in that series are repeated frequently.

We can check the `dtype` of a series, as well as set the `dtype` of a series.

```py
ser = pd.Series([1, 2, 3])
print(ser.dtype) # int64

ser = pd.Series([1, 2, 3], dtype="float64")
print(ser.dtype) # float64

ser = pd.Series([1, 2, "3"])
print(ser.dtype) # object

ser = pd.Series([1, 2, 3.4])
print(ser.dtype) # float64

ser = pd.Series(["Azerbaijan", "Turkiye", "Kazakhstan", "Turkmenistan"], dtype="category")
print(ser)
"""
0      Azerbaijan
1         Turkiye
2      Kazakhstan
3    Turkmenistan
dtype: category
Categories (4, object): ['Azerbaijan', 'Kazakhstan', 'Turkiye', 'Turkmenistan']
"""
```

---

### Converting datatypes of a series

If you want to change the datatype of a series, you can do so with the `.astype()` method, provided a conversion is possible.

```py
ser = pd.Series([1, 2, 3])
ser = ser.astype("float64")
print(ser)
"""
0    1.0
1    2.0
2    3.0
dtype: float64
"""
```

---

---
