---
title : Sample Ratio Mismatch
notetype : feed
date : 19-01-2022
---


> **Summary**
> - SRM is a mismatch between the **expected** sample ratio, and the **observed** sample ratio
> - SRMs are a common data quality issues
> - Approximately 6% of experiments at Microsoft exhibit an SRM
> - SRMs cause a selection bias that invalidates any causal inference
> - We can use a standard t-test or chi-squared test to compute the p-value
> - There are different ways to detect SRMs



### What is SRM

The Sample Ratio Mismatch (SRM) metric looks at the ratio of users (or other units) between two variants. If the experiment design calls for exposing a certain ratio of users to the two variants, then the results should closely match the design.


#### Scenario 1

Given we run an experiment with 2 variants, control and treatment, each assigned 50% of users. We expect to see an approximately equal number of users in each, but our results are:

-   Control: 821,588 users
    
-   Treatment: 815,482 users
    

The ratio between the two is 0.993 whereas the ratio should be 1.0

> Ratio between control and treatment is (815,482/821,588) = 0.993

The p-value of the above .993 Sample Ratio is 1.8E-6

That said, there are an SRM, it is therefore more likely that there is a bug in the implementation of the experiment.



### Causes

-   Buggy randomization of users
-   Data pipeline issues
-   Residual effects (Some deployment, bug fixes or new features, cause the issue on experimentation)
    

### Debugging SRMs

- Validate that there is no difference upstream of randomization point.
- Validate that variant assignment is correct
- Follow the stages of data processing pipeline
	- Bot filtering, SSOID filtering 
- Exclude the initial period
	- Sometimes the initial period did not start together, for example caches take time to prime
- Look at the Sample Ratio for segments
	- Look at each day separately
	- Is there a browser segment, app or platform that stands out (e.g. Android, iOS)
	- Do new users and returning users show different ratios?
- Look at the intersection with other experiments

## Some interesting reads

- [The essential guide to Sample Ratio Mismatch for your A/B tests](https://towardsdatascience.com/the-essential-guide-to-sample-ratio-mismatch-for-your-a-b-tests-96a4db81d7a4)  
- [A Better Way to Test for Sample Ratio Mismatches (SRMs) and Validate Experiment Implementations](https://medium.com/engineers-optimizely/a-better-way-to-test-for-sample-ratio-mismatches-srms-and-validate-experiment-implementations-6da7c0d64552)
- [CH2019 keynote: Lukas Vermeer - One neat trick to run better experiments](https://www.slideshare.net/webanalisten/ch2019-keynote-lukas-vermeer-one-neat-trick-to-run-better-experiments)
- [Trustworthy A/B Tests - Ron Kohavi](https://exp-platform.com/Documents/2017-05-17EmetricsControlledExperimentsPitfallsKohaviNR.pdf "https://exp-platform.com/Documents/2017-05-17EmetricsControlledExperimentsPitfallsKohaviNR.pdf")
- [Diagnosing Sample Ratio Mismatch in Online Controlled Experiments: A Taxonomy and Rules of Thumb for Practitioners](https://exp-platform.com/Documents/2019_KDDFabijanGupchupFuptaOmhoverVermeerDmitriev.pdf "https://exp-platform.com/Documents/2019_KDDFabijanGupchupFuptaOmhoverVermeerDmitriev.pdf")
- [GitHub - optimizely/ssrm: Sequential Sample Ratio Mismatch(SRM) Test](https://github.com/optimizely/ssrm)
- [Detecting Incorrectly Implemented Experiments - Michael Lindon @ Optimizely](https://medium.com/engineers-optimizely/a-better-way-to-test-for-sample-ratio-mismatches-srms-and-validate-experiment-implementations-6da7c0d64552?wvideo=15uvqjcjc1)


---

#ab-testing #sample-ratio-mismatch