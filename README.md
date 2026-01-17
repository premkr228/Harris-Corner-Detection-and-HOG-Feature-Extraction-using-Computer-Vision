# Harris Corner Detection and HOG Feature Extraction using Classical Computer Vision

1. Objective of the Project

The objective of this project is to understand and implement classical feature detection and feature extraction techniques used in computer vision. Specifically, the project focuses on the Harris Corner Detection algorithm for identifying interest points in images and the Histogram of Oriented Gradients (HOG) method for extracting structured gradient-based features. Both techniques are foundational methods widely used before the deep learning era and still remain relevant for understanding how visual features are constructed.

2. Image Loading and Preprocessing

The input image is loaded in grayscale format, as both Harris corner detection and HOG rely primarily on intensity variations rather than color information. Working in grayscale reduces computational complexity and makes gradient calculations more stable. The image is converted into a numerical array that allows pixel-level mathematical operations to be applied efficiently.

3. Gradient Computation using Sobel Operators

The first major step in Harris corner detection is computing image gradients in the horizontal and vertical directions. Sobel operators are used for this purpose because they combine differentiation and smoothing in a single operation. The horizontal gradient captures intensity changes along the x-axis, while the vertical gradient captures changes along the y-axis. These gradients form the basis for detecting local changes in intensity, which are essential for identifying corners.

4. Products of Image Derivatives

After computing the gradients, the squared gradients and cross-product terms are calculated. These values represent how intensity changes behave within a small neighborhood around each pixel. Specifically, the squared terms measure variation in individual directions, while the cross term captures how gradients in both directions interact. Together, these quantities are used to construct the structure tensor, which summarizes local image structure.

5. Gaussian Smoothing for Stability

Gaussian smoothing is applied to the gradient products to reduce noise and ensure that corner responses are computed over local neighborhoods rather than single pixels. This smoothing step improves robustness and prevents spurious corner detections caused by noise or isolated intensity variations. The size of the Gaussian kernel controls the scale at which corners are detected.

6. Harris Corner Response Calculation

Using the smoothed gradient products, the determinant and trace of the structure matrix are computed. These values correspond to the eigenvalues of the matrix, which represent intensity variation along different directions. The Harris response function combines these terms to produce a single scalar value for each pixel. High positive response values indicate strong corners, while low or negative values correspond to flat regions or edges.

7. Thresholding and Corner Detection

To identify actual corners, the Harris response image is thresholded relative to its maximum value. Pixels whose response exceeds the threshold are marked as corners. This step converts the continuous response map into a binary representation that highlights only the most significant interest points. The detected corners are then visualized either as white pixels or overlaid on the original image.

8. Interactive Parameter Exploration

An interactive implementation using sliders allows experimentation with key Harris parameters such as block size, Sobel kernel size, and the sensitivity constant k. Adjusting these parameters helps illustrate how corner detection behavior changes with scale and sensitivity. This interactive exploration provides valuable intuition about the trade-offs involved in feature detection.

9. Visualization of Corners on the Original Image

Detected corners are visualized by drawing colored markers on top of the original grayscale image. This makes it easy to visually verify whether the detected points correspond to meaningful image features such as corners of objects, intersections, or texture-rich regions. The visualization confirms that Harris corners tend to cluster around areas with strong two-dimensional intensity variation.

10. Mathematical Interpretation of Harris Detector

The Harris detector works by analyzing how intensity changes when a small window is shifted in different directions. If intensity changes significantly in both directions, the region is classified as a corner. If it changes in only one direction, it is an edge, and if it changes very little, it is a flat region. This interpretation explains why the detector is invariant to rotation and relatively robust to illumination changes.

11. Histogram of Oriented Gradients (HOG) Feature Extraction

In addition to corner detection, the project also implements Histogram of Oriented Gradients (HOG) for feature extraction. HOG captures the distribution of gradient orientations within localized regions of an image. This makes it especially useful for describing object shape and structure, which is why it has been widely used in tasks such as pedestrian detection.

12. HOG Feature Computation Process

The image is divided into small cells, and within each cell, a histogram of gradient orientations is computed. Neighboring cells are grouped into blocks and normalized to reduce the effects of illumination changes. The result is a feature vector that encodes local edge directions and magnitudes across the image.

13. HOG Visualization and Interpretation

The HOG visualization highlights dominant gradient directions by drawing oriented line segments within each cell. These visual patterns often resemble object contours and edges present in the original image. The visualization helps confirm that HOG captures meaningful structural information rather than raw pixel intensities.

14. Feature Vector Characteristics

The resulting HOG feature vector is high-dimensional and suitable for use in traditional machine learning models such as Support Vector Machines or Logistic Regression. The shape of the feature vector depends on the chosen cell size, block size, and image resolution. These parameters control the balance between spatial detail and computational cost.

15. Observations and Limitations

Harris corner detection performs well on images with strong geometric features but may struggle in low-texture regions. It is also sensitive to parameter choices and does not inherently provide scale invariance. HOG features are effective for capturing shape information but may lose fine texture details and are sensitive to significant geometric distortions.

16. Conclusion

This project demonstrates how classical computer vision techniques extract meaningful features from images using gradient-based analysis. Harris corner detection provides a reliable method for identifying interest points, while HOG offers a structured way to represent object shape and edge information. Together, these methods form an important foundation for understanding modern vision pipelines and highlight how much can be achieved without deep learning models.
