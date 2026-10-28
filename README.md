# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program
### Step 1
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
### Step 2
```
img = cv2.imread('butterfly.jpg')

img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img)
plt.title('Original Image')
plt.axis('off')
plt.show()
```
### Step 3
```
rows, cols = img.shape[:2]

M = np.float32([[1, 0, 50],
                [0, 1, 80]])

translated = cv2.warpAffine(img, M, (cols, rows))

plt.subplot(1, 2, 1)
plt.imshow(img)
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(translated)
plt.title('Translated Image')
plt.axis('off')

plt.show()
```
### Step 4
```
small = cv2.resize(img, None, fx=0.5, fy=0.5)

large = cv2.resize(img, None, fx=2, fy=2)

plt.figure(figsize=(12, 5))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(small)
plt.title('Downscaled Image')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(large)
plt.title('Upscaled Image')
plt.axis('off')

plt.show()
```
### Step 5
```
rows, cols = img.shape[:2]

M = np.float32([[1, 0.5, 0],
                [0, 1, 0]])

sheared_h = cv2.warpAffine(img, M, (cols + int(0.5 * rows), rows))

plt.imshow(sheared_h)
plt.title('Horizontal Shearing')
plt.axis('off')
plt.show()
```
```
rows, cols = img.shape[:2]

M = np.float32([[1, 0, 0],
                [0.5, 1, 0]])

sheared_v = cv2.warpAffine(img, M, (cols, rows + int(0.5 * cols)))

plt.imshow(sheared_v)
plt.title('Vertical Shearing')
plt.axis('off')
plt.show()
```
### Step 6
```
horizontal = cv2.flip(img, 1)

plt.imshow(horizontal)
plt.title('Horizontal Reflection')
plt.axis('off')
plt.show()
```
```
vertical = cv2.flip(img, 0)

plt.imshow(vertical)
plt.title('Vertical Reflection')
plt.axis('off')
plt.show()
```
```
both = cv2.flip(img, -1)

plt.imshow(both)
plt.title('Reflection Along Both Axes')
plt.axis('off')
plt.show()
```
### Step 7
```
rows, cols = img.shape[:2]

M = cv2.getRotationMatrix2D((cols / 2, rows / 2), 45, 1)

rotated_45 = cv2.warpAffine(img, M, (cols, rows))

plt.imshow(rotated_45)
plt.title('Rotation by 45 Degrees')
plt.axis('off')
plt.show()
```
```
rows, cols = img.shape[:2]

M = cv2.getRotationMatrix2D((cols / 2, rows / 2), 90, 1)

rotated_90 = cv2.warpAffine(img, M, (cols, rows))

plt.imshow(rotated_90)
plt.title('Rotation by 90 Degrees')
plt.axis('off')
plt.show()
```

### Developed By:
**Name:** Janesha S 

### Register No: 
212225240056

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

   <img width="545" height="210" alt="image" src="https://github.com/user-attachments/assets/b5c52c00-2820-44f2-8280-ec1e7f48250f" />


### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed

  <img width="958" height="226" alt="image" src="https://github.com/user-attachments/assets/561e3797-6e1b-457d-9541-88d967147d17" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed
- Vertically sheared image is displayed 
 
 <img width="519" height="291" alt="image" src="https://github.com/user-attachments/assets/5addfed8-6b31-49b4-a5f9-1b93bd9b7221" /> <img width="362" height="410" alt="image" src="https://github.com/user-attachments/assets/4a9fa9e6-eacf-416a-ad13-e5b79e2873d6" />
 
### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed

  <img width="520" height="368" alt="image" src="https://github.com/user-attachments/assets/3aee4036-c117-4f04-be05-4aa27063b34e" /> <img width="521" height="372" alt="image" src="https://github.com/user-attachments/assets/adce2838-d756-4c1a-8aaa-c38f20504b1c" /> <img width="514" height="369" alt="image" src="https://github.com/user-attachments/assets/d3387bea-4f18-4109-8b59-18aa6fba0caf" />



### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed

  <img width="526" height="371" alt="image" src="https://github.com/user-attachments/assets/fe9bf1ac-f62c-45f9-a5e5-8dcc0c1b64b7" /> <img width="533" height="375" alt="image" src="https://github.com/user-attachments/assets/9416ff0d-44c5-4204-9659-b2cdb73dafb5" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
