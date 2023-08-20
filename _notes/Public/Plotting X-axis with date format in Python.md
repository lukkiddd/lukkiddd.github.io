---
title : Plotting X-axis with date format in Python
notetype : feed
date : 11-12-2022
---


We can use [Matplotlib Dates API](https://matplotlib.org/stable/api/dates_api.html) together with major and minor tick formatter.

#### Preparing data

```python
import pandas as pd
import numpy as np
import seaborn as sns


random_value = np.random.rand(365, 1)
df = pd.DataFrame(random_value, columns=['Value'])
```

#### Vanila Plot

![plotting-dates-01.png](/assets/img/plotting-dates-01.png)
```python
g = sns.lineplot(x=df.index, y='Value', data=df, color=default_color)
plt.show()
```

#### Re-index and filled in with 0

![plotting-dates-02.png](/assets/img/plotting-dates-02.png)
```python
# Re-index
idx = pd.date_range('2022-01-01', '2022-12-31')  
df.index = pd.DatetimeIndex(idx)
df = df.reindex(idx, fill_value=0)

g = sns.lineplot(x=df.index, y='Value', data=df, color=default_color)
plt.show()
```

#### Modify date format
![plotting-dates-03.png](/assets/img/plotting-dates-03.png)
```python
import matplotlib.dates as md

g = sns.lineplot(x=df.index, y='Value', data=df, color=default_color)
g.xaxis.set_major_formatter(md.DateFormatter('%b, %d'))
plt.show()
```

#### Modify tick frequency both Major and Minor
![plotting-dates-04.png](/assets/img/plotting-dates-04.png)
```python
import matplotlib.dates as md

g = sns.lineplot(x=df.index, y='Value', data=df, color=default_color)
g.xaxis.set_major_formatter(md.DateFormatter('%b, %d'))

g.xaxis.set_major_locator(md.MonthLocator(interval=1))
g.xaxis.set_minor_locator(md.DayLocator(interval = 1))
plt.show()
```