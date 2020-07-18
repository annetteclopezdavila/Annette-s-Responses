# Creating Some Art with Neural Style Transfer!
When I first saw this project, I was really excited because I love photography and photoshopping images! I had very few problems with running and altering the code for the first half, but it did crash my computer several times. I was only able to do this on google colab, but the kernel was really struggling and would often freeze. As soon as I got to the stretch goals, I began to get many strange Value Errors whenever I would change the image. Due to the waiting times, I was not able to continue trying to debug that part of the project. I think that my error was related to weights/step size.

![image](https://user-images.githubusercontent.com/67920563/87858147-d25ddc80-c8f9-11ea-9c08-2b96f0eb7e17.png)

## The First Image: The Northern Lights
The first image I chose was a beautiful image of the Northern Lights. I applied Wassily Kandinsky's Composition 7 onto the Northern Lights.

![image](https://user-images.githubusercontent.com/67920563/87855744-4f805600-c8e8-11ea-9de9-cef5c11c28c6.png)
![image](https://user-images.githubusercontent.com/67920563/87858309-fb32a180-c8fa-11ea-96aa-ac2a29c7a5cd.png)

This image did not perform well with the tranfer, as high levels of noise and frequency disrupted the tranquility of the image. The image on the left is at 15 epochs with a step size of 50 and weights of 30, while the image on the right is at 5 epochs with a step size of 1 and weights of 30:

![image](https://user-images.githubusercontent.com/67920563/87858233-6af45c80-c8fa-11ea-9fb9-be5eb5d10b3f.png)
![image](https://user-images.githubusercontent.com/67920563/87858270-b73f9c80-c8fa-11ea-8841-de3ce57e0c71.png)

As can be seen, a lot of the picture is lost in both of them. Because the picture was completely lost, I ran a frequency plot:

![image](https://user-images.githubusercontent.com/67920563/87858400-9e83b680-c8fb-11ea-82a9-d590413f662c.png)

I decided to try to make abstract art with the two. Setting 100 epochs with a step size of 100 and a weight of 30, I produced the following image:

![image](https://user-images.githubusercontent.com/67920563/87858358-49e03b80-c8fb-11ea-9993-1569ae593845.png)

Although quite pixelated, I really like the results. This model is very overfit; the epochs began to find edges within themselves! In retrospect, this image did not have as much detail as would fit with the transfer, and thus I moved on to better trials!

## The Second Image: Mountaineous Terrain
The second image I chose was of a lake with mountains in the background. I absolutely love this image; I would love to build a log cabin exactly where this was taken! The second image I chose was an abstract illustration.

![image](https://user-images.githubusercontent.com/67920563/87857086-f3baca80-c8f1-11ea-8faf-d3ee84e136a0.png)
![image](https://user-images.githubusercontent.com/67920563/87857091-fae1d880-c8f1-11ea-8938-2884ccd5b35c.png)

I was very afraid of the results after the last disaster, but the first few steps were very promising, as well as the image with high frequency:

![image](https://user-images.githubusercontent.com/67920563/87858483-3aadbd80-c8fc-11ea-9828-e87cd1bc9dfa.png)
![image](https://user-images.githubusercontent.com/67920563/87858541-95dfb000-c8fc-11ea-8516-c060241dffa1.png)

The final image at 12 epochs with a step size of 100 and weight of 30. Once again, the details got a little lost:

![image](https://user-images.githubusercontent.com/67920563/87858605-11416180-c8fd-11ea-80a8-684b115be086.png)

I decided to try to change the weights from the usual 30 to 1 and 50. There are slight differences:
![image](https://user-images.githubusercontent.com/67920563/87858620-3a61f200-c8fd-11ea-86dc-c195d8490d1c.png)
![image](https://user-images.githubusercontent.com/67920563/87858637-61202880-c8fd-11ea-9cac-491aea3e2e3f.png)

