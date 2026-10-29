# Histogram Equalization Using OpenCV (Grayscale & Color Images)

# Aim
To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

Read and display a grayscale image
Plot histogram of the grayscale image
Apply histogram equalization on grayscale image
Read and display a color image
Plot histogram of B, G, R channels
Convert image to HSV color space
Apply histogram equalization on the Value (V) channel
Convert the enhanced image back to BGR format
Display original and enhanced images with histograms
Software Used
Anaconda – Python 3.7
Jupyter Notebook / VS Code
OpenCV (cv2)
NumPy
Matplotlib

# Algorithm
Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the image parrot.jpg in grayscale format.

Step 3:
Display the grayscale image and plot its histogram.

Step 4:
Apply histogram equalization using cv2.equalizeHist() to enhance contrast.

Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

Step 6:
Read the same image in color format.

Step 7:
Split the image into B, G, R channels and plot their histograms.

Step 8:
Convert the image from BGR to HSV color space.

Step 9:
Apply histogram equalization on the V (Value) channel.

Step 10:
Merge the channels and convert the image back to BGR format.

Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

# Program
Developed By:
Name: Yuuvasri R

Register No: 212225230313
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# 1. Grayscale Image Histogram Equalization
img = cv2.imread('grayscale.jpg', cv2.IMREAD_GRAYSCALE)

if img is None:
    print("Error: Could not load grayscale.jpg")
else:
    # Display original grayscale image
    plt.figure(figsize=(12, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img, cmap='gray')
    plt.title('Original Grayscale Image')
    plt.axis('off')

    # Display original histogram
    plt.subplot(1, 2, 2)
    plt.hist(img.ravel(), bins=256, range=[0, 256])
    plt.title('Original Histogram')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.tight_layout()
    plt.show()

    # Apply histogram equalization
    img_eq = cv2.equalizeHist(img)

    # Display equalized image and histogram
    plt.figure(figsize=(12, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img_eq, cmap='gray')
    plt.title('Equalized Grayscale Image')
    plt.axis('off')

    plt.subplot(1, 2, 2)
    plt.hist(img_eq.ravel(), bins=256, range=[0, 256])
    plt.title('Equalized Histogram')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.tight_layout()
    plt.show()


# 2. Color Image Histogram Equalization
img = cv2.imread('rose.png', cv2.IMREAD_COLOR)

if img is None:
    print("Error: Could not load parrot.jpg")
else:
    # Convert BGR to HSV
    img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

    # Equalize the brightness channel (V)
    img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

    # Convert HSV back to BGR
    img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)

    # Display images and their histograms on one page
    plt.figure(figsize=(12, 10))

    plt.subplot(2, 2, 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title('Original Color Image')
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.imshow(cv2.cvtColor(img_eq, cv2.COLOR_BGR2RGB))
    plt.title('Equalized Color Image')
    plt.axis('off')

    plt.subplot(2, 2, 3)
    plt.hist(img.ravel(), bins=256, range=[0, 256])
    plt.title('Original Image Histogram')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.subplot(2, 2, 4)
    plt.hist(img_eq.ravel(), bins=256, range=[0, 256])
    plt.title('Equalized Image Histogram')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.tight_layout()
    plt.show()
```
# OUTPUT:

<img width="1130" height="472" alt="Screenshot 2026-10-29 141001" src="https://github.com/user-attachments/assets/902429f0-c05c-491a-a7c7-6c7b99009f2b" />
<img width="1173" height="481" alt="Screenshot 2026-10-29 141011" src="https://github.com/user-attachments/assets/368aeda4-e91e-46e8-a67f-0b7251007722" />
<img width="1088" height="427" alt="Screenshot 2026-10-29 141024" src="https://github.com/user-attachments/assets/a389c73e-7253-4a9a-abc4-d3c16c52c4e1" />
<img width="1157" height="478" alt="Screenshot 2026-10-29 141035" src="https://github.com/user-attachments/assets/212370da-d594-4593-9274-0a36485ab4c7" />

# Grayscale Histogram Equalization
Original grayscale image is displayed

Histogram of original grayscale image is plotted

Enhanced image after histogram equalization is displayed

Histogram of enhanced grayscale image shows improved contrast

# Color Image Histogram Equalization

Original color image is displayed

Histogram of B, G, R channels is plotted

Enhanced image after HSV-based equalization is displayed

Histogram of enhanced image shows better intensity distribution

# Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
