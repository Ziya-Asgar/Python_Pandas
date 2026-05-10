# Converting series and dataframes to other objects

- [Converting series and dataframes to other objects](#converting-series-and-dataframes-to-other-objects)
  - [Converting a series to a dictionary](#converting-a-series-to-a-dictionary)
  - [Converting a dataframe to an ndarray](#converting-a-dataframe-to-an-ndarray)

---

---

## Converting a series to a dictionary

If we want to convert a series to a dictionary, we can use its `to_dict` method:

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

print(ser.to_dict())
# {'Istanbul': 15.0, 'Baku': 5.0, 'Tashkent': nan, 'Nur-Sultan': 18.0}
```

---

## Converting a dataframe to an ndarray

DataFrame's `to_numpy` method returns the data contained in the DataFrame as a two-dimensional ndarray:

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

print(df.to_numpy())
"""
[[15.46  2.23  2.5   1.  ]
 [15.52  2.25  2.52  1.02]
 [15.6   2.27   nan  1.04]]
"""
```

---

---
