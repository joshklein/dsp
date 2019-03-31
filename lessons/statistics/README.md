
# <a name="section-d"></a>4.  Exercises

### Q1. [Think Stats Chapter 2 Exercise 4](statistics/2-4-cohens_d.md) (effect size of Cohen's d)  

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

### Q2. [Think Stats Chapter 3 Exercise 1](statistics/3-1-actual_biased.md) (actual vs. biased)

```python

resp = nsfg.ReadFemResp()

actual = thinkstats2.Pmf(resp.numkdhh)
print(actual.Mean()) # 1.024205155043831
thinkplot.Pmf(actual)

biased = BiasPmf(actual, label='biased_distribution')
print(biased.Mean()) # 2.403679100664282
thinkplot.Pmf(biased)
```


### Q3. [Think Stats Chapter 4 Exercise 2](statistics/4-2-random_dist.md) (random distribution)  

```python
nums = np.random.random(1000)
p = thinkstats2.Pmf(nums)
thinkplot.Pmf(p)

# what is the problem? imperceptible - we need to bin values, or look at CDF

cdf = thinkstats2.Cdf(nums)
thinkplot.Cdf(cdf)

# yep, straight line means normal distribution!
```

### Q4. [Think Stats Chapter 5 Exercise 1](statistics/5-1-blue_men.md) (normal distribution of blue men)

```python
import scipy.stats
dist = scipy.stats.norm(loc=178, scale=7.7)

# 5'10 to cm = 177.8
# 6'1 to cm = 185.4
min_height = dist.cdf(177.8) 
max_height = dist.cdf(185.4)

print(max_height-min_height) # about 34.2%
```

### Q5. Bayesian (Elvis Presley twin) 

Elvis Presley had a twin brother who died at birth.  What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.  

The probability is almost 30% (or 5/17.)

---

### Q6. Bayesian &amp; Frequentist Comparison  

In the frequentist approach to statistics, there is some "true" or "constant" value that experimental/sample data approximates. Outcomes are considered in a vacuum, without consideration for prior knowledge (like the base rate of some phenomena occurring).

The Bayesian approach is that the probability is itself the "truth". We can leverage prior knowledge and the tools of conditional probability to make inferences, given existing information.
