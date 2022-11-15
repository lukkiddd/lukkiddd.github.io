---
title : Feature Crossing
notetype : feed
date : 25-01-2021
---


> **Summary**
> - Feature crossing is one of the **feature engineering technique**.
> - Feature crossing can **capture the interaction between two or more categorical features**.
> - Feature crossing helps model **train faster**, easier to predict target label.
> - Feature crossing **can degrade** learning performance.
> - Feature crossing can **cause sparsity**.



### Pros and Cons

##### Pros

- Help model to make prediction easier
	- For example, the cross feature ‘**job ⊗ company**’ indicates that an individual takes a specific job in a particular company and is a strong feature to predict one’s income
- Faster training time → Reduce training cost
- Cross features are highly interpretable
    

##### Cons

- Can degrade learning performance
	- Irrelevant or redundant or introduce noise
- Cause sparsity




- Handling numerical features
	- Bucketize or convert into the categorical feature before creating a feature cross
- Handling high cardinality
	- Embedded them into an embedding layer to reduce the dimension



### Additional Resources

- [Kaggle - New York City Taxi Fare Prediction](https://www.kaggle.com/c/new-york-city-taxi-fare-prediction "https://www.kaggle.com/c/new-york-city-taxi-fare-prediction")
- [Google ML Crash Course - Feature Crosses](https://developers.google.com/machine-learning/crash-course/feature-crosses/video-lecture "https://developers.google.com/machine-learning/crash-course/feature-crosses/video-lecture")
- [AutoCross: Automatic Feature Crossing for Tabular Data in Real-World Applications](https://arxiv.org/pdf/1904.12857.pdf "https://arxiv.org/pdf/1904.12857.pdf")


---


#### Reference

- [Machine Learning Design Patterns](https://www.oreilly.com/library/view/machine-learning-design/9781098115777/)

#machine-learning #feature-cross