---
title : Incorporating User Control into Recommender Systems Based on Naive Bayesian Classification
notetype : feed
date : 05-02-2023
---

Published: 2007

#### Abstract
- Recommendation Systems ถูกใช้งานในการทำ Personalized Services เยอะขึ้นเรื่อยๆ
- เทคนิคที่มักจะใช้บ่อยคือ Collaborative filtering และ naive Bayesian classification
- ซึ่งสองเทคนิคนี้ก็มีปัญหาหลายอย่าง เช่น cold-start, หรือ เรื่องของความช้าในการ adapt ตามความชอบของ user
- ปัญหาเหล่านี้ สามารถแก้ได้ ด้วยการที่ให้ user แก้ไข profile ของ user เอง
	- ใน Paper เสนอ extensions ของ naive Bayes โดยทำให้ user สามารถควบคุมผลลัพธ์ได้ จากการ integrate profile 2 แบบ ของ user
		- แบบแรกคือ profile ที่เรียนรู้จาก rating feedback
		- แบบที่สองคือ profile ที่ user เป็นคนสร้างขึ้นมาเอง

#### Introduction
- Positive-negative classification
- A range of like-defrees
- Typically slow, because users need to rate a considerable number of items before recommender can make sensible suggestions
	- Lead to cold-start problem, and slow adaptability of the recommender
- Quick fix: Setting up a rating session first!
	- Unacceptable, and not elegant way to deal with



#### Naive Bayesian Classification
- P(B|A) = P(A|B) * P(B) / P(A)
- Laplace corrections/Laplace smoothing - to prevent "zero frequency problem"
- Imbalance data? -> cost-based approach
- Missing features? -> calculate based on only valid value.


#### Like-degree
- r = P(+|x) / P(-|x) --> [1, inf)
- l = r / 1-r --> [0,1]

#### 2 profile
- l^1 = learned profile
- l^u = user-defined profile

#### Integrated
- l^int = alpha l^1 * (1-alpha) l^u
- alpha = [0,1]
- Nmin = min(N(i, -), N(i, +))
- set minimum threshold alpha(i) = min(1, L-Nmin / L-K)


#### Pruning history

#### Multi-value pair
