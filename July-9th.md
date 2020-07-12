### July 9th, 2020

Response 3
1. **Question 1:**	What is TF Hub?  How did you use it when creating your script for “text classification of movie reviews”?
	a.	Tensor Flow Hub is a repository for machine learning models that are accessible to users. They can be modified in order to be reused, retrained, or composed.
	b.	We used TF Hub to get pre-trained text embedding models in order to skip text pre-processing, keep size easy to manage, and benefit from transfer learning. 
	
2. **Question 2:**	What are the optimizer and loss functions?  How good was your “text classification of movie reviews” model?
	a.	Loss: binary_crossentropy- measures the "distance" between probability distributions, or in our case, between the ground-truth distribution and the predictions
	b.	Optimizer: adam
	c.	It was decent, not the best though. 85-87% Accuracy shows that a better model could have been trained
	
3. **Question 3:**	In “text classification with preprocessed text” you produced a graph of training and validation loss.  Add the graph to this response and provide a brief explanation.
![image](https://user-images.githubusercontent.com/67920563/87247962-d931ae80-c424-11ea-8de1-9e1b70e6541c.png)
	a. This graph is showing training loss and validation loss over epochs. The training loss decreases as epochs increase due to the optimizer minimizing the losses on every iteration
	b. The validation loss peaks at around 15 epochs. This is due to the model over optimizing, meaning the model is overfit when working on the testing data.
 
