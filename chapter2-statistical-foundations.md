## Hypothesis Formation

### What is a hypothesis in the context of A/B testing?
- A hypothesis is a statement that serves as a starting point for further investigation
- A strong hypothesis is the one which is 
	- testable or measurable
	- declarative and concise
	- logical
	- easy to generalize 
	- results in actionable iterations
- Follows a specific format: "Based on X, we believe that if we do Y, then Z will happen, as measured by metric M"
- An example of a hypothesis can be, based on user research, we believe that if we update the recommendation algorithm, then an increase in conversion will happen, as measured by CVR

### How does a null hypothesis differ from an alternative hypothesis?
- Null hypothesis usually states that no changes will occur. For example, the conversion rate will not increase. 
- However, the alternative hypothesis in this case would be the opposite of null hypothesis, for example, the change would increase the conversion rate.


## Statistical Foundations
 
### What is the Central Limit Theorem and why is it important in A/B testing?
 -  CLT states that for a sufficiently large sample size, the distribution of the sample means would be normally distributed around the true population mean, regardless of the distribution of the underlying data.
 - The standard deviation of this distribution equals the standard error of the mean. 

### How does standard deviation and standard error matter in context of AB testing.
- Standard deviation is the 'average distance from the mean in your raw data'. It measures the spread in the original data. Formula: `σ = √(Σ(x - μ)²/N)` Variance is the average of squared difference from the mean.  Standard Deviation = √Variance. Variance is always positive, since it is squared. That's the reason, standard deviation is usually used as it is the same units as the original data.
- Standard error is 'how wobbly your sample average is'.  Standard Error = Standard Deviation/√n. Since it is inversely proportional to the sample size, the more the sample size is, the smaller the standard error is, and more confident you are in your sample mean.
- In A/B testing context, standard deviation show how much the individual users vary. And, the standard error shows how confident you are in the difference of A and B. The smaller the standard error, the better you can detect the small differences between A and B.
- Since variance helps calculate the required sample size, and higher variance means more standard error and thus, we need more sample size to detect the small differences between A and B.

### Under what conditions does the Central Limit Theorem apply?
Some key conditions for the CLT to hold include the following
- Must have sufficiently large sample size(typically >=30 samples)
- Observations must be independent and randomly sampled.
- The population must have finite variance and mean.

### How does sample size affect the distribution of sample means?
As sample size increases:
- The distribution of the sample means becomes more tightly centered around the true population mean.
- The standard error decreases, since it is inversely proportional to the sample size.
- The distribution becomes more reliably normal shaped(due to CLT)

### Why is normal distribution important in hypothesis testing?
- In AB testing, normal distribution is important because it lets us compare the means between the test and the control groups.
- The means of two groups, A and B are normally distributed. The difference between normal distributions is also normal. That means the difference between the means(D) also follows a normal distribution.
- Under null hypothesis, the distribution(D) centers at zero. (that means no difference between A and B)
- The normal distribution of the difference helps us calculate probability of observing differences by chance. It also helps set significance levels and evaluate p-values, and thus make decisions about rejecting or failing to reject the null hypothesis.

## Design Parameters and Error Types

### What is statistical power (1-β) and why is it important?
- Statistical power(1-β) is defined as the opposite of Type II error or false negative rate. Its commonly set at 80% in AB testing contexts.
- Power represents the test's ability to detect true effects when they exist.
- For example, if the test has 80% power, it means that if there is a real difference between A and B variants, then you have an 80% chance of detecting it. There's still a 20%(β) chance of missing it Typically 80% is used because this value represents a standard balance between having enough power to detect real effects and keeping  sample size requirements practical.
- This is important in the context of AB testing because, it helps determine the sample size and balances practicallity(resources/time) with reliability.

### Define Minimum Detectable Effect (MDE) and its role in test design.
- MDE is defined as the smallest difference that we care to capture. It's one of the key design parameters alongside power and statistical significance. It should be based on historical data from similar tests, from business contexts and requirements, and should also take into account the available resources and traffic.
- Higher baseline means smaller relative changes matter, and lower baseline means large relative changes matter.

### What is significance level (α) and how is it typically set?
- α is the Type I error rate and is also the false positive rate. It's commonly set at 5% in AB testing. 
- What it means in practice is that, its the probability of incorrectly rejecting the null hypothesis. In AB testing context, it would be the probability of declaring that a difference exists when there actually isn't one.
- The decision rule is that when the p-value is less than α, we reject the null hypothesis, and when the p-value is greater than α, then we fail to reject the null hypothesis.

### How do you balance between Type I and Type II errors? 
- Type I (α) - false positive rate: commonly set at 5%
- Type II (β) - false negative rate: power = 1-β, commonly set at 80%. This means β is 20%
- Decreasing α (reducing false positives) → Increases β (more false negatives)
- Since both of them depend on each other, we can't optimize both without increasing the sample size.

### How do you take a decision based on the p-value
- If p-value < α (0.05):
    → Reject null hypothesis
    → "We found a significant difference"
    → Risk of Type I error is 5%
