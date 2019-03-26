[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
# reload data from file
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

# slicing dataframe for first born and non-first born
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

print("Firstborn mean weight:", firsts.totalwgt_lb.mean())
print("Others mean weight:", others.totalwgt_lb.mean())

length_d = CohenEffectSize(firsts.prglngth, others.prglngth)
weight_d = CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)

print("The difference in pregnancy length is {} standard deviations.".format(length_d))
print("The difference in total weight is {} standard deviations.".format(weight_d))
```

First-born babies are lighter on average, but the difference in total weight is only 0.089 standard deviations, which is not particularly significant. Still, this is a more significant difference than that of pregnancy length (0.029 standard deviations).
