# Video Background Removal Using KNN

![](https://media.giphy.com/media/WpUkcV8dtrM3qoHFas/giphy.gif)



replace gif with github after making it public

## Introduction

talk about traditional image segmentation



## Methodology



Background removal with known (clean plate)  vs unknown background



**Assumptions:**

- Objects in the foreground are in motion
- Objects in the foreground are relatively small compared to the background
- The video has fixed lighting
- The camera is static



**Background Reconstruction**



**Background Removal**
$$
D(x,y) = |I(x,y) - B(x,y)|
$$
where d is blah blah blah

D is absolute difference between image and background

if we break the previous expression into its colors components, we get the following:
$$
\begin{align*}
{D}_{Red} (x,y) = |{I}_{Red}(x,y) - {B}_{Red}(x,y)| \\ \\
{D}_{Green} (x,y) = |{I}_{Green}(x,y) - {B}_{Green}(x,y)| \\ \\
{D}_{Blue} (x,y) = |{I}_{Blue}(x,y) - {B}_{Blue}(x,y)| \\
\end{align*}
$$
combine the 3 previously expressions into a single one as a weighted average.



**Foreground Extraction**





## Future Works





## References

1. Haralick, Robert M., and Linda G. Shapiro. "Image segmentation techniques." *Computer vision, graphics, and image processing* 29.1 (1985): 100-132.
2. Pal, Nikhil R., and Sankar K. Pal. "A review on image segmentation techniques." *Pattern recognition* 26.9 (1993): 1277-1294.
3. Chen, Qifeng, Dingzeyu Li, and Chi-Keung Tang. "KNN matting." *IEEE transactions on pattern analysis and machine intelligence* 35.9 (2013): 2175-2188.
4. Dhanachandra, Nameirakpam, Khumanthem Manglem, and Yambem Jina Chanu. "Image segmentation using K-means clustering algorithm and subtractive clustering algorithm." *Procedia Computer Science* 54 (2015): 764-771.
5. Zhang, Xiaopeng, et al. "Rain removal in video by combining temporal and chromatic properties." *2006 IEEE International Conference on Multimedia and Expo*. IEEE, 2006.
6. Wang, Jinghua, and Guoyan Zhang. "Video data mining based on K-Means algorithm for surveillance video." *2011 International Conference on Image Analysis and Signal Processing*. IEEE, 2011.