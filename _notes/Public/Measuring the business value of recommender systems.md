---
title : Measuring the business value of recommender systems
notetype : feed
date : 17-01-2022
---


### What is being measured

- [[Click Through Rate]]
	- Easy to measure and established
	- Not the ultimate goal
- [[Adoption and Conversion Rates]]
	- Easy to measure
	- Requires a domain-specific definition
	- Requires interpretation
- Sales and Revenue
	- Most informative measure
	- Cannot always be determined directly
- Effects on Sales Distributions
	- Direct measurement
	- Requires understanding of the effects of the shifts in sales distribution
- User Behavior and Engagement
	- Remain an approximation
	- Correspondence between user engagement and customer retention is assumed
- Others
	- [[Effective Catalog Size]]


### Baseline algorithm
- No recommender
- Popularity-based
	- Age discounted click count
	- Most viewed videos within a day
	- Popular within a given timeframe
	- Top Favorited
	- Top Rated
- Random-based
	- Random from users search
	- Random from the whole catalog
- Simple model
	- Linear model
- Current production baseline model
	- Co-viewed or Co-visitation
	- Collaborative filtering
	- Context-tree


### The challenge of predicting business success from offline experiments

- Beyond-accuracy measures: Novelty, Diversity, Serendipity, and Coverage

---

#### Reference

X. Amatriain and J. Basilico, “Recommender Systems in Industry: A Netflix Case Study,” in _Recommender Systems Handbook_, F. Ricci, L. Rokach, and B. Shapira, Eds. Boston, MA: Springer US, 2015, pp. 385–419. doi: [10.1007/978-1-4899-7637-6_11](https://doi.org/10.1007/978-1-4899-7637-6_11).


#business-value #recommendation