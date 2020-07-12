### July 7th, 2020
1. **Question 1:** In Laurence Maroney’s video, What is ML, he compares traditional programming with machine learning and argues that the main difference between the two is a reorientation of the rules, data and answers. According to Maroney, what is the difference between traditional programming and machine learning?
  - Traditional Programming: One inputs rules and data in order to derive answers 
  - Machine Learning: One inputs data and answers in order to derive rules
2. **Question 2:** With the first basic script that Maroney used to predict a value output from the model he estimated (he initially started with 10 that predicted ~31.  Modify the predict function to produce the output for the value 7.  Do this twice and provide both answers.  Are they the same?  Are they different? Why is this so?
  -	Two answers provided: 22.00014 & 22.000448
  -	The two answers are slightly different due to the fact that neural networks deal with probabilities rather than certainties. Because it is a stochastic process, the answers will be very close but not often the same.
3. **Question:** Using the script you produced to predict housing price, take the provided six houses and train a neural net model that estimates the relationship between them. Based on this model, which of the six homes present a good deal? Which one is the worst deal? Justify your answer.
  -	By making a neural net model, we can estimate what each house should be priced based on bedroom number. Looking at the output of the code, we see that 160 Holly Point Rd, a house with three bedrooms selling for $97,000, is the best deal. Based on the model, we see that 760 New Point Comfort Hwy, a five bedroom house selling for $577,200, is the worst deal.
  - This model could have been strengthened by using square footage instead of bedroom count in the input. Thus, it would account for other spaces and bathroom count.
  
