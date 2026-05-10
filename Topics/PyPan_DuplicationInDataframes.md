# Duplication in Dataframes

- [Duplication in Dataframes](#duplication-in-dataframes)
  - [Checking the existence of duplicate values in a dataframe](#checking-the-existence-of-duplicate-values-in-a-dataframe)
  - [Dropping duplicate values in a dataframe](#dropping-duplicate-values-in-a-dataframe)

---

---

## Checking the existence of duplicate values in a dataframe

The dataframe method `duplicated` returns a Boolean Series indicating whether each row is a duplicate or not:

```py
import pandas as pd

df = pd.DataFrame({
  "k1": ["one", "two"] * 3 + ["two"],
  "k2": [1, 1, 2, 3, 3, 4, 4]
})
print(df)
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
6  two   4
"""

print(df.duplicated())
"""
0    False
1    False
2    False
3    False
4    False
5    False
6     True
dtype: bool
"""
```

If we want to check duplicate values in specific columns, we can do that using the `subset` argument:

```py
import pandas as pd

df = pd.DataFrame({
  "k1": ["one", "two"] * 3 + ["two"],
  "k2": [1, 1, 2, 3, 3, 4, 4]
})
print(df)
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
6  two   4
"""

print(df.duplicated("k1"))
"""
0    False
1    False
2     True
3     True
4     True
5     True
6     True
dtype: bool
"""

df.duplicated(subset=["k1", "k2"])
"""
0    False
1    False
2    False
3    False
4    False
5    False
6     True
dtype: bool
"""
```

---

---

## Dropping duplicate values in a dataframe

If we want to drop the duplicate values in a dataframe, we can use the `drop_duplicates` method:

```py
import pandas as pd

df = pd.DataFrame({
  "k1": ["one", "two"] * 3 + ["two"],
  "k2": [1, 1, 2, 3, 3, 4, 4]
})
print(df)
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
6  two   4
"""

print(df.drop_duplicates())
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
"""
```

It also accepts the `subset` argument:

```py
import pandas as pd

df = pd.DataFrame({
  "k1": ["one", "two"] * 3 + ["two"],
  "k2": [1, 1, 2, 3, 3, 4, 4]
})
print(df)
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
6  two   4
"""

print(df.drop_duplicates(subset=["k1"]))
"""
    k1  k2
0  one   1
1  two   1
"""
```

`duplicated` and `drop_duplicates` by default keep the first observed value combination. Passing `keep="last"` will return the last one:

```py
import pandas as pd

df = pd.DataFrame({
  "k1": ["one", "two"] * 3 + ["two"],
  "k2": [1, 1, 2, 3, 3, 4, 4]
})
print(df)
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
5  two   4
6  two   4
"""

print(df.drop_duplicates(["k1", "k2"], keep="last"))
"""
    k1  k2
0  one   1
1  two   1
2  one   2
3  two   3
4  one   3
6  two   4
"""
```

---

---
