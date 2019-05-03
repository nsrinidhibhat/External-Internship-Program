# **Assignment 1A**

### **Edge detection**

Edge detection is the way to find the boundaries within the image. It's used for image segmentation and data processing, computer vision and machine learning, particularly to feature detection and feature extraction.

![img](https://cdn-images-1.medium.com/max/1500/1*4lPMjSPaS2JLWZAaYrXr2Q.jpeg)

As a machine learning engineer or an aspiring one, one needs to look at an image as a combination of horizontal edge, vertical edge and an angled or a curved edge; with which we can be able to give machine a knowledge to identify the edges to the maximum extent.

As a part of the 1st Assignment, 

![https://fontsarena-cd5e.kxcdn.com/wp-content/uploads/2019/04/helvetica-now-font-400x364.png](https://fontsarena-cd5e.kxcdn.com/wp-content/uploads/2019/04/helvetica-now-font-400x364.png)

We were given this image to be edge detected and there are various methods by which it can be solved. The popular techniques to solve this edge detection are  Sobel Edge Detection and Canny Edge Detection (according to our main search agent!)

**Canny Edge detection** is used as a part of the code, which almost accurately predicts all of the edges in the figure. It was  first created by John Canny for his Master’s thesis at MIT in 1983.

The algorithmic steps are as follows: 

- Convolve image with a Gaussian function to get smooth image 
- Apply first difference gradient operator to compute edge strength then edge magnitude and direction are obtain as before. 
- Apply non-maximal or critical suppression to the gradient magnitude.
-  Apply threshold to the non-maximal suppression image. 

I've tried to manipulate kernels matrix values to produce the *horizontal, vertical and angled edges.*

From my understanding, a kernel with negative numbers will tend to darken the image or will try to amplify the image which is not well lit. Whereas the positive  numbers will convolute with the image, resulting in amplifying the brightly lit areas.

If there is a gradient between the numbers, it will result in identification of the edges; provides a basis for edge detection!

**Horizontal Edge detection**

`kernelone = np.float32([[-2,-2,-2],[4,4,4],[-2,-2,-2]])`

**Vertical Edge detection**

`kernel = np.float32([[-2,4,-2],[-2,4,-2],[-2,4,-2]])`

**Angle edge detection**

`kerneltwo = np.float32([[-4,-4,8],[-4,8,-4],[8,-4,-4]])`

**Blur Kernel**

Blur kernel uses the value in fractions, so that after convolution, the pixel values are reduced to its fraction, making it a blurry image.

`kernelblur = np.float32([[0.11,0.11,0.11],[0.11,0.11,0.11],[0.11,0.11,0.11]])`

**Sharp Kernel**

Centre pixel is highlighted when compared to the other, making it obtain a sharpness when compared to its surrounding pixel.

`kernelsharp = np.float32([[-1,-1,-1],[-1,9,-1],[-1,-1,-1]])`

**Identity Kernel**

Produces a same image as the image itself, thus the name identity!

`kernelid = np.float32([[0,0,0],[0,1,0],[0,0,0]])`