---
title : The Youtube video recommendation system 2010
notetype : feed
date : 18-01-2022
---



- Goals: Recent and Fresh, Diverse and Relevant
- 2 Phase
	- Candidate generations
		- [[Co-visitation Recommendation]] (association rule mining)
	- Ranking
		- Variety of signals for relevance and diversity
- Evaluations
	- CTR ([[Click Through Rate]])
	- CVR — long CTR (only counting clicks that led to watches of a substantial fraction of the video) [[Adoption and Conversion Rates]]
	- Session length
	- Time until first long watch
	- Recommendation coverage (the fraction of logged in users with recommendations)

### Results

They run an experiment as follows.

**Period**: 21 days

**Metrics**: CTR ([[Click Through Rate]])

**Variants**:

1. **Most viewed** - Most popular videos within 1 day
2. **Top Favorited** - Most favorited videos
3. **Top Rated** - Most rated (liked) videos
4. **Recommended** - Co-visitation along with users behaviors

**Results**: CTR increased by 207% compared to most viewed.


![Covisitation6](/assets/img/co-visitation-06.jpeg)


---

#### Reference

James Davidson _et al._, “The YouTube video recommendation system,” in _Proceedings of the fourth ACM conference on Recommender systems - RecSys ’10_, Barcelona, Spain, 2010, p. 293. doi: [10.1145/1864708.1864770](https://doi.org/10.1145/1864708.1864770).


#recommender-system/videos  #recommender-system