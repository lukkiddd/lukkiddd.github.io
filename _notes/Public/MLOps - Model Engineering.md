---
title : MLOps - Model Engineering
notetype : feed
date : 22-03-2022
---


#### Model Engineering
- Model training
	- Include feature engineering, and the hyperparameter tuning
	- https://netflixtechblog.com/machine-learning-platform-meetup-ddec090f3c17
	- Details
		- Feature Engineering
			- Discretize continuous features
			- Decompose features (categorical, date/time)
			- Add transformations features (log(x), sqrt(x), x2, etc.)
			- Aggregate features into promising new features
			- Feature scaling: Standardize or normalize featuers
		- Model engineering
			- Every model specification should go through code review and be versioned
			- Train many ML models from different categories (linear regression, logistic regression, k-means, naive bayes, SVM, Random Forest) using standard parameters
			- Measure and compare their performance. For each model, use N-fold cross-validation and compute the mean and standard deviation of the performance measure on the N folds.
			- Error Analysis: Analyze the types of errors the ML models make
			- Consider further feature selection and engineering
			- Identify the top three to five most promising models, preferring models that make different types of errors
			- Hyperparameters tuning by using cross-validation. Please note that data transformation choices are also hyperparameters. Random search for hyperparameters is preferred over grid search
			- Consider ensemblemethods (majority vote, bagging, boosting, or stacking)
			- https://eng.uber.com/tuning-model-performance/
- Model evaluation
	- Validating the trained model to ensure it meets original codified objectives
- Model testing
	- Performning the final "Model Acceptance Test" with hold backtest dataset
- Model packaging
	- Process of exporting model to the final specific format (ONNX, PMML)