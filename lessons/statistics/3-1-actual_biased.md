[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

```
import thinkstats2 as ts
import thinkplot as tp
import nsfg
from probability import BiasPmf

resp = nsfg.ReadFemResp()

unbiased = ts.Pmf(resp.numkdhh)
tp.Pmf(unbiased)
```

We see a mode of 0, trailing off with a longish tail

```
biased = BiasPmf(unbiased)
tp.Pmf(biased)
```

As expected, we see nothing at 0
We now see a mode at 2 students, right tail only slightly longer

```
unbiased.Mean(), biased.Mean()
```

As expected, bias raises the mean here
