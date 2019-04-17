Kaggle’s “House Prices: Advanced Regression Techniques” competition
====
I. Input:
===
* 1460 training examples and 1459 testing ones (in .csv files)
* 80 input features (38 continuous and 43 categorical). 

II. Analysis procedure: 
===
1. Clean the data: impute missing values

   * Numerical features:
		- For LotFrontage, missing values are estimated (L2 linear regression) from LotArea
![](result/LotFrontageEstimatedFromLotArea.png)
		- Fill 0/None to other missing values

	* Categorical features: Fillna with either 0 or mode 
2. Inspect the data by visualization

3. Preprocessing

	3.1. Removing outliers: using either IsolationForest or normalization (turn on/off for different learning models)
	
	3.2. Handling features having covariate-shift
	
	![](result/distributions_of_numerical_features.png)
	

	![](result/drifting.png)
	
	3.3. Removing features that are least 'importance': "Utilities" (and "Heating")
				
				Train	Val	    Test
				
		AllPub		1138	285.0	1459.0
	
		NoSeWa		1	NaN	  NaN
		
	3.4 Encoding categorical data with value between 0 and number-of-categories - 1. Use either get_dummies or let the algorithm learn the embedding matrix. 

4. Modelling

- Using TensorFlow to implement a deep neural network. 
- Tuning: based on bias/variance analysis and error analysis. 

III. Results:
===
1. NN with 5 layers of 128 unit/each
	- All features: use all feature for training with Adam optimzation
	![](result/allfeatures_epoch1000_adam.png)

	- With early_stop (terminated at the epoch when validation loss stops decreasing)

	![](result/rmse_001.png)

2. NN with 7 layers of 256 unit/each

	![](result/rmse_002.png)
