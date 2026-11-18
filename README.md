# Opening and Closing Operations Using OpenCV

## AIM

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

## SOFTWARE USED

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## ALGORITHM

**Step 1:** Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:** Create an input image using NumPy.

**Step 3:** Insert foreground objects, small white noise pixels, and black holes into the image.

**Step 4:** Display the original image.

**Step 5:** Create a structuring element (kernel) of suitable size.

**Step 6: Opening Operation**
- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving larger objects.
- Display the opened image.

**Step 7: Closing Operation**
- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

**Step 8:** Compare the original, opened, and closed images.

## PROGRAM DEVELOPED BY

**Name:** Varun A

**Register No:** 212224240178

## PROGRAM

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Create a blank image
image = np.zeros((400, 600), dtype=np.uint8)

# Add white foreground objects
cv2.rectangle(image, (100, 100), (300, 300), 255, -1)
cv2.circle(image, (430, 200), 100, 255, -1)

# Add small white noise pixels
cv2.circle(image, (50, 50), 2, 255, -1)
cv2.circle(image, (350, 50), 2, 255, -1)
cv2.circle(image, (550, 350), 2, 255, -1)
cv2.circle(image, (50, 350), 2, 255, -1)

# Add small black holes
cv2.circle(image, (150, 150), 3, 0, -1)
cv2.circle(image, (250, 250), 3, 0, -1)
cv2.circle(image, (430, 200), 4, 0, -1)

# Display original image
plt.figure(figsize=(8, 5))
plt.imshow(image, cmap='gray')
plt.title('Original Image')
plt.axis('off')
plt.show()

# Create structuring element
kernel = np.ones((5, 5), np.uint8)

# Perform Opening
opening = cv2.morphologyEx(
    image,
    cv2.MORPH_OPEN,
    kernel
)

# Display Opening result
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.imshow(image, cmap='gray')
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(opening, cmap='gray')
plt.title('Opening Operation')
plt.axis('off')

plt.show()

# Perform Closing
closing = cv2.morphologyEx(
    image,
    cv2.MORPH_CLOSE,
    kernel
)

# Display Closing result
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.imshow(image, cmap='gray')
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(closing, cmap='gray')
plt.title('Closing Operation')
plt.axis('off')

plt.show()

# Compare all operations
plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(image, cmap='gray')
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(opening, cmap='gray')
plt.title('Opening Operation')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(closing, cmap='gray')
plt.title('Closing Operation')
plt.axis('off')

plt.tight_layout()
plt.show()
```

## OUTPUT

### 1. Original Image

<img width="602" height="375" alt="image" src="https://github.com/user-attachments/assets/756d03f9-4ab3-45d7-a62e-ca5cf181a9c1" />


### 2. Opening Operation

<img width="867" height="278" alt="image" src="https://github.com/user-attachments/assets/c88859dd-cb23-4839-93e8-7b5fefdff548" />


### 3. Closing Operation

<img width="891" height="280" alt="image" src="https://github.com/user-attachments/assets/912bb60d-dc64-42cd-bee0-75f75ad57ab4" />


### 4. Comparison

<img width="1457" height="308" alt="image" src="https://github.com/user-attachments/assets/ce197da7-4efa-4577-b326-10a2c8a997cc" />


## APPLICATIONS

### Opening
- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing
- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## ADVANTAGES

### Opening
- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing
- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## RESULT

Thus, the morphological operations Opening and Closing are successfully implemented using OpenCV.
