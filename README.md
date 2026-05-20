# EXP-6 Edge Detection OpenCV

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---
## PROGRAM:

### Developed By

- **Name:** SANJAI L
- **Register No:** 212223230184
---
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load image
image = cv2.imread('Fish.jpg')  # replace with your path
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# ---------------- SOBEL ----------------
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=5)
sobel = cv2.magnitude(sobel_x, sobel_y)

# ---------------- PREWITT ----------------
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

# ---------------- ROBERTS ----------------
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_edge = cv2.filter2D(gray, -1, roberts_x)
roberts_y_edge = cv2.filter2D(gray, -1, roberts_y)
roberts = cv2.magnitude(roberts_x_edge.astype(np.float32),
                        roberts_y_edge.astype(np.float32))

# ---------------- LAPLACIAN ----------------
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

# ---------------- CANNY ----------------
canny = cv2.Canny(gray, 50, 150)

# ---------------- DISPLAY ----------------
plt.figure(figsize=(12, 10))

plt.subplot(2, 3, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis("off")

plt.subplot(2, 3, 2)
plt.imshow(sobel, cmap='gray')
plt.title("Sobel")
plt.axis("off")

plt.subplot(2, 3, 3)
plt.imshow(prewitt, cmap='gray')
plt.title("Prewitt")
plt.axis("off")

plt.subplot(2, 3, 4)
plt.imshow(roberts, cmap='gray')
plt.title("Roberts")
plt.axis("off")

plt.subplot(2, 3, 5)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian")
plt.axis("off")

plt.subplot(2, 3, 6)
plt.imshow(canny, cmap='gray')
plt.title("Canny")
plt.axis("off")

plt.tight_layout()
plt.show()
```
## Output

###  Sobel Edge Detector

<img width="393" height="448" alt="image" src="https://github.com/user-attachments/assets/068b7a0e-a295-4c2d-9cc5-5c712d209421" />


###  Prewitt Edge Detector

<img width="393" height="449" alt="image" src="https://github.com/user-attachments/assets/3d0d82e1-4889-4c1f-a474-6764f04cba1e" />



###  Roberts Edge Detector

<img width="389" height="442" alt="image" src="https://github.com/user-attachments/assets/1d6cb41e-5cef-4890-afd6-cae6efc4e701" />


###  Laplacian Edge Detector

<img width="396" height="443" alt="image" src="https://github.com/user-attachments/assets/b87afec5-0bea-469e-bc66-97ada8339f5c" />


###  Canny Edge Detector

<img width="528" height="575" alt="image" src="https://github.com/user-attachments/assets/ff4c058d-9d23-4731-a329-29e0958cb474" />


## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
