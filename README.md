# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
### Step 1:
Load the necessary packages.

### Step 2:
Read the Image and convert to grayscale.

### Step 3:
Use Global thresholding to segment the image.

### Step 4:
Use Adaptive thresholding to segment the image.

### Step 5:
Use Otsu's method to segment the image.

### Step 6:
Display the results.

## Program
```
# Load the necessary packages
import numpy as np
import matplotlib.pyplot as plt
import cv2

# Read the Image and convert to grayscale
image = cv2.imread("mashabear.jpg",1)
image = cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
image_gray = cv2.imread("mashabear.jpg",0)

# Use Global thresholding to segment the image
ret,thresh_img1=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY)
ret,thresh_img2=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY_INV)
ret,thresh_img3=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO)
ret,thresh_img4=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO_INV)
ret,thresh_img5=cv2.threshold(image_gray,100,255,cv2.THRESH_TRUNC)

# Use Adaptive thresholding to segment the image
thresh_img7=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
thresh_img8=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Use Otsu's method to segment the image 
ret,thresh_img6=cv2.threshold(image_gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results
titles=["Gray Image","Threshold Image (Binary)","Threshold Image (Binary Inverse)","Threshold Image (To Zero)"
       ,"Threshold Image (To Zero-Inverse)","Threshold Image (Truncate)","Otsu","Adaptive Threshold (Mean)","Adaptive Threshold (Gaussian)"]
images=[image_gray,thresh_img1,thresh_img2,thresh_img3,thresh_img4,thresh_img5,thresh_img6,thresh_img7,thresh_img8]
for i in range(0,9):
    plt.figure(figsize=(10,10))
    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1,2,2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()
```

## Output

### Original Image
![image](https://user-images.githubusercontent.com/93427923/170813704-b30e77c8-c48d-4e27-b71c-5895942ae738.png)

### Global Thresholding
![image](https://user-images.githubusercontent.com/93427923/170813762-783f56f8-f1b1-4fb9-bfc0-a47c9b64136c.png)
![image](https://user-images.githubusercontent.com/93427923/170813805-4220243c-eb12-4c94-9264-0adda72afde8.png)
![image](https://user-images.githubusercontent.com/93427923/170813814-923c9aa6-f072-4192-97c3-adeb9f6fe4ee.png)
![image](https://user-images.githubusercontent.com/93427923/170813825-5ebea5eb-87c8-4d45-b4ff-ea4de30c0cf6.png)
![image](https://user-images.githubusercontent.com/93427923/170813833-314bad77-38c5-40e0-9a06-d9b71f468da3.png)

### Adaptive Thresholding
![image](https://user-images.githubusercontent.com/93427923/170813859-70e32fd0-da93-4486-b679-b4a155acb2b1.png)

### Optimum Global Thesholding using Otsu's Method
![image](https://user-images.githubusercontent.com/93427923/170813879-7f0bc40e-64fc-41c5-8848-34ceddb81f6e.png)

## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

