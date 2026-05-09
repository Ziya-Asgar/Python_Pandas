# Reshaping and Pivoting

- [Reshaping and Pivoting](#reshaping-and-pivoting)
  - [Reshaping with Hierarchical Indexing](#reshaping-with-hierarchical-indexing)
  - [Pivoting “Long” to “Wide” Format](#pivoting-long-to-wide-format)
  - [Pivoting “Wide” to “Long” Format](#pivoting-wide-to-long-format)

---

---

There are a number of basic operations for rearranging tabular data. These are referred to as reshape or pivot operations.

---

---

## Reshaping with Hierarchical Indexing

The `stack` method “rotates” or pivots from the columns in the data to the rows. The `unstack` method pivots from the rows into the columns.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

print(result.unstack())
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""
```

By default, the innermost level is unstacked (same with `stack`). You can unstack a different level by passing a level number or name:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

print(result.unstack())
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

print(result.unstack(level=0))
"""
state   Ohio  Colorado
number
one        0         3
two        1         4
three      2         5
"""

print(result.unstack(level="state"))
"""
state   Ohio  Colorado
number
one        0         3
two        1         4
three      2         5
"""
```

Unstacking might introduce missing data if all of the values in the level aren’t found in each subgroup. Stacking filters out missing data by default, so the operation is more easily invertible:

```py
import pandas as pd

s1 = pd.Series([0, 1, 2, 3], index=["a", "b", "c", "d"], dtype="Int64")
s2 = pd.Series([4, 5, 6], index=["c", "d", "e"], dtype="Int64")
s3 = pd.concat([s1, s2], keys=["one", "two"])

print(s1)
"""
a    0
b    1
c    2
d    3
dtype: Int64
"""

print(s2)
"""
c    4
d    5
e    6
dtype: Int64
"""

print(s3)
"""
one  a    0
     b    1
     c    2
     d    3
two  c    4
     d    5
     e    6
dtype: Int64
"""

print(s3.unstack())
"""
        a     b  c  d     e
one     0     1  2  3  <NA>
two  <NA>  <NA>  4  5     6
"""

print(s3.unstack().stack())
"""
one  a    0
     b    1
     c    2
     d    3
two  c    4
     d    5
     e    6
dtype: Int64
"""

print(s3.unstack().stack(future_stack=True))
"""
one  a       0
     b       1
     c       2
     d       3
     e    <NA>
two  a    <NA>
     b    <NA>
     c       4
     d       5
     e       6
dtype: Int64
"""
```

When you unstack in a DataFrame, the level unstacked becomes the lowest level in the result. As with the `unstack` method, when calling `stack` we can indicate a specific axis:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(6).reshape((2, 3)),
  index = pd.Index(["Ohio", "Colorado"], name="state"),
  columns=pd.Index(["one", "two", "three"], name="number")
)

print(df)
"""
number    one  two  three
state
Ohio        0    1      2
Colorado    3    4      5
"""

result = df.stack()
print(result)
"""
state     number
Ohio      one       0
          two       1
          three     2
Colorado  one       3
          two       4
          three     5
dtype: int64
"""

df = pd.DataFrame({
  "left": result,
  "right": result + 5,
}, columns=pd.Index(["left", "right"], name="side"))

print(df)
"""
side             left  right
state    number
Ohio     one        0      5
         two        1      6
         three      2      7
Colorado one        3      8
         two        4      9
         three      5     10
"""

print(df.unstack(level="state"))
"""
side   left          right
state  Ohio Colorado  Ohio Colorado
number
one       0        3     5        8
two       1        4     6        9
three     2        5     7       10
"""

print(df.unstack(level="state").stack(level="side", future_stack=True))
"""
state         Ohio  Colorado
number side
one    left      0         3
       right     5         8
two    left      1         4
       right     6         9
three  left      2         5
       right     7        10
"""
```

---

---

## Pivoting “Long” to “Wide” Format

In the `pivot` method, the first two values passed are the columns to be used, respectively, as the row and column index, then finally an optional value column to fill the DataFrame. By omitting the last argument, you obtain a DataFrame with hierarchical columns.

```py
import pandas as pd

df = pd.DataFrame({
  'column1': ['one', 'one', 'one', 'two', 'two', 'two'],
  'column2': ['A', 'B', 'C', 'A', 'B', 'C'],
  'column3': [1, 2, 3, 4, 5, 6],
  'column4': ['x', 'y', 'z', 'q', 'w', 't']
})

print(df)
"""
  column1 column2  column3 column4
0     one       A        1       x
1     one       B        2       y
2     one       C        3       z
3     two       A        4       q
4     two       B        5       w
5     two       C        6       t
"""

print(df.pivot(index="column1", columns=["column2"], values=["column3"]))
"""
              column3
column2       A  B  C
column1
one           1  2  3
two           4  5  6
"""

print(df.pivot(index="column1", columns=["column2"], values=["column3", "column4"]))
"""
              column3       column4
column2       A  B  C       A  B  C
column1
one           1  2  3       x  y  z
two           4  5  6       q  w  t
"""
```

---

---

## Pivoting “Wide” to “Long” Format

An inverse operation to `pivot` for DataFrames is `pandas.melt`. Rather than transforming one column into many in a new DataFrame, it merges multiple columns into one, producing a DataFrame that is longer than the input.

```py
import pandas as pd

df = pd.DataFrame({
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   A  B  C
0  1  4  7
1  2  5  8
2  3  6  9
"""

melted = pd.melt(df)
print(melted)
"""
  variable  value
0        A      1
1        A      2
2        A      3
3        B      4
4        B      5
5        B      6
6        C      7
7        C      8
8        C      9
"""
```

When using `pandas.melt`, we can indicate which columns (if any) are group indicators. Let's use `"key"` as the only group indicator in our below example:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

melted = pd.melt(df, id_vars="key")
print(melted)
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
6  foo        C      7
7  bar        C      8
8  baz        C      9
"""
```

After using `pandas.melt`, we can still use the `pivot` method to revert the changes back.

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

melted = pd.melt(df, id_vars="key")
print(melted)
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
6  foo        C      7
7  bar        C      8
8  baz        C      9
"""

reshaped = melted.pivot(index="key", columns="variable", values="value")
print(reshaped)
"""
variable  A  B  C
key
bar       2  5  8
baz       3  6  9
foo       1  4  7
"""

print(reshaped.reset_index())
"""
variable  key  A  B  C
0         bar  2  5  8
1         baz  3  6  9
2         foo  1  4  7
"""
```

We can specify which values should be in the result of the `pandas.melt` command:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

print(pd.melt(df, id_vars="key", value_vars=["A", "B"]))
"""
   key variable  value
0  foo        A      1
1  bar        A      2
2  baz        A      3
3  foo        B      4
4  bar        B      5
5  baz        B      6
"""
```

Just like the `pivot` method, `pandas.melt` can be used without any group identifiers, too:

```py
import pandas as pd

df = pd.DataFrame({
  "key": ["foo", "bar", "baz"],
  "A": [1, 2, 3],
  "B": [4, 5, 6],
  "C": [7, 8, 9]
})

print(df)
"""
   key  A  B  C
0  foo  1  4  7
1  bar  2  5  8
2  baz  3  6  9
"""

print(pd.melt(df, value_vars=["key", "A", "B"]))
"""
  variable value
0      key   foo
1      key   bar
2      key   baz
3        A     1
4        A     2
5        A     3
6        B     4
7        B     5
8        B     6
"""
```

---

---
