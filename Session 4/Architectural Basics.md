# **<u>ARCHITECTURAL BASICS</u>**

1. #### How many layers?

   ​	**YOUR WISH!** As long as the image is fully seen by the model, layers can be added. But this may affect accuracy as number of parameters will keep on increasing with increase in the number of layer. There are many types of layers which we see in detail and add to build our network.

   Generally you can make up how many ever layers you want by using 1x1; By using 3x3 you can 14 layers in place, or you can also maxpool and reduce the number of layers to half and still maintain the accuracy to a large extent

2. #### MaxPooling?

   ​	Max pooling is a sample-based discretization process. This down-samples an input representation (image, hidden-layer output matrix, etc.), reducing its dimensionality and allowing for assumptions to be made about features contained in the sub-regions binned.

   Max pooling is done by applying a *max filter* to (usually) non-overlapping sub regions of the initial representation.This is done to in part to help over-fitting by providing an abstracted form of the representation. As well, it reduces the computational cost by reducing the number of parameters to learn and provides basic translation invariance to the internal representation.

3. #### **1x1 Convolutions**

   ​	A 1x1 convolution simply maps an input pixel with all it's channels  to an output pixel, not looking at anything around itself. It is often  used to reduce the number of channels. It acts like coordinate-dependent transformation in the filter space

   ​	Although 1x1 convolution is a ‘feature pooling’ technique, there is more to it than just sum pooling of features across various channels/feature-maps of a given layer. 1x1 convolution acts like coordinate-dependent transformation in the filter space. Can be used while reducing the number of channels, before and after maxpooling.

4. #### 3x3 Convolutions

   This helps capture smaller, complex features in the image. Due to the larger number of layers, it learns complex, more non-linear features.Due to the lower number of weights, this is computationally efficient. Usually we prefer 3x3 layer/kernel as it adds lesser parameters, because of its efficiency. 

   The features that would be extracted will be highly local and may not have a more general overview of the image. This helps capture smaller, complex features in the image. Due to the larger number of layers, it learns complex, more non-linear features.Due to the lower number of weights, this is computationally efficient. 

5. #### Receptive Field

   The receptive field is defined as the **region in the input space that a particular CNN’s feature is looking at** (i.e. be affected by). A receptive field of a feature can be described by its **center location** and its **size**.

   The “effective receptive field” of a neuron is the area of the original image that can possibly influence the activations (output).Each neuron in a convolutional layer looks at a local region (including its depth) on the output volume of the previous layer. That local region is called Receptive Field. The receptive field must be ideally same as that of the image field size

6. #### SoftMax

   **Softmax** is implemented through a neural network **layer** just before the output **layer**. The **Softmax layer** must have the same number of nodes as the output **layer**.Used for multi-classification in logistic regression model. Used in the last layer.

