# cv-lab-6
gray level slicing

# CV Lab – Gray Level Slicing

## 1. Aim

To implement Gray Level Slicing using Python and OpenCV to enhance specific intensity ranges in a grayscale image and make important features more visible.

## 2. Software Used

- Google Colab
- Python
- OpenCV
- NumPy
- Matplotlib

## 3. Theory

Gray Level Slicing is an image enhancement technique used to highlight a specific range of gray levels in an image. It helps make important features more visible by emphasizing pixels within a selected intensity range.

**Concept:**

The technique defines a minimum and maximum intensity value. Pixels whose intensity values fall within this range are highlighted, while other pixels are either suppressed or preserved depending on the method used.

**Approaches:**

1. **Gray Level Slicing Without Background:** Pixels within the selected intensity range are set to white (255), and all other pixels are set to black (0). This creates a binary-like image that highlights the selected features.

2. **Gray Level Slicing With Background:** Pixels within the selected range are set to white (255), while pixels outside the range retain their original intensity values. This highlights the selected features while preserving the background information.

## 4. Input Image

The input image is read in grayscale format using OpenCV. Replace `input_image.jpg` in the code with the name of your image file.

<img width="515" height="388" alt="doraemon 2" src="https://github.com/user-attachments/assets/5a8a1a3e-a72f-4e6a-9221-faf4326a8c3b" />

<img width="335" height="597" alt="doraemon" src="https://github.com/user-attachments/assets/037ea393-a126-42e1-8f9f-ef5de697b09e" />


The original grayscale image is used to demonstrate both gray level slicing approaches.

## 5. Libraries Used

- **OpenCV (`cv2`):** Used to read the input image in grayscale format.
- **NumPy (`numpy`):** Used to create and manipulate image arrays.
- **Matplotlib (`pyplot`):** Used to display the original and processed images.

## 6. Algorithm

1. Import OpenCV, NumPy, and Matplotlib libraries.
2. Read the input image in grayscale format.
3. Get the number of rows and columns of the image.
4. Create an empty image for slicing without background.
5. Copy the original image for slicing with background.
6. Define the minimum and maximum intensity values as 100 and 150.
7. Check each pixel to determine whether its intensity lies within the selected range.
8. Set pixels within the range to white (255) in both output images.
9. Set pixels outside the range to black (0) in the image without background.
10. Preserve the original pixel values outside the range in the image with background.
11. Display the original image and both processed images.

## 7. Code

```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# Function to display images
def show_comparison(original, with_bg, without_bg):
    plt.figure(figsize=(15, 5))

    # Original Image
    plt.subplot(1, 3, 1)
    plt.imshow(original, cmap='gray')
    plt.title("Original Image")
    plt.axis('off')

    # Slicing Without Background
    plt.subplot(1, 3, 2)
    plt.imshow(without_bg, cmap='gray')
    plt.title("Slicing Without Background")
    plt.axis('off')

    # Slicing With Background
    plt.subplot(1, 3, 3)
    plt.imshow(with_bg, cmap='gray')
    plt.title("Slicing With Background")
    plt.axis('off')

    plt.tight_layout()
    plt.show()


# Load Image
img = cv2.imread('input_image.jpg', cv2.IMREAD_GRAYSCALE)

if img is None:
    print("Error: Image not found.")
else:
    # Get image dimensions
    rows, cols = img.shape

    # Create output images
    slice_without_bg = np.zeros((rows, cols), dtype=np.uint8)
    slice_with_bg = img.copy()

    # Define intensity range
    min_range = 100
    max_range = 150

    # Target value for highlighting
    L = 255

    # Gray Level Slicing
    for i in range(rows):
        for j in range(cols):
            pixel_val = img[i, j]

            if min_range <= pixel_val <= max_range:
                slice_without_bg[i, j] = L
                slice_with_bg[i, j] = L
            else:
                slice_without_bg[i, j] = 0
                slice_with_bg[i, j] = pixel_val

    # Display results
    show_comparison(img, slice_with_bg, slice_without_bg)
```

## 8. Output

The output displays three images:

<img width="1489" height="403" alt="doraemon 2 output" src="https://github.com/user-attachments/assets/5f51e8ad-c531-42e1-993e-1364efa24225" />

<img width="1177" height="490" alt="doraemon output" src="https://github.com/user-attachments/assets/2cdc4703-e6d2-47cd-a19f-f4596b93e498" />




The output demonstrates how gray level slicing enhances selected intensity ranges in an image.

## 9. Result

Gray Level Slicing was successfully implemented using Python, OpenCV, and NumPy. The selected intensity range from 100 to 150 was highlighted using two approaches: with background and without background.

## 10. Conclusion

Thus, Gray Level Slicing was implemented successfully to enhance specific intensity ranges in a grayscale image. The experiment demonstrated how selected features can be highlighted while either suppressing or preserving the background. This technique is useful in medical image analysis, industrial inspection, and other image enhancement applications.
