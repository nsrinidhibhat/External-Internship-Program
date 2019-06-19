

# **Assignment 7A**

The calculations for Receptive field is as follows- Here r out refers to the output receptive field. In consideration, the parameters required for the calculation of receptive field is just the kernel size and the jump. The jump parameter requires the stride parameter to be present.







![3](https://i0.wp.com/syncedreview.com/wp-content/uploads/2017/05/32.png?resize=372%2C171&ssl=1)



The table provided is to which the final RF has to be calculated.

**Kernel size (7x7) and stride (2)** is provided, as seen in the first row of 2nd column (patch size/stride)

In the **inception block,** it's evident from the **output size** column that it's only the number of channels that are varying, and can be attributed to 1x1x(channel size increase/decrease).

So, in the calculation inception block isn't considered as the number of channels is not the variation parameter for the receptive block.





The final receptive field as per the calculation mentioned below is found to be 267.






