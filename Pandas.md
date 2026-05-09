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
