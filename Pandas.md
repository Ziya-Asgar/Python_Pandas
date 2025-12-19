# Pandas

- [Pandas](#pandas)
  - [Some Useful Links](#some-useful-links)
  - [Intro](#intro)
  - [Creating a Series](#creating-a-series)
    - [Creating a Series from a List](#creating-a-series-from-a-list)
      - [Specifying the index column while creating a series from a list](#specifying-the-index-column-while-creating-a-series-from-a-list)
    - [Creating a series from a dictionary](#creating-a-series-from-a-dictionary)
      - [Specifying the index labels while creating a series from a dictionary](#specifying-the-index-labels-while-creating-a-series-from-a-dictionary)
    - [Data Types in a series](#data-types-in-a-series)
      - [Converting datatypes of a series](#converting-datatypes-of-a-series)
  - [Creating a dataframe](#creating-a-dataframe)
    - [Creating a dataframe from a dictionary](#creating-a-dataframe-from-a-dictionary)
    - [Data Types in a dataframe](#data-types-in-a-dataframe)
      - [Specifying the columns while creating a dataframe from a dictionary](#specifying-the-columns-while-creating-a-dataframe-from-a-dictionary)
      - [Specifying the index labels while creating a dataframe from a dictionary](#specifying-the-index-labels-while-creating-a-dataframe-from-a-dictionary)
    - [Creating a dataframe from a nested dictionary](#creating-a-dataframe-from-a-nested-dictionary)
      - [Specifying the index labels while creating a dataframe from a nested dictionary](#specifying-the-index-labels-while-creating-a-dataframe-from-a-nested-dictionary)
    - [Creating a dataframe from an ndarray](#creating-a-dataframe-from-an-ndarray)
  - [Accessing and Retrieving data from a series and a dataframe](#accessing-and-retrieving-data-from-a-series-and-a-dataframe)
    - [Retrieving the array of items and index labels from a series](#retrieving-the-array-of-items-and-index-labels-from-a-series)
    - [Retrieving a list of columns and the index labels from a dataframe](#retrieving-a-list-of-columns-and-the-index-labels-from-a-dataframe)
    - [Retrieving the items from a series](#retrieving-the-items-from-a-series)
    - [Retrieving the items from a dataframe](#retrieving-the-items-from-a-dataframe)
      - [Retrieving the data of the columns of a dataframe](#retrieving-the-data-of-the-columns-of-a-dataframe)
      - [Retrieving the data of several columns of a dataframe](#retrieving-the-data-of-several-columns-of-a-dataframe)
      - [Accessing the items in rows of a dataframe](#accessing-the-items-in-rows-of-a-dataframe)
      - [`loc` and `iloc` operators](#loc-and-iloc-operators)
      - [Retrieving data from a series using the `loc` and `iloc`](#retrieving-data-from-a-series-using-the-loc-and-iloc)
      - [Retrieving data from rows of a dataframe using the `loc` and `iloc` operators](#retrieving-data-from-rows-of-a-dataframe-using-the-loc-and-iloc-operators)
      - [Retrieving the columns of a dataframe using the `loc` and `iloc` operators](#retrieving-the-columns-of-a-dataframe-using-the-loc-and-iloc-operators)
    - [Retrieving a single value using the `at` operator](#retrieving-a-single-value-using-the-at-operator)
    - [Retrieving the data as a copy from series or dataframe using the `take` method](#retrieving-the-data-as-a-copy-from-series-or-dataframe-using-the-take-method)
    - [Retrieving top and bottom rows of a dataframe with `head` and `tail`](#retrieving-top-and-bottom-rows-of-a-dataframe-with-head-and-tail)
    - [Retrieving the rows of a dataframe with the largest values](#retrieving-the-rows-of-a-dataframe-with-the-largest-values)
    - [Retrieving a random sample from a dataframe](#retrieving-a-random-sample-from-a-dataframe)
      - [`numpy.random.permutation` with `iloc`](#numpyrandompermutation-with-iloc)
      - [`numpy.random.permutation` with `pandas.DataFrame.take`](#numpyrandompermutation-with-pandasdataframetake)
      - [`pandas.DataFrame.sample`](#pandasdataframesample)
      - [Retrieving data from a dataframe based on data types](#retrieving-data-from-a-dataframe-based-on-data-types)
  - [Using booleans to access and retrieve data from a series and a dataframe](#using-booleans-to-access-and-retrieve-data-from-a-series-and-a-dataframe)
    - [Using booleans to retrieve specific data from a series](#using-booleans-to-retrieve-specific-data-from-a-series)
    - [Using boolean values to retrieve data from a dataframe](#using-boolean-values-to-retrieve-data-from-a-dataframe)
    - [Retrieving data using bitwise operators](#retrieving-data-using-bitwise-operators)
    - [Retrieving data using regular expressions](#retrieving-data-using-regular-expressions)
    - [Using boolean values to change the data in a dataframe](#using-boolean-values-to-change-the-data-in-a-dataframe)
    - [Checking if an item exists in the index, series and dataframes](#checking-if-an-item-exists-in-the-index-series-and-dataframes)
      - [Checking the Index object with the `in` operator](#checking-the-index-object-with-the-in-operator)
      - [Checking if an item exists in a series or a dataframe using the `isin` method](#checking-if-an-item-exists-in-a-series-or-a-dataframe-using-the-isin-method)
  - [Index Objects](#index-objects)
    - [Immutability of Index objects](#immutability-of-index-objects)
    - [Create a standalone index](#create-a-standalone-index)
    - [Names in a series](#names-in-a-series)
    - [Names in a dataframe](#names-in-a-dataframe)
    - [`set_names`](#set_names)
    - [Changing the index of a series](#changing-the-index-of-a-series)
    - [Changing the index of a dataframe](#changing-the-index-of-a-dataframe)
    - [Changing the column names of a dataframe](#changing-the-column-names-of-a-dataframe)
    - [Using the `rename` method for columns and index labels](#using-the-rename-method-for-columns-and-index-labels)
    - [Turning the column of a dataframe into the index labels](#turning-the-column-of-a-dataframe-into-the-index-labels)
    - [Set-like behaviour of Index objects](#set-like-behaviour-of-index-objects)
      - [Concatenate the index objects with the `append` method](#concatenate-the-index-objects-with-the-append-method)
      - [Find the differences between the index objects with the `difference` method](#find-the-differences-between-the-index-objects-with-the-difference-method)
      - [Find the common items in the index objects with the `intersection` method](#find-the-common-items-in-the-index-objects-with-the-intersection-method)
      - [Combine (without duplication) the index objects with the `union` method](#combine-without-duplication-the-index-objects-with-the-union-method)
      - [Delete the items in the index objects with the `delete` method](#delete-the-items-in-the-index-objects-with-the-delete-method)
      - [Delete the items in the index objects with the `drop` method](#delete-the-items-in-the-index-objects-with-the-drop-method)
      - [Insert elements into a specific position in the index using the `insert` method](#insert-elements-into-a-specific-position-in-the-index-using-the-insert-method)
      - [`is_unique`](#is_unique)
      - [`unique()`](#unique)
    - [Rearranging the indices with the `reindex` method](#rearranging-the-indices-with-the-reindex-method)
      - [Rearranging the indices of a series with `reindex`](#rearranging-the-indices-of-a-series-with-reindex)
      - [Rearranging the indices of a dataframe with `reindex`](#rearranging-the-indices-of-a-dataframe-with-reindex)
      - [Filling in missing values while using the `reindex` method](#filling-in-missing-values-while-using-the-reindex-method)
      - [Table of `reindex` arguments](#table-of-reindex-arguments)
  - [Modifying data in series and dataframes](#modifying-data-in-series-and-dataframes)
    - [Copying series and dataframes](#copying-series-and-dataframes)
    - [Adding new values to a specific position in a series](#adding-new-values-to-a-specific-position-in-a-series)
    - [Adding new columns to a dataframe](#adding-new-columns-to-a-dataframe)
    - [Modifying values in a series](#modifying-values-in-a-series)
      - [Using `loc` and `iloc`](#using-loc-and-iloc)
      - [Using the `replace` method](#using-the-replace-method)
    - [Modifying values in the specific column of a dataframe](#modifying-values-in-the-specific-column-of-a-dataframe)
    - [Modifying values using `where`](#modifying-values-using-where)
    - [Dividing data into groups](#dividing-data-into-groups)
      - [Using the `cut` method](#using-the-cut-method)
      - [Using the `qcut` method](#using-the-qcut-method)
    - [Transposing a dataframe](#transposing-a-dataframe)
  - [Converting series and dataframes to other objects](#converting-series-and-dataframes-to-other-objects)
    - [Converting a series to a dictionary](#converting-a-series-to-a-dictionary)
    - [Converting a dataframe to an ndarray](#converting-a-dataframe-to-an-ndarray)
  - [Deleting the data from series and dataframes](#deleting-the-data-from-series-and-dataframes)
    - [Deleting data from a series](#deleting-data-from-a-series)
      - [Using the `del` keyword to delete the items from a series](#using-the-del-keyword-to-delete-the-items-from-a-series)
      - [Using the `drop` method to delete the items from a series](#using-the-drop-method-to-delete-the-items-from-a-series)
    - [Deleting data from a dataframe](#deleting-data-from-a-dataframe)
      - [Using the `del` keyword to delete a column from a dataframe](#using-the-del-keyword-to-delete-a-column-from-a-dataframe)
      - [Using the `drop` method to delete rows and columns from a dataframe](#using-the-drop-method-to-delete-rows-and-columns-from-a-dataframe)
      - [Using the `pop` method to delete a column of a dataframe](#using-the-pop-method-to-delete-a-column-of-a-dataframe)
  - [Dealing with missing data in series and dataframes](#dealing-with-missing-data-in-series-and-dataframes)
    - [Check for missing data in a series](#check-for-missing-data-in-a-series)
    - [Check for missing data in a dataframe](#check-for-missing-data-in-a-dataframe)
    - [`isnull()`](#isnull)
    - [Replacing missing values in a series](#replacing-missing-values-in-a-series)
    - [Replacing missing values in a dataframe](#replacing-missing-values-in-a-dataframe)
    - [Dropping the missing values in a series](#dropping-the-missing-values-in-a-series)
    - [Dropping the missing values in a dataframe](#dropping-the-missing-values-in-a-dataframe)
  - [Dealing with duplicate values in a dataframe](#dealing-with-duplicate-values-in-a-dataframe)
    - [Checking the existence of duplicate values in a dataframe](#checking-the-existence-of-duplicate-values-in-a-dataframe)
    - [Dropping duplicate values in a dataframe](#dropping-duplicate-values-in-a-dataframe)
  - [Sorting and Ranking](#sorting-and-ranking)
    - [Sorting a series by indices](#sorting-a-series-by-indices)
    - [Sorting a dataframe by indices](#sorting-a-dataframe-by-indices)
    - [Sorting a series by values](#sorting-a-series-by-values)
      - [Placement of missing values while sorting by values](#placement-of-missing-values-while-sorting-by-values)
    - [Sorting a dataframe by values](#sorting-a-dataframe-by-values)
    - [Ranking a series](#ranking-a-series)
      - [Tie-breaking methods with `rank`](#tie-breaking-methods-with-rank)
  - [Arithmetic and Data Alignment](#arithmetic-and-data-alignment)
    - [Table of different arithmetic methods](#table-of-different-arithmetic-methods)
    - [Arithmetic operations on series](#arithmetic-operations-on-series)
    - [Arithmetic operations on dataframes](#arithmetic-operations-on-dataframes)
  - [Descriptive Statistical methods](#descriptive-statistical-methods)
    - [Table of some statistical methods](#table-of-some-statistical-methods)
    - [`sum`](#sum)
    - [`mean`](#mean)
    - [`describe`](#describe)
    - [`info`](#info)
    - [Unique Values, Value Counts](#unique-values-value-counts)
      - [`unique`](#unique-1)
      - [`value_counts`](#value_counts)
  - [Various Functions and Methods](#various-functions-and-methods)
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
    - [`transform`](#transform)
  - [Extension types (Accessors) in Pandas](#extension-types-accessors-in-pandas)
    - [`str`](#str)
    - [`dt`](#dt)
    - [`cat`](#cat)
      - [Table of categorical methods](#table-of-categorical-methods)
      - [Creating a series with `Categorical` data type](#creating-a-series-with-categorical-data-type)
      - [Specifying the ordered categories](#specifying-the-ordered-categories)
      - [Converting an unordered categorial to an ordered one](#converting-an-unordered-categorial-to-an-ordered-one)
      - [Converting a series with a different data type to a `Categorical` type](#converting-a-series-with-a-different-data-type-to-a-categorical-type)
      - [The `categories` attribute](#the-categories-attribute)
      - [The `codes` attribute](#the-codes-attribute)
      - [The `rename_categories` method](#the-rename_categories-method)
      - [The `add_categories` method](#the-add_categories-method)
      - [The `set_categories` method](#the-set_categories-method)
  - [Reading and Writing Data in Text Format](#reading-and-writing-data-in-text-format)
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
  - [Binary Data Formats](#binary-data-formats)
    - [`pickle` module](#pickle-module)
    - [Reading Microsoft Excel Files](#reading-microsoft-excel-files)
      - [Using the `ExcelFile` class](#using-the-excelfile-class)
      - [Using the `read_excel` method](#using-the-read_excel-method)
      - [Writing to an excel file](#writing-to-an-excel-file)
  - [Interacting with Web APIs](#interacting-with-web-apis)
  - [Data Wrangling: Join, Combine, and Reshape](#data-wrangling-join-combine-and-reshape)
    - [Hierarchical Indexing](#hierarchical-indexing)
      - [Create a series with hierarchical indexing](#create-a-series-with-hierarchical-indexing)
      - [Selecting subsets of data in series using partial indexing](#selecting-subsets-of-data-in-series-using-partial-indexing)
      - [Turning hierarchically indexed series into a dataframe](#turning-hierarchically-indexed-series-into-a-dataframe)
      - [Dataframe with Hierarchical index and columns](#dataframe-with-hierarchical-index-and-columns)
      - [Checking the number of index levels](#checking-the-number-of-index-levels)
      - [Selecting subsets of data in a dataframe using partial indexing](#selecting-subsets-of-data-in-a-dataframe-using-partial-indexing)
      - [Creating standalone `MultiIndex`](#creating-standalone-multiindex)
      - [Reordering and sorting levels of hierarchical index](#reordering-and-sorting-levels-of-hierarchical-index)
      - [Indexing with a DataFrame's columns](#indexing-with-a-dataframes-columns)
    - [Combining and Merging Datasets](#combining-and-merging-datasets)
      - [Table for an argument reference on `pandas.merge`](#table-for-an-argument-reference-on-pandasmerge)
      - [Database-Style DataFrame Joins](#database-style-dataframe-joins)
      - [Merging on Index](#merging-on-index)
      - [Concatenating along an axis](#concatenating-along-an-axis)
      - [Combining Data with Overlap](#combining-data-with-overlap)
    - [Reshaping and Pivoting](#reshaping-and-pivoting)
      - [Reshaping with Hierarchical Indexing](#reshaping-with-hierarchical-indexing)
      - [Pivoting “Long” to “Wide” Format](#pivoting-long-to-wide-format)
      - [Pivoting “Wide” to “Long” Format](#pivoting-wide-to-long-format)
  - [Data Aggregation and Group Operations](#data-aggregation-and-group-operations)
    - [Using `groupby` with a series](#using-groupby-with-a-series)
    - [Using `groupby` with a hierarchically indexed series](#using-groupby-with-a-hierarchically-indexed-series)
    - [Grouping using a dictionary](#grouping-using-a-dictionary)
    - [Grouping using a function](#grouping-using-a-function)
    - [Using `groupby` with a dataframe](#using-groupby-with-a-dataframe)
    - [Using `groupby` with a hierarchically indexed dataframe](#using-groupby-with-a-hierarchically-indexed-dataframe)
    - [Group by columns](#group-by-columns)
    - [Iterating over groups](#iterating-over-groups)
    - [Data Aggregation](#data-aggregation)
      - [Custom function for aggregation](#custom-function-for-aggregation)
      - [`pivot_table`](#pivot_table)
      - [Crosstab](#crosstab)
  - [Time Series](#time-series)
    - [Indexing, Selection, Subsetting](#indexing-selection-subsetting)
    - [Date Ranges, Frequencies, and Shifting](#date-ranges-frequencies-and-shifting)
    - [`date_range`](#date_range)
    - [`day_name`](#day_name)
    - [Time Zone Handling](#time-zone-handling)
    - [Periods and Period Arithmetic](#periods-and-period-arithmetic)
    - [Resampling and Frequency Conversion](#resampling-and-frequency-conversion)
      - [Downsampling](#downsampling)
      - [Upsampling and Interpolation](#upsampling-and-interpolation)
      - [Grouped Time Resampling](#grouped-time-resampling)
  - [Introduction to Modeling Libraries in Python](#introduction-to-modeling-libraries-in-python)

<hr>

## Some Useful Links

- https://wesmckinney.com/book/pandas-basics
- https://github.com/wesm/pydata-book
- https://www.practicaldatascience.org/intro.html
- https://towardsdatascience.com/pandas-dtype-specific-operations-accessors-c749bafb30a4

<hr>
<hr>

## Intro

`pandas` is designed for working with tabular or heterogeneous data. We need to import it to use it:

```py
import pandas as pd
```

There are two main data structures in pandas: **Series** and **DataFrame**. Here is an example of separately importing them:

```py
from pandas import Series, DataFrame
```

A `Series` is a one-dimensional array-like object containing a sequence of values of the **same type**. All the values also have corresponding index labels.

A `DataFrame` represents a rectangular table of data and contains an ordered, named collection of columns, each of which can be a different value type (numeric, string, Boolean, etc.). Dataframes have both a row and column index. While a dataframe is physically two-dimensional, you can use it to represent higher dimensional data in a tabular format using hierarchical indexing. Dataframes actually consist of series.

<hr>

## Creating a Series

### Creating a Series from a List

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

#### Specifying the index column while creating a series from a list

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

<hr>

### Creating a series from a dictionary

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

#### Specifying the index labels while creating a series from a dictionary

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

<hr>

### Data Types in a series

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

#### Converting datatypes of a series

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

<hr>

## Creating a dataframe

There are many ways to construct a dataframe. One of the most common is from a dictionary of equal-length lists or NumPy arrays.

### Creating a dataframe from a dictionary

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

### Data Types in a dataframe

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

#### Specifying the columns while creating a dataframe from a dictionary

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

#### Specifying the index labels while creating a dataframe from a dictionary

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

### Creating a dataframe from a nested dictionary

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

#### Specifying the index labels while creating a dataframe from a nested dictionary

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

<hr>

### Creating a dataframe from an ndarray

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

<hr>

## Accessing and Retrieving data from a series and a dataframe

### Retrieving the array of items and index labels from a series

We can get the array representation of series using the `array` attribute. To get the indices, we can use the `index` attribute:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103])
print(ser.array)
"""
<NumpyExtensionArray>
[np.int64(100), np.int64(101), np.int64(102), np.int64(103)]
Length: 4, dtype: int64
"""

print(ser.index)
# RangeIndex(start=0, stop=4, step=1)
```

<hr>

### Retrieving a list of columns and the index labels from a dataframe

We can retrieve the list of columns and the index label in a DataFrame with the `columns` and `index` attributes. They return an index object:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns)
# Index(['Istanbul', 'Baku', 'Tashkent', 'Karbala'], dtype='object')

print(df.index)
# Index([2020, 2021, 2022], dtype='int64')
```

Sometimes one wants direct access to the data, not to the DataFrame. This can be achieved with `<df>.values`

<hr>

### Retrieving the items from a series

We can use the index labels with the square bracket notation to refer to items in a series:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], ["d", "b", "a", "c"])
print(ser["a"]) # 102
```

If we want to retrieve more than one item from a series, we need to use the index labels with double square brackets. The result itself will be a series object:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], ["d", "b", "a", "c"])

print(ser["a"]) # 102
print(ser[["c", "a", "d"]])
"""
c    103
a    102
d    100
dtype: int64
"""
```

<hr>

### Retrieving the items from a dataframe

#### Retrieving the data of the columns of a dataframe

A column in a DataFrame can be retrieved as a Series either by using `frame["column"]` or `frame.column` syntax.

- `frame["column"]` works for any column name,
- but `frame.column` works only when the column name is a valid Python variable name and does not conflict with any of the method names in a `DataFrame`. For example, if a column name contains whitespace or symbols other than underscores, it cannot be accessed with the dot attribute method.

Here is an example of retrieving the data in the specific columns of a dataframe:

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

print(df["Name"])
"""
0       Aisu
1      Temir
2    Gulnara
3     Azamat
4    Dilyara
5     Fatima
6      Aydin
7       Oğuz
8      Asgar
9     Gulzar
Name: Name, dtype: object
"""

print(df.Name)
"""
0       Aisu
1      Temir
2    Gulnara
3     Azamat
4    Dilyara
5     Fatima
6      Aydin
7       Oğuz
8      Asgar
9     Gulzar
Name: Name, dtype: object
"""
```

#### Retrieving the data of several columns of a dataframe

We can also retrieve the data from more than one column. For this, we need to use 2 square brackets:

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
print(df[["Name", "Age"]])
"""
      Name   Age
0     Aisu  27.0
1    Temir  31.0
2  Gulnara   NaN
3   Azamat  29.0
4  Dilyara  34.0
5   Fatima  22.0
6    Aydin  28.0
7     Oğuz   NaN
8    Asgar  30.0
9   Gulzar  24.0
"""
```

String methods can also help us in selecting columns of a dataframe:

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
print(df[["Name"] + [col for col in df.columns if col.startswith("S")]])
"""
      Name    Salary
0     Aisu  60000.50
1    Temir  72000.75
2  Gulnara  55000.00
3   Azamat       NaN
4  Dilyara  75000.10
5   Fatima  50000.00
6    Aydin  68000.50
7     Oğuz  62000.00
8    Asgar       NaN
9   Gulzar  90000.00
"""
```

#### Accessing the items in rows of a dataframe

Here is an example of retrieving rows of data in a dataframe:

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

print(df[:2])
"""
    Name   Age     City    Salary Is_Employed
0   Aisu  27.0   Almaty  60000.50         Yes
1  Temir  31.0  Bishkek  72000.75          No
"""
```

<hr>

#### `loc` and `iloc` operators

#### Retrieving data from a series using the `loc` and `iloc`

The preferred way to select index values is with the special `loc` operator:

```py
import numpy as np
import pandas as pd

ser =  pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
dtype: float64
"""

print(ser["b"]) # 1.0
print(ser.loc["b"]) # 1.0
```

The `loc` operator uses the index labels, but we can also use the index numbers. The `iloc` operator indexes exclusively with integers:

```py
import numpy as np
import pandas as pd

ser =  pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
dtype: float64
"""

print(ser["b"]) # 1
print(ser.loc["b"]) # 1

print(ser.iloc[1]) # 1
```

#### Retrieving data from rows of a dataframe using the `loc` and `iloc` operators

Just like with a series, rows of a dataframe can be retrieved by position or name with the special `iloc` and `loc` attributes:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021])
"""
Istanbul    15.52
Baku         2.25
Tashkent     2.52
Karbala      1.02
Name: 2021, dtype: float64
"""

print(df.iloc[1])
"""
Istanbul    15.52
Baku         2.25
Tashkent     2.52
Karbala      1.02
Name: 2021, dtype: float64
"""
```

If we want to get the data in more than one row, we need to use 2 square brackets with `iloc` and `loc`:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[[2021, 2022]])
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

print(df.iloc[[1, 2]])
"""
      Istanbul  Baku  Tashkent  Karbala
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

#### Retrieving the columns of a dataframe using the `loc` and `iloc` operators

The result of selecting a single row is a Series with an index that contains the DataFrame's column labels. When we use `loc` and `iloc` to retrieve more than one row, we get back another dataframe. This means that we can retrieve the columns of this returned dataframe, as well. In the below example, we are retrieving the `Baku` column of the returned dataframe. Note that with `iloc`, we cannot specify the column name and instead we need to use column number, as `iloc` uses integers to refer to rows and columns.

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[[2021, 2022], "Baku"])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""

print(df.iloc[[1, 2], 1])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""
```

We can implement the index slicing with the `loc` and `iloc` operators:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021:2022, "Baku"])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""

print(df.iloc[1:3, 1])
"""
2021    2.25
2022    2.27
Name: Baku, dtype: float64
"""
```

When we use the `loc` and `iloc`, we can also use the index slicing for columns:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)

print(df.loc[2021:2022, "Istanbul":"Tashkent"])
"""
      Istanbul  Baku  Tashkent
2021     15.52  2.25      2.52
2022     15.60  2.27       NaN
"""

print(df.iloc[1:3, 0:3])
"""
      Istanbul  Baku  Tashkent
2021     15.52  2.25      2.52
2022     15.60  2.27       NaN
"""
```

<hr>

### Retrieving a single value using the `at` operator

If we want to retrieve or change a single value in a series or a dataframe, we can use the `at` operator. This is used more to change a value rather than retrieving data:

```py
import pandas as pd

ser = pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser.at["b"]) # 1
```

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.at[2021, "Baku"]) # 2.25
```

`iat` is the version of `at` that uses only integers to refer to rows and columns (similar to `iloc`).

<hr>

### Retrieving the data as a copy from series or dataframe using the `take` method

`pandas.DataFrame.take` returns the copy of elements in the given row and columns:

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

print(df.take([1, 4]))
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

We may retrieve the copy of items using negative integers, starting from the end of the object:

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


print(df.take([-1]))
"""
     Name   Age      City   Salary Is_Employed
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

By invoking `take` with `axis="columns"`, we could also select the columns:

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

print(df.take([0, 2], axis="columns"))
"""
      Name      City
0     Aisu    Almaty
1    Temir   Bishkek
2  Gulnara  Tashkent
3   Azamat    Astana
4  Dilyara       NaN
5   Fatima     Kazan
6    Aydin  Istanbul
7     Oğuz    Ankara
8    Asgar      Baku
9   Gulzar  Ashgabat
"""
```

<hr>

### Retrieving top and bottom rows of a dataframe with `head` and `tail`

If we have a large DataFrame, we can use the `head` method on the DataFrame instance, to select the first 5 rows:

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
```

If we want to see specific number of rows, we can specify the number of rows to be outputted with the `head` method:

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

# show 2 rows
print(df.head(2))
"""
    Name   Age     City    Salary Is_Employed
0   Aisu  27.0   Almaty  60000.50         Yes
1  Temir  31.0  Bishkek  72000.75          No
"""
```

Similarly, the `tail` method returns the last five rows:

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

print(df.tail())
"""
     Name   Age      City   Salary Is_Employed
5  Fatima  22.0     Kazan  50000.0          No
6   Aydin  28.0  Istanbul  68000.5         NaN
7    Oğuz   NaN    Ankara  62000.0         Yes
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""

print(df.tail(2))
"""
     Name   Age      City   Salary Is_Employed
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

<hr>

### Retrieving the rows of a dataframe with the largest values

If we want to see the largest values in a column of a dataframe, we can use the `nlargest` method:

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

print(df["Age"].nlargest(3))
"""
4    34.0
1    31.0
8    30.0
Name: Age, dtype: float64
"""
```

The above use the of `nlargest` method showed the largest values for a specific column. If we want to retrieve the largest values for a column, but see all the columns in a dataframe, we can use the `nlargest` method in a slightly different way:

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

print(df.nlargest(3, "Age"))
"""
      Name   Age     City    Salary Is_Employed
4  Dilyara  34.0      NaN  75000.10         Yes
1    Temir  31.0  Bishkek  72000.75          No
8    Asgar  30.0     Baku       NaN          No
"""
```

Similarly, for the smallest values in a dataframe, we can use the `nsmallest` method:

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

print(df.nsmallest(3, "Age"))
"""
     Name   Age      City   Salary Is_Employed
5  Fatima  22.0     Kazan  50000.0          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
0    Aisu  27.0    Almaty  60000.5         Yes
"""
```

<hr>

### Retrieving a random sample from a dataframe

#### `numpy.random.permutation` with `iloc`

The `numpy.random.permutation` method randomly permutes a sequence, or returns a permuted range. We can use it together with `iloc` to randomly reorder a series or the rows in a dataframe.

```py
import numpy as np
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame)

sampler = np.random.permutation(5)
print(sampler) # [4 2 0 3 1]

print(df.iloc[sampler])
"""
      Name   Age      City    Salary Is_Employed
4  Dilyara  34.0       NaN  75000.10         Yes
2  Gulnara   NaN  Tashkent  55000.00         Yes
0     Aisu  27.0    Almaty  60000.50         Yes
3   Azamat  29.0    Astana       NaN          No
1    Temir  31.0   Bishkek  72000.75          No
"""
```

#### `numpy.random.permutation` with `pandas.DataFrame.take`

We can use the `numpy.random.permutation` method with the `pandas.DataFrame.take` method as well:

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

sampler = np.random.permutation(5)
print(sampler) # [4 2 0 3 1]

print(df.take(sampler))
"""
      Name   Age      City    Salary Is_Employed
4  Dilyara  34.0       NaN  75000.10         Yes
2  Gulnara   NaN  Tashkent  55000.00         Yes
0     Aisu  27.0    Almaty  60000.50         Yes
3   Azamat  29.0    Astana       NaN          No
1    Temir  31.0   Bishkek  72000.75          No
"""
```

#### `pandas.DataFrame.sample`

To select a random subset without replacement (the same row cannot appear twice), you can use the `sample` method on series and dataframe:

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

print(df.sample(n=3))
"""
      Name   Age    City   Salary Is_Employed
4  Dilyara  34.0     NaN  75000.1         Yes
3   Azamat  29.0  Astana      NaN          No
8    Asgar  30.0    Baku      NaN          No
"""

print(df.sample(n=3))
"""
    Name   Age      City   Salary Is_Employed
7   Oğuz   NaN    Ankara  62000.0         Yes
0   Aisu  27.0    Almaty  60000.5         Yes
6  Aydin  28.0  Istanbul  68000.5         NaN
"""
```

To generate a sample with replacement (to allow repeat choices), pass `replace=True` to `sample`:

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

print(df.sample(n=6, replace=True))
"""
     Name   Age      City   Salary Is_Employed
8   Asgar  30.0      Baku      NaN          No
6   Aydin  28.0  Istanbul  68000.5         NaN
7    Oğuz   NaN    Ankara  62000.0         Yes
3  Azamat  29.0    Astana      NaN          No
8   Asgar  30.0      Baku      NaN          No
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""
```

<hr>

#### Retrieving data from a dataframe based on data types

To retrieve data from a dataframe based on data dtypes, we use `select_dtypes`:

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
print(
  df.dtypes
)
"""
Name            object
Age            float64
City            object
Salary         float64
Is_Employed     object
dtype: object
"""

print(
  df.select_dtypes(include="number")
)
"""
    Age    Salary
0  27.0  60000.50
1  31.0  72000.75
2   NaN  55000.00
3  29.0       NaN
4  34.0  75000.10
5  22.0  50000.00
6  28.0  68000.50
7   NaN  62000.00
8  30.0       NaN
9  24.0  90000.00
"""
```

<hr>

## Using booleans to access and retrieve data from a series and a dataframe

### Using booleans to retrieve specific data from a series

Similar to `numpy` arrays, in `pandas` we can use boolean arrays to retrieve the specific values from a series:

```py
import pandas as pd

ser = pd.Series([100, -101, 102, -103], ["d", "b", "a", "c"])

print(ser)
"""
d    100
b   -101
a    102
c   -103
dtype: int64
"""

print(ser > 0)
"""
d     True
b    False
a     True
c    False
dtype: bool
"""

print(ser[ser > 0])
"""
d    100
a    102
dtype: int64
"""
```

### Using boolean values to retrieve data from a dataframe

We can use boolean arrays to retrieve the specific values from a dataframe:

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

print(df[df["Age"] > 30])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

Boolean arrays can be used with `loc` but not `iloc`:

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

print(df.loc[df.loc[:,"Age"] > 30])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""
```

### Retrieving data using bitwise operators

Another common operation is the use of boolean vectors to filter the data. The operators are:

- `|` for `or`,
- `&` for `and`, and
- `~` for `not`.

These must be grouped by using parentheses, since by default Python will evaluate an expression such as `df['A'] > 2 & df['B'] < 3` as `df['A'] > (2 & df['B']) < 3`, while the desired evaluation order is `(df['A'] > 2) & (df['B'] < 3)`:

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
print( df[ ( df["City"] == "Baku" ) | ( df["City"] == "Istanbul" ) | ( df["City"] == "Ashgabat" ) ] )
"""
     Name   Age      City
6   Aydin  28.0  Istanbul
8   Asgar  30.0      Baku
9  Gulzar  24.0  Ashgabat
"""

print( df[ (df["Salary"] > 60000) & ( (df["City"] == "Almaty") | (df["City"] == "Ashgabat") ) ] )
"""
     Name   Age      City   Salary Is_Employed
0    Aisu  27.0    Almaty  60000.5         Yes
9  Gulzar  24.0  Ashgabat  90000.0         Yes
"""

print( df[~(( df["City"] == "Istanbul" ) | ( df["City"] == "Baku" ))] )
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana       NaN          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
7     Oğuz   NaN    Ankara  62000.00         Yes
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

### Retrieving data using regular expressions

Pandas lets us use regular expressions directly without importing `re` module.

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

print(df.loc[df["Name"].str.contains(r"a$")])
"""
      Name   Age      City   Salary Is_Employed
2  Gulnara   NaN  Tashkent  55000.0         Yes
4  Dilyara  34.0       NaN  75000.1         Yes
5   Fatima  22.0     Kazan  50000.0          No
"""
```

### Using boolean values to change the data in a dataframe

We can use the Boolean DataFrame to assign different values in a dataframe:

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

ageBool = df["Age"] > 30
print(df[ageBool])
"""
      Name   Age     City    Salary Is_Employed
1    Temir  31.0  Bishkek  72000.75          No
4  Dilyara  34.0      NaN  75000.10         Yes
"""

df.loc[ageBool, "Age"] = df.loc[ageBool, "Age"] * 10
print(df[ageBool])
"""
      Name    Age     City    Salary Is_Employed
1    Temir  310.0  Bishkek  72000.75          No
4  Dilyara  340.0      NaN  75000.10         Yes
"""
```

<hr>

### Checking if an item exists in the index, series and dataframes

#### Checking the Index object with the `in` operator

We can check if some item is part of the Index object using the `in` operator:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["a", "b", "c", "d"])

print("a" in ser) # True
print("e" in ser) # False
```

<hr>

#### Checking if an item exists in a series or a dataframe using the `isin` method

`isin` method checks if provided values are in a series or a dataframe:

```py
import pandas as pd

listForSeries = ['Apple', 'Banana', 'Cherry', 'Date', np.nan, 'Fig', 'Grape', np.nan, 'Kiwi', 'Lemon']
ser = pd.Series(listForSeries)

check = ser.isin(["Apple", "Cherry"])
print(check)
"""
0     True
1    False
2     True
3    False
4    False
5    False
6    False
7    False
8    False
9    False
dtype: bool
"""
```

We can use the boolean data that `isin` provides to retrieve the data from original series or dataframe:

```py
import pandas as pd

listForSeries = ['Apple', 'Banana', 'Cherry', 'Date', np.nan, 'Fig', 'Grape', np.nan, 'Kiwi', 'Lemon']
ser = pd.Series(listForSeries)

check = ser.isin(["Apple", "Cherry"])
print(ser[check])
"""
0     Apple
2    Cherry
dtype: object
"""
```

The `isin` method can also check if an item is part of the index:

```py
import pandas as pd

ser = pd.Series([100, 101, 102, 103], index=["a", "b", "c", "d"])

print(ser.index.isin(["a"])) # [ True False False False]
```

<hr>

## Index Objects

`pandas`’s Index objects are responsible for holding the axis labels (including a DataFrame's column names) and other metadata. Any array or other sequence of labels you use when constructing a series or dataframe is internally converted to an Index object.

<hr>

### Immutability of Index objects

Index objects are immutable and thus can’t be modified by the user:

```py
import pandas as pd

ser = pd.Series(np.arange(3), index=["a", "b", "c"])

print(ser)
"""
a    0
b    1
c    2
dtype: int64
"""

print(ser.index)
# Index(['a', 'b', 'c'], dtype='object')

print(ser.index[1]) # b
ser.index[1] = "d" # Error
```

<hr>

### Create a standalone index

We can create an index object on its own and use it later on:

```py
import numpy as np
import pandas as pd

indexObj = pd.Index(np.arange(10, 14), name="numbers")
print(indexObj) # Index([10, 11, 12, 13], dtype='int64', name='numbers')

print(pd.Series(np.arange(1000, 1004), index=indexObj))
"""
numbers
10    1000
11    1001
12    1002
13    1003
dtype: int64
"""
```

<hr>

### Names in a series

Both the series object itself and its index have a `name` attribute:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

ser.name = "population series"
ser.index.name = "cities_index"

print(ser)
"""
cities_index
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Nur-Sultan    18.0
Name: population series, dtype: float64
"""
```

<hr>

### Names in a dataframe

DataFrame’s `index` and `columns` have their `name` attributes. DataFrame itself does not have a `name` attribute:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df.columns.name = "city"
df.index.name = "year"

print(df)
"""
city  Istanbul  Baku  Tashkent  Karbala
year
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

### `set_names`

The `set_names` method in the pandas library is used to set the names of the levels in an index:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df.columns = df.columns.set_names("city")
df.index = df.index.set_names("year")

print(df)
"""
city  Istanbul  Baku  Tashkent  Karbala
year
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""
```

<hr>

### Changing the index of a series

We can change the index labels of a series using the `index` attribute and reassignment:

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

ser.index = ["zeroth", "first", "second", "third"]
print(ser)
"""
zeroth    100
first     101
second    102
third     103
dtype: int64
"""
```

<hr>

### Changing the index of a dataframe

We can change the index labels of a dataframe in the same way:

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

df.index = np.arange(100, 110)
print(df)
"""
        Name   Age      City    Salary Is_Employed
100     Aisu  27.0    Almaty  60000.50         Yes
101    Temir  31.0   Bishkek  72000.75          No
102  Gulnara   NaN  Tashkent  55000.00         Yes
103   Azamat  29.0    Astana       NaN          No
104  Dilyara  34.0       NaN  75000.10         Yes
105   Fatima  22.0     Kazan  50000.00          No
106    Aydin  28.0  Istanbul  68000.50         NaN
107     Oğuz   NaN    Ankara  62000.00         Yes
108    Asgar  30.0      Baku       NaN          No
109   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

We can also use the `map` method with the index object, to change the index labels in a custom way:

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

def func(index):
  return index - 2000

df.index = df.index.map(func)
print(df)
"""
    Istanbul  Baku  Tashkent  Karbala
20     15.46  2.23      2.50     1.00
21     15.52  2.25      2.52     1.02
22     15.60  2.27       NaN     1.04
"""
```

### Changing the column names of a dataframe

To change the column names of a dataframe, we can use the `columns` attribute of a dataframe:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns) # Index(['Istanbul', 'Baku'], dtype='object')

df.columns = ["Ist", "Baku"]
print(df.columns) # Index(['Ist', 'Baku'], dtype='object')
```

### Using the `rename` method for columns and index labels

The above way of renaming columns would be more useful when we need to change all the column names or maybe most of it. However, if we want to rename specific columns, we can use the `rename` method:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.columns) # Index(['Istanbul', 'Baku', 'Tashkent', 'Karbala'], dtype='objec

df.rename(columns={"Istanbul":"Ist"}, inplace=True)
print(df.columns) # Index(['Ist', 'Baku', 'Tashkent', 'Karbala'], dtype='object')
```

The `rename` method can also change the index labels:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
print(df.index) # Index([2020, 2021, 2022], dtype='int64')

df.rename(index={2020:20, 2021:21}, inplace=True)
print(df.index) # Index([20, 21, 2022], dtype='int64')
```

The `rename` method, and many other operations that we are doing on a dataframe do not change the dataframe in place. They usually return a new dataframe. If we want the original dataframe to be changed by our operation, many methods accept the `inplace=True` argument, that we can use.

### Turning the column of a dataframe into the index labels

We turn a specific column of a dataframe into the index label column using the `set_index` method:

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

df.set_index("Name", inplace=True)
print(df)
"""
          Age      City    Salary Is_Employed
Name
Aisu     27.0    Almaty  60000.50         Yes
Temir    31.0   Bishkek  72000.75          No
Gulnara   NaN  Tashkent  55000.00         Yes
Azamat   29.0    Astana       NaN          No
Dilyara  34.0       NaN  75000.10         Yes
Fatima   22.0     Kazan  50000.00          No
Aydin    28.0  Istanbul  68000.50         NaN
Oğuz      NaN    Ankara  62000.00         Yes
Asgar    30.0      Baku       NaN          No
Gulzar   24.0  Ashgabat  90000.00         Yes
"""
```

If we want to revert the changes, we can use the `reset_index` method, which also accepts `inplace=True`.

<hr>

### Set-like behaviour of Index objects

In addition to being array-like, an Index also behaves like a fixed-size set. However, unlike Python sets, a pandas Index can contain duplicate labels. Each Index has a number of methods and properties for set logic. Here are some of them:

| Method/Property  | Description                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------- |
| `append()`       | Concatenate with additional Index objects, producing a new Index                          |
| `difference()`   | Compute set difference as an Index                                                        |
| `intersection()` | Compute set intersection                                                                  |
| `union()`        | Compute set union                                                                         |
| `delete()`       | Compute new Index with element at Index i deleted                                         |
| `drop()`         | Compute new Index by deleting passed values                                               |
| `insert()`       | Compute new Index by inserting element at Index i                                         |
| `is_unique`      | Returns `True` if the Index has no duplicate values                                       |
| `unique()`       | Compute the array of unique values in the Index                                           |
| `isin()`         | Compute Boolean array indicating whether each value is contained in the passed collection |

#### Concatenate the index objects with the `append` method

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(6))
print(ser)
"""
0    0
1    1
2    2
3    3
4    4
5    5
dtype: int64
"""

index1 = pd.Index(["a", "b", "c"])
index2 = pd.Index(["d", "e", "f"])

index1 # Index(['a', 'b', 'c'], dtype='object')
index2 # Index(['d', 'e', 'f'], dtype='object')

index1.append(index2) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')

ser.index = index1.append(index2)
print(ser)
"""
a    0
b    1
c    2
d    3
e    4
f    5
dtype: int64
"""
```

You can also append multiple Index objects at once:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(6))
print(ser)
"""
0    0
1    1
2    2
3    3
4    4
5    5
dtype: int64
"""

index1 = pd.Index(["a", "b"])
index2 = pd.Index(["c", "d"])
index3 = pd.Index(["e", "f"])

index1.append([index2, index3]) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')

ser.index = index1.append([index2, index3])
print(ser)
"""
a    0
b    1
c    2
d    3
e    4
f    5
dtype: int64
"""
```

#### Find the differences between the index objects with the `difference` method

The `difference` method of the Pandas Index object is used to find the different elements between two Index objects.

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c"])

index1.difference(index2) # Index(['b', 'd'], dtype='object')
```

You can also find the difference between an Index and a list or set:

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])

index1.difference(["d", "e"]) # Index(['a', 'b', 'c'], dtype='object')
```

#### Find the common items in the index objects with the `intersection` method

The `intersection` method of the Pandas Index object is used to find the common elements between two Index objects.

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c"])

index1.intersection(index2) # Index(['a', 'c'], dtype='object')
```

You can also find the intersection between an Index and a list or set:

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])

index1.intersection(["d", "a", "e"]) # Index(['a', 'd'], dtype='object')
```

#### Combine (without duplication) the index objects with the `union` method

The `union` method of the Pandas Index object is used to combine two or more Index objects while removing any duplicate elements

```py
import pandas as pd

index1 = pd.Index(["a", "b", "c", "d"])
index2 = pd.Index(["a", "c", "e", "f"])

index1.union(index2) # Index(['a', 'b', 'c', 'd', 'e', 'f'], dtype='object')
```

You can also find the union between an Index and a list or set:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.union(["b", "e"]) # Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
```

#### Delete the items in the index objects with the `delete` method

You can delete a single element by passing a single index value:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.delete(0) # Index(['b', 'c', 'd'], dtype='object')
```

You can also delete several elements by passing an array of index values:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.delete([0, 1]) # Index(['c', 'd'], dtype='object')
```

#### Delete the items in the index objects with the `drop` method

The `drop` method of the Pandas Index object is used to remove specific elements from the Index by their labels. Here’s an example to illustrate how it works:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.drop("a") # Index(['b', 'c', 'd'], dtype='object')
```

You can also delete several elements by passing an array of index labels:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.drop(["a", "b"]) # Index(['c', 'd'], dtype='object')
```

#### Insert elements into a specific position in the index using the `insert` method

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.insert(1, "a2") # Index(['a', 'a2', 'b', 'c', 'd'], dtype='object')
idx.insert([1], ["a2", "a3"]) # Index(['a', 'a2', 'a3', 'b', 'c', 'd'], dtype='object')
```

#### `is_unique`

While many pandas functions (like `reindex`) require that the labels be unique, it’s not mandatory. The `is_unique` property of the index can tell you whether or not its labels are unique:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5), index=["a", "a", "b", "b", "c"])

print(ser)
"""
a    0
a    1
b    2
b    3
c    4
dtype: int64
"""

print(ser.index.is_unique) # False
```

Data selection is one of the main things that behaves differently with duplicates. Indexing a label with multiple entries returns a series, while single entries return a scalar value:

```py
import numpy as np
import pandas as pd

ser = pd.Series(np.arange(5), index=["a", "a", "b", "b", "c"])

print(ser["a"])
"""
a    0
a    1
dtype: int64
"""
print(ser["c"]) # 4
```

#### `unique()`

The `unique()` method computes the array of unique values in the Index:

```py
import pandas as pd

idx = pd.Index(["a", "b", "c", "d"])

idx.is_unique # True
pd.Index(["a", "a", "b"]).is_unique # False
pd.Index(["a", "a", "b"]).unique() # Index(['a', 'b'], dtype='object')
```

<hr>

### Rearranging the indices with the `reindex` method

#### Rearranging the indices of a series with `reindex`

The `reindex` method creates a new object with the values rearranged to align with the new index:

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

ser2 = ser.reindex(["a", "b", "c", "d", "e"])
print(ser2)
"""
a    102.0
b    101.0
c    103.0
d    100.0
e      NaN
dtype: float64
"""
```

#### Rearranging the indices of a dataframe with `reindex`

The `reindex` method works on dataframes as well. It can alter indices (rows) and columns:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(index=[2022, 2021, 2020, 2019])
print(df2)
"""
      Baku  Istanbul  Bishkek
2022   6.0       7.0      8.0
2021   3.0       4.0      5.0
2020   0.0       1.0      2.0
2019   NaN       NaN      NaN
"""
```

The columns can be reindexed with the `columns` keyword:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(columns=["Baku", "Bishkek", "Istanbul", "Almati"])
print(df2)

print(df2)
"""
      Baku  Bishkek  Istanbul  Almati
2020     0        2         1     NaN
2021     3        5         4     NaN
2022     6        8         7     NaN
"""
```

Another way to reindex a particular axis is to use the `axis` keyword:

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex([2022, 2021, 2020, 2019], axis="index")
print(df2)
"""
      Baku  Istanbul  Bishkek
2022   6.0       7.0      8.0
2021   3.0       4.0      5.0
2020   0.0       1.0      2.0
2019   NaN       NaN      NaN
"""
```

```py
import numpy as np
import pandas as pd

df = pd.DataFrame(
  np.arange(9).reshape((3, 3)),
  index=[2020, 2021, 2022],
  columns=["Baku", "Istanbul", "Bishkek"]
)

print(df)
"""
      Baku  Istanbul  Bishkek
2020     0         1        2
2021     3         4        5
2022     6         7        8
"""

df2 = df.reindex(["Baku", "Bishkek", "Istanbul", "Almati"], axis="columns")

print(df2)
"""
      Baku  Bishkek  Istanbul  Almati
2020     0        2         1     NaN
2021     3        5         4     NaN
2022     6        8         7     NaN
"""
```

<hr>

#### Filling in missing values while using the `reindex` method

In the above example, when we added a new index, its value became `NaN`. Istead of `NaN`, we can use pandas to fill the data. In the below example, we are using the `method="ffill"`, forward fill. If there is a missing value, `method="ffill"` takes the value in the previous index and forwards it to the missing value's place:

```py
import numpy as np
import pandas as pd

ser = pd.Series(["blue", "purple", "yellow"], index=[0, 2, 4])
print(ser)
"""
0      blue
2    purple
4    yellow
dtype: object
"""

ser2 = ser.reindex(np.arange(6), method="ffill")
print(ser2)
"""
0      blue
1      blue
2    purple
3    purple
4    yellow
5    yellow
dtype: object
"""
```

`method="bfill"` takes the value in the next index and puts it back in the missing value's place.

```py
import numpy as np
import pandas as pd

ser = pd.Series(["blue", "purple", "yellow"], index=[0, 2, 4])
print(ser)
"""
0      blue
2    purple
4    yellow
dtype: object
"""

ser2 = ser.reindex(np.arange(6), method="bfill")
print(ser2)
"""
0      blue
1    purple
2    purple
3    yellow
4    yellow
5       NaN
dtype: object
"""
```

#### Table of `reindex` arguments

Here is more information about `reindex` function arguments:

| Argument     | Description                                                                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `labels`     | New sequence to use as an index. Can be Index instance or any other sequence-like Python data structure. An Index will be used exactly as is without any copying.                     |
| `index`      | Use the passed sequence as the new index labels.                                                                                                                                      |
| `columns`    | Use the passed sequence as the new column labels.                                                                                                                                     |
| `axis`       | The axis to reindex, whether `"index"` (rows) or `"columns"`. The default is `"index"`. You can alternately do `reindex(index=new_labels)` or `reindex(columns=new_labels)`.          |
| `method`     | Interpolation (fill) method; `"ffill"` fills forward, while `"bfill"` fills backward.                                                                                                 |
| `fill_value` | Substitute value to use when introducing missing data by reindexing. Use `fill_value="missing"` (the default behavior) when you want absent labels to have null values in the result. |
| `limit`      | When forward filling or backfilling, the maximum size gap (in number of elements) to fill.                                                                                            |
| `tolerance`  | When forward filling or backfilling, the maximum size gap (in absolute numeric distance) to fill for inexact matches.                                                                 |
| `level`      | Match simple Index on level of `MultiIndex`; otherwise select subset of.                                                                                                              |
| `copy`       | If `True`, always copy underlying data even if the new index is equivalent to the old index; if `False`, do not copy the data when the indexes are equivalent.                        |

<hr>

## Modifying data in series and dataframes

### Copying series and dataframes

We can use the `copy` method to return the copy of series and dataframes:

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

print(df.copy())
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46  2.23      2.50     1.00
2021     15.52  2.25      2.52     1.02
2022     15.60  2.27       NaN     1.04
"""

fruits = pd.Series(["apple", "banana", "orange"])
print(fruits)
"""
0     apple
1    banana
2    orange
dtype: object
"""

print(fruits.copy())
"""
0     apple
1    banana
2    orange
dtype: object
"""
```

By default, `df.copy()` makes a deep copy of the dataframe, which allows us to make changes to either the copy or the original without repercussions. If we pass in `deep=False`, we can obtain a shallow copy—changes to the shallow copy affect the original and vice versa. We will almost always want the deep copy, since we can change it without affecting the original.

### Adding new values to a specific position in a series

When you want to insert an element at a specific position in a series, you can use the `loc` with a fractional index and then sort and reset the indices.

```py
import pandas as pd

fruits = pd.Series(["apple", "banana", "orange"])
print(fruits)
"""
0     apple
1    banana
2    orange
dtype: object
"""

fruits[1.5] = "pear"
fruits = fruits.sort_index().reset_index(drop=True)

print(fruits)
"""
0     apple
1    banana
2      pear
3    orange
dtype: object
"""
```

<hr>

### Adding new columns to a dataframe

We can easily add a column to a dataframe by assignment:

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

df["Total"] = df["Istanbul"]  + df["Baku"] + df["Tashkent"] + df["Karbala"]
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala  Total
2020     15.46  2.23      2.50     1.00  21.19
2021     15.52  2.25      2.52     1.02  21.31
2022     15.60  2.27       NaN     1.04    NaN
"""
```

In the above example, we summed the columns and assigned the summation to the `"Total"` column. But we don't necessarily have to use existing columns to create a new column by assignment. Here is an example of creating a new column in a dataframe by assinging a series object:

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
ser = pd.Series([10, 20, 30], index=[2, 4, 5])

df["newCol"] = ser

print(df.head())
"""
      Name   Age  newCol
0     Aisu  27.0     NaN
1    Temir  31.0     NaN
2  Gulnara   NaN    10.0
3   Azamat  29.0     NaN
4  Dilyara  34.0    20.0
"""
```

The `assign` method is another way to add or replace a column. With the `assign` method, the arguments are the names of the columns we want to create (or overwrite), and the values are the data for the columns. Note that `assign` doesn't change our original dataframe; instead, it returns a new dataframe object with these columns added.

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
ser = pd.Series([10, 20, 30], index=[2, 4, 5])

df = df.assign(
  newCol = ser
)

print(df.head())
"""
      Name   Age  newCol
0     Aisu  27.0     NaN
1    Temir  31.0     NaN
2  Gulnara   NaN    10.0
3   Azamat  29.0     NaN
4  Dilyara  34.0    20.0
"""
```

The `assign` method also accepts lambda functions.

<hr>

### Modifying values in a series

#### Using `loc` and `iloc`

Assigning values using `loc` and `iloc` methods modifies the corresponding section of the Series:

```py
import numpy as np
import pandas as pd

ser =  pd.Series(np.arange(4.), index=["a", "b", "c", "d"])
print(ser)
"""
a    0.0
b    1.0
c    2.0
d    3.0
dtype: float64
"""

ser.loc["b":"c"] = 5
print(ser)
"""
a    0.0
b    5.0
c    5.0
d    3.0
dtype: float64
"""

ser.iloc[[0, 3]] = 10
print(ser)
"""
a    10.0
b     5.0
c     5.0
d    10.0
dtype: float64
"""
```

#### Using the `replace` method

Another useful method that we can use to change the data in a series is to use the `replace` method. Here is a simple usage of it:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace(-999, np.nan))
"""
0       1.0
1       NaN
2       2.0
3       NaN
4   -1000.0
5       3.0
dtype: float64
"""
```

If we want to replace different values with a single value, we can use a list as the first argument, and a scalar value as the second argument:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace([-999, -1000], np.nan))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    NaN
5    3.0
dtype: float64
"""
```

If we want to replace different values with some other values, we can use a list as the first argument, and another list as the second argument:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace([-999, -1000], [np.nan, 0]))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    0.0
5    3.0
dtype: float64
"""
```

Instead of lists we can also use a dictionary, to indicate what values should be replaced with other values:

```py
import numpy as np
import pandas as pd

ser = pd.Series([1., -999., 2., -999., -1000., 3.])
print(ser)
"""
0       1.0
1    -999.0
2       2.0
3    -999.0
4   -1000.0
5       3.0
dtype: float64
"""

print(ser.replace({-999: np.nan, -1000:0}))
"""
0    1.0
1    NaN
2    2.0
3    NaN
4    0.0
5    3.0
dtype: float64
"""
```

Note that the `.replace` method is distinct from `.str.replace`, which performs element-wise string substitution

### Modifying values in the specific column of a dataframe

Columns can be modified as well. We could assign a scalar value or an array of values to a column of a dataframe:

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

df["Baku"] = 4
print(df)
"""
      Istanbul  Baku  Tashkent  Karbala
2020     15.46     4      2.50     1.00
2021     15.52     4      2.52     1.02
2022     15.60     4       NaN     1.04
"""
```

When we assign lists or arrays to a column, the value’s length must match the length of the DataFrame:

```py
import numpy as np
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Aisu', 'Temir', 'Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar', 'Gulzar'],
    'Age': [27, 31, np.nan, 29, 34, 22, 28, np.nan, 30, 24],
    'City': ['Almaty', 'Bishkek', 'Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', 'Ankara', 'Baku', 'Ashgabat'],
    'Salary': [60000.50, 72000.75, 55000.00, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan, 90000.00],
    'Is_Employed': ['Yes', 'No', 'Yes', 'No', 'Yes', 'No', np.nan, 'Yes', 'No', 'Yes']
}

df = pd.DataFrame(dictionaryForDataFrame, columns=["Name", "Salary"])
df["Salary"] = np.arange(90, 100)
print(df.tail())
"""
     Name  Salary
5  Fatima      95
6   Aydin      96
7    Oğuz      97
8   Asgar      98
9  Gulzar      99
"""
```

If you change the data in a column by assigning a series, its labels will be realigned exactly to the DataFrame’s index, inserting missing values in any index values not present:

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
ser = pd.Series([10, 20, 30], index=[1, 2, 3])

df["Age"] = ser
print(df.head())
"""
      Name   Age
0     Aisu   NaN
1    Temir  10.0
2  Gulnara  20.0
3   Azamat  30.0
4  Dilyara   NaN
"""
```

### Modifying values using `where`

The `where()` method in pandas is called on a series or a dataframe. It accepts a condition and a value after which it assigns the value to the series or the dataframe, when the condition is not met:

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

print(
  df.where(df < 2.5, "small")
)
"""
     Istanbul  Baku Tashkent  Karbala
2020    small  2.23    small     1.00
2021    small  2.25    small     1.02
2022    small  2.27    small     1.04
"""
```

<hr>

### Dividing data into groups

#### Using the `cut` method

Continuous data is often separated into bins for analysis. We can use the `cut` method to divide data into groups:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

age_categories = pd.cut(ages, bins)
print(age_categories)
"""
[(18, 25], (18, 25], (18, 25], (25, 35], (18, 25], ..., (25, 35], (60, 100], (35, 60], (35, 60], (25, 35]]
Length: 12
Categories (4, interval[int64, right]): [(18, 25] < (25, 35] < (35, 60] < (60, 100]]
"""
```

The `cut` method returns a special `Categorical` object. We can check the categories using the `categories` attribute and the codes for each category using the `codes` attribute:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

age_categories = pd.cut(ages, bins)

age_categories.categories
# IntervalIndex([(18, 25], (25, 35], (35, 60], (60, 100]], dtype='interval[int64, right]')

age_categories.codes
# array([0, 0, 0, 1, 0, 0, 2, 1, 3, 2, 2, 1], dtype=int8)

# bin counts
pd.Series(age_categories).value_counts()
"""
(18, 25]     5
(25, 35]     3
(35, 60]     3
(60, 100]    1
Name: count, dtype: int64
"""
```

Each bin is identified by a special (unique to pandas) interval value type, containing the lower and upper limit of each bin. A parenthesis means that the side is open (exclusive), while the square bracket means it is closed (inclusive). By default the right end is inclusive, but we can change that by passing `right=False`:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]

pd.cut(ages, bins, right=False)
"""
[[18, 25), [18, 25), [25, 35), [25, 35), [18, 25), ..., [25, 35), [60, 100), [35, 60), [35, 60), [25, 35)]
Length: 12
Categories (4, interval[int64, left]): [[18, 25) < [25, 35) < [35, 60) < [60, 100)]
"""
```

The interval value points become the default label for the categorical group created by the `cut` method. We can override this using the `labels` option:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]
group_names = ["Youth", "YoungAdult", "MiddleAged", "Senior"]

pd.cut(ages, bins, labels=group_names)
"""
['Youth', 'Youth', 'Youth', 'YoungAdult', 'Youth', ..., 'YoungAdult', 'Senior', 'MiddleAged', 'MiddleAged', 'YoungAdult']
Length: 12
Categories (4, object): ['Youth' < 'YoungAdult' < 'MiddleAged' < 'Senior']
"""
```

If you pass an integer number of bins to the `cut` method instead of explicit bin edges, it will compute equal-length bins based on the minimum and maximum values in the data.

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
pd.cut(ages, 4, precision=2)
"""
[(19.96, 30.25], (19.96, 30.25], (19.96, 30.25], (19.96, 30.25], (19.96, 30.25], ..., (30.25, 40.5], (50.75, 61.0], (40.5, 50.75], (40.5, 50.75], (30.25, 40.5]]
Length: 12
Categories (4, interval[float64, right]): [(19.96, 30.25] < (30.25, 40.5] < (40.5, 50.75] < (50.75, 61.0]]
"""
```

The `precision=2` option limits the decimal precision to two digits.

<hr>

#### Using the `qcut` method

Depending on the distribution of the data, using `cut` will not usually result in each bin having the same number of data points. A closely related function, `qcut`, bins the data based on sample quantiles. Since `qcut` uses sample quantiles instead, you will obtain roughly equally sized bins:

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]

quartiles = pd.qcut(ages, 4, precision=2)
print(quartiles)
"""
[(19.99, 22.75], (19.99, 22.75], (22.75, 29.0], (22.75, 29.0], (19.99, 22.75], ..., (29.0, 38.0], (38.0, 61.0], (38.0, 61.0], (38.0, 61.0], (29.0, 38.0]]
Length: 12
Categories (4, interval[float64, right]): [(19.99, 22.75] < (22.75, 29.0] < (29.0, 38.0] < (38.0, 61.0]]
"""

# Compare number of data points in each bin using qcut vs cut
print(pd.Series(pd.qcut(ages, 4, precision=2)).value_counts())
"""
(19.99, 22.75]    3
(22.75, 29.0]     3
(29.0, 38.0]      3
(38.0, 61.0]      3
Name: count, dtype: int64
"""

print(pd.Series(pd.cut(ages, 4, precision=2)).value_counts())
"""
(19.96, 30.25]    6
(30.25, 40.5]     3
(40.5, 50.75]     2
(50.75, 61.0]     1
Name: count, dtype: int64
"""
```

With the `qcut` method, we can pass our own quantiles (numbers between 0 and 1, inclusive):

```py
import pandas as pd

ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
print(pd.Series(pd.qcut(ages, [0, 0.1, 0.15, 0.5, 0.85, 0.9, 1.])).value_counts())
"""
(29.0, 42.4]      4
(21.65, 29.0]     4
(44.6, 61.0]      2
(19.999, 21.1]    2
(21.1, 21.65]     0
(42.4, 44.6]      0
Name: count, dtype: int64
"""
```

<hr>

### Transposing a dataframe

We can transpose a dataframe (swap rows and columns) with similar syntax to a NumPy array. Note that transposing discards the column data types if the columns do not all have the same data type. So, transposing and then transposing back may lose the previous type information. The columns become arrays of pure Python objects in this case:

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

print(df.T)
"""
           2020   2021   2022
Istanbul  15.46  15.52  15.60
Baku       2.23   2.25   2.27
Tashkent   2.50   2.52    NaN
Karbala    1.00   1.02   1.04
"""
```

<hr>

## Converting series and dataframes to other objects

### Converting a series to a dictionary

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

<hr>

### Converting a dataframe to an ndarray

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

<hr>

## Deleting the data from series and dataframes

### Deleting data from a series

#### Using the `del` keyword to delete the items from a series

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

#### Using the `drop` method to delete the items from a series

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

<hr>

### Deleting data from a dataframe

#### Using the `del` keyword to delete a column from a dataframe

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

#### Using the `drop` method to delete rows and columns from a dataframe

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

<hr>

#### Using the `pop` method to delete a column of a dataframe

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

<hr>

## Dealing with missing data in series and dataframes

### Check for missing data in a series

We can check if data is missing or not using `isna` and `notna` pandas methods:

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

print(pd.isna(ser))
"""
Istanbul      False
Baku          False
Tashkent       True
Nur-Sultan    False
dtype: bool
"""
```

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

print(pd.notna(ser))
"""
Istanbul       True
Baku           True
Tashkent      False
Nur-Sultan     True
dtype: bool
"""
```

The methods `isna` and `notna` are also available as instance methods:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser.notna())
"""
Istanbul       True
Baku           True
Tashkent      False
Nur-Sultan     True
dtype: bool
"""
```

### Check for missing data in a dataframe

Both methods, `isna` and `notna`, also work on dataframes:

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
print(df.isna())
"""
    Name    Age   City  Salary  Is_Employed
0  False  False  False   False        False
1  False  False  False   False        False
2  False   True  False   False        False
3  False  False  False    True        False
4  False  False   True   False        False
5  False  False  False   False        False
6  False  False  False   False         True
7  False   True  False   False        False
8  False  False  False    True        False
9  False  False  False   False        False
"""
```

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
print(df.notna())
"""
   Name    Age   City  Salary  Is_Employed
0  True   True   True    True         True
1  True   True   True    True         True
2  True  False   True    True         True
3  True   True   True   False         True
4  True   True  False    True         True
5  True   True   True    True         True
6  True   True   True    True        False
7  True  False   True    True         True
8  True   True   True   False         True
9  True   True   True    True         True
"""
```

<hr>

### `isnull()`

The `isnull` method is used to detect missing or `NaN` values in a DataFrame or Series.

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
print(df.isnull())
# print(pd.isnull(df)) # This does the same thing
"""
   Name    Age   City  Salary  Is_Employed
0  True   True   True    True         True
1  True   True   True    True         True
2  True  False   True    True         True
3  True   True   True   False         True
4  True   True  False    True         True
5  True   True   True    True         True
6  True   True   True    True        False
7  True  False   True    True         True
8  True   True   True   False         True
9  True   True   True    True         True
"""
```

<hr>

### Replacing missing values in a series

If we want to fill in a missing value, we can use the `fillna` method.

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

ser.fillna(100, inplace=True)
print(ser)
"""
Istanbul       15.0
Baku            5.0
Tashkent      100.0
Nur-Sultan     18.0
dtype: float64
"""
```

Just like we had `method=ffill` with the `reindex` method, we also have `ffill` and `bfill` methods. They take similar arguments as `reindex` takes. `ffill` forward fills, whereas `bfill` backfills missing values:

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Karbala": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""

print(ser.ffill())
"""
Istanbul      15.0
Baku           5.0
Tashkent       5.0
Karbala        5.0
Nur-Sultan    18.0
dtype: float64
"""

print(ser.ffill(limit=1))
"""
Istanbul      15.0
Baku           5.0
Tashkent       5.0
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""
```

```py
import pandas as pd

dictionaryForSeries = {"Istanbul": 15, "Baku": 5, "Tashkent": None, "Karbala": None, "Nur-Sultan": 18}
ser = pd.Series(dictionaryForSeries)

print(ser)
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala        NaN
Nur-Sultan    18.0
dtype: float64
"""

print(ser.bfill())
"""
Istanbul      15.0
Baku           5.0
Tashkent      18.0
Karbala       18.0
Nur-Sultan    18.0
dtype: float64
"""

print(ser.bfill(limit=1))
"""
Istanbul      15.0
Baku           5.0
Tashkent       NaN
Karbala       18.0
Nur-Sultan    18.0
dtype: float64
"""
```

### Replacing missing values in a dataframe

`fillna` method also works with dataframes:

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
print(df.fillna(10000))
"""
      Name      Age      City    Salary Is_Employed
0     Aisu     27.0    Almaty  60000.50         Yes
1    Temir     31.0   Bishkek  72000.75          No
2  Gulnara  10000.0  Tashkent  55000.00         Yes
3   Azamat     29.0    Astana  10000.00          No
4  Dilyara     34.0     10000  75000.10         Yes
5   Fatima     22.0     Kazan  50000.00          No
6    Aydin     28.0  Istanbul  68000.50       10000
7     Oğuz  10000.0    Ankara  62000.00         Yes
8    Asgar     30.0      Baku  10000.00          No
9   Gulzar     24.0  Ashgabat  90000.00         Yes
"""
```

Instead of replacing all the missing values with one value, we can specify different replacement values for different columns in a dataframe:

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
print(df.fillna({"Salary": 0, "Is_Employed": "No"}))
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
3   Azamat  29.0    Astana      0.00          No
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50          No
7     Oğuz   NaN    Ankara  62000.00         Yes
8    Asgar  30.0      Baku      0.00          No
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

### Dropping the missing values in a series

To drop the missing values from a series, we can use the `dropna` instance method. `dropna` gets rid of any rows where there is a missing value.

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

print(ser.dropna())
"""
Istanbul      15.0
Baku           5.0
Nur-Sultan    18.0
dtype: float64
"""
```

### Dropping the missing values in a dataframe

To drop the missing values from a dataframe, we can use the `dropna` method.

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

print(df.dropna())
"""
     Name   Age      City    Salary Is_Employed
0    Aisu  27.0    Almaty  60000.50         Yes
1   Temir  31.0   Bishkek  72000.75          No
5  Fatima  22.0     Kazan  50000.00          No
9  Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

By default `dropna` gets rid of any rows where there is a missing value. However, we can specify `dropna(axis="columns")` to drop the columns where there is a missing value.

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

print(df.dropna(axis="columns"))
"""
      Name
0     Aisu
1    Temir
2  Gulnara
3   Azamat
4  Dilyara
5   Fatima
6    Aydin
7     Oğuz
8    Asgar
9   Gulzar
"""
```

Also, by default `dropna` gets rid of the rows or columns where there is even a single missing value. However, we can specify to get rid of a row or a column, when all the values of a row are missing using `dropna(how="all")`.

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

print(df.dropna(how="all"))
# Nothing dropped because there is not a row where all the values are NaN
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

If we want to specify to drop a row, when there is a missing value in a specific column, we can use the `subset` argument of the `dropna` method.

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

print(df.dropna(subset="Salary"))
"""
      Name   Age      City    Salary Is_Employed
0     Aisu  27.0    Almaty  60000.50         Yes
1    Temir  31.0   Bishkek  72000.75          No
2  Gulnara   NaN  Tashkent  55000.00         Yes
4  Dilyara  34.0       NaN  75000.10         Yes
5   Fatima  22.0     Kazan  50000.00          No
6    Aydin  28.0  Istanbul  68000.50         NaN
7     Oğuz   NaN    Ankara  62000.00         Yes
9   Gulzar  24.0  Ashgabat  90000.00         Yes
"""
```

If we want to specify a threshold number of non-missing values, we can do that using the `thresh` argument:

```py
import pandas as pd

dictionaryForDataFrame = {
    'Name': ['Gulnara', 'Azamat', 'Dilyara', 'Fatima', 'Aydin', 'Oğuz', 'Asgar'],
    'Age': [np.nan, 29, 34, 22, 28, np.nan, 30],
    'City': ['Tashkent', 'Astana', np.nan, 'Kazan', 'Istanbul', np.nan, 'Baku' ],
    'Salary': [np.nan, np.nan, 75000.10, 50000.00, 68000.50, 62000.00, np.nan],
}

df = pd.DataFrame(dictionaryForDataFrame)
print(df)
"""
      Name   Age      City   Salary
0  Gulnara   NaN  Tashkent      NaN
1   Azamat  29.0    Astana      NaN
2  Dilyara  34.0       NaN  75000.1
3   Fatima  22.0     Kazan  50000.0
4    Aydin  28.0  Istanbul  68000.5
5     Oğuz   NaN       NaN  62000.0
6    Asgar  30.0      Baku      NaN
"""

print(df.dropna(thresh=3))
"""
      Name   Age      City   Salary
1   Azamat  29.0    Astana      NaN
2  Dilyara  34.0       NaN  75000.1
3   Fatima  22.0     Kazan  50000.0
4    Aydin  28.0  Istanbul  68000.5
6    Asgar  30.0      Baku      NaN
"""
```

<hr>

## Dealing with duplicate values in a dataframe

### Checking the existence of duplicate values in a dataframe

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

### Dropping duplicate values in a dataframe

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

<hr>

## Sorting and Ranking

### Sorting a series by indices

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

<hr>

### Sorting a dataframe by indices

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

<hr>

### Sorting a series by values

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

#### Placement of missing values while sorting by values

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

<hr>

### Sorting a dataframe by values

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

<hr>

### Ranking a series

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

#### Tie-breaking methods with `rank`

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

<hr>

## Arithmetic and Data Alignment

### Table of different arithmetic methods

Here is a table of some arithmetic methods:

| Method                  | Description                       |
| ----------------------- | --------------------------------- |
| `add`, `radd`           | Methods for addition (+)          |
| `sub`, `rsub`           | Methods for subtraction (-)       |
| `div`, `rdiv`           | Methods for division (/)          |
| `floordiv`, `rfloordiv` | Methods for floor division (//)   |
| `mul`, `rmul`           | Methods for multiplication (\*)   |
| `pow`, `rpow`           | Methods for exponentiation (\*\*) |

### Arithmetic operations on series

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

<hr>

### Arithmetic operations on dataframes

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

<hr>

## Descriptive Statistical methods

### Table of some statistical methods

There are many descriptive and summary statistics methods in pandas:

| Method             | Description                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| `count`            | Number of non-NA values                                                                                                            |
| `describe`         | Compute set of summary statistics                                                                                                  |
| `min, max`         | Compute minimum and maximum values                                                                                                 |
| `argmin`, `argmax` | Compute index locations (integers) at which minimum or maximum value is obtained, respectively; not available on DataFrame objects |
| `idxmin`, `idxmax` | Compute index labels at which minimum or maximum value is obtained, respectively                                                   |
| `quantile`         | Compute sample quantile ranging from 0 to 1 (default: 0.5)                                                                         |
| `sum`              | Sum of values                                                                                                                      |
| `mean`             | Mean of values                                                                                                                     |
| `median`           | Arithmetic median (50% quantile) of values                                                                                         |
| `mad`              | Mean absolute deviation from mean value                                                                                            |
| `prod`             | Product of all values                                                                                                              |
| `var`              | Sample variance of values                                                                                                          |
| `std`              | Sample standard deviation of values                                                                                                |
| `skew`             | Sample skewness (third moment) of values                                                                                           |
| `kurt`             | Sample kurtosis (fourth moment) of values                                                                                          |
| `cumsum`           | Cumulative sum of values                                                                                                           |
| `cummin`, `cummax` | Cumulative minimum or maximum of values, respectively                                                                              |
| `cumprod`          | Cumulative product of values                                                                                                       |
| `diff`             | Compute first arithmetic difference (useful for time series)                                                                       |
| `pct_change`       | Compute percent changes                                                                                                            |

### `sum`

Calling dataframe’s `sum` method returns a series containing column sums:

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

print(df.sum())
"""
Istanbul    46.58
Baku         6.75
Tashkent     5.02
Karbala      3.06
dtype: float64
"""
```

Passing `axis="columns"` or `axis=1` sums across the columns instead:

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

print(df.sum(axis="columns"))
"""
2020    21.19
2021    21.31
2022    18.91
dtype: float64
"""

print(df.sum(axis=1))
"""
2020    21.19
2021    21.31
2022    18.91
dtype: float64
"""
```

If there is any missing value (`NaN`), by default `sum` accepts them as zero. However, we can change this by using `skipna=False`:

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

print(df.sum(axis="index", skipna=False))
"""
Istanbul    46.58
Baku         6.75
Tashkent      NaN
Karbala      3.06
dtype: float64
"""

print(df.sum(axis="columns", skipna=False))
"""
2020    21.19
2021    21.31
2022      NaN
dtype: float64
"""
```

### `mean`

Some aggregations, like `mean`, require at least one non-NA value to yield a value result, so here we have:

```py
import pandas as pd

nestedDictionaryForDataFrame = {
    'Istanbul': {2020: 15.46, 2021: 15.52, 2022: 15.60},
    'Baku': {2020: 2.23, 2021: 2.25, 2022: 2.27},
    'Tashkent': {2020: 2.50, 2021: 2.52, 2022: None},
    'Karbala': {2020: 1.00, 2021: 1.02, 2022: 1.04}
}

df = pd.DataFrame(nestedDictionaryForDataFrame)
df["newCol"] = None

print(df)
"""
      Istanbul  Baku  Tashkent  Karbala newCol
2020     15.46  2.23      2.50     1.00   None
2021     15.52  2.25      2.52     1.02   None
2022     15.60  2.27       NaN     1.04   None
"""

print(df.mean())
"""
Istanbul    15.526667
Baku             2.25
Tashkent         2.51
Karbala          1.02
newCol            NaN
dtype: objec
"""
```

### `describe`

`describe` produces multiple summary statistics:

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

print(df.describe())
"""
        Istanbul  Baku  Tashkent  Karbala
count   3.000000  3.00  2.000000     3.00
mean   15.526667  2.25  2.510000     1.02
std     0.070238  0.02  0.014142     0.02
min    15.460000  2.23  2.500000     1.00
25%    15.490000  2.24  2.505000     1.01
50%    15.520000  2.25  2.510000     1.02
75%    15.560000  2.26  2.515000     1.03
max    15.600000  2.27  2.520000     1.04
"""
```

If we want different percentiles, we can pass them in with the percentiles argument. For example, if we wanted only the 5th and 95th percentiles, we would run `df.describe(percentiles=[0.05, 0.95])`.

If we want the summary statistics for columns with the specific data type, we can use the `include` option of the `describe` method. For example, by default, `describe()` won't give us any information about the columns of the type object, but we can either provide `include='all'` as an argument or run it separately with `include=object`.

The `describe()` method only gives us summary statistics for non-null values. This means that, if we had 100 rows and half of our data was null, then the average would be calculated as the sum of the 50 non-null rows divided by 50.

On nonnumeric data, `describe` produces alternative summary statistics:

```py
import numpy as np
import pandas as pd

ser = pd.Series(["a", "a", "b", "c"] * 4)

print(ser.describe())
"""
count     16
unique     3
top        a
freq       8
dtype: object
"""
```

### `info`

The `info()` method also shows some statistics about the data.

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

print(df.info())
"""
<class 'pandas.core.frame.DataFrame'>
Index: 3 entries, 2020 to 2022
Data columns (total 4 columns):
 #   Column    Non-Null Count  Dtype
---  ------    --------------  -----
 0   Istanbul  3 non-null      float64
 1   Baku      3 non-null      float64
 2   Tashkent  2 non-null      float64
 3   Karbala   3 non-null      float64
dtypes: float64(4)
memory usage: 228.0 bytes
"""
```

<hr>

### Unique Values, Value Counts

#### `unique`

The `unique` method retrieves an array of the unique values from a Series:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.unique()) # ['c' 'a' 'd' 'b']
```

<hr>

#### `value_counts`

`value_counts` computes a Series containing value frequencies:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.value_counts())
"""
c    3
a    3
d    3
b    3
Name: count, dtype: int64
"""
```

If we want to see the value counts as percentage, we can use the `normalize=True` argument:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "b"] * 3)

print(ser.value_counts(normalize=True))
"""
c    0.25
a    0.25
d    0.25
b    0.25
Name: proportion, dtype: float64
"""
```

The Series is sorted by value in descending order as a convenience. But we can undo that using `sort=False`:

```py
import pandas as pd

ser = pd.Series(["c", "a", "d", "a", "a", "b", "b", "c", "c", "a", "a"])

print(ser.value_counts())
"""
a    5
c    3
b    2
d    1
Name: count, dtype: int64
"""

print(ser.value_counts(sort=False))
"""
c    3
a    5
d    1
b    2
Name: count, dtype: int64
"""
```

<hr>

## Various Functions and Methods

### NumPy ufuncs

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

<hr>

### `any`

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

<hr>

### `apply`

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

<hr>

### `map`

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

<hr>

### `agg`

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

<hr>

### `explode`

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

<hr>

### `to_numeric`

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

<hr>

### `clip`

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

<hr>

### `rolling`

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

<hr>

### `expanding`

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

<hr>

### `ewm`

Pandas also provides the `ewm` method for exponentially weighted moving calculations.

<hr>

### `pipe`

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

<hr>

### `query`

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

<hr>

### `first_valid_index` and `last_valid_index`

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

<hr>

### `asof`

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

<hr>

### `at_time`

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

<hr>

### `between_time`

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

<hr>

### `filter`

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

<hr>

### `diff`

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

<hr>

### `transform`

<hr>
<hr>

## Extension types (Accessors) in Pandas

There are methods in pandas that work only with specific data types. These methods are accessed through 4 accessors:

- `str`: String data type
- `cat`: Categorical data type
- `dt`: Datetime, Timedelta, Period data types
- `sparse`: Sparse data type

<hr>

### `str`

`str` accessor provides methods to work with textual data.

The `upper` method turns all the letters to uppercase:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.upper())
"""
0         BAKU
1    KHANKENDI
2       SHUSHA
3     ISTANBUL
4       ANKARA
5        IZMIR
Name: city, dtype: object
"""
```

The `lower` method turns all the letters to lowercase:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.lower())
"""
0         baku
1    khankendi
2       shusha
3     istanbul
4       ankara
5        izmir
Name: city, dtype: object
"""
```

The `len` method returns the length of the strings in a series.

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.len())
"""
0    4
1    9
2    6
3    8
4    6
5    5
Name: city, dtype: int64
"""
```

`str` accessor allows to use indexing on strings:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str[:3])
"""
0    Bak
1    Kha
2    Shu
3    Ist
4    Ank
5    Izm
Name: city, dtype: object
"""
```

We can check if all characters are alphabetical with the `isalpha` method:

```py
import pandas as pd

dictionaryForDataFrame2 = {
  "country": ["Azerbaijan", "Turkiye"],
  "city": [["Baku", "Khankendi", "Shusha"], ["Istanbul", "Ankara", "Izmir"]]
}

df = pd.DataFrame(dictionaryForDataFrame2).explode("city", ignore_index=True)
print(df)
"""
      country       city
0  Azerbaijan       Baku
1  Azerbaijan  Khankendi
2  Azerbaijan     Shusha
3     Turkiye   Istanbul
4     Turkiye     Ankara
5     Turkiye      Izmir
"""

print(df["city"].str.isalpha())
"""
0    True
1    True
2    True
3    True
4    True
5    True
Name: city, dtype: bool
"""
```

The `split` method returns a series of lists:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s)
"""
0    a_b_c
1    c_d_e
2     <NA>
3    f_g_h
dtype: string
"""

print(s.str.split("_"))
"""
0    [a, b, c]
1    [c, d, e]
2         <NA>
3    [f, g, h]
dtype: object
"""
```

Elements in the split lists can be accessed using the `get` method or `[]` notation:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s.str.split("_"))
"""
0    [a, b, c]
1    [c, d, e]
2         <NA>
3    [f, g, h]
dtype: object
"""

print(s.str.split("_").str.get(1))
"""
0       b
1       d
2    <NA>
3       g
dtype: object
"""

print(s.str.split("_").str[1])
"""
0       b
1       d
2    <NA>
3       g
dtype: object
"""
```

We can use the `expand` option to return the output of `split` as a DataFrame:

```py
s = pd.Series(["a_b_c", "c_d_e", np.nan, "f_g_h"], dtype="string")

print(s.str.split("_", expand=True))
"""
      0     1     2
0     a     b     c
1     c     d     e
2  <NA>  <NA>  <NA>
3     f     g     h
"""
```

It is also possible to limit the number of splits using the `n` option:

```py
s = pd.Series(["a_b_c_A", "c_d_e_A", np.nan, "f_g_h_A", "i_j_k_A"], dtype="string")

print(s)
"""
0    a_b_c_A
1    c_d_e_A
2       <NA>
3    f_g_h_A
4    i_j_k_A
dtype: string
"""

print(s.str.split("_", n=1))
"""
0    [a, b_c_A]
1    [c, d_e_A]
2          <NA>
3    [f, g_h_A]
4    [i, j_k_A]
dtype: object
"""

print(s.str.split("_", n=3))
"""
0    [a, b, c, A]
1    [c, d, e, A]
2            <NA>
3    [f, g, h, A]
4    [i, j, k, A]
dtype: object
"""
```

Regular expressions can be used with the `str` accessor as well.

<hr>

### `dt`

`dt` accessor allows to extract many useful properties from datetime data. It also provides methods for manipulation.

We can extract year, month, or day from the dates by simply using `year`, `month`, and `day` properties.

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries)
"""
0   2024-08-10
1   2024-08-20
2   2024-08-30
3   2024-09-09
4   2024-09-19
dtype: datetime64[ns]
"""

print(dateSeries.dt.year)
"""
0    2024
1    2024
2    2024
3    2024
4    2024
dtype: int32
"""

print(dateSeries.dt.month)
"""
0    8
1    8
2    8
3    9
4    9
dtype: int32
"""

print(dateSeries.dt.day)
"""
0    10
1    20
2    30
3     9
4    19
dtype: int32
"""
```

The weekday of a date can be extracted using the `weekday` attribute. It starts from 0 (Monday) and goes up to 6 (Sunday).

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.weekday)
"""
0    5
1    1
2    4
3    0
4    3
dtype: int32
"""
```

We can access the week of the year using the `isocalendar` method:

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.isocalendar())
"""
   year  week  day
0  2024    32    6
1  2024    34    2
2  2024    35    5
3  2024    37    1
4  2024    38    4
"""

print(dateSeries.dt.isocalendar().week)
"""
0    32
1    34
2    35
3    37
4    38
Name: week, dtype: UInt32
"""
```

We are able to check if a date is start or end of a month, quarter, or year.

```py
import pandas as pd

dateSeries = pd.Series(pd.date_range(start="2024-08-10", periods=5, freq="10D"))

print(dateSeries.dt.is_month_start)
"""
0    False
1    False
2    False
3    False
4    False
dtype: bool
"""

print(dateSeries.dt.is_quarter_start)
print(dateSeries.dt.is_year_start)

print(dateSeries.dt.is_month_end)
print(dateSeries.dt.is_quarter_end)
print(dateSeries.dt.is_year_end)
```

<hr>

### `cat`

`cat` is the accessor for categorical data type. At times, it is more efficient to work with categorical data type than using the object data type. It makes a significant difference in terms of memory and speed especially when the data has low cardinality (i.e. number of categories is low compared to the number of observations).

#### Table of categorical methods

Here is a table of categorical methods for series in pandas:

| Method                     | Description                                                                                         |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| `add_categories`           | Append new (unused) categories at end of existing categories                                        |
| `as_ordered`               | Make categories ordered                                                                             |
| `as_unordered`             | Make categories unordered                                                                           |
| `remove_categories`        | Remove categories, setting any removed values to null                                               |
| `remove_unused_categories` | Remove any category values that do not appear in the data                                           |
| `rename_categories`        | Replace categories with indicated set of new category names; cannot change the number of categories |
| `reorder_categories`       | Behaves like `rename_categories`, but can also change the result to have ordered categories         |
| `set_categories`           | Replace the categories with the indicated set of new categories; can add or remove categories       |

#### Creating a series with `Categorical` data type

We can create a series with `Categorical` data type using the `dtype` argument:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""
```

Instead of series or dataframes with categorical data, we can create standalone categories using `pandas.Categorical`:

```py
import pandas as pd

my_categories = pd.Categorical(["test 1", "test 2", "test 3"])
print(my_categories)
"""
['test 1', 'test 2', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""
```

Another way is to use the `pandas.Categorical.from_codes` method:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

my_categories = pd.Categorical.from_codes(codes, categories)
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""
```

#### Specifying the ordered categories

Unless explicitly specified, categorical conversions assume no specific ordering of the categories. So the `categories` array may be in a different order depending on the ordering of the input data. When using `from_codes` or any of the other constructors, you can indicate that the categories have a meaningful ordering:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

ordered_categories = pd.Categorical.from_codes(codes, categories, ordered=True)
print(ordered_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1' < 'test 2' < 'test 3']
"""
```

#### Converting an unordered categorial to an ordered one

An unordered categorical instance can be made ordered with the `as_ordered` method:

```py
import pandas as pd

categories = ["test 1", "test 2", "test 3"]
codes = [0, 1, 2, 1, 0, 2]

my_categories = pd.Categorical.from_codes(codes, categories)
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1', 'test 2', 'test 3']
"""

my_categories = my_categories.as_ordered()
print(my_categories)
"""
['test 1', 'test 2', 'test 3', 'test 2', 'test 1', 'test 3']
Categories (3, object): ['test 1' < 'test 2' < 'test 3']
"""
```

#### Converting a series with a different data type to a `Categorical` type

In addition to `dtype` attribute and `pandas.Categorical.from_codes` method, there is also `astype` method, which can convert a series from one data type to another one. Thus, we can use it to convert a series with a different data type to a `Categorical` type:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"])
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: object
"""

ser = ser.astype("category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(type(ser.array)) # <class 'pandas.core.arrays.categorical.Categorical'>
```

#### The `categories` attribute

The `Categorical` object has `categories` and `codes` attributes. We can check the categories using the `categories` attribute:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.categories)
# Index(['a', 'b', 'c', 'd'], dtype='object')
```

#### The `codes` attribute

Each category also has an integer value associated with it. The integer values that reference the categories are called the category codes or simply codes. We can access them using the `codes` attribute.

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser.cat.codes)
"""
0    0
1    0
2    1
3    1
4    1
5    2
6    2
7    2
8    2
9    3
dtype: int8
"""
```

A useful trick to get a mapping between codes and categories is:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
dict(enumerate(ser.cat.categories)) # {0: 'a', 1: 'b', 2: 'c', 3: 'd'}
```

#### The `rename_categories` method

We can rename the categories using the `rename_categories` method:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser.cat.categories) # Index(['a', 'b', 'c', 'd'], dtype='object')

print(ser.cat.rename_categories({"a": "A", "b": "B", "c": "C", "d":"D"}))
"""
0    A
1    A
2    B
3    B
4    B
5    C
6    C
7    C
8    C
9    D
dtype: category
Categories (4, object): ['A', 'B', 'C', 'D']
"""
```

#### The `add_categories` method

When working with the category data type, the new values must be in one of the existing categories. We can add new categories, even if no data point belongs to that category yet, using the `add_categories` method:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.add_categories("e"))
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""
```

#### The `set_categories` method

We can use the `set_categories` method to set, add, and change categories:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (4, object): ['a', 'b', 'c', 'd']
"""

print(ser.cat.set_categories(["a", "b", "c", "d", "e"]))
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""
```

In large datasets, categoricals are often used as a convenient tool for memory savings and better performance. After you filter a large dataframe or series, many of the categories may not appear in the data. To help with this, we can use the `remove_unused_categories` method to trim unobserved categories:

```py
import pandas as pd

ser = pd.Series(["a", "a", "b", "b", "b", "c", "c", "c", "c", "d"], dtype="category")
ser = ser.cat.set_categories(["a", "b", "c", "d", "e"])

print(ser)
"""
0    a
1    a
2    b
3    b
4    b
5    c
6    c
7    c
8    c
9    d
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""

ser2 = ser[ser.isin(["a", "b"])]
print(ser2)
"""
0    a
1    a
2    b
3    b
4    b
dtype: category
Categories (5, object): ['a', 'b', 'c', 'd', 'e']
"""

ser2 = ser2.cat.remove_unused_categories()
"""
0    a
1    a
2    b
3    b
4    b
dtype: category
Categories (2, object): ['a', 'b']
"""
```

<hr>

## Reading and Writing Data in Text Format

### Table of methods to load data

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

<hr>

### Practical usage of `read_csv`

#### Table of some `read_csv` arguments

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

<hr>

#### Basic use of `read_csv`

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

#### Use `read_csv` to retrieve data without headers

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

#### Converting columns of a dataframe to an index

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

```
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

#### Using custom delimiter with `read_csv`

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

#### Skipping rows using the `read_csv` method

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

#### Dealing with missing data while using the `read_csv` method

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

<hr>

### Reading Text Files in Pieces

#### Using options to display a small number of rows and columns

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

#### Using the `nrows` to retrieve a small number of rows

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

#### Using the `chunksize` to retrieve a small number of rows

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

#### Using the `get_chunk` to retrieve a small number of rows

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

<hr>

### Writing Data to Text Format

#### Basic use of the `to_csv` method

Using the `to_csv` method, we can write the data out to a comma-separated file:

```py
import pandas as pd

df = pd.read_csv("examples/ex5.csv")
df.to_csv("examples/out.csv")
```

#### Using the `to_csv` method with other delimiters

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

#### Dealing with the missing values while using the `to_csv` method

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

#### Getting rid of the index and column headers while using the `to_csv` method

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

#### Outputting specific columns while using the `to_csv` method

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

<hr>

### Dealing with the JSON Data

#### Parse JSON to a python object

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

#### Convert a python object to JSON

`json.dumps` converts a Python object to JSON:

```py
import json

asjson = json.dumps(result)
asjson
'{"name": "Wes", "cities_lived": ["Akron", "Nashville", "New York", "San Francisco"], "pet": null, "siblings": [{"name": "Scott", "age": 34, "hobbies": ["guitars", "soccer"]}, {"name": "Katie", "age": 42, "hobbies": ["diving", "art"]}]}'
```

#### Convert JSON to a dataframe

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

#### Convert a pandas object to JSON

If you need to export data from pandas to JSON, one way is using the `to_json` method on series and dataframe:

```py
import pandas as pd

df = pd.read_json("./examples/example.json")

df.to_json(sys.stdout)
# {"a":{"0":1,"1":4,"2":7},"b":{"0":2,"1":5,"2":8},"c":{"0":3,"1":6,"2":9}}

df.to_json(sys.stdout, orient="records")
# [{"a":1,"b":2,"c":3},{"a":4,"b":5,"c":6},{"a":7,"b":8,"c":9}]
```

<hr>

### XML and HTML: Web Scraping

Python has many libraries for reading and writing data in HTML and XML formats. Examples include lxml, Beautiful Soup, and html5lib. pandas has a built-in function, `read_html`, which uses all of these libraries to automatically parse tables out of HTML files as dataframe objects.

```py
import pandas as pd

listVar = pd.read_html("./examples/fdic_failed_bank_list.html")

len(listVar) # 1

df = listVar[0]
print(df.head())
# Because df has many columns, pandas inserts a line break character \.
```

<hr>

## Binary Data Formats

### `pickle` module

One simple way to store (or serialize) data in binary format is using Python’s built-in `pickle` module. Pandas objects all have a `to_pickle` method that writes the data to disk in pickle format:

```py
import pandas as pd

df = pd.read_csv("examples/ex1.csv")
df.to_pickle("examples/frame_pickle")
```

Pickle files are in general readable only in Python. You can read any "pickled" object stored in a file by using the built-in `pickle` directly, or even more conveniently using `read_pickle`:

```py
import pandas as pd

print(pd.read_pickle("./examples/frame_pickle"))
"""
   a   b   c   d message
0  1   2   3   4   hello
1  5   6   7   8   world
2  9  10  11  12     foo
"""
```

> `pickle` is recommended only as a short-term storage format. The problem is that it is hard to guarantee that the format will be stable over time; an object pickled today may not unpickle with a later version of a library. Pandas has tried to maintain backward compatibility when possible, but at some point in the future it may be necessary to “break” the pickle format.

> Pandas has built-in support for several other open source binary data formats, such as HDF5, ORC, and Apache Parquet.

<hr>

### Reading Microsoft Excel Files

Pandas also supports reading tabular data stored in Excel 2003 (and higher) files using either the `ExcelFile` class or `read_excel` function. Internally, these tools use the add-on packages `xlrd` and `openpyxl` to read old-style XLS and newer XLSX files, respectively. These must be installed separately from pandas using pip or conda.

#### Using the `ExcelFile` class

To use `ExcelFile`,

- create an instance by passing a path to an `xls` or `xlsx` file.
- The returned object has the `sheet_names` attribute, which gives the access to the list of available sheet names in the file.
- Data stored in a sheet can be read into dataframe using the `parse` method:

```py
import pandas as pd

xlsx = pd.ExcelFile("./examples/ex1.xlsx")
print(xlsx.sheet_names) # ['Sheet1']

print(xlsx.parse(sheet_name="Sheet1"))
"""
   Unnamed: 0  a   b   c   d message
0           0  1   2   3   4   hello
1           1  5   6   7   8   world
2           2  9  10  11  12     foo
"""
```

This Excel table has an index column, so we can indicate that with the `index_col` argument:

```py
import pandas as pd

xlsx = pd.ExcelFile("./examples/ex1.xlsx")

print(xlsx.parse(sheet_name="Sheet1", index_col=0))
"""
   a   b   c   d message
0  1   2   3   4   hello
1  5   6   7   8   world
2  9  10  11  12     foo
"""
```

#### Using the `read_excel` method

If you are reading multiple sheets in a file, then it is faster to create the `ExcelFile`, but you can also simply pass the filename to `read_excel`:

```py
import pandas as pd

df = pd.read_excel("examples/ex1.xlsx", sheet_name="Sheet1")
print(df)
"""
   Unnamed: 0  a   b   c   d message
0           0  1   2   3   4   hello
1           1  5   6   7   8   world
2           2  9  10  11  12     foo
"""
```

#### Writing to an excel file

To write pandas data to Excel format, you must first create an `ExcelWriter`, then write data to it using the pandas object's `to_excel` method:

```py
import pandas as pd

df = pd.read_excel("examples/ex1.xlsx", sheet_name="Sheet1")

writer = pd.ExcelWriter("examples/ex2.xlsx")
df.to_excel(writer, sheet_name="Sheet1")
writer.close()
```

You can also pass a file path to `to_excel` and avoid the `ExcelWriter`:

```py
import pandas as pd

df = pd.read_excel("examples/ex1.xlsx", sheet_name="Sheet1")
df.to_excel("./examples/ex2.xlsx")
```

<hr>

## Interacting with Web APIs

There are a number of ways to access public APIs from Python; one method is the `requests` package, which is an external package and needs to be installed.

To send a GET request to a url, we use the `requests.get` method. It's a good practice to always call `raise_for_status` after using `requests.get` to check for HTTP errors.

```py
import requests

url = "https://api.github.com/repos/pandas-dev/pandas/issues"

resp = requests.get(url)
resp.raise_for_status()

print(resp) # <Response [200]>
```

We can use response object’s `json` method to parse JSON data as a dictionary or list (depending on what JSON is returned). We can then pass the returned data directly to `DataFrame` and extract fields of interest:

```py
import pandas as pd
import requests

url = "https://api.github.com/repos/pandas-dev/pandas/issues"

resp = requests.get(url)
resp.raise_for_status()

data = resp.json()
print(type(data)) # list

issues = pd.DataFrame(data, columns=["number", "title", "labels", "state"])
print(issues)
```

Hence, we can easily interact with a web API using the `requests` package and create a dataframe from the returned data using the `pandas`.

<hr>

## Data Wrangling: Join, Combine, and Reshape

### Hierarchical Indexing

Hierarchical indexing is an important feature of pandas that enables you to have multiple (two or more) index levels on an axis. Another way of thinking about it is that it provides a way for you to work with higher dimensional data in a lower dimensional form.

#### Create a series with hierarchical indexing

Here is an example of creating a series with hierarchical indexing. The created index in this example is called `MultiIndex`.

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)
print(ser)
"""
a  1    0.452329
   2    0.102518
   3    0.737254
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
d  2    0.502630
   3    0.207505
dtype: float64
"""

print(ser.index)
"""
MultiIndex([('a', 1),
            ('a', 2),
            ('a', 3),
            ('b', 1),
            ('b', 3),
            ('c', 1),
            ('c', 2),
            ('d', 2),
            ('d', 3)],
           )
"""
```

#### Selecting subsets of data in series using partial indexing

We can select the subset of the hierarchical indexed data using the partial indexing:

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)

print(ser["b"])
"""
1    0.329789
3    0.684907
dtype: float64
"""

print(ser["b":"c"])
"""
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
dtype: float64
"""

print(ser.loc[["b", "d"]])
"""
b  1    0.329789
   3    0.684907
d  2    0.502630
   3    0.207505
dtype: float64
"""

print(ser.loc[:, 2])
"""
a    0.102518
c    0.679707
d    0.502630
dtype: float64
"""
```

#### Turning hierarchically indexed series into a dataframe

Hierarchical indexing plays an important role in reshaping data and forming a pivot table. For example, you can rearrange the hierarchically indexed series into a dataframe using its `unstack` method. The inverse operation of `unstack` is `stack`:

```py
import pandas as pd

ser = pd.Series(
  np.random.uniform(size=9),
  index=[
    ["a", "a", "a", "b", "b", "c", "c", "d", "d"],
    [1, 2, 3, 1, 3, 1, 2, 2, 3]
  ]
)

print(ser.unstack())
"""
          1         2         3
a  0.452329  0.102518  0.737254
b  0.329789       NaN  0.684907
c  0.601178  0.679707       NaN
d       NaN  0.502630  0.207505
"""

print(ser.unstack().stack())
"""
a  1    0.452329
   2    0.102518
   3    0.737254
b  1    0.329789
   3    0.684907
c  1    0.601178
   2    0.679707
d  2    0.502630
   3    0.207505
dtype: float64
"""
```

#### Dataframe with Hierarchical index and columns

With a DataFrame, either axis can have a hierarchical index:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
print(df)
"""
      column1             column2
    column1.1 column1.2 column2.1
a 1         0         1         2
  2         3         4         5
b 1         6         7         8
  2         9        10        11
"""
```

We can set the names for hierarchical levels using the `names` attribute. The `names` supersede the `name` attribute, which is used only with single-level indexes.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]
print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""
```

#### Checking the number of index levels

You can see how many levels an index has by accessing its `nlevels` attribute:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

print(df.index.nlevels) # 2
print(df.columns.nlevels) # 2
```

#### Selecting subsets of data in a dataframe using partial indexing

With partial column indexing you can similarly select groups of columns in a dataframe:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)

print(df["column1"])
"""
     column1.1  column1.2
a 1          0          1
  2          3          4
b 1          6          7
  2          9         10
"""
```

#### Creating standalone `MultiIndex`

A `MultiIndex` can be created by itself and then reused; the columns in the preceding DataFrame with level names could also be created like this:

```py
import pandas as pd

pd.MultiIndex.from_arrays([
  ["column1", "column1", "column2"],
  ["column1.1", "column1.2", "column2.1"]
], names=["columnKey1", "columnKey2"])

"""
MultiIndex([('column1', 'column1.1'),
            ('column1', 'column1.2'),
            ('column2', 'column2.1')],
           names=['columnKey1', 'columnKey2'])
"""
```

#### Reordering and sorting levels of hierarchical index

At times you may need to rearrange the order of the levels on an axis or sort the data by the values in one specific level. The `swaplevel` method takes two level numbers or names and returns a new object with the levels interchanged (but the data is otherwise unaltered):

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.swaplevel("key1", "key2"))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key2 key1
1    a             0         1         2
2    a             3         4         5
1    b             6         7         8
2    b             9        10        11
"""
```

Instead of using index level names, we can also use index level numbers with `swaplevel`:

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.swaplevel(0, 1))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key2 key1
1    a             0         1         2
2    a             3         4         5
1    b             6         7         8
2    b             9        10        11
"""
```

`sort_index` by default sorts the data lexicographically using all the index levels, but you can choose to use only a single level or a subset of levels to sort by passing the `level` argument.

```py
import pandas as pd

df = pd.DataFrame(
  np.arange(12).reshape((4, 3)),
  index=[["a", "a", "b", "b"], [1, 2, 1, 2]],
  columns=[
    ["column1", "column1", "column2"],
    ["column1.1", "column1.2", "column2.1"]
  ]
)
df.index.names = ["key1", "key2"]
df.columns.names = ["columnKey1", "columnKey2"]

print(df)
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
     2             3         4         5
b    1             6         7         8
     2             9        10        11
"""

print(df.sort_index(level=1))
"""
columnKey1   column1             column2
columnKey2 column1.1 column1.2 column2.1
key1 key2
a    1             0         1         2
b    1             6         7         8
a    2             3         4         5
b    2             9        10        11
"""
```

#### Indexing with a DataFrame's columns

It’s not unusual to want to use one or more columns from a DataFrame as the row index; alternatively, you may wish to move the row index into the DataFrame’s columns. We can do both of this. DataFrame’s `set_index` function will create a new DataFrame using one or more of its columns as the index:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

df2 = df.set_index(["c", "d"])
print(df2)
"""
       a  b
c   d
one 0  0  7
    1  1  6
    2  2  5
two 0  3  4
    1  4  3
    2  5  2
    3  6  1
"""
```

By default, the columns are removed from the DataFrame, though you can leave them in by passing `drop=False` to `set_index`:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

print(df.set_index(["c", "d"], drop=False))
"""
       a  b    c  d
c   d
one 0  0  7  one  0
    1  1  6  one  1
    2  2  5  one  2
two 0  3  4  two  0
    1  4  3  two  1
    2  5  2  two  2
    3  6  1  two  3
"""
```

`reset_index`, on the other hand, does the opposite of `set_index`; the hierarchical index levels are moved into the columns:

```py
import pandas as pd

df = pd.DataFrame({
  "a": range(7),
  "b": range(7, 0, -1),
  "c": ["one", "one", "one", "two", "two", "two", "two"],
  "d": [0, 1, 2, 0, 1, 2, 3]
  })

print(df)
"""
   a  b    c  d
0  0  7  one  0
1  1  6  one  1
2  2  5  one  2
3  3  4  two  0
4  4  3  two  1
5  5  2  two  2
6  6  1  two  3
"""

df2 = df.set_index(["c", "d"])
print(df2)
"""
       a  b
c   d
one 0  0  7
    1  1  6
    2  2  5
two 0  3  4
    1  4  3
    2  5  2
    3  6  1
"""

print(df2.reset_index())
"""
     c  d  a  b
0  one  0  0  7
1  one  1  1  6
2  one  2  2  5
3  two  0  3  4
4  two  1  4  3
5  two  2  5  2
6  two  3  6  1
"""
```

<hr>

### Combining and Merging Datasets

#### Table for an argument reference on `pandas.merge`

`pandas.merge` function arguments

| Argument      | Description                                                                                                                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `left`        | DataFrame to be merged on the left side.                                                                                                                                                               |
| `right`       | DataFrame to be merged on the right side.                                                                                                                                                              |
| `how`         | Type of join to apply: one of `"inner"`, `"outer"`, `"left"`, or `"right"`; defaults to `"inner"`.                                                                                                     |
| `on`          | Column names to join on. Must be found in both DataFrame objects. If not specified and no other join keys given, will use the intersection of the column names in `left` and `right` as the join keys. |
| `left_on`     | Columns in `left` DataFrame to use as join keys. Can be a single column name or a list of column names.                                                                                                |
| `right_on`    | Analogous to `left_on` for `right` DataFrame.                                                                                                                                                          |
| `left_index`  | Use row index in `left` as its join key (or keys, if a `MultiIndex`).                                                                                                                                  |
| `right_index` | Analogous to `left_index`.                                                                                                                                                                             |
| `sort`        | Sort merged data lexicographically by join keys; `False` by default.                                                                                                                                   |
| `suffixes`    | Tuple of string values to append to column names in case of overlap; defaults to `("_x", "_y")` (e.g., if `"data"` in both DataFrame objects, would appear as `"data_x"` and `"data_y"` in result).    |
| `copy`        | If `False`, avoid copying data into resulting data structure in some exceptional cases; by default always copies.                                                                                      |
| `validate`    | Verifies if the merge is of the specified type, whether one-to-one, one-to-many, or many-to-many. See the docstring for full details on the options.                                                   |
| `indicator`   | Adds a special column `_merge` that indicates the source of each row; values will be `"left_only"`, `"right_only"`, or `"both"` based on the origin of the joined data in each row.                    |

#### Database-Style DataFrame Joins

Merge or join operations combine datasets by linking rows using one or more keys. To do this with pandas, we can use the `merge` method:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   a      5
6   b      6
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   d      2
"""

print(pd.merge(df1, df2))
"""
  key  data1  data2
0   b      0      1
1   b      1      1
2   a      2      0
3   a      4      0
4   a      5      0
5   b      6      1
"""
```

Note that I didn’t specify which column to join on. If that information is not specified, `pandas.merge` uses the overlapping column names as the keys. It’s a good practice to specify explicitly, though:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   a      5
6   b      6
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   d      2
"""

print(pd.merge(df1, df2, on="key"))
"""
  key  data1  data2
0   b      0      1
1   b      1      1
2   a      2      0
3   a      4      0
4   a      5      0
5   b      6      1
"""
```

If the column names are different in each object, you can specify them separately:

```py
import pandas as pd

df3 = pd.DataFrame({
  "lkey": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df4 = pd.DataFrame({
  "rkey": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(df3)
"""
  lkey  data1
0    b      0
1    b      1
2    a      2
3    c      3
4    a      4
5    a      5
6    b      6
"""

print(df4)
"""
  rkey  data2
0    a      0
1    b      1
2    d      2
"""

print(pd.merge(df3, df4, left_on="lkey", right_on="rkey"))
"""
  lkey  data1 rkey  data2
0    b      0    b      1
1    b      1    b      1
2    a      2    a      0
3    a      4    a      0
4    a      5    a      0
5    b      6    b      1
"""
```

You may notice that `"c"` and `"d"` values and associated data are missing from the result. By default, `pandas.merge` does an `"inner"` join; the keys in the result are the intersection, or the common set found in both tables. Other possible options are `"left"`, `"right"`, and `"outer"`.

Different join types with the `how` argument:

| Option        | Behavior                                                  |
| ------------- | --------------------------------------------------------- |
| `how="inner"` | Use only the key combinations observed in both tables     |
| `how="left"`  | Use all key combinations found in the left table          |
| `how="right"` | Use all key combinations found in the right table         |
| `how="outer"` | Use all key combinations observed in both tables together |

The outer join takes the union of the keys, combining the effect of applying both left and right joins:

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

df3 = pd.DataFrame({
  "lkey": ["b", "b", "a", "c", "a", "a", "b"],
  "data1": pd.Series(range(7), dtype="Int64")
})

df4 = pd.DataFrame({
  "rkey": ["a", "b", "d"],
  "data2": pd.Series(range(3), dtype="Int64")
})

print(pd.merge(df1, df2, how="outer"))
"""
  key  data1  data2
0   a      2      0
1   a      4      0
2   a      5      0
3   b      0      1
4   b      1      1
5   b      6      1
6   c      3   <NA>
7   d   <NA>      2
"""

print(pd.merge(df3, df4, left_on="lkey", right_on="rkey", how="outer"))
"""
  lkey  data1 rkey  data2
0    a      2    a      0
1    a      4    a      0
2    a      5    a      0
3    b      0    b      1
4    b      1    b      1
5    b      6    b      1
6    c      3  NaN   <NA>
7  NaN   <NA>    d      2
"""
```

```py
import pandas as pd

df1 = pd.DataFrame({
  "key": ["b", "b", "a", "c", "a", "b"],
  "data1": pd.Series(range(6), dtype="Int64")
})

df2 = pd.DataFrame({
  "key": ["a", "b", "a", "b", "d"],
  "data2": pd.Series(range(5), dtype="Int64")
})

print(df1)
"""
  key  data1
0   b      0
1   b      1
2   a      2
3   c      3
4   a      4
5   b      5
"""

print(df2)
"""
  key  data2
0   a      0
1   b      1
2   a      2
3   b      3
4   d      4
"""

print(pd.merge(df1, df2, on="key", how="left"))
"""
   key  data1  data2
0    b      0      1
1    b      0      3
2    b      1      1
3    b      1      3
4    a      2      0
5    a      2      2
6    c      3   <NA>
7    a      4      0
8    a      4      2
9    b      5      1
10   b      5      3
"""
```

To merge with multiple keys, pass a list of column names:

```py
import pandas as pd

left = pd.DataFrame({
  "key1": ["foo", "foo", "bar"],
  "key2": ["one", "two", "one"],
  "lval": pd.Series([1, 2, 3], dtype='Int64')
})

right = pd.DataFrame({
  "key1": ["foo", "foo", "bar", "bar"],
  "key2": ["one", "one", "one", "two"],
  "rval": pd.Series([4, 5, 6, 7], dtype='Int64')
})

print(left)
"""
  key1 key2  lval
0  foo  one     1
1  foo  two     2
2  bar  one     3
"""

print(right)
"""
  key1 key2  rval
0  foo  one     4
1  foo  one     5
2  bar  one     6
3  bar  two     7
"""

print(pd.merge(left, right, on=["key1", "key2"], how="outer"))
"""
  key1 key2  lval  rval
0  bar  one     3     6
1  bar  two  <NA>     7
2  foo  one     1     4
3  foo  one     1     5
4  foo  two     2  <NA>
"""
```

> When you're joining columns on columns, the indexes on the passed DataFrame objects are discarded. If you need to preserve the index values, you can use `reset_index` to append the index to the columns.

A last issue to consider in merge operations is the treatment of overlapping column names. `pandas.merge` has a `suffixes` parameter for specifying strings to append to overlapping names in the left and right DataFrame objects:

```py
import pandas as pd

left = pd.DataFrame({
  "key1": ["foo", "foo", "bar"],
  "key2": ["one", "two", "one"],
  "lval": pd.Series([1, 2, 3], dtype='Int64')
})

right = pd.DataFrame({
  "key1": ["foo", "foo", "bar", "bar"],
  "key2": ["one", "one", "one", "two"],
  "rval": pd.Series([4, 5, 6, 7], dtype='Int64')
})

# without suffixes
print(pd.merge(left, right, on="key1"))
"""
  key1 key2_x  lval key2_y  rval
0  foo    one     1    one     4
1  foo    one     1    one     5
2  foo    two     2    one     4
3  foo    two     2    one     5
4  bar    one     3    one     6
5  bar    one     3    two     7
"""

# with suffixes
print(pd.merge(left, right, on="key1", suffixes=("_left", "_right")))
"""
  key1 key2_left  lval key2_right  rval
0  foo       one     1        one     4
1  foo       one     1        one     5
2  foo       two     2        one     4
3  foo       two     2        one     5
4  bar       one     3        one     6
5  bar       one     3        two     7
"""
```

#### Merging on Index

In some cases, the merge key(s) in a DataFrame will be found in its index (row labels). In this case, you can pass `left_index=True` or `right_index=True` (or both) to indicate that the index should be used as the merge key:

```py
import pandas as pd

left1 = pd.DataFrame({
  "key": ["a", "b", "a", "a", "b", "c"],
  "value": pd.Series(range(6), dtype="Int64")
})

right1 = pd.DataFrame(
  {"group_val": [3.5, 7]},
  index=["a", "b"]
)

print(left1)
"""
  key  value
0   a      0
1   b      1
2   a      2
3   a      3
4   b      4
5   c      5
"""

print(right1)
"""
   group_val
a        3.5
b        7.0
"""

print(pd.merge(left1, right1, left_on="key", right_index=True))
"""
  key  value  group_val
0   a      0        3.5
1   b      1        7.0
2   a      2        3.5
3   a      3        3.5
4   b      4        7.0
"""
```

Using the indexes of both sides of the merge is also possible:

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(pd.merge(left2, right2, how="outer", left_index=True, right_index=True))
"""
   Ohio  Nevada  Missouri  Alabama
a     1       2      <NA>     <NA>
b  <NA>    <NA>         7        8
c     3       4         9       10
d  <NA>    <NA>        11       12
e     5       6        13       14
"""
```

With hierarchically indexed data, things are more complicated, as joining on index is equivalent to a multiple-key merge. In this case, you have to indicate multiple columns to merge on as a list

```py
import pandas as pd

lefth = pd.DataFrame({
  "key1": ["Ohio", "Ohio", "Ohio", "Nevada", "Nevada"],
  "key2": [2000, 2001, 2002, 2001, 2002],
  "data": pd.Series(range(5), dtype="Int64")
})

righth_index = pd.MultiIndex.from_arrays(
  [
    ["Nevada", "Nevada", "Ohio", "Ohio", "Ohio", "Ohio"],
    [2001, 2000, 2000, 2000, 2001, 2002]
  ]
)

righth = pd.DataFrame({
  "event1": pd.Series([0, 2, 4, 6, 8, 10], dtype="Int64", index=righth_index),
  "event2": pd.Series([1, 3, 5, 7, 9, 11], dtype="Int64", index=righth_index)
})

print(lefth)
"""
     key1  key2  data
0    Ohio  2000     0
1    Ohio  2001     1
2    Ohio  2002     2
3  Nevada  2001     3
4  Nevada  2002     4
"""

print(righth)
"""
             event1  event2
Nevada 2001       0       1
       2000       2       3
Ohio   2000       4       5
       2000       6       7
       2001       8       9
       2002      10      11
"""

print(pd.merge(lefth, righth, left_on=["key1", "key2"], right_index=True))
"""
     key1  key2  data  event1  event2
0    Ohio  2000     0       4       5
0    Ohio  2000     0       6       7
1    Ohio  2001     1       8       9
2    Ohio  2002     2      10      11
3  Nevada  2001     3       0       1
"""

print(pd.merge(lefth, righth, left_on=["key1", "key2"], right_index=True, how="outer"))
"""
     key1  key2  data  event1  event2
4  Nevada  2000  <NA>       2       3
3  Nevada  2001     3       0       1
4  Nevada  2002     4    <NA>    <NA>
0    Ohio  2000     0       4       5
0    Ohio  2000     0       6       7
1    Ohio  2001     1       8       9
2    Ohio  2002     2      10      11
"""
```

DataFrame has a `join` instance method to simplify merging by index. It can also be used to combine many DataFrame objects having the same or similar indexes but nonoverlapping columns.

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(left2.join(right2, how="outer"))
"""
   Ohio  Nevada  Missouri  Alabama
a     1       2      <NA>     <NA>
b  <NA>    <NA>         7        8
c     3       4         9       10
d  <NA>    <NA>        11       12
e     5       6        13       14
"""
```

DataFrame’s `join` method performs a left join on the join keys by default. It also supports joining the index of the passed DataFrame on one of the columns of the calling DataFrame:

```py
import pandas as pd

left1 = pd.DataFrame({
  "key": ["a", "b", "a", "a", "b", "c"],
  "value": pd.Series(range(6), dtype="Int64")
})

right1 = pd.DataFrame(
  {"group_val": [3.5, 7]},
  index=["a", "b"]
)

print(left1)
"""
  key  value
0   a      0
1   b      1
2   a      2
3   a      3
4   b      4
5   c      5
"""

print(right1)
"""
   group_val
a        3.5
b        7.0
"""

print(left1.join(right1, on="key"))
"""
  key  value  group_val
0   a      0        3.5
1   b      1        7.0
2   a      2        3.5
3   a      3        3.5
4   b      4        7.0
5   c      5        NaN
"""
```

For simple index-on-index merges, you can pass a list of DataFrames to `join`:

```py
import pandas as pd

left2 = pd.DataFrame(
  [[1., 2.], [3., 4.], [5., 6.]],
  index=["a", "c", "e"],
  columns=["Ohio", "Nevada"]
).astype("Int64")

right2 = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
  index=["b", "c", "d", "e"],
  columns=["Missouri", "Alabama"]
).astype("Int64")

another = pd.DataFrame(
  [[7., 8.], [9., 10.], [11., 12.], [16., 17.]],
  index=["a", "c", "e", "f"],
  columns=["New York", "Oregon"]
)

print(left2)
"""
   Ohio  Nevada
a     1       2
c     3       4
e     5       6
"""

print(right2)
"""
   Missouri  Alabama
b         7        8
c         9       10
d        11       12
e        13       14
"""

print(another)
"""
   New York  Oregon
a       7.0     8.0
c       9.0    10.0
e      11.0    12.0
f      16.0    17.0
"""

print(left2.join([right2, another]))
"""
   Ohio  Nevada  Missouri  Alabama  New York  Oregon
a     1       2      <NA>     <NA>       7.0     8.0
c     3       4         9       10       9.0    10.0
e     5       6        13       14      11.0    12.0
"""

print(left2.join([right2, another], how="outer"))
"""
   Ohio  Nevada  Missouri  Alabama  New York  Oregon
a     1       2      <NA>     <NA>       7.0     8.0
c     3       4         9       10       9.0    10.0
e     5       6        13       14      11.0    12.0
b  <NA>    <NA>         7        8       NaN     NaN
d  <NA>    <NA>        11       12       NaN     NaN
f  <NA>    <NA>      <NA>     <NA>      16.0    17.0
"""
```

#### Concatenating along an axis

Here is a table of `concat` function arguments:

| Argument           | Description                                                                                                                                                                                                                                       |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `objs`             | List or dictionary of pandas objects to be concatenated; this is the only required argument                                                                                                                                                       |
| `axis`             | Axis to concatenate along; defaults to concatenating along rows (`axis="index"`)                                                                                                                                                                  |
| `join`             | Either `"inner"` or `"outer"` (`"outer"` by default); whether to intersect (inner) or union (outer) indexes along the other axes                                                                                                                  |
| `keys`             | Values to associate with objects being concatenated, forming a hierarchical index along the concatenation axis; can be a list or array of arbitrary values, an array of tuples, or a list of arrays (if multiple-level arrays passed in `levels`) |
| `levels`           | Specific indexes to use as hierarchical index level or levels if keys passed                                                                                                                                                                      |
| `names`            | Names for created hierarchical levels if `keys` and/or `levels` passed                                                                                                                                                                            |
| `verify_integrity` | Check new axis in concatenated object for duplicates and raise an exception if so; by default (`False`) allows duplicates                                                                                                                         |
| `ignore_index`     | Do not preserve indexes along concatenation axis, instead produce a new `range(total_length)` index                                                                                                                                               |

To append a single value, a list of values, or another series object to a given series, we need to use the `concat` method:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a single value
ser = pd.concat([ser, pd.Series([5])])

# append a list of values
ser = pd.concat([ser, pd.Series([6, 7, 8])])
print(ser)
"""
0    1
1    2
2    3
3    4
0    5
0    6
1    7
2    8
dtype: int64
"""
```

By default, `concat` works along `axis="index"`, producing another Series. If you pass `axis="columns"`, the result will instead be a DataFrame:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a single value
ser = pd.concat([ser, pd.Series([5])])

# append a list of values
ser = pd.concat([ser, pd.Series([6, 7, 8])], axis="columns")
print(ser)
"""
   0    1
0  1  6.0
1  2  7.0
2  3  8.0
3  4  NaN
0  5  6.0
"""
```

By default, the way the `concat` concatenates the series along indices is the `outer` join. We can also concatenate using the `join="inner"`:

```py
import pandas as pd

ser = pd.Series([1, 2, 3, 4])

# append a list of values
print(pd.concat([ser, pd.Series([6, 7, 8])], axis="columns"))
"""
   0    1
0  1  6.0
1  2  7.0
2  3  8.0
3  4  NaN
"""

print(pd.concat([ser, pd.Series([6, 7, 8])], axis="columns", join="inner"))
"""

   0  1
0  1  6
1  2  7
2  3  8
"""
```

Suppose you wanted to create a hierarchical index on the concatenation axis. To do this, use the `keys` argument:

```py
import pandas as pd

ser1 = pd.Series([1, 2, 3, 4])
ser2 = pd.Series([6, 7, 8])

# append a list of values
print(pd.concat([ser1, ser2], keys=["one", "two"]))
"""
one  0    1
     1    2
     2    3
     3    4
two  0    6
     1    7
     2    8
dtype: int64
"""

print(pd.concat([ser1, ser2], keys=["one", "two"]).unstack())
"""
       0    1    2    3
one  1.0  2.0  3.0  4.0
two  6.0  7.0  8.0  NaN
"""
```

In the case of combining Series along `axis="columns"`, the `keys` become the DataFrame column headers:

```py
import pandas as pd

ser1 = pd.Series([1, 2, 3, 4])
ser2 = pd.Series([6, 7, 8])

# append a list of values
print(pd.concat([ser1, ser2], keys=["one", "two"], axis="columns"))
"""
   one  two
0    1  6.0
1    2  7.0
2    3  8.0
3    4  NaN
"""
```

In the below example, the `keys` argument is used to create a hierarchical index where the first level can be used to identify each of the concatenated DataFrame objects.

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat([df1, df2], axis="columns", keys=["level1-df1", "level1-df2"]))
"""
  level1-df1     level1-df2
         one two      three four
a          0   1        5.0  6.0
b          2   3        NaN  NaN
c          4   5        7.0  8.0
"""
```

If you pass a dictionary of objects instead of a list, the dictionary’s keys will be used for the `keys` option:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat({"level1-df1": df1, "level1-df2":df2}, axis="columns"))
"""
  level1-df1     level1-df2
         one two      three four
a          0   1        5.0  6.0
b          2   3        NaN  NaN
c          4   5        7.0  8.0
"""
```

There are additional arguments governing how the hierarchical index is created. For example, we can name the created axis levels with the `names` argument:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.arange(6).reshape(3, 2),
  index=["a", "b", "c"],
  columns=["one", "two"]
)

df2 = pd.DataFrame(
  5 + np.arange(4).reshape(2, 2),
  index=["a", "c"],
  columns=["three", "four"]
)

print(df1)
"""
   one  two
a    0    1
b    2    3
c    4    5
"""

print(df2)
"""
   three  four
a      5     6
c      7     8
"""

print(pd.concat([df1, df2], axis="columns", keys=["level1-df1", "level1-df2"], names=["upper", "lower"]))
"""
upper level1-df1     level1-df2
lower        one two      three four
a              0   1        5.0  6.0
b              2   3        NaN  NaN
c              4   5        7.0  8.0
"""
```

A last consideration concerns DataFrames in which the row index does not contain any relevant data. To recreate an index from scratch after the concatenation, we can use the `ignore_index=True` option:

```py
import numpy as np
import pandas as pd

df1 = pd.DataFrame(
  np.random.standard_normal((3, 4)),
  columns=["a", "b", "c", "d"]
)

df2 = pd.DataFrame(
  np.random.standard_normal((2, 3)),
  columns=["b", "d", "a"]
)

print(df1)
"""
          a         b         c         d
0 -0.482666  0.520581 -0.339681  1.190217
1  0.670140  1.482087 -0.182321  0.406985
2 -1.509289 -0.480640 -1.029361  1.272381
"""

print(df2)
"""
          b         d         a
0  0.176479 -0.140522  0.958965
1 -0.105916  0.653925  0.647811
"""

print(pd.concat([df1, df2], ignore_index=True))
"""
          a         b         c         d
0 -0.482666  0.520581 -0.339681  1.190217
1  0.670140  1.482087 -0.182321  0.406985
2 -1.509289 -0.480640 -1.029361  1.272381
3  0.958965  0.176479       NaN -0.140522
4  0.647811 -0.105916       NaN  0.653925
"""
```

#### Combining Data with Overlap

If you want to join series with overlap, you can use the series `combine_first` method. This method keeps the data from the first series, if the data is available, and takes the data from the other series if the data from the first series is not available:

```py
import pandas as pd

a = pd.Series(
  [np.nan, 2.5, 0.0, 3.5, 4.5, np.nan],
  index=["f", "e", "d", "c", "b", "a"]
)

b = pd.Series(
  [0., np.nan, 2., np.nan, np.nan, 5.],
  index=["a", "b", "c", "d", "e", "f"]
)

print(a.sort_index())
"""
a    NaN
b    4.5
c    3.5
d    0.0
e    2.5
f    NaN
dtype: float64
"""

print(b)
"""
a    0.0
b    NaN
c    2.0
d    NaN
e    NaN
f    5.0
dtype: float64
"""

print(a.combine_first(b))
"""
a    0.0
b    4.5
c    3.5
d    0.0
e    2.5
f    5.0
dtype: float64
"""
```

With DataFrames, `combine_first` does the same thing column by column, so you can think of it as “patching” missing data in the calling object with data from the object you pass:

```py
import pandas as pd

df1 = pd.DataFrame({
  "a": [1., np.nan, 5., np.nan],
  "b": [np.nan, 2., np.nan, 6.],
  "c": range(2, 18, 4)
})

df2 = pd.DataFrame({
  "a": [5., 4., np.nan, 3., 7.],
  "b": [np.nan, 3., 4., 6., 8.]
})

print(df1)
"""
     a    b   c
0  1.0  NaN   2
1  NaN  2.0   6
2  5.0  NaN  10
3  NaN  6.0  14
"""

print(df2)
"""
     a    b
0  5.0  NaN
1  4.0  3.0
2  NaN  4.0
3  3.0  6.0
4  7.0  8.0
"""

print(df1.combine_first(df2))
"""
     a    b     c
0  1.0  NaN   2.0
1  4.0  2.0   6.0
2  5.0  4.0  10.0
3  3.0  6.0  14.0
4  7.0  8.0   NaN
"""
```

<hr>

### Reshaping and Pivoting

There are a number of basic operations for rearranging tabular data. These are referred to as reshape or pivot operations.

#### Reshaping with Hierarchical Indexing

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

#### Pivoting “Long” to “Wide” Format

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

#### Pivoting “Wide” to “Long” Format

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

<hr>

## Data Aggregation and Group Operations

The way the `groupby` method works is that we use it to split the data into groups, then we apply a function to the groups, and combine them into a result. This can be particularly useful in aggregating or summarizing data.

### Using `groupby` with a series

The basic use case of the `pandas.Series.groupby()` method is to group data by the index and then apply an aggregation function, like sum or mean. The `groupby` method returns `GroupBy` object, which in itself has not anything computed yet. But it's ready to be used for computation on groups of data.

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
print(grouped) # <pandas.core.groupby.generic.SeriesGroupBy object at 0x000001BBB69ED4F0>

print(grouped.sum())
"""
A    15
B     9
C    21
D     0
dtype: int32
"""
```

There are several useful attributes and methods of the `GroupBy` object:

- The `ngroups` attribute of the `GroupBy` object returns the number of groups.
- To access the groups themselves, we can use the `groups` attribute.
- To access the group keys, we can use the `groups.keys()` method.
- Another `GroupBy` method `size` returns a Series containing group sizes

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
grouped.ngroups # 4
grouped.groups # {'A': ['A', 'A', 'A'], 'B': ['B', 'B'], 'C': ['C', 'C', 'C', 'C'], 'D': ['D']}
grouped.groups.keys() # dict_keys(['A', 'B', 'C', 'D'])
grouped.size()
"""
A    3
B    2
C    4
D    1
dtype: int64
"""
```

To get the data of a specific group, we can use the `get_group` method:

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

grouped = ser.groupby(level=0)
grouped.get_group("A")
"""
A    5
A    2
A    8
dtype: int32
"""
```

We can apply custom functions to the groups using the `apply` method:

```py
ser = pd.Series(np.random.permutation(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    5
A    2
A    8
B    6
B    3
C    9
C    7
C    4
C    1
D    0
dtype: int32
"""

def func(x):
  return x.max() - x.min()

result = ser.groupby(level=0).apply(func)
print(result)
"""
A    6
B    3
C    8
D    0
dtype: int32
"""
```

We can also provide arbitrary grouping to group the data.

```py
ser = pd.Series(np.arange(10, 15))
print(ser)
"""
0    10
1    11
2    12
3    13
4    14
dtype: int64
"""

ser.groupby(["sameGroup", "sameGroup", "sameGroup", "sameGroup", "anotherGroup"]).sum()
"""
anotherGroup    14
sameGroup       46
dtype: int64
"""
```

### Using `groupby` with a hierarchically indexed series

When we have a hierarchically indexed series, we can group and aggregate by each level of index:

```py
# Create a Series with MultiIndex
multiIndex = pd.MultiIndex.from_arrays([
    ['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'],
    ['one', 'one', 'two', 'two', 'three', 'one', 'two', 'two', 'three', 'one']
], names=['letters', 'numbers'])

ser = pd.Series(np.random.permutation(10), index=multiIndex)
print(ser)
"""
letters  numbers
A        one        1
         one        0
         two        7
B        two        6
         three      8
C        one        5
         two        9
         two        2
         three      4
D        one        3
dtype: int32
"""

ser.groupby(level=["letters"]).sum()
"""
letters
A     8
B    14
C    20
D     3
dtype: int32
"""

ser.groupby(level=["numbers"]).sum()
"""
numbers
one       9
three    12
two      24
dtype: int32
"""

ser.groupby(level=["letters", "numbers"]).sum()
"""
letters  numbers
A        one         1
         two         7
B        three       8
         two         6
C        one         5
         three       4
         two        11
D        one         3
dtype: int32
"""
```

### Grouping using a dictionary

We can group using a dictionary:

```py
ser = pd.Series(np.arange(10), index=['A', 'A', 'A', 'B', 'B', 'C', 'C', 'C', 'C', 'D'])
print(ser)
"""
A    0
A    1
A    2
B    3
B    4
C    5
C    6
C    7
C    8
D    9
dtype: int64
"""

mapping = {"A": "group1", "B": "group1", "C": "group2", "D": "group2"}

ser.groupby(mapping).sum()
"""
group1    10
group2    35
dtype: int64
"""
```

### Grouping using a function

We can group using a function as well. Any function passed as a group key will be called once per index value with the return values being used as the group names.

```py
ser = pd.Series(np.arange(10), index=['abc', 'abc', 'abc', 'abcd', 'abcd', 'abcd', 'abcd', 'abcde', 'abcde', 'abcde'])
print(ser)
"""
abc      0
abc      1
abc      2
abcd     3
abcd     4
abcd     5
abcd     6
abcde    7
abcde    8
abcde    9
dtype: int64
"""

ser.groupby(len).sum()
"""
3     3
4    18
5    24
dtype: int64
"""
```

### Using `groupby` with a dataframe

We can use the `groupby` method on the dataframe itself or using its columns. Here is how it looks when we use it in different ways:

```py
toBeGrouped = [['Istanbul', 'Turkiye', 15.0],
        ['Ankara', 'Turkiye', 5.0],
        ['Baku', 'Azerbaijan', 2.5],
        ['Ganja', 'Azerbaijan', 0.5],
        ['Sumgayit', 'Azerbaijan', 0.5],
        ['Najaf', 'Iraq', None],
        ['Karbala', 'Iraq', 0.6]]

df = pd.DataFrame(toBeGrouped, columns=["city", "country", "population"])
print(df)
"""
       city     country  population
0  Istanbul     Turkiye        15.0
1    Ankara     Turkiye         5.0
2      Baku  Azerbaijan         2.5
3     Ganja  Azerbaijan         0.5
4  Sumgayit  Azerbaijan         0.5
5     Najaf        Iraq         NaN
6   Karbala        Iraq         0.6
"""

df.groupby(df["country"]).sum()
"""
                         city  population
country
Azerbaijan  BakuGanjaSumgayit         3.5
Iraq             NajafKarbala         0.6
Turkiye        IstanbulAnkara        20.0
"""

df["population"].groupby(df["country"]).sum()
"""
country
Azerbaijan     3.5
Iraq           0.6
Turkiye       20.0
Name: population, dtype: float64
"""

df.groupby(df["country"])["population"].sum()
"""
country
Azerbaijan     3.5
Iraq           0.6
Turkiye       20.0
Name: population, dtype: float64
"""
```

We can also provide arbitrary grouping to group the data.

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df["data1"].groupby(["sameGroup", "sameGroup", "sameGroup", "sameGroup", "sameGroup", "sameGroup", "anotherGroup"]).sum()
"""
anotherGroup    106
sameGroup       615
Name: data1, dtype: int64
"""
```

### Using `groupby` with a hierarchically indexed dataframe

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df["data1"].groupby([df["key1"], df["key2"]]).sum()
"""
key1  key2
a     1       100
      2       101
b     1       104
      2       103
Name: data1, dtype: int64
"""
```

Note that any missing values in a group key are excluded from the result by default. This behavior can be disabled by passing `dropna=False` to `groupby`:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df.groupby("key1").size()
"""
key1
a    3
b    2
dtype: int64
"""

df.groupby("key1", dropna=False).size()
"""
key1
a      3
b      2
NaN    2
dtype: int64
"""
```

The `count` method, used with `groupby` computes the number of nonnull values in each group:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

df.groupby("key1").count()
"""
      key2  data1  data2
key1
a        2      3      3
b        2      2      2
"""
```

### Group by columns

If we want to group by columns of a dataframe, we need to transpose it:

```py
df = pd.DataFrame(
  np.random.standard_normal((3, 3)),
  columns=["a", "b", "c"],
  index=["Joe", "Steve", "Wanda", ]
)

print(df)
"""
              a         b         c
Joe    0.981803  1.133051  0.402913
Steve -0.599898 -0.683760  0.031298
Wanda -0.030887 -0.877773  1.450590
"""

print(df.T)
"""
        Joe     Steve     Wanda
a  0.981803 -0.599898 -0.030887
b  1.133051 -0.683760 -0.877773
c  0.402913  0.031298  1.450590
"""

print(df.T.groupby({"a": "red", "b": "red", "c": "blue", "d": "blue"}).sum())
"""
           Joe     Steve    Wanda
blue  0.402913  0.031298  1.45059
red   2.114854 -1.283658 -0.90866
"""
```

### Iterating over groups

The object returned by `groupby` supports iteration. When we iterate using the `for` loop, we get a sequence of 2-tuples containing the group name along with the chunk of data.

```py
df = pd.DataFrame(
  np.random.standard_normal((3, 3)),
  columns=["a", "b", "c"],
  index=["Joe", "Steve", "Wanda"]
)

print(df)
"""
              a         b         c
Joe    0.302227 -0.284364 -2.379351
Steve -0.998659 -0.732793 -0.908273
Wanda -0.218942 -1.280910  0.733926
"""

for groupName, groupData in df.groupby(level=0):
  print(groupName)
  print(groupData)
"""
Joe
            a         b         c
Joe  0.302227 -0.284364 -2.379351
Steve
              a         b         c
Steve -0.998659 -0.732793 -0.908273
Wanda
              a        b         c
Wanda -0.218942 -1.28091  0.733926
"""
```

When we group by multiple keys and iterate through the group, the first element in the tuple will be a tuple of key values:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

for keyTuple, groupData in df.groupby(["key1", "key2"]):
  print(keyTuple)
  print(groupData, "\n")
"""
('a', np.int64(1))
  key1  key2  data1  data2
0    a     1    100    200

('a', np.int64(2))
  key1  key2  data1  data2
1    a     2    101    201

('b', np.int64(1))
  key1  key2  data1  data2
4    b     1    104    204

('b', np.int64(2))
  key1  key2  data1  data2
3    b     2    103    203
"""
```

<hr>

### Data Aggregation

Aggregations refer to any data transformation that produces scalar values from arrays. We used a few aggregations, above, while focusing on the ways of grouping data. There are more methods that we can use with the `groupby`. Here is a table of optimized `groupby` methods:

| Function name      | Description                                                                  |
| ------------------ | ---------------------------------------------------------------------------- |
| `any`, `all`       | Return True if any (one or more values) or all non-NA values are "truthy"    |
| `nunique()`        | Number of unique values                                                      |
| `count`            | Number of non-NA values                                                      |
| `cummin`, `cummax` | Cumulative minimum and maximum of non-NA values                              |
| `cumsum`           | Cumulative sum of non-NA values                                              |
| `cumprod`          | Cumulative product of non-NA values                                          |
| `first`, `last`    | First and last non-NA values                                                 |
| `mean`             | Mean of non-NA values                                                        |
| `median`           | Arithmetic median of non-NA values                                           |
| `min`, `max`       | Minimum and maximum of non-NA values                                         |
| `nth`              | Retrieve value that would appear at position n with the data in sorted order |
| `ohlc`             | Compute four "open-high-low-close" statistics for time series-like data      |
| `prod`             | Product of non-NA values                                                     |
| `quantile`         | Compute sample quantile                                                      |
| `rank`             | Ordinal ranks of non-NA values, like calling Series.rank                     |
| `size`             | Compute group sizes, returning result as a Series                            |
| `sum`              | Sum of non-NA values                                                         |
| `std`, `var`       | Sample standard deviation and variance                                       |

There is also an `aggregate` method or `agg`, that could be used for aggregations. Note than you can pass the name of the functions in the above table to the `aggregate` method as a string.

#### Custom function for aggregation

To use your own aggregation functions, pass any function that aggregates an array to the `aggregate` method or its short alias `agg`:

```py
df = pd.DataFrame({
  "key1" : ["a", "a", None, "b", "b", "a", None],
  "key2" : pd.Series([1, 2, 1, 2, 1, None, 1], dtype="Int64"),
  "data1" : np.arange(100, 107),
  "data2" : np.arange(200, 207)
})

print(df)
"""
   key1  key2  data1  data2
0     a     1    100    200
1     a     2    101    201
2  None     1    102    202
3     b     2    103    203
4     b     1    104    204
5     a  <NA>    105    205
6  None     1    106    206
"""

grouped = df.groupby("key1")

def func(arr):
  return arr.max() - arr.min()

grouped.agg(func)
"""
      key2  data1  data2
key1
a        1      5      5
b        1      1      1
"""
```

You may want to aggregate using a different function, depending on the column, or multiple functions at once.

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

grouped_pct = grouped["tip_pct"]

def func(arr):
  return arr.max() - arr.min()

print(grouped_pct.agg(["mean", "std", func]))
"""
                 mean       std      func
day  smoker
Fri  No      0.151650  0.028123  0.067349
     Yes     0.174783  0.051293  0.159925
Sat  No      0.158048  0.039767  0.235193
     Yes     0.147906  0.061375  0.290095
Sun  No      0.160113  0.042347  0.193226
     Yes     0.187250  0.154134  0.644685
Thur No      0.160298  0.038774  0.193350
     Yes     0.163863  0.039389  0.151240
"""
```

You don’t need to accept the names, that `GroupBy` gives, to the columns. If you pass a list of `(<name>, <function>)` tuples, the first element of each tuple will be used as the DataFrame column names:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

grouped_pct = grouped["tip_pct"]

grouped_pct.agg([("average", "mean"), ("stdev", "std")])
"""
              average     stdev
day  smoker
Fri  No      0.151650  0.028123
     Yes     0.174783  0.051293
Sat  No      0.158048  0.039767
     Yes     0.147906  0.061375
Sun  No      0.160113  0.042347
     Yes     0.187250  0.154134
Thur No      0.160298  0.038774
     Yes     0.163863  0.039389
"""
```

In the above example, we used only one column of a dataframe, which means we used a series. With a DataFrame we have more options, as we can specify a list of functions to apply to all of the columns or different functions per column.

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped[["tip_pct", "total_bill"]].agg(["count", "mean", "max"])
result
"""
            tip_pct                     total_bill
              count      mean       max      count       mean    max
day  smoker
Fri  No           4  0.151650  0.187735          4  18.420000  22.75
     Yes         15  0.174783  0.263480         15  16.813333  40.17
Sat  No          45  0.158048  0.291990         45  19.661778  48.33
     Yes         42  0.147906  0.325733         42  21.276667  50.81
Sun  No          57  0.160113  0.252672         57  20.506667  48.17
     Yes         19  0.187250  0.710345         19  24.120000  45.35
Thur No          45  0.160298  0.266312         45  17.113111  41.19
     Yes         17  0.163863  0.241255         17  19.190588  43.11
"""
```

As before, a list of tuples with custom names can be passed:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped[["tip_pct", "total_bill"]].agg([("Average", "mean"), ("Variance", "var")])
print(result)
"""
              tip_pct           total_bill
              Average  Variance    Average    Variance
day  smoker
Fri  No      0.151650  0.000791  18.420000   25.596333
     Yes     0.174783  0.002631  16.813333   82.562438
Sat  No      0.158048  0.001581  19.661778   79.908965
     Yes     0.147906  0.003767  21.276667  101.387535
Sun  No      0.160113  0.001793  20.506667   66.099980
     Yes     0.187250  0.023757  24.120000  109.046044
Thur No      0.160298  0.001503  17.113111   59.625081
     Yes     0.163863  0.001551  19.190588   69.808518
"""
```

Now, suppose we wanted to apply potentially different functions to one or more of the columns. To do this, pass a dictionary to `agg` that contains a mapping of column names to any of the function specifications listed so far:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"])

result = grouped.agg({"tip": "max", "size": "sum"})
print(result)
"""
               tip  size
day  smoker
Fri  No       3.50     9
     Yes      4.73    31
Sat  No       9.00   115
     Yes     10.00   104
Sun  No       6.00   167
     Yes      6.50    49
Thur No       6.70   112
     Yes      5.00    40
"""

result = grouped.agg({"tip": ["max", "min"], "size": "sum"})
print(result)
"""
               tip       size
               max   min  sum
day  smoker
Fri  No       3.50  1.50    9
     Yes      4.73  1.00   31
Sat  No       9.00  1.00  115
     Yes     10.00  1.00  104
Sun  No       6.00  1.01  167
     Yes      6.50  1.50   49
Thur No       6.70  1.25  112
     Yes      5.00  2.00   40
"""
```

In all of the examples up until now, the aggregated data comes back with an index, potentially hierarchical, composed from the unique group key combinations. Since this isn’t always desirable, you can disable this behavior in most cases by passing `as_index=False` to `groupby`:

```py
tips = pd.read_csv("examples/tips.csv")
tips["tip_pct"] = tips["tip"] / tips["total_bill"]

grouped = tips.groupby(["day", "smoker"], as_index=False)
print(grouped.mean(numeric_only=True))
"""
    day smoker  total_bill       tip      size   tip_pct
0   Fri     No   18.420000  2.812500  2.250000  0.151650
1   Fri    Yes   16.813333  2.714000  2.066667  0.174783
2   Sat     No   19.661778  3.102889  2.555556  0.158048
3   Sat    Yes   21.276667  2.875476  2.476190  0.147906
4   Sun     No   20.506667  3.167895  2.929825  0.160113
5   Sun    Yes   24.120000  3.516842  2.578947  0.187250
6  Thur     No   17.113111  2.673778  2.488889  0.160298
7  Thur    Yes   19.190588  3.030000  2.352941  0.163863
"""

grouped = tips.groupby(["day", "smoker"])
print(grouped.mean(numeric_only=True))
"""
             total_bill       tip      size   tip_pct
day  smoker
Fri  No       18.420000  2.812500  2.250000  0.151650
     Yes      16.813333  2.714000  2.066667  0.174783
Sat  No       19.661778  3.102889  2.555556  0.158048
     Yes      21.276667  2.875476  2.476190  0.147906
Sun  No       20.506667  3.167895  2.929825  0.160113
     Yes      24.120000  3.516842  2.578947  0.187250
Thur No       17.113111  2.673778  2.488889  0.160298
     Yes      19.190588  3.030000  2.352941  0.163863
"""
```

#### `pivot_table`

While `pivot` provides general purpose pivoting with various data types, pandas also provides `pivot_table` method for pivoting with aggregation of numeric data. In addition to providing a convenient interface to `groupby`, `pivot_table` can add partial totals, also known as margins.

Here is a basic use of it:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "smoker"], values=["size", "tip"]))
"""
                 size       tip
day  smoker
Fri  No      2.250000  2.812500
     Yes     2.066667  2.714000
Sat  No      2.555556  3.102889
     Yes     2.476190  2.875476
Sun  No      2.929825  3.167895
     Yes     2.578947  3.516842
Thur No      2.488889  2.673778
     Yes     2.352941  3.030000
"""
```

In the above example, we indicated the `index` and `values`. We can also specify what data should be presented as `columns`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"]))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000       NaN  3.000000       NaN
     Lunch   2.500000  2.352941  2.666364  3.030000
"""
```

We could augment this table to include partial totals by passing `margins=True`. This has the effect of adding `All` row and column labels.

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"], margins=True))
"""
                 size                           tip
smoker             No       Yes       All        No       Yes       All
day  time
Fri  Dinner  2.000000  2.222222  2.166667  2.750000  3.003333  2.940000
     Lunch   3.000000  1.833333  2.000000  3.000000  2.280000  2.382857
Sat  Dinner  2.555556  2.476190  2.517241  3.102889  2.875476  2.993103
Sun  Dinner  2.929825  2.578947  2.842105  3.167895  3.516842  3.255132
Thur Dinner  2.000000       NaN  2.000000  3.000000       NaN  3.000000
     Lunch   2.500000  2.352941  2.459016  2.666364  3.030000  2.767705
All          2.668874  2.408602  2.569672  2.991854  3.008710  2.998279
"""
```

The default function of the `pivot_table` is the `mean`. We can choose to apply different aggregation function to data using the `aggfunc` option:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"] ,values=["size", "tip"], margins=True, aggfunc=["count"]))
"""
             count
              size               tip
smoker          No   Yes  All     No   Yes  All
day  time
Fri  Dinner    3.0   9.0   12    3.0   9.0   12
     Lunch     1.0   6.0    7    1.0   6.0    7
Sat  Dinner   45.0  42.0   87   45.0  42.0   87
Sun  Dinner   57.0  19.0   76   57.0  19.0   76
Thur Dinner    1.0   NaN    1    1.0   NaN    1
     Lunch    44.0  17.0   61   44.0  17.0   61
All          151.0  93.0  244  151.0  93.0  244
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"], margins=True, aggfunc=len))
"""
              size               tip
smoker          No   Yes  All     No   Yes  All
day  time
Fri  Dinner    3.0   9.0   12    3.0   9.0   12
     Lunch     1.0   6.0    7    1.0   6.0    7
Sat  Dinner   45.0  42.0   87   45.0  42.0   87
Sun  Dinner   57.0  19.0   76   57.0  19.0   76
Thur Dinner    1.0   NaN    1    1.0   NaN    1
     Lunch    44.0  17.0   61   44.0  17.0   61
All          151.0  93.0  244  151.0  93.0  244
"""
```

If some combinations are empty (or otherwise NA), you may wish to pass a `fill_value`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"], values=["size", "tip"]))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000       NaN  3.000000       NaN
     Lunch   2.500000  2.352941  2.666364  3.030000
"""

print(tips.pivot_table(index=["day", "time"], columns=["smoker"] ,values=["size", "tip"], fill_value=0))
"""
                 size                 tip
smoker             No       Yes        No       Yes
day  time
Fri  Dinner  2.000000  2.222222  2.750000  3.003333
     Lunch   3.000000  1.833333  3.000000  2.280000
Sat  Dinner  2.555556  2.476190  3.102889  2.875476
Sun  Dinner  2.929825  2.578947  3.167895  3.516842
Thur Dinner  2.000000  0.000000  3.000000  0.000000
     Lunch   2.500000  2.352941  2.666364  3.030000
"""
```

Here is a table of `pivot_table` options:

| Argument       | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| `values`       | Column name or names to aggregate; by default, aggregates all numeric columns                                         |
| `index`        | Column names or other group keys to group on the rows of the resulting pivot table                                    |
| `columns`      | Column names or other group keys to group on the columns of the resulting pivot table                                 |
| `aggfunc`      | Aggregation function or list of functions (`"mean"` by default); can be any function valid in a `groupby` context     |
| `fill_value`   | Replace missing values in the result table                                                                            |
| `dropna`       | If `True`, do not include columns whose entries are all NA                                                            |
| `margins`      | Add row/column subtotals and grand total (`False` by default)                                                         |
| `margins_name` | Name to use for the margin row/column labels when passing `margins=True;` defaults to `"All"`                         |
| `observed`     | With Categorical group keys, if `True`, show only the observed category values in the keys rather than all categories |

<hr>

#### Crosstab

A cross-tabulation (or crosstab for short) is a special case of a pivot table that can compute group frequencies. The `pandas.crosstab` method does not require a dataframe as an input. It can also accept array-like objects for its rows and columns. The default function for `crosstab` is `len`.

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(index=[tips["day"], tips["time"]], columns=tips["smoker"]))
"""
smoker       No  Yes
day  time
Fri  Dinner   3    9
     Lunch    1    6
Sat  Dinner  45   42
Sun  Dinner  57   19
Thur Dinner   1    0
     Lunch   44   17
"""
```

If we are using the `values` option, we also have to specify the `aggfunc`:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(index=[tips["day"], tips["time"]], columns=tips["smoker"], values=tips["size"], aggfunc="mean"))
"""
smoker             No       Yes
day  time
Fri  Dinner  2.000000  2.222222
     Lunch   3.000000  1.833333
Sat  Dinner  2.555556  2.476190
Sun  Dinner  2.929825  2.578947
Thur Dinner  2.000000       NaN
     Lunch   2.500000  2.352941
"""
```

We can also rename the index and columns, using the `rownames` and the `colnames` options:

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  rownames=["day", "time"],
  columns=tips["smoker"],
  colnames=["smoker"],
  values=tips["size"], aggfunc="mean"))
"""
smoker             No       Yes
day  time
Fri  Dinner  2.000000  2.222222
     Lunch   3.000000  1.833333
Sat  Dinner  2.555556  2.476190
Sun  Dinner  2.929825  2.578947
Thur Dinner  2.000000       NaN
     Lunch   2.500000  2.352941
"""
```

To normalize the data using the `crosstab`, we use the `normalize` option. It accepts a number of different options:

- `‘all’` or `True` – normalizes the values across the entire dataframe (as a percentage of the total across rows and columns)
- `‘index’` – normalizes across rows
- `‘columns’` – normalizes down columns

```py
tips = pd.read_csv("examples/tips.csv")
print(tips.head())
"""
   total_bill   tip smoker  day    time  size
0       16.99  1.01     No  Sun  Dinner     2
1       10.34  1.66     No  Sun  Dinner     3
2       21.01  3.50     No  Sun  Dinner     3
3       23.68  3.31     No  Sun  Dinner     2
4       24.59  3.61     No  Sun  Dinner     4
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize="index"
  ))
"""
smoker             No       Yes
day  time
Fri  Dinner  0.250000  0.750000
     Lunch   0.142857  0.857143
Sat  Dinner  0.517241  0.482759
Sun  Dinner  0.750000  0.250000
Thur Dinner  1.000000  0.000000
     Lunch   0.721311  0.278689
All          0.618852  0.381148
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize="columns"
  ))
"""
smoker             No       Yes       All
day  time
Fri  Dinner  0.019868  0.096774  0.049180
     Lunch   0.006623  0.064516  0.028689
Sat  Dinner  0.298013  0.451613  0.356557
Sun  Dinner  0.377483  0.204301  0.311475
Thur Dinner  0.006623  0.000000  0.004098
     Lunch   0.291391  0.182796  0.250000
"""

print(pd.crosstab(
  index=[tips["day"], tips["time"]],
  columns=tips["smoker"],
  margins=True,
  normalize=True
  ))
"""
smoker             No       Yes       All
day  time
Fri  Dinner  0.012295  0.036885  0.049180
     Lunch   0.004098  0.024590  0.028689
Sat  Dinner  0.184426  0.172131  0.356557
Sun  Dinner  0.233607  0.077869  0.311475
Thur Dinner  0.004098  0.000000  0.004098
     Lunch   0.180328  0.069672  0.250000
All          0.618852  0.381148  1.000000
"""
```

<hr>

## Time Series

The `pandas.to_datetime` method parses many different kinds of date representations and turns them into a `DatetimeIndex`. Standard date formats like ISO 8601 can be parsed quickly:

```py
import pandas as pd

datestrs = ["2011-07-06 12:00:00", "2011-08-06 00:00:00"]

pd.to_datetime(datestrs)
# DatetimeIndex(['2011-07-06 12:00:00', '2011-08-06 00:00:00'], dtype='datetime64[ns]', freq=None)
```

It also handles values that should be considered missing (`None`, empty string, etc.). `NaT` (Not a Time) is pandas’s null value for timestamp data.

```py
import pandas as pd

datestrs = ["2011-07-06 12:00:00", "2011-08-06 00:00:00"]

pd.to_datetime([None])
# DatetimeIndex(['NaT'], dtype='datetime64[ns]', freq=None)

pd.to_datetime([None])[0] # NaT

idx = pd.to_datetime(datestrs + [None])
pd.isna(idx) # array([False, False,  True])
```

A basic kind of time series object in pandas is a Series indexed by timestamps, which is often represented outside of pandas as Python strings or `datetime` objects. Under the hood, these `datetime` objects are put in a `DatetimeIndex`.

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [
  datetime(2011, 1, 2),
  datetime(2011, 1, 5),
  datetime(2011, 1, 7),
  datetime(2011, 1, 8),
  datetime(2011, 1, 10),
  datetime(2011, 1, 12)
]

ts = pd.Series(np.random.standard_normal(6), index=dates)
ts
"""
2011-01-02   -0.322679
2011-01-05    0.311913
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
2011-01-12   -0.317292
dtype: float64
"""

ts.index
"""
DatetimeIndex(['2011-01-02', '2011-01-05', '2011-01-07', '2011-01-08', '2011-01-10', '2011-01-12'],
              dtype='datetime64[ns]', freq=None)
"""

# ts[::2] selects every second element in ts
ts + ts[::2]
"""
2011-01-02   -0.645357
2011-01-05         NaN
2011-01-07   -0.842129
2011-01-08         NaN
2011-01-10    0.899739
2011-01-12         NaN
dtype: float64
"""
```

`DatetimeIndex` includes pandas `Timestamp` object. pandas stores timestamps using NumPy’s `datetime64` data type at the nanosecond resolution. A `pandas.Timestamp` can be substituted at most places where you would use Python's `datetime` object. The reverse is not true, however, because `pandas.Timestamp` can store nanosecond precision data, while `datetime` stores only up to microseconds.

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts.index.dtype # dtype('<M8[ns]')
ts.index[0] # Timestamp('2011-01-02 00:00:00')
```

### Indexing, Selection, Subsetting

To index data in a time series, we can use a timestamp, `datetime` object or a string that is interpretable as a date:

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts.index[2] # Timestamp('2011-01-07 00:00:00')
ts[ts.index[2]] # np.float64(-0.42106435533063935)

ts["2011-01-07"] # np.float64(-0.42106435533063935)

ts[datetime(2011, 1, 7)] # np.float64(-0.42106435533063935)
```

For longer time series, a year or only a year and month can be passed to easily select slices of data:

```py
import numpy as np
import pandas as pd

longer_ts = pd.Series(np.random.standard_normal(1000), index=pd.date_range("2000-01-01", periods=1000))

longer_ts["2001"]
longer_ts["2001-05"]
```

Slicing with `datetime` objects or strings interpretable as dates work as well. Because most time series data is ordered chronologically, you can even slice with timestamps not contained in a time series:

```py
import numpy as np
import pandas as pd
from datetime import datetime

dates = [datetime(2011, 1, 2), datetime(2011, 1, 5),
         datetime(2011, 1, 7), datetime(2011, 1, 8),
         datetime(2011, 1, 10), datetime(2011, 1, 12)]

ts = pd.Series(np.random.standard_normal(6), index=dates)

ts[datetime(2011, 1, 7):]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
2011-01-12   -0.317292
dtype: float64
"""

ts[datetime(2011, 1, 7):datetime(2011, 1, 10)]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
dtype: float64
"""

ts["2011-01-07":"2011-01-10"]
"""
2011-01-07   -0.421064
2011-01-08   -1.069759
2011-01-10    0.449870
dtype: float64
"""

ts["2010-01-01":]
"""
2011-01-02   -0.014972
2011-01-05    1.747874
2011-01-07    1.132017
2011-01-08   -1.062250
2011-01-10    0.170324
2011-01-12   -0.608212
dtype: float64
"""
```

Remember that slicing in this manner produces views on the source time series, like slicing NumPy arrays. This means that no data is copied, and modifications on the slice will be reflected in the original data. There is an equivalent instance method, `truncate`, that slices a Series between two dates.

### Date Ranges, Frequencies, and Shifting

### `date_range`

The `date_range` method in Pandas generates a `DatetimeIndex` with an indicated length according to a particular frequency.

```py
import pandas as pd

dr = pd.date_range(start="2024-08-10", end="2024-08-20")
print(dr)
"""
DatetimeIndex(['2024-08-10', '2024-08-11', '2024-08-12', '2024-08-13',
               '2024-08-14', '2024-08-15', '2024-08-16', '2024-08-17',
               '2024-08-18', '2024-08-19', '2024-08-20'],
              dtype='datetime64[ns]', freq='D')
"""
```

The `date_range` method takes following arguments:

- `start` - left bound for generating dates
- `end` - right bound for generating dates
- `periods` (optional) - number of periods to generate
- `freq` (optional) - specifies the frequency of the generated dates
- `tz` (optional) - time zone name for returning localized DatetimeIndex.
- `name` (optional) - name for the resulting DateTimeIndex
- `kwargs` (optional) - the unit of the arg for epoch times.

Here is one more example, this time using the `periods` keyword argument, as well. Remember, if you pass only one of `start` or `end` dates, you must pass a number of `periods` to generate:

```py
import pandas as pd

dr = pd.date_range(start="2024-08-10", end="2024-08-20", periods=5)
print(dr)
"""
DatetimeIndex(['2024-08-10 00:00:00', '2024-08-12 12:00:00',
               '2024-08-15 00:00:00', '2024-08-17 12:00:00',
               '2024-08-20 00:00:00'],
              dtype='datetime64[ns]', freq=None)
"""

print(pd.date_range(start="2024-08-10", periods=5))
"""
DatetimeIndex(['2024-08-10', '2024-08-11', '2024-08-12', '2024-08-13', '2024-08-14'],
              dtype='datetime64[ns]', freq='D')
"""

print(pd.date_range(end="2024-08-20", periods=5))
"""
DatetimeIndex(['2024-08-16', '2024-08-17', '2024-08-18', '2024-08-19', '2024-08-20'],
              dtype='datetime64[ns]', freq='D')
"""
```

In the above example, we have generated 5 periods, and because we haven't provided the `freq` argument, it defaulted to `D`, which means daily frequency. There are many values that we could provide to `freq`. Here is a table of base time series frequencies (not comprehensive):

| Alias                     | Offset type            | Description                                                                                                                                                     |
| ------------------------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `D`                       | `Day`                  | Calendar daily                                                                                                                                                  |
| `B`                       | `BusinessDay`          | Business daily                                                                                                                                                  |
| `h`                       | `Hour`                 | Hourly                                                                                                                                                          |
| `min`                     | `Minute`               | Once a minute                                                                                                                                                   |
| `L` or `ms`               | `Milli`                | Millisecond (1/1,000 of 1 second)                                                                                                                               |
| `S`                       | `Second`               | Once a second                                                                                                                                                   |
| `U`                       | `Micro`                | Microsecond (1/1,000,000 of 1 second)                                                                                                                           |
| `ME`                      | `MonthEnd`             | Last calendar day of month                                                                                                                                      |
| `BME`                     | `BusinessMonthEnd`     | Last business day (weekday) of month                                                                                                                            |
| `MS`                      | `MonthBegin`           | First calendar day of month                                                                                                                                     |
| `BMS`                     | `BusinessMonthBegin`   | First weekday of month                                                                                                                                          |
| `W-MON, W-TUE, ...`       | `Week`                 | Weekly on given day of week (MON, TUE, WED, THU, FRI, SAT, or SUN)                                                                                              |
| `WOM-1MON, WOM-2MON, ...` | `WeekOfMonth`          | Generate weekly dates in the first, second, third, or fourth week of the month (e.g., WOM-3FRI for the third Friday of each month)                              |
| `Q-JAN, Q-FEB, ...`       | `QuarterEnd`           | Quarterly dates anchored on last calendar day of each month, for year ending in indicated month (JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, or DEC) |
| `BQ-JAN, BQ-FEB, ...`     | `BusinessQuarterEnd`   | Quarterly dates anchored on last weekday day of each month, for year ending in indicated month                                                                  |
| `QS-JAN, QS-FEB, ...`     | `QuarterBegin`         | Quarterly dates anchored on first calendar day of each month, for year ending in indicated month                                                                |
| `BQS-JAN, BQS-FEB, ...`   | `BusinessQuarterBegin` | Quarterly dates anchored on first weekday day of each month, for year ending in indicated month                                                                 |
| `Y-JAN, Y-FEB, ...`       | `YearEnd`              | Annual dates anchored on last calendar day of given month (JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, or DEC)                                       |
| `BA-JAN, BA-FEB, ...`     | `BusinessYearEnd`      | Annual dates anchored on last weekday of given month                                                                                                            |
| `AS-JAN, AS-FEB, ...`     | `YearBegin`            | Annual dates anchored on first day of given month                                                                                                               |
| `BAS-JAN, BAS-FEB, ...`   | `BusinessYearBegin`    | Annual dates anchored on first weekday of given month                                                                                                           |

Here is an example of using `pandas.date_range` with the `freq` argument:

```py
import pandas as pd

print(pd.date_range("2000-01-01", "2000-12-01", freq="BME"))
"""
DatetimeIndex(['2000-01-31', '2000-02-29', '2000-03-31', '2000-04-28',
               '2000-05-31', '2000-06-30', '2000-07-31', '2000-08-31',
               '2000-09-29', '2000-10-31', '2000-11-30'],
              dtype='datetime64[ns]', freq='BME')
"""
```

We can also use the combination of the frequencies from the above table:

```py
import pandas as pd

print(pd.date_range("2000-01-01", periods=5, freq="1h30min"))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 01:30:00',
               '2000-01-01 03:00:00', '2000-01-01 04:30:00',
               '2000-01-01 06:00:00'],
              dtype='datetime64[ns]', freq='90min')
"""

print(pd.date_range("2000-01-01", "2000-01-02 00:00", freq="4h"))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 04:00:00',
               '2000-01-01 08:00:00', '2000-01-01 12:00:00',
               '2000-01-01 16:00:00', '2000-01-01 20:00:00',
               '2000-01-02 00:00:00'],
              dtype='datetime64[ns]', freq='4h')
"""
```

For each base frequency, there is an object referred to as a date offset. We can use these as well:

```py
import pandas as pd
from pandas.tseries.offsets import Hour, Minute

print(Hour(4)) # <4 * Hours>
print(Hour(2) + Minute(30)) # <150 * Minutes>

print(pd.date_range("2000-01-01", periods=5, freq=Hour(1)+Minute(30)))
"""
DatetimeIndex(['2000-01-01 00:00:00', '2000-01-01 01:30:00',
               '2000-01-01 03:00:00', '2000-01-01 04:30:00',
               '2000-01-01 06:00:00'],
              dtype='datetime64[ns]', freq='90min')
"""
```

If we provide time to the `pandas.date_range`, by default it preserves the time of the timestamp:

```py
import pandas as pd

pd.date_range("2012-05-02 12:56:31", periods=5)
"""
DatetimeIndex(['2012-05-02 12:56:31', '2012-05-03 12:56:31',
               '2012-05-04 12:56:31', '2012-05-05 12:56:31',
               '2012-05-06 12:56:31'],
              dtype='datetime64[ns]', freq='D')
"""
```

Sometimes you will have start or end dates with time information but want to generate a set of timestamps normalized to midnight as a convention. To do this, there is a `normalize` option:

```py
import pandas as pd

pd.date_range("2012-05-02 12:56:31", periods=5, normalize=True)
"""
DatetimeIndex(['2012-05-02', '2012-05-03', '2012-05-04', '2012-05-05', '2012-05-06'],
              dtype='datetime64[ns]', freq='D')
"""
```

Shifting refers to moving data backward and forward through time. Both Series and DataFrame have a `shift` method for doing naive shifts forward or backward, leaving the index unmodified:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(2))
"""
2000-01-31         NaN
2000-02-29         NaN
2000-03-31   -0.623963
2000-04-30   -0.363125
Freq: ME, dtype: float64
"""

print(ts.shift(-2))
"""
2000-01-31    0.586776
2000-02-29   -0.117355
2000-03-31         NaN
2000-04-30         NaN
Freq: ME, dtype: float64
"""
```

Because naive shifts leave the index unmodified, some data is discarded. Thus if the frequency is known, it can be passed to `shift` to advance the timestamps in the index. The `freq` option shifts the data by the provided frequency:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(2))
"""
2000-01-31         NaN
2000-02-29         NaN
2000-03-31   -0.623963
2000-04-30   -0.363125
Freq: ME, dtype: float64
"""

print(ts.shift(2, freq="ME"))
"""
2000-03-31   -0.623963
2000-04-30   -0.363125
2000-05-31    0.586776
2000-06-30   -0.117355
Freq: ME, dtype: float64
"""
```

Here are few more examples of shifting the time series index by a provided frequency:

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31   -0.623963
2000-02-29   -0.363125
2000-03-31    0.586776
2000-04-30   -0.117355
Freq: ME, dtype: float64
"""

print(ts.shift(3, freq="D"))
"""
2000-02-03   -0.623963
2000-03-03   -0.363125
2000-04-03    0.586776
2000-05-03   -0.117355
dtype: float64
"""

print(ts.shift(1, freq="90min"))
"""
2000-01-31 01:30:00   -0.623963
2000-02-29 01:30:00   -0.363125
2000-03-31 01:30:00    0.586776
2000-04-30 01:30:00   -0.117355
dtype: float64
"""
```

### `day_name`

The `day_name` method in the pandas library is used to extract the names of the days of the week from a DatetimeIndex, Series, or DataFrame containing datetime-like values.

```py
import pandas as pd

ts = pd.Series(np.random.standard_normal(4), index=pd.date_range("2000-01-01", periods=4, freq="ME"))

print(ts)
"""
2000-01-31    0.143187
2000-02-29    2.248076
2000-03-31    1.136395
2000-04-30   -0.789329
Freq: ME, dtype: float64
"""

print(ts.index.day_name())
# Index(['Monday', 'Tuesday', 'Friday', 'Sunday'], dtype='object')
```

### Time Zone Handling

Many time series users choose to work with time series in coordinated universal time or UTC, which is the geography-independent international standard. In Python, time zone information comes from the third-party `pytz` library (installable with pip or conda), which exposes the Olson database, a compilation of world time zone information. Since pandas has a hard dependency on `pytz`, it isn't necessary to install it separately.

To get a time zone object from `pytz`, use `pytz.timezone`. Methods in pandas will accept either time zone names or these objects.

```py
import pytz

tz = pytz.timezone("America/New_York")
```

By default, time series in pandas are time zone naive. We can indicate that time series belongs to a specific local time using the `<timeSeries>.tz_localize("<time zone>")` method. After having the time series localized, we can convert it to different time zones using the `<timeSeries>.tz_convert("<time zone>")` method:

```py
import pandas as pd

dates = pd.date_range("2012-03-09 09:30", periods=6)
print(dates)
"""
DatetimeIndex(['2012-03-09 09:30:00', '2012-03-10 09:30:00',
               '2012-03-11 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00', '2012-03-14 09:30:00'],
              dtype='datetime64[ns]', freq='D')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-09 09:30:00   -1.200803
2012-03-10 09:30:00    0.448043
2012-03-11 09:30:00   -0.092872
2012-03-12 09:30:00    0.962243
2012-03-13 09:30:00   -0.272828
2012-03-14 09:30:00   -1.912672
Freq: D, dtype: float64
"""

ts_utc = ts.tz_localize("UTC")
print(ts_utc)
"""
2012-03-09 09:30:00+00:00   -1.200803
2012-03-10 09:30:00+00:00    0.448043
2012-03-11 09:30:00+00:00   -0.092872
2012-03-12 09:30:00+00:00    0.962243
2012-03-13 09:30:00+00:00   -0.272828
2012-03-14 09:30:00+00:00   -1.912672
Freq: D, dtype: float64
"""

print(ts_utc.tz_convert("Europe/Berlin"))
"""
2012-03-09 10:30:00+01:00   -1.200803
2012-03-10 10:30:00+01:00    0.448043
2012-03-11 10:30:00+01:00   -0.092872
2012-03-12 10:30:00+01:00    0.962243
2012-03-13 10:30:00+01:00   -0.272828
2012-03-14 10:30:00+01:00   -1.912672
Freq: D, dtype: float64
"""
```

`tz_localize` and `tz_convert` are also instance methods on `DatetimeIndex`.

```py
import pandas as pd

dates = pd.date_range("2012-03-09 09:30", periods=6)
print(dates)
"""
DatetimeIndex(['2012-03-09 09:30:00', '2012-03-10 09:30:00',
               '2012-03-11 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00', '2012-03-14 09:30:00'],
              dtype='datetime64[ns]', freq='D')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-09 09:30:00   -1.200803
2012-03-10 09:30:00    0.448043
2012-03-11 09:30:00   -0.092872
2012-03-12 09:30:00    0.962243
2012-03-13 09:30:00   -0.272828
2012-03-14 09:30:00   -1.912672
Freq: D, dtype: float64
"""

print(ts.index.tz_localize("America/New_York"))
"""
DatetimeIndex(['2012-03-09 09:30:00-05:00', '2012-03-10 09:30:00-05:00',
               '2012-03-11 09:30:00-04:00', '2012-03-12 09:30:00-04:00',
               '2012-03-13 09:30:00-04:00', '2012-03-14 09:30:00-04:00'],
              dtype='datetime64[ns, America/New_York]', freq=None)
"""
```

It should be noted that time zone localization and conversion might not always be necessary. For example, `date_range` can generate time series with a pre-set time zone:

```py
import pandas as pd

print(pd.date_range("2012-03-09 09:30", periods=10, tz="UTC"))
"""
DatetimeIndex(['2012-03-09 09:30:00+00:00', '2012-03-10 09:30:00+00:00',
               '2012-03-11 09:30:00+00:00', '2012-03-12 09:30:00+00:00',
               '2012-03-13 09:30:00+00:00', '2012-03-14 09:30:00+00:00',
               '2012-03-15 09:30:00+00:00', '2012-03-16 09:30:00+00:00',
               '2012-03-17 09:30:00+00:00', '2012-03-18 09:30:00+00:00'],
              dtype='datetime64[ns, UTC]', freq='D')
"""
```

Individual `Timestamp` objects similarly can be localized from naive to time zone-aware and converted from one time zone to another:

```py
import pandas as pd

stamp = pd.Timestamp("2011-03-12 04:00")
print(stamp) # Timestamp('2011-03-12 04:00:00')

stamp_utc = stamp.tz_localize("utc")
print(stamp_utc) # Timestamp('2012-03-12 04:00:00+0000', tz='UTC')

print(stamp_utc.tz_convert("America/New_York"))
# Timestamp('2011-03-11 23:00:00-0500', tz='America/New_York')
```

You can also pass a time zone when creating the `Timestamp`:

```py
import pandas as pd

stamp_Istanbul = pd.Timestamp("2011-03-12 04:00", tz="Europe/Istanbul")

print(stamp_Istanbul) # 2011-03-12 04:00:00+02:00

# Time zone-aware Timestamp objects internally store a UTC timestamp value as nanoseconds since the Unix epoch (January 1, 1970)
print(stamp_Istanbul.value) # 1299895200000000000
```

When performing time arithmetic using pandas’s DateOffset objects, pandas respects daylight saving time transitions where possible.

```py
import pandas as pd
from pandas.tseries.offsets import Hour, Minute

stamp = pd.Timestamp("2012-03-11 01:30", tz="US/Eastern")

print(stamp)
# Timestamp('2012-03-11 01:30:00-0500', tz='US/Eastern')

stamp + Hour()
# Timestamp('2012-03-11 03:30:00-0400', tz='US/Eastern')

stamp = pd.Timestamp("2012-11-04 00:30", tz="US/Eastern")

print(stamp)
# Timestamp('2012-11-04 00:30:00-0400', tz='US/Eastern')

stamp + 2 * Hour()
# Timestamp('2012-11-04 01:30:00-0500', tz='US/Eastern')
```

Operations between time zone-naive and time zone-aware data are not supported and will raise an exception.

If two time series with different time zones are combined, the result will be UTC. Since the timestamps are stored under the hood in UTC, this is a straightforward operation and requires no conversion.

```py
import pandas as pd

dates = pd.date_range("2012-03-07 09:30", periods=10, freq="B")
print(dates)
"""
DatetimeIndex(['2012-03-07 09:30:00', '2012-03-08 09:30:00',
               '2012-03-09 09:30:00', '2012-03-12 09:30:00',
               '2012-03-13 09:30:00'],
              dtype='datetime64[ns]', freq='B')
"""

ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)
print(ts)
"""
2012-03-07 09:30:00   -0.797245
2012-03-08 09:30:00    0.344233
2012-03-09 09:30:00   -1.297468
2012-03-12 09:30:00   -0.151718
2012-03-13 09:30:00    0.490548
Freq: B, dtype: float64
"""

ts1 = ts[:3].tz_localize("Europe/London")
print(ts1)
"""
2012-03-07 09:30:00+00:00   -0.797245
2012-03-08 09:30:00+00:00    0.344233
2012-03-09 09:30:00+00:00   -1.297468
dtype: float64
"""

ts2 = ts1[1:].tz_convert("Europe/Moscow")
print(ts2)
"""
2012-03-08 13:30:00+04:00    0.344233
2012-03-09 13:30:00+04:00   -1.297468
dtype: float64
"""

result = ts1 + ts2
print(result)
"""
2012-03-07 09:30:00+00:00         NaN
2012-03-08 09:30:00+00:00    0.688465
2012-03-09 09:30:00+00:00   -2.594936
dtype: float64
"""

print(result.index)
"""
DatetimeIndex(['2012-03-07 09:30:00+00:00', '2012-03-08 09:30:00+00:00', '2012-03-09 09:30:00+00:00'],
              dtype='datetime64[ns, UTC]', freq=None)
"""
```

### Periods and Period Arithmetic

The `pandas.Period` class represents the period data type, requiring a string or integer and a supported frequency (the same frequencies as in the table for the `date_range` method). In the below example, the `Period` object represents the full time span from January 1, 2011, to December 31, 2011, inclusive.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
print(p) # Period('2011', 'Y-DEC')
```

Adding and subtracting integers from periods has the effect of shifting their frequency. If two periods have the same frequency, their difference is the number of units between them as a date offset.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
print(p) # Period('2011', 'Y-DEC')

print(p + 5) # Period('2016', 'Y-DEC')

print(pd.Period("2014", freq="Y-DEC") - p)
# <3 * YearEnds: month=12>
```

Regular ranges of periods can be constructed with the `period_range` function. It creates the `PeriodIndex` object. The `PeriodIndex` class stores a sequence of periods and can serve as an axis index in any pandas data structure.

```py
import numpy as np
import pandas as pd

periods = pd.period_range("2000-01-01", "2000-06-30", freq="M")
print(periods)
# PeriodIndex(['2000-01', '2000-02', '2000-03', '2000-04', '2000-05', '2000-06'], dtype='period[M]')

print(pd.Series(np.random.standard_normal(6), index=periods))
"""
2000-01    1.991928
2000-02   -1.836094
2000-03   -1.116105
2000-04    0.971672
2000-05    1.723111
2000-06    0.547108
Freq: M, dtype: float64
"""
```

We can also create a `PeriodIndex` object using the `PeriodIndex` method and an array of strings representing periods:

```py
import pandas as pd

values = ["2001Q3", "2002Q2", "2003Q1"]

index = pd.PeriodIndex(values, freq="Q-DEC")
print(index)
# PeriodIndex(['2001Q3', '2002Q2', '2003Q1'], dtype='period[Q-DEC]')
```

Periods and `PeriodIndex` objects can be converted to another frequency with their `asfreq` method.

```py
import pandas as pd

p = pd.Period("2011", freq="Y-DEC")
p # Period('2011', 'Y-DEC')

p.asfreq("M", how="start") # Period('2011-01', 'M')
p.asfreq("M", how="end") # Period('2011-12', 'M')
p.asfreq("M") # Period('2011-12', 'M')
```

For a fiscal year ending on a month other than December, the corresponding monthly subperiods are different:

```py
import pandas as pd

p = pd.Period("2011", freq="Y-JUN")
p # Period('2011', 'Y-JUN')

p.asfreq("M", how="start") # Period('2010-07', 'M')
p.asfreq("M", how="end") # Period('2011-06', 'M')
```

Just like a single period could be converted, whole `PeriodIndex` objects or time series can be similarly converted using the `asfreq` method:

```py
import pandas as pd

periods = pd.period_range("2006", "2009", freq="Y-DEC")
periods # PeriodIndex(['2006', '2007', '2008', '2009'], dtype='period[Y-DEC]')

ts = pd.Series(np.random.standard_normal(len(periods)), index=periods)
ts
"""
2006    0.890714
2007    1.207863
2008   -0.566002
2009    0.128466
Freq: Y-DEC, dtype: float64
"""

ts.asfreq("M", how="start")
"""
2006-01    0.890714
2007-01    1.207863
2008-01   -0.566002
2009-01    0.128466
Freq: M, dtype: float64
"""

ts.asfreq("D", how="end")
"""
2006-12-31    0.890714
2007-12-31    1.207863
2008-12-31   -0.566002
2009-12-31    0.128466
Freq: D, dtype: float64
"""
```

Here is an example of creating a quarterly period. This one ends in January, and we can confirm it by converting it to a daily period:

```py
import pandas as pd

p = pd.Period("2012Q4", freq="Q-JAN")
p # Period('2012Q4', 'Q-JAN')

p.asfreq("D", how="start") # Period('2011-11-01', 'D')
p.asfreq("D", how="end") # Period('2012-01-31', 'D')
```

The `to_timestamp` method returns the `Timestamp` at the start of the period by default.

```py
import pandas as pd

p = pd.Period("2012Q4", freq="Q-JAN")
p # Period('2012Q4', 'Q-JAN')

p.to_timestamp() # Timestamp('2011-11-01 00:00:00')
```

You can generate quarterly ranges using `pandas.period_range`.

```py
import pandas as pd

periods = pd.period_range("2011Q3", "2012Q4", freq="Q-JAN")
periods
# PeriodIndex(['2011Q3', '2011Q4', '2012Q1', '2012Q2', '2012Q3', '2012Q4'], dtype='period[Q-JAN]')

ts = pd.Series(np.arange(len(periods)), index=periods)
ts
"""
2011Q3    0
2011Q4    1
2012Q1    2
2012Q2    3
2012Q3    4
2012Q4    5
Freq: Q-JAN, dtype: int64
"""

periods.asfreq("D", "end")
"""
PeriodIndex(['2010-10-31', '2011-01-31', '2011-04-30', '2011-07-31', '2011-10-31', '2012-01-31'],
            dtype='period[D]')
"""

periods.asfreq("D", "end") - 1
"""
PeriodIndex(['2010-10-30', '2011-01-30', '2011-04-29', '2011-07-30', '2011-10-30', '2012-01-30'],
            dtype='period[D]')
"""

(periods.asfreq("D", "end") - 1).asfreq("h", "start")
"""
PeriodIndex(['2010-10-30 00:00', '2011-01-30 00:00', '2011-04-29 00:00',
             '2011-07-30 00:00', '2011-10-30 00:00', '2012-01-30 00:00'],
            dtype='period[h]')
"""

(periods.asfreq("D", "end") - 1).asfreq("h", "start") + 1
"""
PeriodIndex(['2010-10-30 01:00', '2011-01-30 01:00', '2011-04-29 01:00',
             '2011-07-30 01:00', '2011-10-30 01:00', '2012-01-30 01:00'],
            dtype='period[h]')
"""
```

Series and DataFrame objects indexed by timestamps can be converted to periods with the `to_period` method. While the frequency of the new PeriodIndex is inferred from the timestamps by default, you can specify any supported frequency. To convert back to timestamps, use the `to_timestamp` method, which returns a `DatetimeIndex`.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=3, freq="ME")
dates
# DatetimeIndex(['2000-01-31', '2000-02-29', '2000-03-31'], dtype='datetime64[ns]', freq='ME')

ts = pd.Series(np.random.standard_normal(3), index=dates)
ts
"""
2000-01-31    0.389436
2000-02-29   -0.492043
2000-03-31    0.011621
Freq: ME, dtype: float64
"""

pts = ts.to_period()
pts
"""
2000-01    0.389436
2000-02   -0.492043
2000-03    0.011621
Freq: M, dtype: float64
"""

ts.to_period("Q-DEC")
"""
2000Q1    0.389436
2000Q1   -0.492043
2000Q1    0.011621
Freq: Q-DEC, dtype: float64
"""

pts.to_timestamp(how="end")
"""
2000-01-31 23:59:59.999999999    0.389436
2000-02-29 23:59:59.999999999   -0.492043
2000-03-31 23:59:59.999999999    0.011621
dtype: float64
"""
```

We can set a dataframe that doesn't have a `PeriodIndex` to have one using the `pandas.PeriodIndex.from_fields` method. Here is an example, we change the index of a dataframe to have a `PeriodIndex`.

```py
import pandas as pd

data = pd.read_csv("examples/macrodata.csv")

print(data[["year", "quarter", "realgdp"]].head(5))
"""
   year  quarter   realgdp
0  1959        1  2710.349
1  1959        2  2778.801
2  1959        3  2775.488
3  1959        4  2785.204
4  1960        1  2847.699
"""

# create a PeriodIndex from the columns "year", and "quarter"
index = pd.PeriodIndex.from_fields(year=data["year"], quarter=data["quarter"], freq="Q-DEC")

# change the index of a dataframe
data.index = index

print(data[["year", "quarter", "realgdp"]].head(5))
"""
        year  quarter   realgdp
1959Q1  1959        1  2710.349
1959Q2  1959        2  2778.801
1959Q3  1959        3  2775.488
1959Q4  1959        4  2785.204
1960Q1  1960        1  2847.699
"""
```

### Resampling and Frequency Conversion

**Resampling** refers to the process of converting a time series from one frequency to another. Aggregating higher frequency data to lower frequency is called **downsampling**, while converting lower frequency to higher frequency is called **upsampling**.

`pandas` objects are equipped with a `resample` method, which is the workhorse function for all frequency conversion. `resample` has a similar API to `groupby`; you call `resample` to group the data, then call an aggregation function:

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=100)
ts = pd.Series(np.random.standard_normal(len(dates)), index=dates)

ts.resample("ME").mean()
"""
2000-01-31    0.161922
2000-02-29    0.178505
2000-03-31   -0.104694
2000-04-30   -0.913025
Freq: ME, dtype: float64
"""

ts.resample("QE-JAN").mean()
"""
2000-01-31    0.161922
2000-04-30   -0.091103
Freq: QE-JAN, dtype: float64
"""
```

`resample` is a flexible method that can be used to process large time series. Here is a summary of `resample` method arguments.

| Argument      | Description                                                                                                                                                                                           |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rule`        | String, DateOffset, or timedelta indicating desired resampled frequency (for example, `"M"`, `"5min"`, or `Second(15)`)                                                                               |
| `axis`        | Axis to resample on; default `axis=0`                                                                                                                                                                 |
| `fill_method` | How to interpolate when upsampling, as in `"ffill"` or `"bfill"`; by default does no interpolation                                                                                                    |
| `closed`      | In downsampling, which end of each interval is closed (inclusive), `"right"` or `"left"`                                                                                                              |
| `label`       | In downsampling, how to label the aggregated result, with the `"right"` or `"left"` bin edge (e.g., the 9:30 to 9:35 five-minute interval could be labeled `9:30` or `9:35`)                          |
| `limit`       | When forward or backward filling, the maximum number of periods to fill                                                                                                                               |
| `convention`  | When resampling periods, the convention (`"start"` or `"end"`) for converting the low-frequency period to high frequency; defaults to `"start"`                                                       |
| `origin`      | The "base" timestamp from which to determine the resampling bin edges; can also be one of `"epoch"`, `"start"`, `"start_day"`, `"end"`, or `"end_day"`; see the `resample` docstring for full details |
| `offset`      | An offset timedelta added to the origin; defaults to `None`                                                                                                                                           |

#### Downsampling

Here is an example of downsampling.

- We'll create a date range with a minute frequency.
- We'll create a time series data using the created date range.
- Then, we'll resample the time series from 1-minute frequency to 5-minute one. Our aggregation function for the resampling will be the `sum`.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min").sum()
"""
2000-01-01 00:00:00    10
2000-01-01 00:05:00    35
2000-01-01 00:10:00    21
Freq: 5min, dtype: int64
"""
```

The frequency you pass defines bin edges in five-minute increments. For this frequency, by default the left bin edge is inclusive, so the 00:00 value is included in the 00:00 to 00:05 interval, and the 00:05 value is excluded from that interval.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min").sum()
"""
2000-01-01 00:00:00    10
2000-01-01 00:05:00    35
2000-01-01 00:10:00    21
Freq: 5min, dtype: int64
"""

ts.resample("5min", closed="right").sum()
"""
1999-12-31 23:55:00     0
2000-01-01 00:00:00    15
2000-01-01 00:05:00    40
2000-01-01 00:10:00    11
Freq: 5min, dtype: int64
"""
```

The resulting time series is labeled by the timestamps from the left side of each bin. By passing label="right" you can label them with the right bin edge:

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

ts.resample("5min", closed="right").sum()
"""
1999-12-31 23:55:00     0
2000-01-01 00:00:00    15
2000-01-01 00:05:00    40
2000-01-01 00:10:00    11
Freq: 5min, dtype: int64
"""

ts.resample("5min", closed="right", label="right").sum()
"""
2000-01-01 00:00:00     0
2000-01-01 00:05:00    15
2000-01-01 00:10:00    40
2000-01-01 00:15:00    11
Freq: 5min, dtype: int64
"""
```

Lastly, you might want to shift the result index by some amount, say subtracting one second from the right edge to make it more clear which interval the timestamp refers to.

```py
import pandas as pd
from pandas.tseries.frequencies import to_offset

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts = pd.Series(np.arange(len(dates)), index=dates)

result = ts.resample("5min", closed="right", label="right").sum()
result
"""
2000-01-01 00:00:00     0
2000-01-01 00:05:00    15
2000-01-01 00:10:00    40
2000-01-01 00:15:00    11
Freq: 5min, dtype: int64
"""

result.index = result.index + to_offset("-1s")
result
"""
1999-12-31 23:59:59     0
2000-01-01 00:04:59    15
2000-01-01 00:09:59    40
2000-01-01 00:14:59    11
Freq: 5min, dtype: int64
"""
```

A popular way to aggregate a time series is to compute four values for each bucket: the first (open), last (close), maximum (high), and minimal (low) values. By using the `ohlc` aggregate function, you will obtain a DataFrame having columns containing these four aggregates.

```py
import pandas as pd

dates = pd.date_range("2000-01-01", periods=12, freq="min")
ts.resample("5min").ohlc()
"""
                     open  high  low  close
2000-01-01 00:00:00     7    11    0     10
2000-01-01 00:05:00     3     8    2      8
2000-01-01 00:10:00     1     9    1      9
"""
```

#### Upsampling and Interpolation

Upsampling is converting from a lower frequency to a higher frequency, where no aggregation is needed. We use the `asfreq` method to convert to the higher frequency without any aggregation:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""
```

Suppose you wanted to fill forward each weekly value on the non-Wednesdays. The same filling or interpolation methods available in the `fillna` and `reindex` methods are available for resampling:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("D").ffill())
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-07  1.962125  0.288492  0.143442  0.785525
2000-01-08  1.962125  0.288492  0.143442  0.785525
2000-01-09  1.962125  0.288492  0.143442  0.785525
2000-01-10  1.962125  0.288492  0.143442  0.785525
2000-01-11  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("D").ffill(limit=2))
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-07  1.962125  0.288492  0.143442  0.785525
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""
```

Notably, the new date index need not coincide with the old one at all:

```py
import pandas as pd

df = pd.DataFrame(
  np.random.standard_normal((2, 4)),
  index = pd.date_range("2000-01-01", periods=2, freq="W-WED"),
  columns=["Colorado", "Texas", "New York", "Ohio"]
)

print(df)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

df_daily = df.resample("D").asfreq()
print(df_daily)
"""
            Colorado     Texas  New York      Ohio
2000-01-05  1.962125  0.288492  0.143442  0.785525
2000-01-06       NaN       NaN       NaN       NaN
2000-01-07       NaN       NaN       NaN       NaN
2000-01-08       NaN       NaN       NaN       NaN
2000-01-09       NaN       NaN       NaN       NaN
2000-01-10       NaN       NaN       NaN       NaN
2000-01-11       NaN       NaN       NaN       NaN
2000-01-12  1.432357 -1.841665  1.317754 -2.983131
"""

print(df.resample("W-THU").ffill())
"""
            Colorado     Texas  New York      Ohio
2000-01-06  1.962125  0.288492  0.143442  0.785525
2000-01-13  1.432357 -1.841665  1.317754 -2.983131
"""
```

#### Grouped Time Resampling

Suppose that a DataFrame contains multiple time series, marked by an additional group key column. To do the same resampling for each value of "key", we introduce the `pandas.Grouper` object.

```py
import numpy as np
import pandas as pd

times = pd.date_range("2017-05-20 00:00", freq="1min", periods=15)

df = pd.DataFrame({
  "time": times.repeat(3),
  "key": np.tile(["a", "b", "c"], 15),
  "value": np.arange(45)
})

print(df.head())
"""
                 time key  value
0 2017-05-20 00:00:00   a      0
1 2017-05-20 00:00:00   b      1
2 2017-05-20 00:00:00   c      2
3 2017-05-20 00:01:00   a      3
4 2017-05-20 00:01:00   b      4
"""

time_key = pd.Grouper(freq="5min")

resampled = (df.set_index("time")
             .groupby(["key", time_key])
             .sum())

print(resampled)
"""
                         value
key time
a   2017-05-20 00:00:00     30
    2017-05-20 00:05:00    105
    2017-05-20 00:10:00    180
b   2017-05-20 00:00:00     35
    2017-05-20 00:05:00    110
    2017-05-20 00:10:00    185
c   2017-05-20 00:00:00     40
    2017-05-20 00:05:00    115
    2017-05-20 00:10:00    190
"""
```

One constraint with using `pandas.Grouper` is that the time must be the index of the Series or DataFrame.

<hr>
<hr>

## Introduction to Modeling Libraries in Python

https://wesmckinney.com/book/modeling
