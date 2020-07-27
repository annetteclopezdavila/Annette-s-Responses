# Project 3: Population Estimation for the City of Accra

INSERT A COLLAGE OF PICTURES

## About the Data
For this project, we were given 10,000 images of a neighborhood in Accra, the capital of Ghana, and its corresponding populations in order to train a Neural Network that could estimate population from satellite images. 
Each image of the Korle Gonno neighborhood was equally sized and was of high resolution (~60 cm). 
Looking at the corresponding population counts from September 2005, we see that the minimum population count is 0, the maximum is 119.7171, and the average is 55.3722. 

INSERT BLUE HISTOGRAM

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
INSERT FIRST W STEP SIZE

## PHASE 3: Seeing the Light at Model 3
After some internet searching, I found a table that cleared up what the floating names in my head meant (not that I didn't know; the concepts I learn in ML tend to get tangled in my head). Below is the beautiful chart I found (I lost the source unfortunately). 

#INSERT CHART

From the chart, I was able to deduce several things I needed to know: I needed to find a float point since I needed to predict a population, the problem was some type of regression, and my loss function needed to be MSE!
Thus, I fixed my code and produced my best DNN model





Future:
analyze the problem before starting to code: what type of output do i need. how big is my data set

