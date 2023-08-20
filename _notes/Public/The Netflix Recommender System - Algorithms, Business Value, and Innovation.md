---
title : The Netflix Recommender System - Algorithms, Business Value, and Innovation
notetype : feed
date : 18-01-2022
---

### Notes
1. Personalize Video Ranker: PVR
	- Orders the entire catalog of videos (or subsets selected by genre or another filtering)
2. Top-N Video Ranker
	- Find the best few personalized recommendations in the entire catalog for each member
3. [Trending Now](https://netflixtechblog.com/whats-trending-on-netflix-f00b4b037f61)
	- Short-term temporal trends, ranging from a few minutes to perhaps a few days, are potent predictors of videos that our members will watch.
	- 2 Types
		1. Those that repeat every several months (or yearly) yet have a short-term effect
			- Uptick of romantic video watching during Valentine's day
		2. One-off, short-term events, for example, a big hurricane with an impending arrival to some densely populated area
4. [Continue Watching](https://netflixtechblog.com/to-be-continued-helping-you-find-shows-to-continue-watching-on-7c0d8ee4dab6)
	- Sorts the subset of recently viewed titles based on the best estimate
		- Time elapsed since viewing
		- Point of abandonment (min-program, beginning or end)
		- Devices used
5. Video-Video similarity
	- Unpersonalized algorithm that computes a ranked list of videos.
6. Page Generation: Rows selection and ranking
	- Diverse selection of rows [[Personalized Homepage]]
7. Evidence
	- Evidence selection, select the most helpful evidence items for each member
	- For example,
		- Decide whether to show a movie that won an Oscar instead of a film is similar to another video recently watched by that member
		- Decide which image is the best support a given recommendation
8. Search
	- 20% of hours streamed come from a search for videos
	- Users often search for videos, actors, or genres that are not in our catalog
	- Consist of a different algorithm, when the query is "fre"
		- Retrieve item (Frenemies)
		- Retrieve concept (French)
		- Retrieve relevant items given concept.



---


#### Reference

C. A. Gomez-Uribe and N. Hunt, “The Netflix Recommender System: Algorithms, Business Value, and Innovation,” _ACM Trans. Manage. Inf. Syst._, vol. 6, no. 4, pp. 1–19, Jan. 2016, doi: [10.1145/2843948](https://doi.org/10.1145/2843948).


#netflix #recommender-system #recommender-system/videos