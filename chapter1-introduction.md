## Basic Concepts

### What is A/B testing, and how does it differ from other types of experiments?

- A/B testing is an experimentatal design which is set up to decide which version is better based on certain metrics.
- One of the core characteristic of an A/B test is that, it should have two variants- Control variant, which is the current state or design, and a treatment variant, which is the new design that is being tested.
- Random assigment is another key characteristic of an A/B test, where the users are randomly enrolled in the experiment. Participants are randomly assigned to either control or treatment variant, and this randomization is crucial in minimizing bias and establishing causality.

### What is the role of random assignment in A/B testing?

- Randomization creates generalizability and representiveness, by ensuring that the test groups reflect the broader population and the test results can be applied to general user base.
- Randomization also ensures that it minimizes bias between different groups. This means that the known and the unknown variables would have an equal distribution between different groups, and thus there is no systematic difference between the groups.
- It also helps to establish causality better by isolating the variable being tested and eliminating the confounding variables.

### Explain the difference between control variant and treatment variant.

- Control variant, or the "current state" represents the existing version, usually the version which is in production or in use. It serves as the benchmark against which the changes are measured.
- Treatment variant is the "new design" and represents the modified version that is being tested. This version is potentially hypothesized to perform better.

### Why is it important to have a control group in A/B testing?


- A/B testing helps to reduce uncertainty around the impact of new features or designs. And, without a control group, we can't isolate if the changes are due to the new design/feature, or external factors or just random fluctuations.
- A control group thus helps by providing a baseline, and isolating the treatment effect. Following which, we can carry out a proper statistical comparison.  

### How does A/B testing help in making data-driven decisions?

- A/B testing allows scientific evidence based decision making, which are not 'based on intuition'
- It helps in establishing clear business impacts by tracking specific metrics(such as North start, granular) and quantifies the effect of changes in terms of business value
- A/B testing enables risk optimization as well, by testing features before roll out, enabling continuous improvement and, thus reducing uncertainty in business decision making

## Use Cases & Applications

### What are three primary business scenarios where A/B testing is most valuable?

Some use cases in businesses include
1. Conversion Rate Optimization
- Improving conversion rates in checkout processes or signup flows
- Testing app or web functionalities to increase user conversions
- Optimizing marketing funnels and improving conversion rates for emails or notifications

2. New Feature Releases
- Adding new functionalities and testing before rolling out
- Validatin new UI/UX

3. Measuring Product Impact
- Assessing and measuring impact on key metrics during product changes
- Testing marketing campaigns, pricing and other strategies.



### List situations where A/B testing might not be appropriate or necessary.

Despite a lot of use cases to establish causality, there can be certain situations where A/B testing might not be appropriate or necessary
1. Insufficient data
- There can be situations where the traffic volume is quite low or the sample size is too less
- Less traffic would cause the test to not reach enough statistical significance

2. Ethical considerations
- There can be instances, where testing a certain feature could harm user experience
- Other instances where experiment on pricing can be considered ethically inappropriate

3. Lack of a clear hypothesis
- If there's a lack of a clear hypothesis, then A/B testing can be tricky
- Or, there are no clear metrics to measure

4. Resource constraints
- This can happen when the cost of each sample is significant for example.
- This can also happen when there is not enough technical infrastructure to set up an A/B test
- High opportunity cost



### How can A/B testing be used in:
- E-commerce optimization?
- Drug trials?
- Feature releases?
- Marketing campaigns?


E commerce optimizations:
- Testing checkout flow variations
- Testing product recommendations
- Testing UI/UX changes

Drug Trials
- Measuring efficacy of a drug
- Controlling for placebo effects
- Measuring specific health outcomes

Feature releases
- Managing gradual release of new features
- Measuring UI/UX changes
- Validating performance improvements

Marketing Campaigns
- Testing ad copy or designs
- Comparing email campaign variations
- Optimizing landing pages


### What role does sample size play in determining whether to conduct an A/B test?

Sample sizes can plays a crucial role in A/B test decisions
- Insufficient samples makes it impossible to detect true differences and can lead to unreliable results
- Too small sample sizes waste resources on inconclusive tests
- Inadequate samples can lead to incorrect business decisions

### How do ethical considerations impact A/B testing decisions?

