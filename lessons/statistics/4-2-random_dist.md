[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```
import thinkstats2 as ts
import thinkplot as tp

from random import random

nums = [random() for i in range(0,1000)]

tp.Pmf(ts.Pmf(nums))

tp.Cdf(ts.Cdf(nums))
```

The Pmf and Cdf both look uniform
(i.e. ~constant and linear, respectively)