7. #### Learning Rate

   Learning rate is a hyper-parameter that controls how much we are adjusting the weights of our network with respect the loss gradient.The lower the value, the slower we travel along the downward slope.

   ![](https://cdn-images-1.medium.com/max/1000/0*uIa_Dz3czXO5iWyI.)

8. #### Kernels and how do we decide the number of kernels?

   Kernels are used in convolutional layers to extract features. They basically are filters that you apply on a small region of the image. They are implemented as matrices, the kernel “moves” above the input data and at each step the dot product between the kernel and the subregion of the input matrix below it is calculated. 

   The ideal way of structuring number of kernels is to place less kernels in the beginning and, placing more number of kernels in the latter stages. The addition of number of kernels has to be seen as a matter of hardware compatibility. We want initial layers to learn simple features like edge detectors etc. There are a limited number of such features. Hence the low number of kernels in the beginning.

   Not all of those ways will be exhaustively needed, so a rough rule of thumb is to double the number of filters as you increase layers because the number of complex patterns will be exponentially more than number of simple patterns to learn.

9. #### Batch Normalization

   To increase the stability of a neural network, batch normalization normalizes the output of a previous activation layer by subtracting the batch mean and dividing by the batch standard deviation. We normalize the input layer by adjusting and scaling the activations. For example, when we have features from 0 to 1 and some from 1 to 1000, we should normalize them to speed up learning.It reduces overfitting because it has a slight regularization effects.

10. #### Image Normalization

    **Image normalization** is a process that changes the range of pixel intensity values.This is to ensure that the images have the same size and aspect ratio. We want all images to be in one range.

11. #### Position of MaxPooling, Position of Transition Layer, 

    It's ideal that we add maxpooling as a layer after edges and gradients start to form, which is at 11x11, so when the the actual edges and gradients start to form, we can cut down the unwanted computation to half and can be graphical processing of your system- complaint

12. #### Concept of Transition Layers, 

    Pooling layer will always reduce the size of each feature map by a factor of 2, e.g. each dimension is halved, reducing the number of pixels or values in each feature map to one quarter the size. Pooling helps to make the representation become approximately invariant to small translations of the input. Invariance to translation means that if we translate the input by a small amount, the values of most of the pooled outputs do not change.

14. #### Number of Epochs and when to increase them?

    As the number of epochs increases, more number of times the weight are changed in the neural network and the curve goes from **underfitting** to **optimal** to **overfitting** curve. So, what is the right numbers of epochs? Unfortunately,  there is no right answer to this question. The answer is different for different datasets but you can say that the numbers of epochs is related to how diverse your data is.

15. #### DropOut

    Dropout turns off neurons for training thus reducing overfitting and learning more.The term dropout refers to dropping out units (both hidden and visible) in a neural network.Dropout forces a neural network to learn more robust features that are useful in conjunction with many different random subsets of the other neurons. 

16. #### When do we introduce DropOut, or when do we know we have some overfitting?

    We introduce dropout when the network is learning very specific to training set and works badly on our testing data. One can know that the network is overfitting by looking at the gap between training and testing accuracy. Dropouts reduces this gap by turning off neurons while training. 

    

17. #### The distance of MaxPooling from Prediction

    When Maxpooling is used in the end, before leading it to softmax, will take the maximum of the previous layer. Because in the final prediction layer, we are supposed to retain information of all the convolution we have done in the previous layers. So, maxpooling is supposed to be 2-3 layers before the final prediction.

18. #### The distance of Batch Normalization from Prediction

    We don't want normalization of values before going to the final prediction layer, because the values are to be in the form of convolution output so that the prediction is done. 

19. #### When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

    We stop convolutions when we are near prediction layer. Using 3x3 convolutions will only pick middle one pixel with which we do not have information about other pixels. Where as if we use larger kernels, the last layer looks at more pixels and more information is required to make predictions.

20. #### How do we know our network is not going well, comparatively, very early?

    Generally we could add validation checks to the epochs while training the batches with so and so- epochs. By comparing the validation accuracy as to how it's increasing or decreasing, we can predict if it's going well or not

21. #### Batch Size, and effects of batch size

    In general, **batch size** of 32 is a good starting point, and you should also try with 64, 128, and 256. Other values (lower or higher) may be fine for some data sets, but the given range is generally the best to start experimenting with. Batch size is dependent on  *available GPU memory* and *trainable parameters*

22. #### When to add validation checks

    A simple way to detect this effect in practice is cross-validation. This attempts to examine the trained model with new data set to check it’s predictive accuracy. Given a dataset, some portion of this is held out (say 30%) while the rest is used in training the model. Upon training the model, the held out data is then used to check the accuracy compared to the accuracy of derived from the data used in training. A significant variance in these two flags overfitting.

23. #### LR schedule and concept behind it

    The simplest and perhaps most used adaptation of learning rate during training are techniques that reduce the learning rate over time. These have the benefit of making large changes at the beginning of the training procedure when larger learning rate values are used, and decreasing the learning rate such that a smaller rate and therefore smaller training updates are made to weights later in the training procedure.This has the effect of quickly learning good weights early and fine tuning them later.

    Two popular and easy to use learning rate schedules are as follows:

    * Decrease the learning rate gradually based on the epoch.
    * Decrease the learning rate using punctuated large drops at specific epochs.

24. #### Adam vs SGD

    **SGD** is a variant of gradient descent. Instead of performing computations on the whole dataset — which is redundant and inefficient — SGD only computes on a small subset or random selection of data examples. SGD produces the same performance as regular gradient descent when the learning rate is low. Whereas **Adam**  is derived from adaptive moment estimation. This method computes individual adaptive learning rates for different parameters from estimates of first and second moments of the gradients.














