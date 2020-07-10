# Welcome to my GitHub page!
![image](https://user-images.githubusercontent.com/67920563/86965771-0553e380-c136-11ea-841e-ca6878d8cc8e.png)
## Response Index
1. Response 1: July 7th, 2020

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
  
  ### July 8th, 2020
  1. **Question:** In the video, First steps in computer vision, Laurence Maroney introduces us to the Fashion MNIST data set and using it to train a neural network in order to teach a computer “how to see.” One of the first steps towards this goal is splitting the data into two groups, a set of training images and training labels and then also a set of test images and test labels.  Why is this done?  What is the purpose of splitting the data into a training set and a test set?
  -	The training set is data used to train a model. The test set is the data used to test the model. In other words, the test set is used to check whether the model is satisfactory or if other models should be tried. By knowing how accurate the model is, we know how accurate it may perform with new data. If we do not split the data, we have no way of knowing if the model is sufficient.
  2. **Question 2:** The fashion MNIST example has increased the number of layers in our neural network from 1 in the past example, now to 3.  The last two are Dense layers that have activation arguments using the relu and softmax functions.  What is the purpose of each of these functions.  Also, why are there 10 neurons in the third and last layer in the neural network.
  -	 Relu function: output of a neuron is less than zero, set it to zero so it doesn’t cancel out positive outputs (so it doesn’t skew downwards)
  -	Softmax function: in the final layer, helps u find most likely candidate, sets largest value to 1 
  -	10 neurons: the number or neurons in the last layer should match the number of classes we are classifying for. Since there are 10 types of clothing, the last layer has 10.
  3. **Question 3:** The last ten outputs calculate the probability that a piece of clothing is for that particular class.
In the past example we used the optimizer and loss function, while in this one we are using the function adam in the optimizer argument and sparse_categorical-
crossentropy for the loss argument.  How do the optimizer and loss functions operate to produce model parameters (estimates) within the model.compile() function?
  -	The neural network makes a prediction based on the relationship between the data and labels. The loss function evaluates how good or bad that prediction is. The optimizer uses the results to improve that guess. It minimizes the prediction errors by manipulating weights and biases. Thus, the neural network is trained as it repeats, thus producing model parameters. 
  4. **Question 4:** Using the mnist drawings dataset (the dataset with the hand written numbers with corresponding labels) answer the following questions.
    1.What is the shape of the images training set (how many and the dimension of 
  each)?
      - 28x28, 60,000
    2. What is the length of the labels training set? 
      -60,000
    3.What is the shape of the images test set? 
      -10,000
  

  

  
