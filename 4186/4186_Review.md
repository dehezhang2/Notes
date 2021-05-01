# CS 4186 Computer Vision Review

[TOC]



## Exam Info

* Time: 18:30 - 20:30 05/May (20:45 for submission)

* Two monitoring device

* Open book, online

* Materials

  * Calculator
  * Books, notes (hard copy)

* Types of questions

  * Short answer question (2-3 sentences)
  * Calculations
  * 

* The first page with academic honesty should be submitted together with the answers, as you need to reaffirm the academic honesty policy. 

  Academic Honesty

   

  *I pledge that the answers in this examination are my own and that I will not seek or obtain an unfair advantage in producing these answers. Specifically,*

  * *I will not plagiarize (copy without citation) from any source;*
  * *I will not communicate or attempt to communicate with any other person during the examination; neither will I give or attempt to give assistance to another student taking the examination; and*
  * *I will use only approved devices (e.g., calculators) and/or approved device models.*
  * *I understand that any act of academic dishonesty can lead to disciplinary action.*

  *I pledge to follow the Rules on Academic Honesty and understand that violations may lead to severe penalties.*

  Student ID:  55199998

  Name: ZHANG Deheng

## Image Filtering

* Image: A grid of intensity values
* Linear Filter: 
* Cross-correlation
* Convolution
* Mean Filter / Box Filter
* Gaussian Filter
* Image Sharpening

## Edge Detection

* Image Derivatives
* Image Gradient (used in the SIFT detector)
* Sobel (smooth before derivative)
* Laplacian of Gaussian (LoG) => Zero crossing

## Image Sampling

* Gaussian Pyramid (sequence of blur and subsample)
* Image Upsampling
  * nearest neibor

## Color and Texture

* Histogram (no calculation in the exam)
* Edge-based Texture Measures
  * gradient magnitude
  * magnitude & direction histogram
* Local Binary Pattern Measure
  * 8-bit number
* Co-occurrence Matrix Features
  * spatial relationship d
  * co-occurrence matrix

## Corners and Blobs

* Harris corner detection
  * Harris matrix
  * eigenvalues analysis
  * property (invariance?)
    * Translation
    * rotation
    * affine intensity scaling => try in Gaussian Pyramid
* Blob detection
  * Application of LoG (maximum and minimum)

## Scale Invariance Feature Transform (Important)

* **Building scale-space**
  * Pick the peak
* Interest point detection
* **Orientation Assignment**
  * dominate direction (rotation invariant)
* **SIFT feature descriptor**
* SIFT distance calculator
  * L2 distance
  * Ratio distance

## Bag of Words

* The BoW representation
* TF-IDF weighting
  * TF-IDF
* Inverted File
  * Sparse histogram
  * Mapping from words to the document

## Transformation and Alignment

* Image Warping
  * Forward Warping (holes)
  * Inverse Warping (no holes)
* All 2D Linear Transformations
* Homogeneous Coordinates
* Affine Transformations
* RANSAC (no calculation)
  * Randomly choose s examples
  * fit a model 
  * count the number of inliners
  * repeat n times
  * choose the model with the most number of inliners

## Camera

* Pinhole camera
  * map scene point into the virtual image plane
* Camera parameters
  * world vs. camera coordinate
  * intrinsic (fixed for each cameras)
  * extrinsic (change the position of camera=> change)
    * rotation + translation
* Modeling projection

## Stereo Vision and Structure from Motion

* Depth and Disparity
* Epipolar Geometry (reduce searching scale)
* Stereo Matching
  * horizontal
  * matching cost
* Structure from motion: problem definition

## Optical Flow

* Assumptions in Lucas-Kanade method
* Lucas-Kanade Algorithm (brightness Constancy Equation)