Some tests can be technically possible but ethically inappropriate
- In terms of user experience and safety, there can be certain tests that can put users at risk, for example, testing medicine dosages
- Testing on vulnerable population without safeguards can be ethically inappropriate as well
- Testing deceptive messaging, discriminatory pricing or hiding important information from users can also be considered as unethical business practices

## Experimental Design

### What are the fundamental steps in conducting an A/B test?

These can be some of the fundamental steps necessary to conduct an A/B test
1. Goal and design specification
- Define a clear objective and a clear hypothesis to test
- Define a success criteria and have clear metrics to measure. For example, there can be primary and secondary metrics in addition to some monitoring or guardrail metrics

2. Random sampling
- Determine the required sample size for the experiment
- Ensure that the sample is representative of the population
- Also, things like duration, timing should be kept in mind

3. Random assignment
- Ensure that the randomization algorithm works to split the user into control and treatment groups
- Verify the balanced distributions

4. Data collection
- Once the test has been initiated, ensure that the logging is in place and correctly track the necessary metrics
- Ensure that the data is consistent and check for data quality issues, such as balance or SRM issues

5. Statistical analysis
- After the test duration is over, collect the metrics for both the groups and test for statistical significant differences
- Account for any confounding variables
- Draw conclusions based on the statistical tests

### What factors should be considered when designing an A/B test?

- Key factors for AB test design include, sample considerations(size and representation), metric selection(primary, secondary and guardrail) and test parameters(test and control)
- Practical constraints such as technical feasibility and resource availability should also be considered. Statistical rigor through significance levels and power analysis should be considered
- Finally, business risks, ethical considerations and clear success criteria should be considered. 


### How do you determine the duration of an A/B test?

- The duration of an AB test can be determined by following three factors, required sample size to achieve statistical significance, expected traffic or user volume and business cycle considerations.
- There should be enough time to collect sufficient data points, while accounting for any seasonal variations or cyclical variations in the users behavior.

## Randomization & Causality

### What is the relationship between randomization and bias minimization?

Randomization helps to minimize bias by ensuring that any systematic differences or confounding variables are evenly distributed between control and treatment groups. When users are randomly assigned, the factors that can influence the outcome, both known and unknown have an equal chance in appearing in either of the groups.
This makes randomization a critical tool for creating comparable groups and isolating the true effect of the treatment being tested.

### What are potential threats to randomization in A/B testing?

There can be potential threats to randomization
- Selection Bias: Users can self-select themselves into groups. This can also happen because of certain time based assignment patterns, or geographic or device patterns.
- Technical Issues: Cookie deletion after assignment can also cause users to move to different groups. There can be other challenges like, user using multiple devices, that can also lead to randomization issues.
- Implementation Issues: Issues with Randomization algorithm, inconsitent assignment rules, or traffic allocation issues can also cause randomization problems.
- External factors: Then there can be seasonal variations, or market events, or even changes in user behavior that can cause issues with randomization.

### How does proper randomization differ from pseudo-random assignment?

Proper randomization provides true independence and unpredictability, while pseudo-random assignments might seem random, but they can introduce subtle biases and patterns that could compromise the validity of the test

## Metrics & Measurement

### What is a North Star metric and why is it important?

A north star or a primary metric is a key measure that best describes the success of the business. Its important because it can be single metric around which different teams can align, and guides the decision making in experiments. It can indicate the fundamental business objective and, thus indicate overall business health.

### Distinguish between primary and granular metrics with examples.

Primary metrics are usually higher-level and best describes the overall business objective. While granular metrics explain user specific behaviors, and can be more sensitive and more actionable. 
For example, overall conversion rate can be a primary metric, while sign-up rate, click per visit can be granular metrics.

### What makes a metric "non-gameable"?

A metric is non-gameable when it directly reflects the business impact or reflects real user value. It shouldn't be something that can be artificially inflated through superficial changes. For example, a metric like revenue per visit can be non-gameable, while another metric such as time-on-page can be gamified by adding distracting elements.

### How do you evaluate if a metric is stable, sensitive and measurable?

A metric can be considered 
- Stable: If its consistent under normal circumstance, shows minimal random fluctuations, and doesn't get overly affected by external factors
- Sensitive: If it responds to relevant changes in user behavior, detects meaningful differences between the variants and changes when actual improvement occurs.
- Measurable: If it can be accurately calculated, tracked and logged, and has a clear definition and a calculation method.

