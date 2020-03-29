[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```
from scipy.stats import norm

def to_cm(inches): return inches * 2.54

cdf = norm(loc=178, scale=7.7).cdf

not_too_short = cdf(to_cm(5*12 + 10))
not_too_tall = cdf(to_cm(6*12 + 1))

in_range = not_too_tall - not_too_short
```

About 34%
