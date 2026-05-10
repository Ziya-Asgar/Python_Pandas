# Pandas

---

---

## Useful Links

- https://wesmckinney.com/book/pandas-basics
- https://github.com/wesm/pydata-book
- https://www.practicaldatascience.org/intro.html
- https://towardsdatascience.com/pandas-dtype-specific-operations-accessors-c749bafb30a4

---

---

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

---

---

## Topics

- [Creating Series](./Topics/PyPan_CreatingSeries.md)
- [Creating Dataframe](./Topics/PyPan_CreatingDataframe.md)
- [Accessing Data](./Topics/PyPan_AccessingData.md)
- [Accessing Data With Booleans](./Topics/PyPan_AccessingDataWBooleans.md)
- [Index Objects](./Topics/PyPan_IndexObjects.md)
- [Modifying Data](./Topics/PyPan_ModifyingData.md)
- [Converting Series and Dataframes](./Topics/PyPan_ConvertingSeriesDataframes.md)
- [Deleting Data](./Topics/PyPan_DeletingData.md)
- [Missing Data](./Topics/PyPan_MissingData.md)
- [Duplication in Dataframes](./Topics/PyPan_DuplicationInDataframes.md)
- [Sorting and Ranking](./Topics/PyPan_SortingRanking.md)
- [Arithmetic Operations](./Topics/PyPan_Arithmetic.md)
- [Descriptive Statistics](./Topics/PyPan_DescriptiveStatistics.md)
- [Some Functions and Methods](./Topics/PyPan_SomeFuncsMethods.md)
- [Accessors](./Topics/PyPan_Accessors.md)
- [Reading from and Writing to Files](./Topics/PyPan_Files.md)
- [Pandas and Web APIs](./Topics/PyPan_APIs.md)
- [Hierarchical Indexing](./Topics/PyPan_HierarchicalIndexing.md)
- [Combining and Merging](./Topics/PyPan_CombiningMerging.md)
- [Reshaping and Pivoting](./Topics/PyPan_ReshapingPivoting.md)
- [Data Aggregation and Group Operations](./Topics/PyPan_AggregationGrouping.md)
- [Time Series](./Topics/PyPan_TimeSeries.md)

---

---
