# Video Background Extraction Using K-means

![](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/Demo.gif?raw=true)



## Introduction

Image segmentation is a common and crucial task in image processing. It consists of clustering the elements of an image into different groups. Although there are different ways of doing image segmentation, the most popular by far is k-means clustering. The main issue with using traditional k-means clustering for image segmentation is that it does not only affects the resolution of the image but it also completely neglects the background and makes it almost an impossible task to reconstruct it.

In this project, I provide you with the methodology necessary to reconstruct the background of a video (if the video meets certain assumptions) without having a significant negative impact on the quality of the image. After rebuilding the background, you'll be able to quickly isolate the foreground objects by subtracting the background from the rest of the video.



## Methodology

Removing the background from a video is a pretty trivial task when we have a known background. Unfortunately, there will be situations in which the background is unknown, and it has to be modeled using video data. The approach presented in this project is experimental and only works under particular assumptions, but when a video meets those assumptions, it yields satisfactory results.

**Assumptions:**

- Objects in the foreground are in motion
- Objects in the foreground are relatively small compared to the background
- The video has fixed lighting
- The camera is static



**Background Reconstruction**

The presented approach is based on the concept that each frame from a given video has partial information about the background. By analyzing enough frames, our model will eventually have enough information to reconstruct the background in its entirety. 



![pixel comparison2](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/pixel%20comparison2.gif?raw=true)



Other important concept in which this approach is based on the distribution of background and foreground pixels. Take a look at the previous image; The square on the left represents a background pixel with a relatively constant color with minimal variations in lighting and the right square represents a pixel with background and foreground information. By applying the k-means algorithm to pixel on the left with we get the following:



![background scatter](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/background%20scatter.gif?raw=true)

The points in the previous scatter plot are very close to each other because they all represent the same color with slight variations in lighting. If the k-means algorithm is applied to a pixel with foreground and background information, we get the following:

![background and foreground](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/background%20and%20foreground.gif?raw=true)

If all of the assumptions stated at the beginning are true, then it is safe to assume that the cluster with the greatest number of elements corresponds to the background. By taking the median of the background cluster, the background can be easily reconstructed without having to worry too much about outliers.

![Background](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/Background.png?raw=true)



**Background Removal**

Given an image I and a background B, the absolute difference can be calculated the following way:

![formulas1](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/formulas1.png?raw=true)

Breaking the previous expression into its color components, results in the following:

![formulas2](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/formulas2.png?raw=true)

Finally, combining the 3 previously mentioned expressions into a single one as a weighted average will yield a single black and white image that will be referred to as the mask.

![formulas3](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/formulas3.png?raw=true)

![formulas4](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/formulas4.png?raw=true)



![](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/Mask.png?raw=true)



**Foreground Extraction**

The foreground is extracted by using the mask from the previous section. The foreground is reconstructed based on the following criteria: if the absolute difference of a given pixel is greater than a predefined threshold, that means that such pixel is the foreground and it will be assigned the RGB value as the pixel from the original video in that same location. Otherwise, it will be considered part of the background and will be assigned the color black. 

![Foreground](https://github.com/fescobar96/Video-Background-Removal/blob/master/Images/Foreground.png?raw=true)



## Future Work

This project could be further improved by considering the following enhancements:

- Varying lighting
  - Experimenting with different values for K > 2 could yield better results than k=2 for videos with  significant variations in lighting.
- Moving camera
  - To deal with a moving camera, the presented methodology could be improved to keep track of the motion of the camera, then stabilize the video, apply the k-means background extraction algorithm, and then finally reintegrate the previously captured camera motion.



## References

1. Haralick, Robert M., and Linda G. Shapiro. "Image segmentation techniques." *Computer vision, graphics, and image processing* 29.1 (1985): 100-132.
2. Pal, Nikhil R., and Sankar K. Pal. "A review on image segmentation techniques." *Pattern recognition* 26.9 (1993): 1277-1294.
3. Chen, Qifeng, Dingzeyu Li, and Chi-Keung Tang. "KNN matting." *IEEE transactions on pattern analysis and machine intelligence* 35.9 (2013): 2175-2188.
4. Dhanachandra, Nameirakpam, Khumanthem Manglem, and Yambem Jina Chanu. "Image segmentation using K-means clustering algorithm and subtractive clustering algorithm." *Procedia Computer Science* 54 (2015): 764-771.
5. Zhang, Xiaopeng, et al. "Rain removal in video by combining temporal and chromatic properties." *2006 IEEE International Conference on Multimedia and Expo*. IEEE, 2006.
6. Wang, Jinghua, and Guoyan Zhang. "Video data mining based on K-Means algorithm for surveillance video." *2011 International Conference on Image Analysis and Signal Processing*. IEEE, 2011.