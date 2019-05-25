# **<u>ARCHITECTURAL BASICS</u>**

How many layers, 

MaxPooling, 

1x1 Convolutions, 

3x3 Convolutions, 

Receptive Field, 

SoftMax, 

Learning Rate, 

Kernels and how do we decide the number of kernels?

Batch Normalization, 

Image Normalization, 

Position of MaxPooling, 

Concept of Transition Layers, 

Position of Transition Layer, 

Number of Epochs and when to increase them, 

DropOut

When do we introduce DropOut, or when do we know we have some overfitting

The distance of MaxPooling from Prediction, 

The distance of Batch Normalization from Prediction, 

When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

How do we know our network is not going well, comparatively, very early

Batch Size, and effects of batch size

When to add validation checks

LR schedule and concept behind it

Adam vs SGD



- [ ] 1. Generally you can make up how many ever layers you want by using 1x1; By using 3x3 you can 14 layers in place, or you can also maxpool and reduce the number of layers to half and still maintain the accuracy to a large extent

- [ ] 2. Max pooling is done by applying a *max filter* to (usually) non-overlapping sub regions of the initial representation.This is done to in part to help over-fitting by providing an abstracted form of the representation. As well, it reduces the computational cost by reducing the number of parameters to learn and provides basic translation invariance to the internal representation.

- [ ] 3. Although 1x1 convolution is a ‘feature pooling’ technique, there is more to it than just sum pooling of features across various channels/feature-maps of a given layer. 1x1 convolution acts like coordinate-dependent transformation in the filter space. Can be used while reducing the number of channels, before and after maxpooling.

- [ ] 1. 3x3- The features that would be extracted will be highly local and may not have a more general overview of the image. This helps capture smaller, complex features in the image. Due to the larger number of layers, it learns complex, more non-linear features.Due to the lower number of weights, this is computationally efficient. 

  2. . The “effective receptive field” of a neuron is the area of the original image that can possibly influence the activations (output).Each neuron in a convolutional layer looks at a local region (including its depth) on the output volume of the previous layer. That local region is called Receptive Field. The receptive field must be ideally same as that of the image field size

  3. Softmax is a function that takes as input a vector of K real numbers, and normalizes it into a probability distribution consisting of K probabilities. The standard (unit) softmax function ![{\displaystyle \sigma :\mathbb {R} ^{K}\to \mathbb {R} ^{K}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bb6dcacfc9ca0838f84aeba1bab2699b711e434f)

     is defined by the formula: 

     ![{\displaystyle \sigma (\mathbf {z} )_{i}={\frac {e^{z_{i}}}{\sum _{j=1}^{K}e^{z_{j}}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/02a859ba32ab892a2cdbfdafcd5a8f56e49e3d1c) 

      for *i* = 1, …, *K*   and ![{\displaystyle \mathbf {z} =(z_{1},\ldots ,z_{K})\in \mathbb {R} ^{K}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/493163e807bd591adc504a5cb1352f73b665bd25)

     The input to the softmax should be in the form of positive for when the activation fires for the previous layers, and negative for when the activation doesn’t fire( or in other words, the activation hasn’t detected the object in the frame or kernel). Suppose a RELU activation is added before the softmax, it’ll try to diminish the gap between the positive and negative numbers and softmax ( which in layman terms, widens the gap between
     the positive and negative numbers) can’t act upon the lesser difference between both the signed numbers, and thus can’t produce a higher accuracy.

     

     - **Learning rate**- Deep learning neural networks are trained using the stochastic gradient descent algorithm.

       Stochastic gradient descent is an optimization algorithm that estimates the error gradient for the current state of the model using examples from the training dataset, then updates the weights of the model using the back-propagation of errors algorithm, referred to as simply backpropagation.

       The amount that the weights are updated during training is referred to as the step size or the learning rate. 

       The learning rate hyperparameter controls the rate or speed at which the model learns. Specifically, it controls the amount of apportioned error that the weights of the model are updated with each time they are updated, such as at the end of each batch of training examples.

       Given a perfectly configured learning rate, the model will learn to best approximate the function given available resources (the number of layers and the number of nodes per layer) in a given number of training epochs (passes through the training data). Learning rate can be configured to be slowed down once the highest accuracy, or the minimum error point is about to be reached in the gradient graph.

     - **Kernel**

       Kernels are used in convolutional layers to extract features. They basically are filters that you apply on a small region of the image. They are implemented as matrices, the kernel “moves” above the input data and at each step the dot product between the kernel and the subregion of the input matrix below it is calculated. 

       The ideal way of structuring number of kernels is to place less kernels in the beginning and, placing more number of kernels in the latter stages. 

       The addition of number of kernels has to be seen as a matter of hardware compatibility.

        

       We want initial layers to learn simple features like edge detectors etc. There are a limited number of such features. Hence the low number of kernels in the beginning.

        

       Each of the filters in the previous layers can be combined in exponential number of ways to detect complex patterns.

        

       Not all of those ways will be exhaustively needed, so a rough rule of thumb is to double the number of filters as you increase layers because the number of complex patterns will be exponentially more than number of simple patterns to learn.

     - **Batch Normalization**

        To increase the stability of a neural network, batch normalization normalizes the output of a previous activation layer by subtracting the batch mean and dividing by the batch standard deviation.

       We normalize the input layer by adjusting and scaling the activations. For example, when we have features from 0 to 1 and some from 1 to 1000, we should normalize them to speed up learning. If the input layer is benefiting from it, why not do the same thing also for the values in the hidden layers, that are changing all the time, and get 10 times or more
       improvement in the training speed.

       It reduces overfitting because it has a slight regularization effects.

       We can use higher learning rates because batch normalization makes sure that there’s no activation that’s gone really high or really low.

       

       **Number of Epochs and when to increase them,** 

       **DropOut**

       **When do we introduce DropOut, or when do we know we have some overfitting**

       

       As the number of epochs increases, more number of times the weight are changed in the neural network and the curve goes from **underfitting** to **optimal** to **overfitting** curve. So, what is the right numbers of epochs? Unfortunately,  there is no right answer to this question. The answer is different for  different datasets but you can say that the numbers of epochs is related  to how diverse your data is.

       

       **Batch size:** In general, **batch size** 
       of 32 is a good starting point, and you should also try with 64, 128, 
       and 256. Other values (lower or higher) may be fine for some data sets, 
       but the given range is generally the best to start experimenting with. 

       Batch size is dependent on  *available GPU memory* and *trainable parameters*

       **Dropouts**:

       The term dropout refers to dropping out units (both hidden and visible) in a neural network.

       Dropout forces a neural network to learn more robust features that are 
       useful in conjunction with many different random subsets of the other 
       neurons.

        **The answer to why we use dropouts  is “to prevent over-fitting”.**

       A  fully connected layer occupies most of the parameters, and hence,  neurons develop co-dependency amongst each other during training which  curbs the individual power of each neuron leading to over-fitting of  training data.

       

       **SGD** is a variant of gradient descent. Instead of performing computations
       on the whole dataset — which is redundant and inefficient — SGD only 
       computes on a small subset or random selection of data examples. SGD 
       produces the same performance as regular gradient descent when the 
       learning rate is low.

       **Adam** Adam is derived from adaptive moment estimation. This method computes individual adaptive learning rates for different 
       parameters from estimates of first and second moments of the gradients.

       -> Straightforward to implement.

       -> Computationally efficient.

       -> 	Little memory requirements.

       

     

     

     


