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
		1. What is the shape of the images training set (how many and the dimension of 
  each)? 28x28 & 60,000
		2. What is the length of the labels training set? 60,000
		3. What is the shape of the images test set? 10,000
#### **PLOTS**
![image](https://user-images.githubusercontent.com/67920563/87109210-0ec27600-c232-11ea-96b4-f9b770866c1c.png)

![image](https://user-images.githubusercontent.com/67920563/87109200-066a3b00-c232-11ea-80f1-2a820c67641b.png)
![image](https://user-images.githubusercontent.com/67920563/87109225-1550ed80-c232-11ea-8552-f80089c955bb.png)
