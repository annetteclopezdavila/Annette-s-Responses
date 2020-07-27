# Project 3: Population Estimation for the City of Accra

INSERT A COLLAGE OF PICTURES

## About the Data
For this project, we were given 10,000 images of a neighborhood in Accra, the capital of Ghana, and its corresponding populations in order to train a Neural Network that could estimate population from satellite images. 
Each image of the Korle Gonno neighborhood was equally sized and was of high resolution (~60 cm). 
Looking at the corresponding population counts from September 2005, we see that the minimum population count is 0, the maximum is 119.7171, and the average is 55.3722.

![image](https://user-images.githubusercontent.com/67920563/88500505-e909d080-cf96-11ea-9096-74517665d2e0.png)

Looking at the histogram, we see that almost 2,250 images have populations between 0 and 6.7, thus being the population range with the most pictures.
The other images are evenly spread amongst each population range, with a notable exception in the 13.4 to 20.1 population range.

## Phase 1: Organizing the Data and Creating the First Model
Now that we have an idea of what our data looks like, we can organize it in a fashion that will make the data more accessible. Every model needs a training and a test set. 
For my first model, I divided the training data and testing data equally. In order to save time and avoid RAM issues, I took the first 18 pictures and split it into two. 
I decided to first attempt Pycharm in order to create the first model. Using the method provided, I took out the for loop nested inside the train_imgs line (line 3 in code) 
in order to only run the first 9 images. My first model was truly terrible; I used every incorrect hyperparameter I could have. 
The model was so terrible that it crashed on anything bigger than 50 images. To be fair, when I first saw this assignment, I was in a panic.
My model was derived off of the one used for the fashion computer vision tensorflow exercise; I used a Sequential model with two Dense layers and one Flat layer. 
The two Dense layers had 128 neurons and 10 neurons respectively. Considering I was only using 9 images, this could have been a little computationally expensive. 
To accompany my terrible model, I chose Adam as my optimizer and sparse_categorical_crossentropy as my loss function. 
This loss function converts everything into a categorical format. Although it served its purpose for categorizing images into mutually exclusive fashion categories,
it was not the best choice for this dataset. The biggest mistake, however, was guaging the data on accuracy. The accuracy was so low, it was rounded to 0.
After trying to apply more images into this model, my computer crashed and RAM errors began to ensue. 

## Phase Two: Reorienting Myself and Creating Model 2
After a few tears of panic and many strange settings changes to my computer, I decided to scrap the entire model and Pycharm.
I began on my quest to find a way to process this project on Colab, since Jupyter Notebook and Pycharm both use outdated Python Versions and TensorFlow versions. 
Uploading data from my hard drive to colab was not working. Thus, I had to upload my data into google drive and later download it into Colab. 
Now that I was finally oriented, had a better understanding of the project, and had overcome the fear that I had to make my own DNN, I began on my second model.
Because managing files is a little different on Google Drive, I had to scrap my for loop and upload the seperate training and testing files with the amount of images I needed.
I split my first data set into 100 training images and 30 testing images. My second model had a few changes, but some conceptual errors.
I used a Sequential Model with one Flat layer and 3 Dense layers. My model contained 256 neurons in the first Dense layer, 128 in the second, and 1 in the third. I added a step size of 10 and a batch size of 5 and trained my model for 5 epochs.
I knew I had to change the loss function, yet I really wasn't sure which one to use yet. I was still a little disoriented, and chose binary_crossentropy loss function.
This loss function is used for binary multi-label classification. To this very hour, I am still not sure what came over me to choose that, since very obviously that was the wrong loss function.
This was not a binary problem; that loss function is better off for the cats vs dogs problem or the horse vs human NN. What we *were* looking for in this problem, were floats. To top it all off,
I still used the accuracy metric. Because I was getting a 0 in accuracy and losses of about 300, I decided that I needed to do some more research before blindly continuing.
Below is my output for the 2nd model. As seen, I had terrible results.

![image](https://user-images.githubusercontent.com/67920563/88500558-0343ae80-cf97-11ea-9b8e-be039e207e79.png)

## PHASE 3: Seeing the Light at Model 3
After some internet searching, I found a table that cleared up what the floating names in my head meant (not that I didn't know; the concepts I learn in ML tend to get tangled in my head). Below is the beautiful chart I found (I lost the source unfortunately). 

![image](https://user-images.githubusercontent.com/67920563/88500617-2bcba880-cf97-11ea-838c-a9d1c184794f.png)
From the chart, I was able to deduce several things I needed to know: I needed to find a float point since I needed to predict a population, the problem was some type of regression, and my loss function needed to be MSE!
Thus, I fixed my code and produced my best DNN model. Still using the 100:30 trianing/testing split, my first Sequential model had neuron layers of 128, 64, and 1. I changed my optimizer to RMSprop due to the fact that it can work a little better on bigger data sets. I changed my loss to mse, my metrics to 'mse', 'mae', and 'acc'. I ran 500 epochs and produced the following after an hour:

![image](https://user-images.githubusercontent.com/67920563/88500645-430a9600-cf97-11ea-8922-653fc5209263.png)
![image](https://user-images.githubusercontent.com/67920563/88500667-57e72980-cf97-11ea-9c42-ce83f37832cf.png)

From the tables, we see that the MSE began at ~680 and was reduced to ~556. Because the MSE, or Mean Squared Errors, and the losses should be as *low* as it can be, this meant that the model was still not optimal for this data. Because it was still decreasing, it seemed that perhaps the model was underfit. The validation were mostly in the thousands, the last being an MSE of 1398.6. Because the model was already at 500 epochs and was not reducing the losses quickly enough, a new model needed to be fit. As can be seen in the Mean Absolute Errors, the head of the data set shows a quick drop in the overal MAE in the first five epochs, but then continues to decrease at the same rate for the remainder of the epochs.

![image](https://user-images.githubusercontent.com/67920563/88500694-6b929000-cf97-11ea-9ed3-6e92f8d74591.png)

I decided to add one more Dense layer to the modell with 512 neurons. This took even longer, and only reduced the MSE to ~553. The MSE and MAE graphs for this last DNN are included below. 

![image](https://user-images.githubusercontent.com/67920563/88500722-806f2380-cf97-11ea-9854-5da5cc60ca97.png)
![image](https://user-images.githubusercontent.com/67920563/88500747-911f9980-cf97-11ea-800e-7f338af1a7a4.png)

## Phase 4: The Convolutional Networks
Because adding more neurons or more epochs would be too computationally expensive, I decided to move on to a convolutional neural network. My first CNN had 2 convolutions and used pooling. I set the neurons to 128 and 64, and designed my next three Dense layers to have two layers of 64 units and one of 1 unit. My optimizers and loss functions remained the same, and my epochs were set to 5. My first CNN seemed overfit; the MSE began around 800 and dropped to 750, but then peaked in the thousands. Overall, it seemed like the MSE was on an upward trend. The MAE graph shows a similar peak to the MAE, but never dropped after the first epoch. 

![image](https://user-images.githubusercontent.com/67920563/88500796-b6140c80-cf97-11ea-9214-5db7c7fb9fbc.png)
![image](https://user-images.githubusercontent.com/67920563/88500819-c6c48280-cf97-11ea-90c3-29ea053391c8.png)
Thus, this model was only increasing in error.

The second model I ran on the 100:30 training and testing split and had promisng results. I used one convolutional layer of 64 neurons and changed the epochs to 3. Everything else stayed the same. 

![image](https://user-images.githubusercontent.com/67920563/88500941-02f7e300-cf98-11ea-90bb-6f12857e8fba.png)

My MSE was 362 while my MAE was about ~15.  

![image](https://user-images.githubusercontent.com/67920563/88500979-1e62ee00-cf98-11ea-92a7-f938ecc2c1e9.png)

This was the best MSE out of all the models, and thus I ran it several times to see if it was consistent. Below are my MSE and MAE graphs.

![image](https://user-images.githubusercontent.com/67920563/88501033-45b9bb00-cf98-11ea-853e-40dddb44aa9f.png)
![image](https://user-images.githubusercontent.com/67920563/88501056-59652180-cf98-11ea-84d7-5a5f6aa61f38.png)

My validation loss was 73 and the MAE was 8.52. Thus, the validation results were not all that different than the previous models.

![image](https://user-images.githubusercontent.com/67920563/88501009-30dd2780-cf98-11ea-8c55-12978b441444.png)

## Conclusion
Because the CNN was my best model, I decided to run a training: test split of 1000:40. This produced an MSE of ~50. In my excitement, I closed out on the browser, and lost all my graphs and data before I saved it. I am currently running it again but am not sure if it will be ready before midnight due to the fact that it continues to crash. It could have been a soletary case, considering none of my previous models with smaller data sets were close to such a small MSE.
I decided to then try running a model with a 3000:30 split. Although my model would run through the majority of my training data, the session would crash due to a RAM error. Thus, I was only able to run it on 1040 images total. Overall, I do not feel like I did a very good job with minimizing the losses. Perhaps this was due to the fact that for the majority of the project, I was still figuring out how to write a better DNN. For the future, I plan to analyze the problem *before* starting to code. Although I expected my first model to immediately show me what I would need to fix, it would have saved many hours to figure out the type of problem, what type of output I needed, how big my data set was and which models worked best with those sizes, and troubleshoot future problems I could have. Had I initially thought that out, I would have avoided my many steps of catastrophe, and also worked on better solutions rather than just producing a model that sort of works. The image sizes were a problem. A little bit of preprocessing would have helped with that. Another thing I didn't even notice until I went to make a collage out of the pictures was that they were not cut to just the image. They had a white boarder that could have been discarded. Another thing I noticed when I went to make the collage is that perhaps I should have randomly chose the images, as they are all in order by particular area. Thus, I could have trained the model with a completely rural set and expected it to work in a more urban area. The images needed to be more randomized if I wasn't using the entire data set. Thirdly, I didn't change my activation functions in the model. I'm not sure if it would have affected it, but I didn't take it into consideration in the chaos. Lastly, due to the way I imported my pictures, I am not sure that the labels truly matched. When I was looking through the data sets on google drive, they were all mixed up. In the file they were in order, but when I printed them they were not. I only just realized that error, so that may have been a big part as to why my numbers were so high. Oh well. At least I won't be forgetting how to choose a loss function now.

