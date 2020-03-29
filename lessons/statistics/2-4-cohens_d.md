[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```
def CohenEffectSize(group1, group2):
    n1, n2 = len(group1), len(group2)
    pooled_var = (n1 * group1.var() + n2 * group2.var()) / (n1 + n2)
    return (group1.mean() - group2.mean()) / np.sqrt(pooled_var)

firsts.prglngth.mean()
others.prglngth.mean()
```

We see first babies have longer pregnancies on average

```
firsts.birthwgt_lb.mean()
others.birthwgt_lb.mean()
```

Yet are lighter on average -- odd

```
CohenEffectSize(firsts.prglngth, others.prglngth)
CohenEffectSize(firsts.birthwgt_lb, others.birthwgt_lb)
```

Thus d is negative for weight but not preg. length
The effect is quite small for weight, but very small for length
Since length would be expected to correlate with weight,
I'd guess the effect of the former is an artifact.
