# July 28, 2020

### Word Embeddings 
1.	**Question 1:** Why is using one-hot encoding an ineﬃcient towards vectorizing a corpus of words?  How are word embeddings diﬀerent? (see this video https:// www.youtube.com/watch?v=EEk6OiOOT2c) 
-	If we one hot encode the phrases, it would look something like:
 
 ![image](https://user-images.githubusercontent.com/67920563/89103514-735f9380-d3e0-11ea-8656-0711ffaac0bf.png)
 
-	However, this is inefficient due to the fact that a one hot encoded vector is sparse, thus meaning the indices are zero. Lets assume we were applying this approach to a book. We would have to one hot encode each word in the book, thus we end up with many vectors full of zeroes. It would take up a massive amount of space.
-	Word embeddings do not need to be specified by hand and are a dense representation in which similar words have similar encoding. Embeddings are vectors with floats; they are weights learned by the model during training. 

![image](https://user-images.githubusercontent.com/67920563/89103535-870afa00-d3e0-11ea-8e06-5c7b4369fb6d.png)
	 
2. Compile and train the model from the tensorﬂow exercise.  Plot the training and validation loss as well as accuracy.  Post your plots and describe them.

![image](https://user-images.githubusercontent.com/67920563/89103550-98ec9d00-d3e0-11ea-921a-2ad0d9f759a4.png)

-	As seen in the graph, the training loss quickly declines in a logarithmic manner. The validation loss declines until the third epoch; from the third to the tenth epoch, the validation loss increases. Thus, the model becomes more overfit.

![image](https://user-images.githubusercontent.com/67920563/89103552-aace4000-d3e0-11ea-9fdd-f32fa513a3dd.png)
 
- This graph measures accuracy. Training accuracy increases logarithmically over time, but becomes more steady as the epochs continue. Thus, the accuracy is not improving by much past epoch 4. The validation accuracy has two peaks, but stays steady overall. It peaks at epoch three and epoch 8. This matches the loss graph; thus, the model should be left to run only 3 epochs before becoming overfit.

### Text Classiﬁcation with an RNN
1. Again compile and train the model from the tensorﬂow exercise.  Plot the training and validation loss as well as accuracy.  Stack two or more LSTM layers in your model.  Post your plots and describe them.
An RNN, or Recurrent Neural Network, works with sequences of data. Rather than passing through one layer and then another, these networks link each layer by sending certain information back into previous layers. This not only works on the input information, but past information given to the network. Recurrent layers include LSTM (Long Short Term Memory) and GRU (Gated Recurrent Units). LSTMs are capable of learning long-term dependencies in order to find patterns across time. LSTMs work best for classifying, processing, and predicting when using time series data.

**WITHOUT LSTM**
 
 ![image](https://user-images.githubusercontent.com/67920563/89103560-b6ba0200-d3e0-11ea-8512-1582ba98e6eb.png)
 ![image](https://user-images.githubusercontent.com/67920563/89103573-cb969580-d3e0-11ea-95e8-7ec55d163dd9.png)
 
**WITH LSTM**
 
 ![image](https://user-images.githubusercontent.com/67920563/89103579-d5b89400-d3e0-11ea-9c60-7a756afaf303.png)
 ![image](https://user-images.githubusercontent.com/67920563/89103598-e10bbf80-d3e0-11ea-8a85-f36239ae03fb.png)
 
- Looking at the loss graphs, we see that both have a very similar shape. The training loss decreases while the validation loss decreases until the first epoch, and then increases. Thus we can estimate that the model is becoming over fit after this point. Looking at the accuracy plots, we see a sharp increase in training accuracy until epoch one, and then begin to see the rate slow down. Matching that trend, the validation accuracy increases the most in the first epoch, and then levels off for the remainder of the runs. Thus, we can assume that both models are overfit.
