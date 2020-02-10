#What is in the notebook?

In the notebook I recreated the neuronal network VGG-13. The goal is train a neuronal neutwork to classify the german traffic signs with an accuracy of at least 80%.

The images provided by the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset) were too small, so I make the preprocess to the images before making them bigger (resized) to be able to go through the network. The preprocess consist of conversion to gray scale and gaussian blur. Dilatation and erosion wasn't a good option, gaussian blur already eliminates noise for small images, applying dilatation and erosion may delete important information for some images resulting in a bad training. There is also a generator for the images, just to add some extra modifications like angle inclination and displacement.

For this network I just added batch normalization and changed the padding to same, so there is more information for the next layers.

There are two networks, the one previously described that I made and the second that is provided by keras. I this case I used VGG16 because it was the closest network to the one I used. With this second network I used fine tunning, freezing the first four groups of layers and training the lower parts of the network that I create (the dense part).

For the trainning I used two callbacks, one for stop the training if there was no change in the valdiation loss and another to save the best weights in the training. Also I just used 10 epochs per training, more may be useful for the first network since it wasn't stopped by the callback and reached a good percentage in accuracy. The second network was stopped in the ninth epoch, meaning that some modifications in the architecture are needed. 

The final part is testing with ten images I found on internet. These images went through the same preprocess and created a new generator to send the to the networks and get a prediction. After getting the prediction there is calculated the accuracy and printed the missclassified images, Also printing the top five most possible signs found by the network.

**Grade: 90**
