
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

Bayes' Theorem is an important tool in understanding what we really know, given evidence of other information we have, in a quantitative way.  It helps incorporate conditional probabilities into our conclusions.

Elvis Presley had a twin brother who died at birth.  What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.  

>> REPLACE THIS TEXT WITH YOUR RESPONSE

---

### Q6. Bayesian &amp; Frequentist Comparison  
How do frequentist and Bayesian statistics compare?

>> REPLACE THIS TEXT WITH YOUR RESPONSE