### What are the different types of quantitative metrics (with examples): Means/percentiles, proportions, ratios?

## - The means or percentile metrics are measures of central tendency or distribution points. They represent an average or typical value in the original unit of measurement.  For example, a metric like average sales can be obtained by dividing total sales by the number of sales. It returns the value back in the sale amount in dollars.  They preserve the original unit here(dollars), while other metrics (ratios and proportions behave different). Other examples of means metrics include median time on page, or average revenue per user or percentile load times.
- Proportions are part of a whole; they must be same unit/type in numerator and denominator. While ratios are basically the comparison between different measures(can be different units/types).
- For example, active users/total users(as active users is a subset of total users) is a proportion metric. 500/1000 or 0.5. The value lies between 0-1. Contrast that with a ratio, such as messages per user. For example, 1500 messages/500 users or 3 messages per user. Her we are comparing different measures.
- Other examples of proportion measures include signup rate(signups/visits), page abandonment rate(page abandons/total visitors), or conversion rate(purchases/vistors)
- Examples or ratio are click through rate(clicks/visits), clicks per ad impression, or pages per visit.

## Correlation & Statistical Concepts

### What is Pearson's correlation coefficient?

- Pearson's correlation coefficient is a statistical measure that quantifies the strength of linear relationship between two variables. 
It's usually denoted by R. Some interpretation
	- R>0 means that there is a positive correlation
	- R=0 mesns no correlation
	- R<0 means negative correlation
- Since Pearson's correlation coefficient is a parametric test, it relies on the assumption that the data should be normally distributed


### What are the assumptions behind correlation analysis?

- The data should follow a normal distribution. When the data is non-normal, transformations can be applied to make it normal. Or, there are other tests like Spearman's rank coefficient or Kendall's test.
- The data should satisfy the assumption of linearity

### Why doesn't correlation always imply causation?

Correlation sits at the bottom of the evidence pyramid, and is grouped with opinions and gut feelings. Observational studies or natural experiments provide stronger evidence, which require some modeling efforts and randomization. 
There are often situations where we see a strong correlation, such as page load times and conversion rates, but it doesn't tell us that slow load times is equal to lower conversions, or both are affected by another factor, which is the poor internet connection.


## Evidence Hierarchy

### Describe the hierarchy of evidence in experimental design.

The hierarchy of evidence can be thought of as a pyramid structure of establishing causation.
- The bottom layer consists of correlations, opinions and gut feelings
- The middle layer consists of observational studies/natural experiments, quasi experiments(which require high modeling efforts)
- The top layer consists of RCT or Randomly controlled trials, which are like the gold standard in establishing causation.

### What distinguishes randomized controlled experiments from observational studies?

RCT's are considered the gold standard because they:
- create generalizability and representativeness
- minimize bias between different groups through randomization
- can establish causality by isolating treatment effects
- are more trustworthy unlike other methods where randomization and control groups are absent
- have greater control unlike observational studies, where certain variables cannot be controlled.

### How do quasi-experiments differ from true experiments?

True experiments differ from the quasi-experiments in several ways
- Random assignment: In case of true experiments, there is a complete random assignment to treatment conditions, compared to a quasi-experiment, where groups are formed by natural circumstances or pre-existing conditions
- Control over Variables: There is a greater control over the independent variables and the treatment conditions in a true experiment setting, unlike quasi-experiments where researchers have to work with naturally occurring conditions.
- Research settings and applicability: True experiments are conducted in controlled environments such as labs or online platforms. While, quasi experiments are carried out in natural settings where full control isn't possible. On the other hand, true experiments are often more feasible for real-world situations where randomizations isn't possible or ethical.

## Implementation & Practical Considerations

### What infrastructure is needed to implement A/B testing?

Essential infrastructure needed for A/B testing
1. User assignment system:
    - A robust randomization algorithm and tool to effectively randomize traffic and ensure consistent assignment.
    - User identification and tracking capabilities(eg UserIds, cookies or session tracking)
2. Data logging and storage
    - Infrastructure to log hits and clickstream data about user behavior and activities
    - Data storage solutions for collecting test metrics
