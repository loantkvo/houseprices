Kaggle’s “House Prices: Advanced Regression Techniques” competition
===
Input:
==
* 1460 training examples and 1459 testing ones (in .csv files)
* 80 input features (38 continuous and 43 categorical). 

Analysis procedure: 
==
* remove outliers manually or using sklearn.ensemble.IsolationForest, normalize features (turn on/off for different learning models), 
* encode categorical labels with value between 0 and number_of_categories-1, handle missing (NA) values, 
* use TensorFlow to implement a deep neural network, 
* do bias/variance analysis and error analysis. 

Result:
==
All features:
= 
![](result/allfeatures_epoch1000_adam.png)
