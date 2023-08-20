---
title : Recommending ephemeral items at web scale
notetype : feed
date : 18-01-2022
---


- Generative Clustering Model
	- Objective
		- To maximize the total intra-cluster coherence
	- Use-cases
		- Naive Bayes for ranking
		- (Similar product) Inferring latent product for unseen one
- Evaluate using offline and online
	- Offline evaluation
		- The area under the click-view ROC curve (AOC)
			- Plots the click recall vs view recall from the testing examples ranked in descending order
		- Relative CTR lift over a baseline predictor at a certain recall level of view
	- Online evaluation
		- CTR
		- BTR (bid-through rate)
		- PTR (purchase-through rate
		- GMB (gross merchandising bought)

### Result
- 3-5 folds improvement in CTR and Purchase-through rate

---

#### Reference

Y. Chen and J. F. Canny, “Recommending ephemeral items at web scale,” in _Proceedings of the 34th international ACM SIGIR conference on Research and development in Information - SIGIR ’11_, Beijing, China, 2011, p. 1013. doi: [10.1145/2009916.2010051](https://doi.org/10.1145/2009916.2010051).


#recommender-system