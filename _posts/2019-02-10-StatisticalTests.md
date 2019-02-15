---
title: "Playing Devils' Advocate to your data"
date: 2019-02-04
tags: [Statistics]
header:
    #image: "/assets/images/post/ProLegoPost.png"
    
excerpt: "Open for test!! "

---

`
If you beat-up your date enough,  it will surrender to anything
`

True.  As a scientist, where day to day lab work destined to be bored by mundane data, it 
is crucial that we play devils' advocate to out results ane data. The beauty of science is 
if something is true it has to be simple to understand and explain. But there is a 
tread-off. 

With a "good and appropriate" statistical test, we can be certain upto a point about the
correctness of our results/claims.

### P-value correction
When you perform multiple statistical tests, some tests will have a P-value less than 0.05 purely by chance, 
even when your null hypothesis are really true.[see](http://www.biostathandbook.com/multiplecomparisons.html)


False Positive correction is crucial . Control family wise error rate: 
### Bonferroni correction:
if all the null hypotheses are true, the probability that the family of tests 
includes one or more false positives due to chance is 0.05.
Thus if you are doing 100 statistical tests, the critical value for an individual 
test would be 0.05/100=0.0005, and you would only consider individual tests 
with P<0.0005 to be significant.

The Bonferroni correction is appropriate when a single false positive in a set of 
tests would be a problem.
It is mainly useful when there are a fairly small number of multiple comparisons 
and you're looking for one or two that might be significant. 
Bonferroni correction may lead to a very high rate of false negatives

Controlling False discovery Rate: 
### Bejamini-Hochberg
This is the proportion of "discoveries" (significant results) that are actually false
positives. Se the false discovery rate.

1. Put the individual P values in order, from smallest to largest.
2. The smallest P value has a rank of i=1, then next smallest has i=2, etc. 
3. Compare each individual P value to its Benjamini-Hochberg critical value, 

```  
  (i/m)Q, 
  where 
  i is the rank,
  m is the total number of tests, and 
  Q is the false discovery rate you choose. 
  
```
          
    
The largest P value that has ```P<(i/m)Q``` is significant, 
and all of the P values smaller than it are not significant,
even the ones that are not less than their Benjamini-Hochberg critical value.

### Welch’s T-Test:
This is an adaptation of students’ T-test. Welch’s Test is used to test the 
hypothesis that two population have unequal means. 
This is more reliable when two samples have unequal variance and unequal sample size. 
Also called as Unequal variances.
Both student’s T-test and Welch’s test has the assumption that data under 
consideration has normal distribution.

Main difference from students Test is that Welch test do not assume that variance in 
two sample is same.  

It returns the same result as the t-test even if the variances are equal 
(this however, is not true for small sample sizes, where Welch’s performance is questionable).

Interesting post : [from 20% statistian](http://daniellakens.blogspot.com/2015/01/always-use-welchs-t-test-instead-of.html)