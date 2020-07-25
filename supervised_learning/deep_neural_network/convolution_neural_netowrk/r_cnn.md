# R-CNN

First approach was to use a sliding window of different sizes, which will slide over the image and whichever box will find an object will be declared its bounding box.

But this is a very slow process and we will be looking at the same images mutiple times just with a bigger box each time.

To resolve this issue, the region proposal algorithm was built.

## Region Proposal

There are plenty region proposal algorithms which work without training them. 

The R-CNN used the selecting search method.

> R-CNN is agnostic to the region proposal method

This algorithm is used to get 2000 differet regions.



## CNN

These proposed regions are then fed to a CNN to represent the images in a smaller dimension. For this **AlexNet** was used. 

This issue here is that AlexNet is a pre-trained model