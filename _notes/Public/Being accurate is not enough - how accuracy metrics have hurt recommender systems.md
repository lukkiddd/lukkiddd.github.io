---
title : Being accurate is not enough - how accuracy metrics have hurt recommender systems
notetype : feed
date : 22-01-2022
---



### Conclusion
- We need to judge the quality of recommendations as users see them: as recommendation lists
	- We need to create a variety of metrics that act on recommendation lists (e.g., intra-list similarity as introduced in [[Improving recommendation lists through topic diversification]])
- We need to understand the differences between recommender algorithms and measure them in ways beyond their ratability.
- Users return to recommenders over a while, growing from new to experienced users. If we understand their purpose and intent, we can generate better recommendations



- Propose new user-centric directions for evaluating recommender systems
- We reward a travel recommender for recommending places a user has already visited instead of rewarding it for finding new places for the user to visit
- We review 3 aspects
	- **Similarity**
		- Once a user rated one Star Trek movie, she would only receive recommendations for more Star Trek movies)
		- This problem is more noticeable for "cold-start" users.
		- This problem could convince a user to leave the recommendation
		- Accuracy metrics cannot see this problem.
		- One approach to solve was [[Improving recommendation lists through topic diversification]]
	- **[[Recommender System - Serendipity]]**
		- Recommending the highest ratability items have good accuracy but is not useful for users
			- Recommend the item already owned or consumed. Those recommendations were rarely acted on by users
		- Serendipity metric may be difficult to create without feedback from users
	- **User needs and expectations**
		- New users have different needs from an experienced user
			- Highly ratable items - establish trust
			- The choice of the algorithm used for new users dramatically affects the user experience
				- [[Getting to know you - learning new user preference in recommender systems]]
					- Suggest that popularity, item-item personalized can perform well for new users
			- Differences in language and cultural background influenced user satisfaction
	


---

#### Reference
S. M. McNee, J. Riedl, and J. A. Konstan, “Being accurate is not enough: how accuracy metrics have hurt recommender systems,” in _CHI ’06 Extended Abstracts on Human Factors in Computing Systems_, Montréal Québec Canada, Apr. 2006, pp. 1097–1101. doi: [10.1145/1125451.1125659](https://doi.org/10.1145/1125451.1125659).


#recommender-system #recommender-system/quality #recommender-system/accuracy #recommender-system/serendipity 