# **Assignment 1B**

1. What are Channels and Kernels (according to EVA)?

   **Kernels**:  Kernel is a feature extractor. A unit which tries to distinguish one feature from another. Suppose in a problem statement such as cats vs dogs, ( i.e., when you're teaching a machine to learn and distinguish features) you could choose a kernel to distinguish both based on *the structure of their nose/ mouth if your subject is a person*. Now this becomes a kernel for that particular feature. Collecting these distinguished features is the work of Kernels.

   ![Image result for kernel in neural network](https://i.stack.imgur.com/9Iu89.gif)

   Here the kernel is that 3x3 matrix with a set of numbers (orange matrix) and an activation function is levied upon the original matrix or the image - arithmetic operation, multiplication and then addition is done on the image and then the convolved matrix is obtained, thus feature from 5x5 image is extracted into a new 3x3 matrix.

   

   **Channels**: Collection of kernels. Collection of features.

   A channel in a TV, channelized to show news or sport or many other kinds of features that is adapted to the genre of content it's been showing. Similarly, after the feature extraction, many collection of features make up channels and are all provided to our model for it to mostly learn the entire feature set that exists.


   This image below is a normal color image, thought of as having RGB components.

     ![Image result for channels in CNN](https://user-images.githubusercontent.com/15133695/173181307-daa2f894-d49f-4587-b5e7-c330f6d9cfd9.png)


2. Why should we only (well mostly) use 3x3 Kernels?

   Mainly because of the following reasons- 

   - Smaller filter looks at very few pixels at a time hence it has small receptive field. Where as large filter will look at lot of pixels at once, hence it will have large receptive field
   - When we work with larger (greater than 3x3) filters we tend to search for only the predominant features and that tends to rule out the possibilities of smaller, yet an important one.
   - Takes a lot of processing but considers most of the features, which might be of use. 
   - Can't use 1x1 because it considers all the pixels and doesn't help lower the dimension of the image.



3. How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)

   We need to perform **100** iterations, with **99** 3x3 matrices as kernels,s

   199x199 |  197x197 |  195x195 |  193x193 |  191x191 |  189x189 |  187x187 |  185x185 |  183x183 |  181x181 |  179x179 |  177x177 |  175x175 |  173x173 |  171x171 |  169x169 |  167x167 |  165x165 |  163x163 |  161x161 |  159x159 |  157x157 |  155x155 |  153x153 |  151x151 |  149x149 |  147x147 |  145x145 |  143x143 |  141x141 |  139x139 |  137x137 |  135x135 |  133x133 |  131x131 |  129x129 |  127x127 |  125x125 |  123x123 |  121x121 |  119x119 |  117x117 |  115x115 |  113x113 |  111x111 |  109x109 |  107x107 |  105x105 |  103x103 |  101x101 |  99x99 |  97x97 |  95x95 |  93x93 |  91x91 |  89x89 |  87x87 |  85x85 |  83x83 |  81x81 |  79x79 |  77x77 |  75x75 |  73x73 |  71x71 |  69x69 |  67x67 |  65x65 |  63x63 |  61x61 |  59x59 |  57x57 |  55x55 |  53x53 |  51x51 |  49x49 |  47x47 |  45x45 |  43x43 |  41x41 |  39x39 |  37x37 |  35x35 |  33x33 |  31x31 |  29x29 |  27x27 |  25x25 |  23x23 |  21x21 |  19x19 |  17x17 |  15x15 |  13x13 |  11x11 |  9x9 |  7x7 |  5x5 |  3x3 |  1x1

   

