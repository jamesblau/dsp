[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

```
import numpy as np
import pandas as pd
import nsfg
import thinkstats2 as ts
import thinkplot as tp
import first

preg = nsfg.ReadFemPreg()
```

Why can't I do this?

```
# live = preg[preg.outcome == 1].dropna(subset=['birthwgt_lb', 'agepreg'])
```
Anyway...

```
live = preg[preg.outcome == 1]
live = live.rename(columns={'birthwgt_lb': 'weight', 'agepreg': 'age'})
live = live.dropna(subset=['weight', 'age'])
weights, ages = live.weight, live.age

tp.Scatter(live.weight, live.age)
```

It looks like maybe there's a small positive correlation?

```
bins = np.arange(floor(ages.min()), ceil(ages.max()), 5)
indices = np.digitize(ages, bins)
groups = live.groupby(indices)

ages = [group.age.mean() for i, group in groups][1:-1]
cdfs = [ts.Cdf(group.totalwgt_lb) for i, group in groups][1:-1]

for percent in [75, 50, 25]:
    weights = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    tp.Plot(ages, weights, label=label)

ts.Corr(ages, weights)
ts.SpearmanCorr(ages, weights)
```

This seems consistent with a small positive correlation.
