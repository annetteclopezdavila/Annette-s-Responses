## July 21, 2020

### Premade estimators
1. How did you split the labels from the training set?  What was the name of the labels dataset?
	-	In order to split the labels, we use the pop function. The model will be using the species labels which are Setosa, Versicolor, Virginica.
2. List 5 diﬀerent estimators from tf.estimator and include the base command as you would write it in a script 
	-	DNNClassifier:
		- For deep models that perform multi-class classification
		
				tf.estimator.DNNClassifier(
    				feature_columns=my_feature_columns,
  				hidden_units=[30, 10], n_classes=3)
				
				
	-	DNNLinearCombinedClassifier:
		- For wide and deep models
		
		
				tf.estimator.DNNLinearCombinedClassifier(
    				model_dir=None, linear_feature_columns=None, linear_optimizer='Ftrl',
   				dnn_feature_columns=None, dnn_optimizer='Adagrad', dnn_hidden_units=None,
    				dnn_activation_fn=tf.nn.relu, dnn_dropout=None, n_classes=2, weight_column=None,
   				label_vocabulary=None, config=None, warm_start_from=None,
    				loss_reduction=losses_utils.ReductionV2.SUM_OVER_BATCH_SIZE, batch_norm=False,
    				linear_sparse_combiner='sum'
				)
	-	LinearClassifier:
		-	For classifiers based on linear models
			
			
			tf.estimator.LinearClassifier(
    			feature_columns, model_dir=None, n_classes=2, weight_column=None,
    			label_vocabulary=None, optimizer='Ftrl', config=None, warm_start_from=None,
    			loss_reduction=losses_utils.ReductionV2.SUM_OVER_BATCH_SIZE,
    			sparse_combiner='sum'
			)
	-	LinearRegressor:
		-	Estimator for linear regression problems
		
		
			tf.estimator.LinearRegressor(
    			feature_columns, model_dir=None, label_dimension=1, weight_column=None,
   			optimizer='Ftrl', config=None, warm_start_from=None,
    			loss_reduction=losses_utils.ReductionV2.SUM_OVER_BATCH_SIZE,
    			sparse_combiner='sum'
			)

	-	DNNRegressor:
		-	A regressor for DNN models
		
		
			tf.estimator.DNNRegressor(
    			hidden_units, feature_columns, model_dir=None, label_dimension=1,
    			weight_column=None, optimizer='Adagrad', activation_fn=tf.nn.relu, dropout=None,
    			config=None, warm_start_from=None,
    			loss_reduction=losses_utils.ReductionV2.SUM_OVER_BATCH_SIZE, batch_norm=False
			)
3. What are the purposes input functions and deﬁning feature columns?
	-	Input functions: return a Dataset object which then outputs a label for the training batch and a dictionary of feature column names that map them to the tensors containing feature data. In other words, input function pass the input data to the model
	-	Feature Columns: specifications for how model should interpret the data from the features dictionaries. The feature columns describe the features you want the model to use.
	<img width="361" alt="estimators" src="https://user-images.githubusercontent.com/67920563/88458116-92e34300-ce59-11ea-8fc1-4bda58de5648.PNG">
	
4. Describe the command classiﬁer.train() in detail.  What is the classiﬁer and how did you deﬁne it?  Which nested function (and how have you deﬁned it) are you applying to the training and test detests?
	-	The classifier.train() command trains the model. Its input can be the steps of the function as well as the training input function. The first part of the command, classifier, describes which estimator we are using. In this example, we are referring to DNN Classifier. However, if it were the LinearRegressor estimator, our command could look like linear_regressor.train(). The classifier command is defined earlier in the model when we instantiate the estimator. For example, classifier has been defined as classifier=tf.estimator.DNNClassifier(). Thus, this is the part of the code that actually lets us apply the estimator!
	-	Our training input function was defined with all the other input functions; however, this one takes the training set features and labels, specifies batch size, whether the data is shuffled, and the number of epochs to iterate over the data.
5. Redeﬁne your classiﬁer using the DNNLinearCombinedClassiﬁer() as well as the LinearClassiﬁer().  Retrain your model and compare the results using the three diﬀerent estimators you instantiated.  Rank the three estimators in terms of their performance.
	-	LinearClassifier: 0.967 accuracy
	-	DNNLinearCombinedClassifier:0.733
	-	DNNClassifier: 0.533
### Build a Linear Model
1. Using the dftrain dataset, upload an image where you used the seaborn library to produce a sns.pairplot().  Also include a histogram of age using the training set and compare it to the seaborn plot for that same feature (variable).  What interpretation can you provide of the data based on this plot? 

<img width="295" alt="PAIRPlOT" src="https://user-images.githubusercontent.com/67920563/88457930-0dab5e80-ce58-11ea-8db5-c628a5f09992.PNG">
<img width="262" alt="histogram" src="https://user-images.githubusercontent.com/67920563/88458308-0fc2ec80-ce5b-11ea-9ccf-5b965646df82.PNG">

- When looking at the age x age plot in the pairplot in the top left corner, we can see that the pdf follows a very similar trend to the histogram. The plots peak at about ages 20-30, signifying that this was the average age of people on board.
2. What is the diﬀerence between a categorial column and a dense feature?
	-	Categorical columns are types of feature columns that contain non-numerical strings as input. A dense feature uses a categorical column to produce a tensor, or vector. Categorical columns must first be transformed into indicator columns in order for DenseFeatures to accept it. This is because DenseFeatures only accepts dense tensors. Dense tensors are equivalent to the concept of arrays in Python.
3. Describe the feature columns that have been input to your LinearClassiﬁer().  How would you assess the result from your initial output?  What is the purpose of adding a cross featured column?  Did your attempt to capture the interaction between age and gender and incorporate it into your model improve performance?  Include and interpret your predicted probabilities and ROC curve plots.
	-	The linear classifier’s feature columns include both categorical and numeric columns such as class, age, sex, town embarked, fare, etc. The training accuracy was 75%. Although this is a decent amount, we can probably make a better model. Perhaps we have not set up our feature columns correctly. To help us train a model that correlates our variables in better combinations, we can do cross feature columns. For example, there may be a difference in correlation between thirty year old males and fourty year old males. By training our model with cross features, we get a higher accuracy. Crossing age and gender alone improved our model to 77.6%. 
	
	![image](https://user-images.githubusercontent.com/67920563/88458418-f0788f00-ce5b-11ea-8ba4-1a21df173c4d.png)
	
	-	The predicted probabilities plot is skewed to the right, meaning most people had less than 50% chance of survival. Strangely enough, the lowest point of the graph is at the half way point. The probability for survival increases at 70% drastically, thus prompting us to wonder what could have made the data skewed towards 0 and 1 but not 0.5.
	![image](https://user-images.githubusercontent.com/67920563/88458472-4a795480-ce5c-11ea-9b76-d2010b26b5be.png)
	
	-	The ROC curve shows the tradeoff between the true positive rate and false positive rate. As can be seen, the curve mimics a logarithmic shape, meaning that it plateaus as the false positive rate increases. The curve is skewed towards the true positive rate, meaning that the tradeoff in this case did pay off! The true positive rate is higher than the false positive rate. Why does the curve plateau though? Is our model overfit or underfit? Because the accuracy is still a little low, I would first try to make the model improve before troubleshooting for other problems.
