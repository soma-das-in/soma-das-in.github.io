---
layout: post
title:  "Optimizing performance of Deep Neural Networks by tuning its Hyper-parameters"
author: soma
categories: [Deep Learning]
tags: [Deep Learning, Neural Networks, Hyper-parameter Optimization]
image: assets/images/2022-11-10-hyperparameter-optimization-deep-neural-networks/Hyperparameter-optimization-cover1.jpg
description: "Optimizing performance of Deep Learning Models by tuning its hyper-parameters."
# featured: false
# hidden: true
# rating: 4.5
comments: true
---

The performance of a Deep Neural Network depends on a wide range of hyperparameters which makes manual tuning an extremely challenging and tedious task. The  search space is vast and it is not feasible to try all combinations, also a hit and trial method does not scale. Hence a  hyperparameter tuning strategy using efficient algorithms needs to be adopted to find the optimal hyperparameters for a Deep Neural Network. 

The approach for Hyperparameter Optimization entails :

*	Define the search space for the hyperparameters for sampling 
*	Select an algorithm which the tuner would use.
*	Generate a new set of hyperparameter values from the search space for each trial using the tuner
*	Build and evaluate the models using the hyperparameters and record the metrics 
*	Finally, a good set of hyperparameter values is found which results in good performance 


In this blog a comparative study of several popular hyperparameter optimization algorithms like **Random Search**,**Bayesian Optimization** and **Hyperband** has been performed.
These algorithms can be experimented with to improve the model’s efficiency.




![Adding a data source](/assets/images/2022-11-10-hyperparameter-optimization-deep-neural-networks/Hyperparameter-Optimization-1.jpg)




