---
title : Personalized Homepage
notetype : feed
date : 22-01-2022
---




- [Learning a Personalized Homepage - Netflix Tech Blog](https://netflixtechblog.com/learning-a-personalized-homepage-aa8ec670359a)
- [Recent Trends in Personalization: A Netflix Perspective](https://www.slideshare.net/justinbasilico/recent-trends-in-personalization-a-netflix-perspective "https://www.slideshare.net/justinbasilico/recent-trends-in-personalization-a-netflix-perspective")  
- [Personalization at Netflix - Making Stories Travel](https://www.slideshare.net/SudeepDasPhD/personalization-at-netflix-making-stories-travel-170353196 "https://www.slideshare.net/SudeepDasPhD/personalization-at-netflix-making-stories-travel-170353196")  
- [Personalized Page Generation for Browsing Recommendations](https://www.slideshare.net/justinbasilico/personalized-page-generation-for-browsing-recommendations "https://www.slideshare.net/justinbasilico/personalized-page-generation-for-browsing-recommendations")
- [Homepage Personalization at Spotify](https://www.slideshare.net/OguzSemerci/homepage-personalization-at-spotify "https://www.slideshare.net/OguzSemerci/homepage-personalization-at-spotify")  
- [Personalizing the listening experience](https://www.slideshare.net/mounialalmas/personalizing-the-listening-experience "https://www.slideshare.net/mounialalmas/personalizing-the-listening-experience")

---


### Process for creating and choosing rows

- **Finding candidates** - Decide which items should be on the homepage for this user.
- **Adding evidence** - Come up with the evidence or explanation to support the presentation of the row (e.g., Because you watched X, Dark TV Thrillers).
- **Filtering** - Filter each group to handle concerns like maturity rating or remove some previously watched videos.
- **Ranking** - Rank the videos in each group according to a row-appropriate ranking algorithm. We can then apply a row selection algorithm to assemble the entire page. Additional filtering like deduplication to remove duplicate videos on the same page.
- **Formating** - Format rows to the appropriate size for the device.

### Page Algorithmic

1. **Rule-based** - A set of rules defines a template that dictates for all members what types of rows can be in a particular position of the page.
	1. Continue Watching (if any)
	2. Top Picks (if any)
	3. Because you watch X (if any)
2. **Row-independent** - Rank each row independently
	1. User A - See Action movies first
	2. User B - See Comedy movies first
3. **Stage-wise** - Use information about already picked rows to pick the next rows
	1. User A - Click on the action movies shelf. When the user scrolls down, the following rows may show more action-related movies.
4. **Page-wise** - Optimize the whole page
	1. The whole page is designed specifically for User A
	2. Specific and ordered shelve for User A.
	3. Each shelf contains specific and ordered items for User A
	4. Each item may contain a specific image for User A.
	5. Each item may show information specifically for User A
		1. User A sees genres
		2. User B sees actors.
5. **Multi-armed bandit** - Optimize the result based on the user’s interaction and function score.


#recommender-system #netflix #spotify #personalized-homepage