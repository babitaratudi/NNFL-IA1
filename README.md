# NNFL-IA1
1. Our topic is plant classification using Deep CNN, the objective of our project is that given an image of a leaf we need to classify to which species the leaf or the part belongs, it means that we are using a multiclass classification problem where we want to classify the given image into 44 different species of 44 different classes. 
2. So for that purpose, we have taken dataset D1 that consists of images where the entire leaf is seen in the image. 
3. For the implementation firstly we have imported all the required libraries i.e. OS to access images in the directories and as we are handling the images, so we have used the PIL library to obtain the NumPy equivalent for the images. 
4. As we are using Keras to implement our CNN architecture, we have also imported all the required layers for our module. 
5. Now the dataset we obtained consisted of 44 folders corresponding to the 44 different species of the plants, containing respective of their leaf images. 
6. Here we have looped over to access each image. Initially, the image size was 258*258 pixels, we have cropped them equally from all the sides to generate 228*228 pixels images, since we are using Alex Net, so we require 228*228 pixels images for the input. 
7. By using PIL we have converted the image into a NumPy array of size 228*228*3, 3 because we are using the RGB images, so we need 3 different channels for red, green, and blue. 
8. Then this we append to trainX and simultaneously we append a one-hot vector for the current image to trainY. 
9. So we got 2288 for training and similarly, we have converted images for testing and we got 528 images for testing. 
10. Now let us understand the model that we are implementing, it begins with convolution layers with 96 filters of size(11*11*3), 3 because we have to apply a filter over the 3 channels because of RGB image, with strides=4 which means the filter will shift on the image, horizontally and vertically by 4px. 
11. Then we have used the relu activation function because we don’t want our gradient to easily saturate to 0, also we want partial learning rates and another advantage of using relu is that it does not activate all the neurons at the same time because if the input is negative than the result is 0 that means no neuron gets activated and some neuron gets deactivated which may also increase computational speed for our model. 
12. Further, we have used kernel initializer to initialize weights for this layer with random values using the normal distribution, such that for any value the standard deviation is 0.01. 13. In each convolution layer, we have applied a filter and the length and width of the feature matrix reduce whereas height increase because in each filter outputs are 2D matrix and results of such matrix filters are stacked together so that the height of the feature matrix increases and becomes 96. 
14. Next in the max-pooling layer the filter size we have used is 3*3, this 3*3 filter will be applied across the feature map obtained from the previous layer and the max pooling operation will select the maximum element from the region of the feature map covered by the filter currently. 
15. Thus the output of the max-pooling layer will be the most prominent feature of the previous feature. 
16. Further, one convolution is applied with 256 filters of 5*5 also we added padding which will add a pixel border on the image such that the output size is equal to the input size. 
17. After some more convolution layers, we had used a dropout of 0.5 which will deactivate 50% of neurons which will save us from overfitting. 
18. Lastly, we got 44 neurons because we have 44 classes of plants.  
19. Then we had given batch_size 50 with 40 epoch we got validation accuracy.
