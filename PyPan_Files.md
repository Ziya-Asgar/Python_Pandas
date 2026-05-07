# Reading from and Writing to Files

- [Reading from and Writing to Files](#reading-from-and-writing-to-files)
  - [Table of methods to load data](#table-of-methods-to-load-data)
  - [Practical usage of `read_csv`](#practical-usage-of-read_csv)
    - [Table of some `read_csv` arguments](#table-of-some-read_csv-arguments)
    - [Basic use of `read_csv`](#basic-use-of-read_csv)
    - [Use `read_csv` to retrieve data without headers](#use-read_csv-to-retrieve-data-without-headers)
    - [Converting columns of a dataframe to an index](#converting-columns-of-a-dataframe-to-an-index)
    - [Using custom delimiter with `read_csv`](#using-custom-delimiter-with-read_csv)
    - [Skipping rows using the `read_csv` method](#skipping-rows-using-the-read_csv-method)
    - [Dealing with missing data while using the `read_csv` method](#dealing-with-missing-data-while-using-the-read_csv-method)
  - [Reading Text Files in Pieces](#reading-text-files-in-pieces)
    - [Using options to display a small number of rows and columns](#using-options-to-display-a-small-number-of-rows-and-columns)
    - [Using the `nrows` to retrieve a small number of rows](#using-the-nrows-to-retrieve-a-small-number-of-rows)
    - [Using the `chunksize` to retrieve a small number of rows](#using-the-chunksize-to-retrieve-a-small-number-of-rows)
    - [Using the `get_chunk` to retrieve a small number of rows](#using-the-get_chunk-to-retrieve-a-small-number-of-rows)
  - [Writing Data to Text Format](#writing-data-to-text-format)
    - [Basic use of the `to_csv` method](#basic-use-of-the-to_csv-method)
    - [Using the `to_csv` method with other delimiters](#using-the-to_csv-method-with-other-delimiters)
    - [Dealing with the missing values while using the `to_csv` method](#dealing-with-the-missing-values-while-using-the-to_csv-method)
    - [Getting rid of the index and column headers while using the `to_csv` method](#getting-rid-of-the-index-and-column-headers-while-using-the-to_csv-method)
    - [Outputting specific columns while using the `to_csv` method](#outputting-specific-columns-while-using-the-to_csv-method)
  - [Dealing with the JSON Data](#dealing-with-the-json-data)
    - [Parse JSON to a python object](#parse-json-to-a-python-object)
    - [Convert a python object to JSON](#convert-a-python-object-to-json)
    - [Convert JSON to a dataframe](#convert-json-to-a-dataframe)
    - [Convert a pandas object to JSON](#convert-a-pandas-object-to-json)
  - [XML and HTML: Web Scraping](#xml-and-html-web-scraping)

---

---

## Table of methods to load data

`pandas` features a number of functions for reading tabular data as a dataframe object.

| Function         | Description                                                                                                                   |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `read_csv`       | Load delimited data from a file, URL, or file-like object; use comma as default delimiter                                     |
| `read_fwf`       | Read data in fixed-width column format (i.e., no delimiters)                                                                  |
| `read_clipboard` | Variation of `read_csv` that reads data from the clipboard; useful for converting tables from web pages                       |
| `read_excel`     | Read tabular data from an Excel XLS or XLSX file                                                                              |
| `read_hdf`       | Read HDF5 files written by pandas                                                                                             |
| `read_html`      | Read all tables found in the given HTML document                                                                              |
| `read_json`      | Read data from a JSON (JavaScript Object Notation) string representation, file, URL, or file-like object                      |
| `read_feather`   | Read the Feather binary file format                                                                                           |
| `read_orc`       | Read the Apache ORC binary file format                                                                                        |
| `read_parquet`   | Read the Apache Parquet binary file format                                                                                    |
| `read_pickle`    | Read an object stored by pandas using the Python pickle format                                                                |
| `read_sas`       | Read a SAS dataset stored in one of the SAS system's custom storage formats                                                   |
| `read_spss`      | Read a data file created by SPSS                                                                                              |
| `read_sql`       | Read the results of a SQL query (using SQLAlchemy)                                                                            |
| `read_sql_table` | Read a whole SQL table (using SQLAlchemy); equivalent to using a query that selects everything in that table using `read_sql` |
| `read_stata`     | Read a dataset from Stata file format                                                                                         |
| `read_xml`       | Read a table of data from an XML file                                                                                         |

---

---

## Practical usage of `read_csv`

### Table of some `read_csv` arguments

Here is a table with some of the `read_csv` function arguments, before we dive into using some of them:

| Argument             | Description                                                                                                                                                                                                                                                                                                            |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `path`               | String indicating filesystem location, URL, or file-like object.                                                                                                                                                                                                                                                       |
| `sep` or `delimiter` | Character sequence or regular expression to use to split fields in each row.                                                                                                                                                                                                                                           |
| `header`             | Row number to use as column names; defaults to 0 (first row), but should be `None` if there is no header row.                                                                                                                                                                                                          |
| `index_col`          | Column numbers or names to use as the row index in the result; can be a single name/number or a list of them for a hierarchical index.                                                                                                                                                                                 |
| `names`              | List of column names for result.                                                                                                                                                                                                                                                                                       |
| `skiprows`           | Number of rows at beginning of file to ignore or list of row numbers (starting from 0) to skip.                                                                                                                                                                                                                        |
| `na_values`          | Sequence of values to replace with NA. They are added to the default list unless `keep_default_na=False` is passed.                                                                                                                                                                                                    |
| `keep_default_na`    | Whether to use the default NA value list or not (`True` by default).                                                                                                                                                                                                                                                   |
| `comment`            | Character(s) to split comments off the end of lines.                                                                                                                                                                                                                                                                   |
| `parse_dates`        | Attempt to parse data to `datetime`; `False` by default. If `True`, will attempt to parse all columns. Otherwise, can specify a list of column numbers or names to parse. If element of list is tuple or list, will combine multiple columns together and parse to date (e.g., if date/time split across two columns). |
| `keep_date_col`      | If joining columns to parse date, keep the joined columns; `False` by default.                                                                                                                                                                                                                                         |
| `converters`         | Dictionary containing column number or name mapping to functions (e.g., `{"foo": f}` would apply the function `f` to all values in the `"foo"` column).                                                                                                                                                                |
| `dayfirst`           | When parsing potentially ambiguous dates, treat as international format (e.g., 7/6/2012 -> June 7, 2012); `False` by default.                                                                                                                                                                                          |
| `date_parser`        | Function to use to parse dates.                                                                                                                                                                                                                                                                                        |
| `nrows`              | Number of rows to read from beginning of file (not counting the header).                                                                                                                                                                                                                                               |
| `iterator`           | Return a `TextFileReader` object for reading the file piecemeal. This object can also be used with the `with` statement.                                                                                                                                                                                               |
| `chunksize`          | For iteration, size of file chunks.                                                                                                                                                                                                                                                                                    |
| `skip_footer`        | Number of lines to ignore at end of file.                                                                                                                                                                                                                                                                              |
| `verbose`            | Print various parsing information, like the time spent in each stage of the file conversion and memory use information.                                                                                                                                                                                                |
| `encoding`           | Text encoding (e.g., `"utf-8"` for UTF-8 encoded text). Defaults to `"utf-8"` if `None`.                                                                                                                                                                                                                               |
| `squeeze`            | If the parsed data contains only one column, return a series.                                                                                                                                                                                                                                                          |
| `thousands`          | Separator for thousands (e.g., `","` or `"."`); default is `None`.                                                                                                                                                                                                                                                     |
| `decimal`            | Decimal separator in numbers (e.g., `"."` or `","`); default is `"."`.                                                                                                                                                                                                                                                 |
| `engine`             | CSV parsing and conversion engine to use; can be one of `"c"`, `"python"`, or `"pyarrow"`. The default is `"c"`, though the newer `"pyarrow"` engine can parse some files much faster. The `"python"` engine is slower but supports some features that the other engines do not.                                       |

---

### Basic use of `read_csv`

Let's say we have this data in a csv file:

```
a,b,c,d,message
1,2,3,4,hello
5,6,7,8,world
9,10,11,12,foo
```

Here is a simple way to use the `read_csv` method:

```py
import pandas as pd

df = pd.read_csv("examples/ex1.csv")
print(df)
"""
   a   b   c   d message
0  1   2   3   4   hello
1  5   6   7   8   world
2  9  10  11  12     foo
"""
```

---

### Use `read_csv` to retrieve data without headers

A file will not always have a header row. Consider this file:

```
1,2,3,4,hello
5,6,7,8,world
9,10,11,12,foo
```

When a file doesn't have a header row, we can specify `header=None` in `read_csv`, so that pandas would not automatically accept the first row as headers. In this case, pandas will create headers automatically, itself:

```py
import pandas as pd

df = pd.read_csv("examples/ex2.csv", header=None)
print(df)
"""
   0   1   2   3      4
0  1   2   3   4  hello
1  5   6   7   8  world
2  9  10  11  12    foo
"""
```

We can also specify column names ourselves using the `names` argument:

```py
import pandas as pd

df = pd.read_csv("examples/ex2.csv", names=["a", "b", "c", "d", "message"])
print(df)
"""
   a   b   c   d message
0  1   2   3   4   hello
1  5   6   7   8   world
2  9  10  11  12     foo
"""
```

---

### Converting columns of a dataframe to an index

We can convert columns of the dataframe, returned by `read_csv`, into an index using the `index_col` argument:

```py
import pandas as pd

df = pd.read_csv("examples/ex2.csv", names=["a", "b", "c", "d", "message"], index_col="message")
print(df)
"""
         a   b   c   d
message
hello    1   2   3   4
world    5   6   7   8
foo      9  10  11  12
"""
```

Instead of the column name, we can also use the column number with `index_col`:

```py
import pandas as pd

df = pd.read_csv("examples/ex2.csv", names=["a", "b", "c", "d", "message"], index_col=4)
print(df)
"""
         a   b   c   d
message
hello    1   2   3   4
world    5   6   7   8
foo      9  10  11  12
"""
```

Let's say, we have this data:

```csv
key1,key2,value1,value2
one,a,1,2
one,b,3,4
one,c,5,6
one,d,7,8
two,a,9,10
two,b,11,12
two,c,13,14
two,d,15,16
```

We can create a hierarchical index using this data. If you want to form a hierarchical index from multiple columns, pass a list of column numbers or names:

```py
import pandas as pd

df = pd.read_csv("examples/csv_mindex.csv", index_col=["key1", "key2"])
print(df)
"""
           value1  value2
key1 key2
one  a          1       2
     b          3       4
     c          5       6
     d          7       8
two  a          9      10
     b         11      12
     c         13      14
     d         15      16
"""
```

---

### Using custom delimiter with `read_csv`

In some cases, a table might not have a fixed delimiter, using whitespace or some other pattern to separate fields. Consider a text file that looks like this:

```
A         B         C
aaa -0.264438 -1.026059 -0.619500
bbb  0.927272  0.302904 -0.032399
ccc -0.264273 -0.386314 -0.217601
ddd -0.871858 -0.348382  1.100491
```

In these cases, you can pass a custom separator using the `sep` argument. For our example, we can use the regular expression `\s+`:

```py
import pandas as pd

df = pd.read_csv("examples/ex3.txt", sep="\\s+")
print(df)
"""
            A         B         C
aaa -0.264438 -1.026059 -0.619500
bbb  0.927272  0.302904 -0.032399
ccc -0.264273 -0.386314 -0.217601
ddd -0.871858 -0.348382  1.100491
"""
```

In the above example, because there was one fewer column name than the number of data rows, `read_csv` infers that the first column should be the dataframe’s index.

---

### Skipping rows using the `read_csv` method

The file parsing functions have many additional arguments that helps to handle the wide variety of exception file formats that occur. For example, you can skip some rows of a file with `skiprows`:

```py
import pandas as pd

df = pd.read_csv("examples/ex4.csv")
print(df)
"""
                                                                      # hey!
a                                                  b        c   d    message
# just wanted to make things more difficult for... NaN      NaN NaN      NaN
# who reads CSV files with computers                anyway? NaN NaN      NaN
1                                                  2        3   4      hello
5                                                  6        7   8      world
9                                                  10       11  12       foo
"""

df = pd.read_csv("examples/ex4.csv", skiprows=[0, 2, 3])
print(df)
"""
   a   b   c   d message
0  1   2   3   4   hello
1  5   6   7   8   world
2  9  10  11  12     foo
"""
```

---

### Dealing with missing data while using the `read_csv` method

Missing data is usually either not present (empty string) or marked by some placeholder value. By default, pandas uses a set of commonly occurring placeholders, such as NA and NULL. Let's say this is the data in the file:

```
something,a,b,c,d,message
one,1,2,3,4,NA
two,5,6,,8,world
three,9,10,11,12,foo
```

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv")
print(df)
"""
  something  a   b     c   d message
0       one  1   2   3.0   4     NaN
1       two  5   6   NaN   8   world
2     three  9  10  11.0  12     foo
"""
```

Pandas outputs missing values as `NaN`, so we have two null or missing values.

If we want to add to the default list of strings recognized as missing, we can use the `na_values` argument:

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv", na_values=["NULL"])
print(df)
"""
  something  a   b     c   d message
0       one  1   2   3.0   4     NaN
1       two  5   6   NaN   8   world
2     three  9  10  11.0  12     foo
"""

print(pd.read_csv("examples/ex5.csv", na_values=["foo"]))
"""
  something  a   b     c   d message
0       one  1   2   3.0   4     NaN
1       two  5   6   NaN   8   world
2     three  9  10  11.0  12     NaN
"""
```

`read_csv` has a list of many default NA value representations, but these defaults can be disabled with the `keep_default_na` option:

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv", keep_default_na=False)
print(df)
"""
  something  a   b   c   d message
0       one  1   2   3   4      NA
1       two  5   6       8   world
2     three  9  10  11  12     foo
"""

print(pd.read_csv("examples/ex5.csv", keep_default_na=False, na_values=["NA"]))
"""
  something  a   b   c   d message
0       one  1   2   3   4     NaN
1       two  5   6       8   world
2     three  9  10  11  12     foo
"""
```

Different NA placeholders can be specified for each column in a dictionary:

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv", na_values={"message":["foo", "NA"], "something": ["two"]})
print(df)
"""
  something  a   b     c   d message
0       one  1   2   3.0   4     NaN
1       NaN  5   6   NaN   8   world
2     three  9  10  11.0  12     NaN
"""
```

---

---

## Reading Text Files in Pieces

### Using options to display a small number of rows and columns

When we have a large dataframe, if we try to print it, we might see a cropped version of the table. For example, the jupyter notebook might not show all the columns or rows. If we want to specify maximum number of columns or rows that could be outputted, we can use the `set_option` method:

```py
import pandas as pd

# show maximum 10 rows and columns
pd.set_option("display.max_rows", 10)
pd.set_option("display.max_columns", 10)
```

Another way to set the above settings is this:

```py
import pandas as pd

# show maximum 10 rows and columns
pd.options.display.max_rows = 10
pd.options.display.max_columns = 10
```

---

### Using the `nrows` to retrieve a small number of rows

If you want to read only a small number of rows (avoiding reading the entire file), you can specify that with `nrows`:

```py
import pandas as pd

df = pd.read_csv("examples/ex6.csv", nrows=5)
print(df)
"""
        one       two     three      four key
0  0.467976 -0.038649 -0.295344 -1.824726   L
1 -0.358893  1.404453  0.704965 -0.200638   B
2 -0.501840  0.659254 -0.421691 -0.057688   G
3  0.204886  1.074134  1.388361 -0.982404   R
4  0.354628 -0.133116  0.283763 -0.837063   Q
"""
```

---

### Using the `chunksize` to retrieve a small number of rows

To read a file in pieces, specify a `chunksize` as a number of rows. This will return `TextFileReader` object. We can iterate through the file in chunks using this:

```py
import pandas as pd

chunker = pd.read_csv("examples/ex6.csv", chunksize=5)

chunkCount = 0
for chunk in chunker:
  while chunkCount < 2:
    print("chunk:", chunkCount, "\n", chunk)
    chunkCount += 1

"""
chunk: 0
         one       two     three      four key
0  0.467976 -0.038649 -0.295344 -1.824726   L
1 -0.358893  1.404453  0.704965 -0.200638   B
2 -0.501840  0.659254 -0.421691 -0.057688   G
3  0.204886  1.074134  1.388361 -0.982404   R
4  0.354628 -0.133116  0.283763 -0.837063   Q
chunk: 1
         one       two     three      four key
0  0.467976 -0.038649 -0.295344 -1.824726   L
1 -0.358893  1.404453  0.704965 -0.200638   B
2 -0.501840  0.659254 -0.421691 -0.057688   G
3  0.204886  1.074134  1.388361 -0.982404   R
4  0.354628 -0.133116  0.283763 -0.837063   Q
"""
```

---

### Using the `get_chunk` to retrieve a small number of rows

`TextFileReader` also has a `get_chunk` method that enables you to read pieces of an arbitrary size:

```py
import pandas as pd

chunker = pd.read_csv("examples/ex6.csv", chunksize=100)

print(chunker.get_chunk(5))
"""
        one       two     three      four key
0  0.467976 -0.038649 -0.295344 -1.824726   L
1 -0.358893  1.404453  0.704965 -0.200638   B
2 -0.501840  0.659254 -0.421691 -0.057688   G
3  0.204886  1.074134  1.388361 -0.982404   R
4  0.354628 -0.133116  0.283763 -0.837063   Q
"""

print(chunker.get_chunk(5))
"""
        one       two     three      four key
5  1.817480  0.742273  0.419395 -2.251035   Q
6 -0.776764  0.935518 -0.332872 -1.875641   U
7 -0.913135  1.530624 -0.572657  0.477252   K
8  0.358480 -0.497572 -0.367016  0.507702   S
9 -1.740877 -1.160417 -1.637830  2.172201   G
"""
```

---

---

## Writing Data to Text Format

### Basic use of the `to_csv` method

Using the `to_csv` method, we can write the data out to a comma-separated file:

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv")
df.to_csv("examples/out.csv")
```

---

### Using the `to_csv` method with other delimiters

Other delimiters can be used using the `sep` argument:

```py
import pandas as pd
import sys

df = pd.read_csv("examples/ex5.csv")
df.to_csv(sys.stdout, sep="|")
"""
|something|a|b|c|d|message
0|one|1|2|3.0|4|
1|two|5|6||8|world
2|three|9|10|11.0|12|foo
"""
```

---

### Dealing with the missing values while using the `to_csv` method

Missing values appear as empty strings in the output. You might want to denote them by some other placeholder value using the `na_rep` argument:

```py
import pandas as pd
import sys

df = pd.read_csv("examples/ex5.csv")
df.to_csv(sys.stdout, na_rep="NULL")
"""
,something,a,b,c,d,message
0,one,1,2,3.0,4,NULL
1,two,5,6,NULL,8,world
2,three,9,10,11.0,12,foo
"""
```

---

### Getting rid of the index and column headers while using the `to_csv` method

By default, both the row and column labels are written to the output. Both of these can be disabled using the `index` and `header` arguments:

```py
import pandas as pd
import sys

df = pd.read_csv("examples/ex5.csv")
df.to_csv(sys.stdout, index=False, header=False)
"""
one,1,2,3.0,4,
two,5,6,,8,world
three,9,10,11.0,12,foo
"""
```

---

### Outputting specific columns while using the `to_csv` method

You can also write only a subset of the columns, and in an order of your choosing using the `columns` argument:

```py
import pandas as pd
import sys

df = pd.read_csv("examples/ex5.csv")
df.to_csv(sys.stdout, index=False, columns=["a", "b", "c"])
"""
a,b,c
1,2,3.0
5,6,
9,10,11.0
"""
```

---

---

## Dealing with the JSON Data

### Parse JSON to a python object

There are several Python libraries for reading and writing JSON data. `json` is the one that is built into the Python standard library. To convert a JSON string to Python form with this library, use `json.loads`:

```py
import json

obj = """
{"name": "Wes",
 "cities_lived": ["Akron", "Nashville", "New York", "San Francisco"],
 "pet": null,
 "siblings": [{"name": "Scott", "age": 34, "hobbies": ["guitars", "soccer"]},
              {"name": "Katie", "age": 42, "hobbies": ["diving", "art"]}]
}
"""

result = json.loads(obj)
result
"""
{'name': 'Wes',
 'cities_lived': ['Akron', 'Nashville', 'New York', 'San Francisco'],
 'pet': None,
 'siblings': [{'name': 'Scott', 'age': 34, 'hobbies': ['guitars', 'soccer']},
  {'name': 'Katie', 'age': 42, 'hobbies': ['diving', 'art']}]}
"""
```

---

### Convert a python object to JSON

`json.dumps` converts a Python object to JSON:

```py
import json

asjson = json.dumps(result)
asjson
'{"name": "Wes", "cities_lived": ["Akron", "Nashville", "New York", "San Francisco"], "pet": null, "siblings": [{"name": "Scott", "age": 34, "hobbies": ["guitars", "soccer"]}, {"name": "Katie", "age": 42, "hobbies": ["diving", "art"]}]}'
```

---

### Convert JSON to a dataframe

There are different ways of converting a JSON object to a dataframe:

- We can use the `json.loads` method to parse the data into a python dictionary and then convert that dictionary to a dataframe using `DataFrame` method.
- We can also use `read_json` method to read from a json file:

```py
import pandas as pd

df = pd.read_json("./examples/example.json")
print(df)
"""
   a  b  c
0  1  2  3
1  4  5  6
2  7  8  9
"""
```

---

### Convert a pandas object to JSON

If you need to export data from pandas to JSON, one way is using the `to_json` method on series and dataframe:

```py
import pandas as pd

df = pd.read_json("./examples/example.json")

df.to_json(sys.stdout)
# {"a":{"0":1,"1":4,"2":7},"b":{"0":2,"1":5,"2":8},"c":{"0":3,"1":6,"2":9}}

df.to_json(sys.stdout, orient="records")
# [{"a":1,"b":2,"c":3},{"a":4,"b":5,"c":6},{"a":7,"b":8,"c":9}]
```

---

---

## XML and HTML: Web Scraping

Python has many libraries for reading and writing data in HTML and XML formats. Examples include lxml, Beautiful Soup, and html5lib. Pandas has a built-in function, `read_html`, which uses all of these libraries to automatically parse tables out of HTML files as dataframe objects.

```py
import pandas as pd

listVar = pd.read_html("./examples/fdic_failed_bank_list.html")

len(listVar) # 1

df = listVar[0]
print(df.head())
# Because df has many columns, pandas inserts a line break character \.
```

---

---
