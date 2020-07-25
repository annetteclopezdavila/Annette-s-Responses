## July 22, 2020
### Boosted Trees
1. What is a one-hot-encoded column and why might it be needed when transforming a feature?  Are the source values continuous or discrete? 
  -	One-hot coding is a process where categorical variables are converted into ways that are easier for the machine to read and process. Instead of just substituting a value for each company, it applies binarization to each category in order to avoid mistakes and jumbling value numbers could offer. Their source values are discrete.

<img width="272" alt="ENCODING" src="https://user-images.githubusercontent.com/67920563/88458115-924aac80-ce59-11ea-9516-1dcdca4ccd01.PNG">

2. What is a dense feature?  For example, if you execute example = dict(dftrain) and then tf.keras.layers.DenseFeatures(your_features)(your_object).numpy(), how has the content of your data frame been transformed?  Why might this be useful?
  -	Dense features produce tensors. As seen with the one-hot-encoding, the categorical features are turned into vectors. Zeros are placed to show an absence of data, which could further help efficiency in the machine. As we often saw in Data 146, missing data often means that the data must be reorganized in order for the machine to make sense of it, or thrown out.  Because throwing data out can mean we lose other valuable data, putting a placeholder for the absence of data can help us mitigate such losses.
3. Provide a histogram of the probabilities for the logistic regression as well as your boosted tree model.  How do you interpret the two diﬀerent models?  Are their predictions essentially the same or is there some area where they are noticeable diﬀerent.  Plot the probability density function of the resulting probability predictions from the two models and use them to further illustrate your argument.  Include the ROC plot and interpret it with regard to the proportion of true to false positive rates, as well as the area under the ROC curve.  How does the measure of the AUC reﬂect upon the predictive power of your model?

  ### Linear
  
  <img width="228" alt="linear" src="https://user-images.githubusercontent.com/67920563/88457927-0be19b00-ce58-11ea-9c3b-0e7def3c7606.PNG">
  
  ### Boosted Trees
  
 <img width="218" alt="boosted trees" src="https://user-images.githubusercontent.com/67920563/88457912-fb312500-ce57-11ea-80b8-ee0c20fd3905.PNG">
 
  -	The prediction plots both are right leaning. Although the have a slightly different tail, we essentially get very similar information. In the linear mode, there is a slight increase at 0.6. In the boosted tree model, the probability spikes at 0.99. The linear model did show that the peak frequency was around 75, while the boosted trees spiked at ~83. Both models do not have probabilities of 0% nor 100%. Although the predictions both have very similar information, one must be more accurate than the other when looking closer at specifics. The linear model’s accuracy was 0.765 while the boosted tree model had an accuracy of 0.818. This both proves that the trends are very similar in information given, and shows us which model is slightly better.
<img width="213" alt="7 23roc" src="https://user-images.githubusercontent.com/67920563/88457904-f2405380-ce57-11ea-9cf3-89b51570637b.PNG">

-	The ROC plot leans towards the true positive rate very quickly at first; the gradient is very steep up until 0.2 on the false positive rate. After 0.5, the model plateaus. When examining ROC, we should always be looking for how close the curve is to the top left corner, as this would indicate better accuracy. Thus, by looking at the curve, we can see that the curve is significantly close to the left corner with a little bit of improvement. But how do we know how much improvement exactly? Another useful measure to interpret the ROC curve is area. The area under the curve is equivalent to the probability that when a positive and negative instance are drawn, the function will assign a higher value to the positive instance. Thus, the higher the area under the curve is, the better our model is.

### Boosted Trees continued (with model understanding)
1. Upload your feature values contribution to predicted probability horizontal bar plot as well as your violin plot.  Interpret and discuss the two plots.  Which features appear to contribute the most to the predicted probability?

  <img width="286" alt="boosted trees continued 1" src="https://user-images.githubusercontent.com/67920563/88457909-fb312500-ce57-11ea-9f07-4d2153cc91c5.PNG">
  <img width="290" alt="violin plot" src="https://user-images.githubusercontent.com/67920563/88457931-14d26c80-ce58-11ea-9630-275ec9b06d7a.PNG">
  
  -	Because the larger magnitudes have a larger impact on prediction, we see that sex, male, and class have the top three biggest contributions. These values are negative; this, they reduced the model’s prediction. There is one major positive value: fare. However, the majority of features reduced the prediction. Thus, we can conclude that as a 31 year old second class male was more susceptible to death, while people who payed for a fare of 26.25 had a higher chance of survival.
2. Upload at least 2 feature importance plots.  Which features are the most important in their contribution to your models predictive power?
  ![image](https://user-images.githubusercontent.com/67920563/88458808-9a591b00-ce5e-11ea-9672-a0e388430d7e.png)
  -	Gain based feature importance measures the loss change when splitting on a particular feature. From the plot, we can see that sex and fare had the most feature importance in the contribution to the model.
  
  <img width="299" alt="average" src="https://user-images.githubusercontent.com/67920563/88457906-f5d3da80-ce57-11ea-96ad-fcf20d9a23c8.PNG">
  -	The Average absolute DFC plot averages the absolute value of DFCs to gauge impact. From the means, we can see that sex was the feature with the most contribution, while age class and fare were all very similar and second most impacting.

