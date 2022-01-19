---
title : Optimizing Similar Item Recommendations in a semi-structured marketplace to maximize conversion
notetype : feed
date : 18-01-2022
---



### Notes
- Recall + Ranking
	- Recall: Candidate Generation
		- Coviewed items
			- A pair of items which have been frequently viewed together in the same browsing session by multiple users
			- Filter out covered from a different item category to ensure similarity.
		- Title similarity
			- Using ElasticSearch indexing scheme (TF/IDF) give higher quality than previous approaches [[Recommending Similar Items in Large-scale Online Marketplaces]] which used Locality Sensitive Hashing (LSH)
	- Ranking
		- Pointwise learning to rank problem
		-  Binary classification whether purchased (positive class) vs non-clicked (negative class)
		- Sampling
			- KL divergence to get a quantitative measure of the overlap of the probability distributions for 2 classes
			- The non- clicked / purchased strategy is optimal for class separation. Reflect…
				- Non-clicked show absolutely no user interest
				- Purchased indicate complete user intention
- Baseline = Linear model with manually adjusted weights based on domain exports



### Results
- CTR +3.0%
- PTR (Purchase-Through-Rate) +6.6%
- Revenue +6.0%


---

#### Reference

Y. M. Brovman _et al._, “Optimizing Similar Item Recommendations in a Semi-structured Marketplace to Maximize Conversion,” in _Proceedings of the 10th ACM Conference on Recommender Systems_, Boston Massachusetts USA, Sep. 2016, pp. 199–202. doi: [10.1145/2959100.2959166](https://doi.org/10.1145/2959100.2959166).


#recommendation/ecommerce #recommendation