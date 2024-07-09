## Image Masking and Post-Processing for Leaf Trait Extraction

### Overview

This project demonstrates an automated method for extracting and post-processing masks of a rectangular frame using techniques inspired by the paper "Automated Extraction of Phenotypic Leaf Traits of Individual Intact Herbarium Leaves from Herbarium Specimen Images Using Deep Learning Based Semantic Segmentation."

## Output

Here is the final output.

![alt text](https://github.com/MakrooOwais/SkyLine_Task/blob/main/output.jpg?raw=true)

### Requirements

- Python 3.x
- OpenCV
- NumPy
- Matplotlib
- SciPy
- scikit-image

### Installation

To install the required packages, run:
```bash
pip install opencv-python numpy matplotlib scipy scikit-image
```

### Working of the Code

1. **Loading the Image**:
   - The input image is loaded using `cv2.imread()`.

2. **Converting to HSV Color Space**:
   - The image is converted from BGR to HSV using `cv2.cvtColor()`. The HSV color space helps in effective color segmentation.

3. **Defining HSV Bounds**:
   - The lower and upper bounds for the HSV values are defined to create a mask for the desired color range.

4. **Creating the Mask**:
   - The `cv2.inRange()` function is used to create a binary mask based on the defined HSV bounds.

5. **Displaying the Mask and HSV Image**:
   - The mask and the HSV image are displayed side by side using Matplotlib.

6. **Applying Gaussian Blur**:
   - Gaussian blur is applied to the mask to smooth it using `cv2.GaussianBlur()`.

7. **Otsu's Thresholding**:
   - Otsu's thresholding is applied to convert the blurred mask to a binary image using `cv2.threshold()`.

8. **Filling Holes in the Mask**:
   - Holes in the binary mask are filled using `scipy.ndimage.binary_fill_holes()`.

9. **Dilating the Mask**:
   - The mask is dilated to enhance the regions using `cv2.dilate()`.

10. **Applying the Mask to the Original Image**:
    - The dilated mask is applied to the original image using `cv2.bitwise_and()`.

11. **Blurring and Grayscale Conversion**:
    - The masked image is blurred and converted to grayscale using `cv2.GaussianBlur()` and `cv2.cvtColor()`.

12. **Displaying Non-zero Regions**:
    - The non-zero regions of the blurred image are displayed.

13. **Filling Holes in the Mask from Blurred Image**:
    - Holes in the mask created from the blurred image are filled.

14. **Distance Transform and Peak Detection**:
    - Euclidean distance transform is computed using `scipy.ndimage.distance_transform_edt()`, and peaks are detected using `skimage.feature.peak_local_max()`.

15. **Watershed Segmentation**:
    - The watershed algorithm is applied for segmentation using `skimage.segmentation.watershed()`.

16. **Identifying the Largest Region**:
    - The largest segmented region is identified and displayed.

17. **Creating and Applying the Final Mask**:
    - A final mask for the largest region is created and applied to the original image, displaying the result.


