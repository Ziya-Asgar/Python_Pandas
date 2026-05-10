# Sorting and Ranking

- [Sorting and Ranking](#sorting-and-ranking)
  - [Sorting a series by indices](#sorting-a-series-by-indices)
  - [Sorting a dataframe by indices](#sorting-a-dataframe-by-indices)
  - [Sorting a series by values](#sorting-a-series-by-values)
    - [Placement of missing values while sorting by values](#placement-of-missing-values-while-sorting-by-values)
  - [Sorting a dataframe by values](#sorting-a-dataframe-by-values)
  - [Ranking a series](#ranking-a-series)
    - [Tie-breaking methods with `rank`](#tie-breaking-methods-with-rank)

---

---

## Sorting a series by indices

To sort index of a series lexicographically, use the `sort_index` method, which returns a new, sorted object:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(4), index=["d", "a", "c", "b"])

print(ser)
"""
d    0
a    1
c    2
b    3
dtype: int64
"""

print(ser.sort_index())
"""
a    1
b    2
c    3
d    0
dtype: int64
"""
```

`sort_index` also sorts the numerical index labels:

```py
import pandas as pd

ser = pd.Series(["a", "b", "c", "d"], index=[3, 2, 1, 0])

print(ser)
"""
3    a
2    b
1    c
0    d
dtype: object
"""

print(ser.sort_index())
"""
0    d
1    c
2    b
3    a
dtype: object
"""
```

---

---

## Sorting a dataframe by indices

With a DataFrame, you can sort by label on either axis:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame, index=[2021, 2020, 2022])

print(df)
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2020     15.46  2.23      2.50     1.00
2022     15.60  2.27       NaN     1.04
"""

print(df.sort_index())
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

print(df.sort_index(axis="columns"))
"""
      Baku  Istanbul  Karbala  Tashkent
2021  2.25     15.52     1.02      2.52
2020  2.23     15.46     1.00      2.50
2022  2.27     15.60     1.04       NaN
"""
```

The data is sorted in ascending order by default but can be sorted in descending order, too:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame, index=[2021, 2020, 2022])

print(df.sort_index(axis="columns", ascending=False))
"""
      Tashkent  Karbala  Istanbul  Baku
2021      2.52     1.02     15.52  2.25
2020      2.50     1.00     15.46  2.23
2022       NaN     1.04     15.60  2.27
"""
```

---

---

## Sorting a series by values

To sort a series by its values, use its `sort_values` method:

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

print(ser.sort_values())
"""
Baku           5.0
Istanbul      15.0
Nur-Sultan    18.0
Tashkent       NaN
dtype: float64
"""
```

---

### Placement of missing values while sorting by values

Any missing values are sorted to the end of the series by default. Missing values can be sorted to the start instead by using the `na_position` option:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser.sort_values())
"""
Baku           5.0
Istanbul      15.0
Nur-Sultan    18.0
Tashkent       NaN
dtype: float64
"""

print(ser.sort_values(na_position="first"))
"""
Tashkent       NaN
Baku           5.0
Istanbul      15.0
Nur-Sultan    18.0
dtype: float64
"""
```

---

---

## Sorting a dataframe by values

When sorting a DataFrame, you can use the data in one or more columns as the sort keys. To do so, pass one or more column names to `sort_values`:

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

print(df.sort_values("Baku", ascending=False))
"""
      Istanbul  Baku  Tashkent  Karbala
2022     15.60  2.27       NaN     1.04
2021     15.52  2.25      2.52     1.02
2020     15.46  2.23      2.50     1.00
"""
```

To sort by multiple columns, pass a list of column names:

```py
import pandas as pd

listForDataFrame = [['Istanbul', 'Turkiye', 15.0],
        ['Ankara', 'Turkiye', 5.0],
        ['Baku', 'Azerbaijan', 2.5],
        ['Tashkent', 'Uzbekistan', None],
        ['Nur-Sultan', 'Kazakhstan', 18.0],
        ['Najaf', 'Iraq', None],
        ['Karbala', 'Iraq', 0.6]]

df = pd.DataFrame(listForDataFrame, columns=["city", "country", "population"])

print(df.sort_values(["country", "population"]))
"""
         city     country  population
2        Baku  Azerbaijan         2.5
6     Karbala        Iraq         0.6
5       Najaf        Iraq         NaN
4  Nur-Sultan  Kazakhstan        18.0
1      Ankara     Turkiye         5.0
0    Istanbul     Turkiye        15.0
3    Tashkent  Uzbekistan         NaN
"""
```

If we are sorting by 2 different columns, we can specify if we want each of them in descending order or ascending one:

```py
import pandas as pd

listForDataFrame = [['Istanbul', 'Turkiye', 15.0],
        ['Ankara', 'Turkiye', 5.0],
        ['Baku', 'Azerbaijan', 2.5],
        ['Tashkent', 'Uzbekistan', None],
        ['Nur-Sultan', 'Kazakhstan', 18.0],
        ['Najaf', 'Iraq', None],
        ['Karbala', 'Iraq', 0.6]]

df = pd.DataFrame(listForDataFrame, columns=["city", "country", "population"])

print(df.sort_values(["country", "population"], ascending=[False, True]))
"""
         city     country  population
3    Tashkent  Uzbekistan         NaN
1      Ankara     Turkiye         5.0
0    Istanbul     Turkiye        15.0
4  Nur-Sultan  Kazakhstan        18.0
6     Karbala        Iraq         0.6
5       Najaf        Iraq         NaN
2        Baku  Azerbaijan         2.5
"""
```

If we want to change the index while sorting the values, we can pass the `ignore_index=True` to `sort_values()`.

---

---

## Ranking a series

Ranking assigns ranks from one through the number of valid data points in an array, starting from the lowest value.

```py
import pandas as pd

ser = pd.Series([1e2, 1e1, 1e4, 1e3, 1e5, 1e3])

print(ser)
"""
0       100.0
1        10.0
2     10000.0
3      1000.0
4    100000.0
5      1000.0
dtype: float64
"""

print(ser.rank())
"""
0    2.0
1    1.0
2    5.0
3    3.5
4    6.0
5    3.5
dtype: float64
"""
```

You can rank in descending order, too:

```py
import pandas as pd

ser = pd.Series([1e2, 1e1, 1e4, 1e3, 1e5, 1e3])

print(ser)
"""
0       100.0
1        10.0
2     10000.0
3      1000.0
4    100000.0
5      1000.0
dtype: float64
"""

print(ser.rank(ascending=False))
"""
0    5.0
1    6.0
2    2.0
3    3.5
4    1.0
5    3.5
dtype: float64
"""
```

---

### Tie-breaking methods with `rank`

In the above example, when the `rank` method encountered equal values, it broke ties by assigning each value the mean rank. Instead of assigning a mean rank, ranks can also be assigned according to the order in which they’re observed in the data. Here, instead of using the average rank of `3.5` for the values `1000` at index 3 and 5, they instead have been set to 3 and 4.

```py
import pandas as pd

ser = pd.Series([1e2, 1e1, 1e4, 1e3, 1e5, 1e3])

print(ser)
"""
0       100.0
1        10.0
2     10000.0
3      1000.0
4    100000.0
5      1000.0
dtype: float64
"""

print(ser.rank(method="first"))
"""
0    2.0
1    1.0
2    5.0
3    3.0
4    6.0
5    4.0
dtype: float64
"""
```

There are other values that we can use to break a tie during ranking:

| Method      | Description                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------- |
| `"average"` | Default: assign the average rank to each entry in the equal group                                                      |
| `"first"`   | Assign ranks in the order the values appear in the data                                                                |
| `"min"`     | Use the minimum rank for the whole group                                                                               |
| `"max"`     | Use the maximum rank for the whole group                                                                               |
| `"dense"`   | Like `method="min"`, but ranks always increase by 1 between groups rather than the number of equal elements in a group |

---

---
