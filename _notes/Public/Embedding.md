---
title : Embedding
notetype : feed
date : 13-03-2022
---

### What is Embedding

[Google ML Crash Course - Embedding](https://developers.google.com/machine-learning/crash-course/embeddings/video-lecture#:~:text=An%20embedding%20is%20a%20relatively,like%20sparse%20vectors%20representing%20words.) said

> An embedding is a relatively **low-dimensional space** into which you can translate high-demensional vectors. Embeddings make it easier to do machine learning on large inputs like sparse vectors representing words. Ideally, an embedding **captures some of the semantics** of the input placing sementically similar inputs close together in the embedding space. An **embedding can be learned** and resued across models


[Will Koehrsen (Data Scientist at Cortex Intel)](https://www.linkedin.com/in/william-koehrsen-48a643a5/) has mentioned embeddings in his [medium article](https://towardsdatascience.com/neural-network-embeddings-explained-4d028e6f0526)

> An embedding is a mapping of a discrete - categorical - variable to a vector of continuous numbers. [In the context of neural networks, embeddings](https://www.tensorflow.org/text/guide/word_embeddings) are low-dimensional, **learned continuous vector representations** of discrete variables.
> Neural network embeddings are useful because they can **reduce the dimensionality** of categorical variables and **meaningfully** represent categories in the transformed space.


In [Machine Learning Design Patterns book](https://www.amazon.com/Machine-Learning-Design-Patterns-Preparation/dp/1098115783) written by [Valliappa Lakshmanan](https://www.linkedin.com/in/valliappalakshmanan/), [Sara Robinson](https://www.linkedin.com/in/sara-robinson-40377924/) & [Michael Munn](https://www.linkedin.com/in/munnm/) mentioned embeddings in Design Pattern 2: Embedding that

> Embeddings are a **learnable data representation** that map **high-cardinality data into a lower dimensional space** in such a way that the information **relevant to the learning problem** is preserved. Embeddings are at the heart of modern-day machine learning and have various incarnations through the field.



In brief, Embeddings are *"A learnable continuous vector presentation, use to reduce the dimensionalty and expected to captures semantics relationship of the input data"*


---

### Why Embedding

Most of the reason we widely use embedding is to **reduce the dimensionalty** of the input data in a **meaningful** way.

Basically we start by encode the categorical input into a one-hot encoding that maps each input string into a 1 and 0 of vectors.

Using one-hot encoding can causes 2 issues
1. **Sparse matrix** where there are high dimensions with a lot of zero values.
2. **Independent** where each variable considered as independent.


#### Sparse Matrix

For example we have the input as followed

```
input = [
	['Dog'],
	['Cat'],
	['Cat'],
	['Dog']
]
```

When we encode it as a one-hot encoding the result will be

```
Dog = [1, 0]
Cat = [0, 1]

### The encoded will be

encoded_input = [
	[1, 0],
	[0, 1],
	[0, 1],
	[1, 0]
]

```

As you can see 2 dimensions is very low, but if we have many many more categories, it may cause a problem.


Imagine the recommendation system, we usually have multiple products which user interacted with, let's say we have 5k products, our one-hot encoding of each product should contains 5k dimensions. If we need to consider last 5 interactions for each users, the input will be 25k dimensions! 

```
inputs = [
	"user_id": "1",
	"product_id_1": [0,0, ...., 0], # (length = 5,000, only one value as 1)
	"product_id_2": [1,0, ...., 0], # (length = 5,000, only one value as 1)
	"product_id_3": [0,0, ...., 1], # (length = 5,000, only one value as 1)
	"product_id_4": [0,0, ...., 0], # (length = 5,000, only one value as 1)
	"product_id_5": [0,0, ...., 0], # (length = 5,000, only one value as 1)
]
```

#### Independent

- http://colah.github.io/posts/2014-07-NLP-RNNs-Representations/

---

### How to Embedding

The embedding layer is just another hidden layer of the neural network. We can either use the embeding layer from any neural network libraries ([Keras](https://keras.io/api/layers/core_layers/embedding/), [Tensorflow](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Embedding), [Tensorflow Feature Column](https://www.tensorflow.org/api_docs/python/tf/feature_column/embedding_column), [Pytorch](https://pytorch.org/docs/stable/generated/torch.nn.Embedding.html), etc.)

**Here're the generic steps:**

1. Create a lookup table (Mapped a string to an index)
2. Transform those categories into a one-hot encoding (Mapped the number(index) to the one-hot encoding)
3. Connect one-hot encoding to an embedding layer (Typically just a hidden layer with a lower dimensional space compared to one-hot layer)
4. Connect to a hidden layer to produce the output
5. Finally connect to the output layer with a softmax activation function.


For more detail consider look into the interesting articles.
- [Tensorflow - Word Embedding](https://www.tensorflow.org/text/guide/word_embeddings)
- [Word2vec from scratch - Jake Tae](https://jaketae.github.io/study/word2vec/)


#### To train generic embeddings

We also can leverage the complete packages to train the general purpose embeddings
- [Gensim](https://radimrehurek.com/gensim/)
- [StarSpace from Facebook](https://github.com/facebookresearch/StarSpace)


### Alternatives to Embedding

- Autoencoders


---

###### Other Notes:
- Choosing the embedding dimension
	- [Use the forth root](https://developers.googleblog.com/2017/11/introducing-tensorflow-feature-columns.html) of the total number of unique categorical elements
	- [1.6 times the square root](https://github.com/fastai/fastai2/blob/82c82fd499ea675e40580f6a6354a3fb8dc86f25/fastai2/tabular/model.py) of the number of unique elements in the category, and no less than 600
- [Introducing TensorFlow Feature Columns](https://developers.googleblog.com/2017/11/introducing-tensorflow-feature-columns.html) said that

> How do the values in the embeddings vectors magically get assigned? Actually, the assignments happen during training. That is, the model learns the best way to map your input numeric categorical values to the embeddings vector value in order to solve your problem. Embedding columns increase your model's capabilities, since an embeddings vector learns new relationships between categories from the training data.