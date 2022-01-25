---
title : System Design for Recommendations and Search - Eugene Yan
notetype : feed
date : 24-01-2022
---



### Notes
- Typically
	- Batch
		- Pre-computed
		- Decouple compute from serving
		- Lower operational load
		- Make prediction for everyone
	- Real-time
		- Responsive to time-sensitive context
		- Reduced cost on non-visiting users
		- Make prediction per request
		- Higher cost on operation
- In this talk, we will focus on real-time aka on-demand

#### Overview

![System Design for Recommendations and Search](/assets/img/system-design-for-recommendations-and-search.png)


#### Taobao

![Taobao Architecture](/assets/img/taobao-architecture.png)


#### Facebook
![facebook embedding system overview](/assets/img/facebook-search-architecture.png)



#### Taobao - ATBRG
![taobao-atbrg-system-overview](/assets/img/taobao-atbrg-system-overview.png)


#### Doordash

![doordash-understanding-search-intent-with-better-recall](/assets/img/doordash-understanding-search-intent-with-better-recall.png)


----

### Retrieval

#### The Youtube Recommendations (DNN)

![deep-neural-networks-for-youtube-recommendations](/assets/img/deep-neural-networks-for-youtube-recommendations.png)


#### Instagram (word2vec)

![ig2vec](/assets/img/ig2vec.png)

### Ranker

#### The Youtube Recommendations (via DNN)
![youtube-recommendation-ranker](/assets/img/youtube-recommendation-ranker.png)


#### Alibaba (via Transformer)

![bst-ranker](/assets/img/bst-ranker.png)


### Offline-to-online transitions

![offline-to-online-transitions](/assets/img/offline-to-online-transitions.png)


---

#### Related
- [[Billion-scale Comodity Embedding for E-commerce Recommendation an Alibaba]]
- [[Embedding-based Retrieval in Facebook Search]]
- [[ATBRG - Adaptive Target-Behavior Relational Graph Network for Effective Recommendation]]
- [[Deep Neural Networks for YouTube Recommendations]]
- [[Behavior Sequence Transformer for E-commerce Recommendation in Alibaba]]
- [DoorDash: Understanding Search Intent with Better Recall](https://doordash.engineering/2020/12/15/understanding-search-intent-with-better-recall/)
- [Powered by AI - Instagrams explore recommender system](https://ai.facebook.com/blog/powered-by-ai-instagrams-explore-recommender-system/)

#### Reference:
- [Eugene Yan - System Design for Recommendations and Search - MLOps Community](https://eugeneyan.com/speaking/mlops-community-recsys/)
- [Keynote 7: Moving Beyond Recommender Models - Even Oldridge (NVIDIA), Karl Byleen-Higley (NVIDIA)](https://www.youtube.com/watch?v=5qjiY-kLwFY)


#recommender-system #recommender-system/archtecture #search 