3. Experimentation platform
    - Feature flagging system to control variant deployment 
    - Traffic allocation mechanisms and audience sizing or filtering
    - Treatment assignment mechanisms to ensure consistent user experience
4. Analytics infrastucture
    - Statistical analytical tools for hypothesis testing
    - Real time data processing tools to process metrics and analyze results
    - Monitoring and visualization tools to real-time experiment tracking and interpreting results
5. Documentation and Experiment management tools
    - Test configuration management
    - Experiment tracking and version control
    - Results documentation and sharing capabilities
    


### What are common challenges in A/B test implementation?


Common challenges in A/B testing implementation
- Technical complexity: Ensuring consistent user assignment across sessions; maintaining proper tracking  instrumentations; handling edge cases such as users moving between different platforms; preventing contamination between variants
- Sample size and duration trade offs: Balancing the need for sufficient statistical power with business pressures for quick results; especially dealing with limited traffic or trying to detect small changes in metrics which often require large sample sizes.
- Data Quality issues: Managing inconsistent tracking; missing data points, or incorrect event logging, while ensuring proper metric computation and avoiding bias from technical issues that might affect one variant differently than other.

### How do you ensure data quality in A/B testing?

Here are some of the ways to ensure data quality in A/B testing
- Technical validation: Implement automated checks for data integrity(proper event logging, consistent event tracking, accurate metric computation), using AA testing to verify the experiment setup; and maintaining consistent instrumentation across variants to ensure there's no systematic bias.
- Statistical monitoring: Tracking key metrics stability over time; implementing and tracking guardrail metrics to detect anomalies and unexpected changes; and checks for unusual patterns in user behavior or metric distributions that might indicate data quality issues.
- Process controls: Document clear metric definitions and logging requirements, and implementing clear procedures for handling data discrepancies or tracking issues when they arise.

### What role does documentation play in A/B testing?


```python

```

## Advanced Concepts

### How do you handle multiple metrics in A/B testing?

Here are some ways to handle multiple metrics in A/B testing
- Create a metric hierarchy: Establish a clear structure or hierarchy with the Primary or north start metrics, the secondary or the granular metrics and the guardrail metrics. This helps prioritize decision-making when metrics show conflicting results.
- Apply Statistical Rigor: Account for multiple comparison problems when testing several metrics simultaneously, ensure each metric meets requirements of being stable, sensitive, measurable, and non-gameable, and consider the correlation between different metrics when analyzing results
- Use Comprehensive Success Criteria: Combine multiple metrics to form more complete success/failure criteria, balance the trade-offs between different metrics (like speed vs accuracy), and ensure metrics together provide a complete picture of the experiment's impact without redundancy

### What are guardrail metrics and why are they important?

- Guardrail metrics are safety metrics that ensure core business metrics or user experience aren't negatively impacted by the test variant. While they're not the primary success metrics, they help prevent unintended negative consequences of an experiment.
- Help catch potential issues early before they impact the business significantly
- Even if your primary test metric improves, a significant drop in guardrail metrics could indicate hidden problems

### How do you balance speed of testing with reliability?

Here are some ways to balance testing speed with reliablity
- Statistical rigor vs Time trade-off: Set minimum required sample size based on desired effect size and confidence levels
- Efficient test designs: Run tests in parallel when the metrics don't interfere; maintain clear, non-overlapping user groups to avoid interaction effects
- Risk-based approach: For low risk changes(UI and copy tweaks) accept lower confidence intervals. For high risk changes, maintain strict statistical requirements.
- Use guardrail metrics with strict stopping rules for critical business metrics
- Consider the cost of potential errors vs the cost of delayed decisions

## Test your understanding

Design an A/B test for a new website checkout process, including:
- Primary and granular metrics
- Sampling strategy
- Duration consideration
- Success criteria

Analyze this scenario: An e-commerce site wants to test two different product recommendation algorithms. What would be your:
- Key metrics?
- Randomization strategy?
- Potential confounding variables?
- Testing duration?

Critique this approach: "We'll let users choose which version they prefer and measure the results." What are the problems with this method?

Your A/B test shows strong correlation between page load time and conversion rate. What steps would you take to:
- Validate causality?
- Control for confounding variables?
- Make recommendations?

Design a framework for deciding whether to A/B test a feature, considering:
- Resource requirements
- Expected impact
- Technical feasibility
- Ethical considerations
