---
title : Recommending Similar Items in Large-scale Online Marketplaces
notetype : feed
date : 18-01-2022
---


### Notes

- Offline process, generates long-term cluster based on product’s title
	- e.g.
		- c1 = {nike, air-max, white, gray, running}
			- Nike white gray 7 mesh Air Max -> c1
			- WOMENS 10.5 Nike Air Max Navi. Gray pink white running shoes -> c1
- Maintains similarity “importance” weight for each cluster by matching keywords against known entities (brand=Nike)
- Associate statistics with clusters based on cluster dictionary.



### Results

- 38.18% increase in CTR
- 89.6% increase in saving to “watch-list”



---

#### Reference

J. Katukuri, T. Konik, R. Mukherjee, and S. Kolay, “Recommending similar items in large-scale online marketplaces,” in _2014 IEEE International Conference on Big Data (Big Data)_, Washington, DC, USA, Oct. 2014, pp. 868–876. doi: [10.1109/BigData.2014.7004317](https://doi.org/10.1109/BigData.2014.7004317).


#recommendation  #recommendation/ecommerce 