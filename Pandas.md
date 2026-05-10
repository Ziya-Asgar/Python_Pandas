# Pandas

- [Pandas](#pandas)
  - [Some Useful Links](#some-useful-links)
  - [Intro](#intro)
  - [Creating Series](#creating-series)
  - [Creating Dataframe](#creating-dataframe)
  - [Accessing Data](#accessing-data)
  - [Accessing Data With Booleans](#accessing-data-with-booleans)
  - [Index Objects](#index-objects)
  - [Modifying Data](#modifying-data)
  - [Converting Series and Dataframes](#converting-series-and-dataframes)
  - [Deleting Data](#deleting-data)
  - [Missing Data](#missing-data)
  - [Duplication in Dataframes](#duplication-in-dataframes)
  - [Sorting and Ranking](#sorting-and-ranking)
  - [Arithmetic Operations](#arithmetic-operations)
  - [Descriptive Statistics](#descriptive-statistics)
  - [Some Functions and Methods](#some-functions-and-methods)
  - [Accessors](#accessors)
  - [Reading from and Writing to Files](#reading-from-and-writing-to-files)
  - [Pandas and Web APIs](#pandas-and-web-apis)
  - [Hierarchical Indexing](#hierarchical-indexing)
  - [Combining and Merging](#combining-and-merging)
  - [Reshaping and Pivoting](#reshaping-and-pivoting)
  - [Data Aggregation and Group Operations](#data-aggregation-and-group-operations)
  - [Time Series](#time-series)

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

## Creating Series

[Creating Series](./PyPan_CreatingSeries.md)

<hr>

## Creating Dataframe

[Creating Dataframe](./PyPan_CreatingDataframe.md)

<hr>

## Accessing Data

[Accessing Data](./PyPan_AccessingData.md)

<hr>

## Accessing Data With Booleans

[Accessing Data With Booleans](./PyPan_AccessingDataWBooleans.md)

<hr>

## Index Objects

[Index Objects](./PyPan_IndexObjects.md)

<hr>

## Modifying Data

[Modifying Data](./PyPan_ModifyingData.md)

<hr>

## Converting Series and Dataframes

[Converting Series and Dataframes](./PyPan_ConvertingSeriesDataframes.md)

<hr>

## Deleting Data

[Deleting Data](./PyPan_DeletingData.md)

<hr>

## Missing Data

[Missing Data](./PyPan_MissingData.md)

<hr>

## Duplication in Dataframes

[Duplication in Dataframes](./PyPan_DuplicationInDataframes.md)

<hr>

## Sorting and Ranking

[Sorting and Ranking](./PyPan_SortingRanking.md)

<hr>

## Arithmetic Operations

[Arithmetic Operations](./PyPan_Arithmetic.md)

<hr>

## Descriptive Statistics

[Descriptive Statistics](./PyPan_DescriptiveStatistics.md)

<hr>

## Some Functions and Methods

[Some Functions and Methods](./PyPan_SomeFuncsMethods.md)

<hr>

## Accessors

[Accessors](./PyPan_Accessors.md)

<hr>

## Reading from and Writing to Files

[Reading from and Writing to Files](./PyPan_Files.md)

<hr>

## Pandas and Web APIs

[Pandas and Web APIs](./PyPan_APIs.md)

<hr>

## Hierarchical Indexing

[Hierarchical Indexing](./PyPan_HierarchicalIndexing.md)

<hr>

## Combining and Merging

[Combining and Merging](./PyPan_CombiningMerging.md)

<hr>

## Reshaping and Pivoting

[Reshaping and Pivoting](./PyPan_ReshapingPivoting.md)

<hr>

## Data Aggregation and Group Operations

[Data Aggregation and Group Operations](./PyPan_AggregationGrouping.md)

<hr>

## Time Series

[Time Series](./PyPan_TimeSeries.md)

<hr>

<hr>
