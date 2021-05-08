# horizon_finding
Finding horizon on images and rotating them accordingly.

## Why?
This project is my baby. I did it for the Image Processing course (last semester of my Bachelor's at AGH), and somehow I became very invested in it.
I know it's far from perfect, but I'm working on it.

## Giving credit where it's due
Initially, I was very lost on what to do. I had a vague idea of using the Hough transform to find lines, which was later confirmed to be a viable approach [on this stackoverflow post](https://stackoverflow.com/questions/4705837/horizon-detection-algorithm). Both of the articles mentioned there ([1](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.16.6951), [2](http://eprints.qut.edu.au/12839/1/3067a485.pdf)) were great sources of inspiration as well.

[This article on detecting horizon on marine images](https://doi.org/10.1007/s00773-017-0464-8) was also used as a basis for this little program.

I looked at many other sources, but they were a bit too fancy for what I was trying to do (and capable of doing in what time I had...).

## The algorithm
I definitely have to describe this more in depth, but here's what happens in the nutshell:
1. Changing to grayscale
2. Strong Gaussian blur
3. Binarizing with Otsu's method for tresholding
4. Canny edge detection
5. Hough transform - finding lines
6. For every line:
    1. Rotating the image
    2. Cutting the image into two parts based on the found line
    3. Subtracting mean of pixel values of one cut from the mean of the other's
7. Choosing the line with the greatest difference between the means

Since this was written as a Uni assignment, I plot all sorts of intermediate results. Getting rid of that might speed up the program.

## What I plan to fix
The performance is really bad (as in, it is sloooow). Also, while it was convenient for me to get the input images from my Google Drive, now that I'm putting this up, I'll need to change the method to local upload. Most of all - even in the images I tested it on, you can see that the horizon is not always marked correctly at all and the rotation is kinda fishy... It was actually the thing that gave me the most trouble overall, rotating the images. I am not looking forward to correcting that.

## How to test this
Please don't.



Okay... I only said that because of all the things I have to fix. For now, I get the image from my Drive, so follow the link on top of [the code](horizon_finding.ipynb) to Google Colab (what a wonderful tool!) and running the code there should let you test this program on my carefully pre-selected images :)
