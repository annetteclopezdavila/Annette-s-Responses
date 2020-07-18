### July 14th, 2020 

**Question 1:** Last week you did an exercise where you manually applied a 3x3 array as a ﬁlter to an image of two people ascending an outdoor staircase.  Modify the existing ﬁlter and if needed the associated weight in order to apply your new ﬁlters to the image 3 times.  Plot each result, upload them to your response, and describe how each ﬁlter transformed the existing image as it convolved through the original array and reduced the object size.  What are you functionally accomplishing as you apply the ﬁlter to your original array (see the following snippet for reference)?  Why is the application of a convolving ﬁlter to an image useful for computer vision?  

  - Convolutions are layers added to a neural network that process images, aide in classification, and add a filter. This improves the performance of the model, as it can increase accuracy of its predictions. In other words, we are filtering specific characteristics in order to look at the data in the image that is necessary. What is a convolution doing? Looking deeper into what is actually occurring, we notice that convolutions are performing linear transformations on the image. A singular pixel is multiplied with a matrix of integers, or the filter. This is all added together to produce one value. The convolution will scan each input value and apply the filter to the pixel’s neighbors. However, this leaves a problem for pixels with no neighbors. Those pixels are then lost, and thus our image may become 26x26.

  - Image One:

    - Filter Applied: [ [5, -3, 0], [1, 5, 1], [0, 1, 10]]

    - Although the filter applied was meant to detect edges, our values may have overblown the exposure, thus wiping out a lot of the edges. This filter would probably not be very effective for edge detection.

   - Image Two:
	   - Filter Applied: [ [-1, 2, -1], [0, -4, 0], [1, 2, 1]]
	   - This filter detected vertical lines. The filter eliminated the noise of the horizontal lines, thus making the picture look almost unrecognizable. However, it could be effective for vertical edges.

  - Image Three:

    - Filter Applied:   [ [-1, -150, 1], [-2, 0, 2], [-1, 150, 1]] 

    - This filter detected every edge it could detect. Due to the nature of photography, every image has some added noise. The filter seemed to have detected this noise and miscategorized it. For example, we know the sky in the original does not have any lines. However, we can clearly see that horizontal lines were detected by the filter. This filter would be good for capturing detail, but could add a lot of unnecessary data to the neural network. Thus, it may not be the most effective filter. 

**Question 2:** Another useful method is pooling.  Apply a 2x2 ﬁlter to one of your convolved images, and plot the result.  In eﬀect what have you accomplished by applying this ﬁlter?  Can you determine from the code which type of pooling ﬁlter is applied, and the method for selecting a pixel value (see the following snippet)?  Did the result increase in size or decrease?  Why would this method be method?  Stretch goal:  again, instead of using misc.ascent(), apply the pooling ﬁlter to one of your transformed images.

  -	Pooling refers to a process which reduces the dimensionality of an input in order to increase accuracy and efficiency.  In more simpler terms, pooling reduces the amount of data that must be processed in a neural network while maintaining the feature detection. This is done by combining the output of a cluster of pixels into a smaller unit. There are many methods of downsampling; more specifically, we will be looking at max pooling. Max pooling applies a max filter to the cluster of pixels. The filter will take the max value of the cluster and create a new matrix with those max values. Thus, we have a reduced image (1/4 size of original) that reduces the chances of overfitting a model and optimizes computational costs.

  -	At first glance, the pooled image may not seem very different. Looking closer, we can see that the corresponding features were enhanced. Because of the decrease in size, we should be able to see a more blurry/distorted image when zooming in comparatively. *Disclaimer: Because both images were copied and resized, such differences may not be noticeable from the presented image*

**Question 3:**  The lecture for today (Coding with Convolutional Neural Network) compared the application of our previously speciﬁed deep neural network with a newly speciﬁed convolutional neural network.  Instead of using the fashion_MNIST dataset, use the mnist dataset (the hand written letters) to train and compare your DNN and CNN output. Were you able to improve your model by adding the Conv2D and MaxPooling2D layers to your neural network?  Plot the convolutions graphically, include them in your response and describe them.  Edit the convolutions be changing the 32s to either 16 or 64 and describe what impact this had on accuracy and training time.  What happens if you add more convolution layers?

  -	At ten epochs:

    - 32 Filters: Training Accuracy: 99.88%, Validation Accuracy: 98.80%

    - 16 Filters: Training Accuracy: 99.86%, Validation Accuracy: 98.49%

    - 64 Filters: Training Accuracy: 99.89%, Validation Accuracy: 98.95%

    - 3 Convolution Layers at 64 Filters: Training Accuracy: 99.52%, Validation Accuracy: 98.64%

    - DNN: Training Accuracy: 99.64%, Validation Accuracy: 97.97%

	- In the example, CNN with 1 layer of convolutions worked better than DNN. This was expected, as CNNs are very effective and efficient on images. The convolutions allowed the neural network to use feature learning, which offers many benefits in image recognition tasks.  

  - Between the CNN output, the neural network with 64 filters worked best. This shows that the task was more complex and thus required a higher number of filters to optimize accuracy. Running it at 512 filters resulted in a lower accuracy (99.86%). Thus, although it was better at 64 filters, too many filters can overfit the data.

  - Adding more convolution layers decreased the accuracy. This perhaps can be explained by overfitting of the data. Since it is a relatively small data set, such a high number of convolution layers was unnecessary.

	

	