- If p-value > α (0.05):
    → Fail to reject null hypothesis
    → "No significant difference found"
    → Risk of Type II error depends on effect size

### What are the different Cohen's measures?
- The purpose of the Cohen's measures is to standardize the effect size across various metrics. It enables sample size calculations, and thus provides a framework for comparing different tests. 
- Now there are two types of Cohen's measures- Cohen's h for proportions, and Cohen's d for means.
	- Cohen's h is used for proportion metrics such as conversion metrics, click-through rates and things of that nature.
	- Formula: h = 2 * (arcsin(√P₂) - arcsin(√P₁))
		- Where:
			- P₁ is baseline proportion
			- P₂ is target proportion
	- Cohen's d is used for means such as revenue based metrics or time based metrics, for example RPV and average checkout time.
	- Formula: d = (μ₂ - μ₁)/σ
		- Where:		
			- μ₁, μ₂ are means
			- σ is pooled standard deviation

### How do you use the Cohen's measures to measure the effect size?
- To interpret the effect size, the following numbers can be referred to
	- Small effect: 0.2
	- Medium effect: 0.5
	- Large effect: 0.8
- Now once the effect size is calculated, the sample size can be calculated using the following formula
	- n = 2(Zα + Zβ)² / effect_size²
	- Where:
	    - n is sample size per variant
	    - Zα is z-score for significance level (1.96 for α = 5%)
	    - Zβ is z-score for power (0.84 for 80% power)
	    - effect_size is Cohen's h or d
- Example:
	Baseline: 10% conversion
	Target: 11% conversion (10% improvement)
	Cohen's h ≈ 0.033
	Sample size needed ≈ 14,728 per variant
	With 5,000 daily visitors = 6 days test duration

## Correction Methods

### What is the difference between single comparison and multiple comparison tests?
- Single comparison tests usually involve comparing A versus just one treatment. They might deal with just a single metric and usually doesn't involve subcategories. An example can be testing a new feature against the existing current feature.
- Mutliple comparison tests involve multiple categories and granular categories(A/B/n tests). They may include multiple metrics being tested simultaneously, and thus require correction methods like Bonefferoni methods for correction. 

### What is family-wise error rate (FWER)? Why is FWER important in multiple comparison scenarios?
- FWER is defined as the probability of making at least one Type I errors while performing multiple hypothesis tests
- Imagine you're running tests on a recommendation module with 4 metrics. If you use the standard significance level of α = 0.05 for each test:
	- For each individual test, you have a 5% chance of a false positive
	- However, across all tests, the probability of at least one false positive is much higher
	- The formula for FWER is: FWER = 1 - (1 - α)^m, where m is the number of tests
	- With 4 tests: FWER = 1 - (1 - 0.05)^4 = 0.19 or 19%
	- This 19% FWER means:
		- You have a 19% chance of getting at least one false positive across all your tests
		- This is nearly 4 times higher than your intended error rate of 5%
		- This inflated error rate could lead to incorrect business decisions
- To control FWER, you can use correction methods like:
	- Bonferroni correction: Adjust α to α/m (where m is number of tests)
	- Šidák correction: A less stringent alternative to Bonferroni

### What is the Bonferroni correction and how is it calculated? when is this most appropriate?
- The Bonferroni correction is the simplest and the most popular approach for controlling the family-wise error rate in multiple correction testing
- Here's how it's calculated:	
	- Adjusted α = Individual test α / M
	- Where M is the number of tests being performed
	- For example, if running 5 tests with α = 0.05:
	    - Bonferroni adjusted α = 0.05/5 = 0.01
	    - This means each individual test must achieve p < 0.01 to be considered significant
- The Bonferroni correction is most appropriate in these scenarios:
	- When you have a relatively small number of comparisons (typically less than 10)
	- When controlling Type I errors (false positives) is critical to your business decision
	- When you need a simple, conservative approach that's easy to explain to stakeholders
	- When the tests are independent of each other
	- When the cost of a false positive is high (e.g., major product changes, high-stakes decisions)


### What is the Šidák correction?
- The Šidák correction is an alternative method for controlling the family-wise error rate in multiple comparisons. 
- The formula for Šidák correction is:
	- Adjusted α = 1 - (1 - α)^(1/m)
	- Where:
	  - α is the original significance level (typically 0.05)
	  - m is the number of independent tests
- Key differences from Bonferroni:
	1. It's slightly less conservative than Bonferroni
	2. It provides exactly the desired family-wise error rate when tests are independent
	3. For the same scenario, Šidák will give a slightly larger adjusted α than Bonferroni
- For example, if you're running 4 tests with α = 0.05:
	- Bonferroni correction: 0.05/4 = 0.0125
	- Šidák correction: 1 - (1 - 0.05)^(1/4) ≈ 0.0127
- The Šidák correction is most appropriate when:
	1. Tests are truly independent
	2. You want slightly more power than Bonferroni
	3. You need a mathematically exact correction for independent tests