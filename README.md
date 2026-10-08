# 🚗 Lane Detection Using Python & OpenCV

A computer vision project that detects road lane lines from images/video using **Python and OpenCV**. The project applies classical image-processing techniques to identify lane markings and overlay the detected lanes on the original road scene.

## 📌 Project Overview

Lane detection is an important component of driver-assistance and autonomous driving systems. This project implements a basic lane detection pipeline without using deep learning.

The system processes a road image/video through multiple stages:

**Input Image → Grayscale → Gaussian Blur → Canny Edge Detection → Region of Interest → Hough Line Transform → Lane Line Detection**

The approach works particularly well for roads with relatively straight and clearly visible lane markings.

---

## 🛠️ Technologies Used

* **Python**
* **OpenCV**
* **NumPy**
* **Matplotlib**
* **Jupyter Notebook / Kaggle**

---

## 🔍 Methodology

### 1. Grayscale Conversion

The input image is converted to grayscale to simplify processing and focus on intensity changes.

```python
gray = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
```

### 2. Gaussian Blur

Gaussian smoothing is applied to reduce image noise before edge detection.

```python
blur = cv2.GaussianBlur(gray, (5, 5), 0)
```

### 3. Canny Edge Detection

The Canny algorithm identifies strong edges that may correspond to lane markings.

```python
edges = cv2.Canny(blur, 50, 150)
```

### 4. Region of Interest (ROI)

Only the portion of the image containing the road is retained. This helps eliminate irrelevant edges from areas such as the sky, buildings and vegetation.

A polygon mask is applied to focus the algorithm on the lane area.

### 5. Hough Line Transform

The detected edges within the ROI are processed using the **Probabilistic Hough Line Transform** to identify line segments.

```python
lines = cv2.HoughLinesP(
    cropped_edges,
    rho=2,
    theta=np.pi / 180,
    threshold=100,
    minLineLength=40,
    maxLineGap=25
)
```

### 6. Lane Line Estimation

Multiple detected line segments belonging to the same lane are grouped and averaged. The resulting lines are then extrapolated to represent the left and right lane boundaries.

---

## 📊 Processing Pipeline

```text
                Input Road Image
                       │
                       ▼
              Grayscale Conversion
                       │
                       ▼
                Gaussian Blur
                       │
                       ▼
              Canny Edge Detection
                       │
                       ▼
              Region of Interest
                       │
                       ▼
             Hough Line Transform
                       │
                       ▼
          Line Filtering & Averaging
                       │
                       ▼
             Lane Line Overlay
                       │
                       ▼
                 Final Output
```

---

## 📂 Project Structure

```text
Lane-Detection/
│
├── Lane_Detection.ipynb
├── README.md
├── requirements.txt
│
├── input/
│   └── road images / videos
│
└── output/
    └── detected lane results
```

> Update the filenames/folder structure above according to the files you upload to this repository.

---

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

Install the required libraries:

```bash
pip install opencv-python numpy matplotlib jupyter
```

Or, if `requirements.txt` is available:

```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run

### Using Jupyter Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Lane_Detection.ipynb
```

Run the cells sequentially and provide the required input image/video.

### Using Google Colab

The notebook can also be uploaded to Google Colab and executed cell by cell.

---

## 📷 Results

The algorithm identifies the lane boundaries and overlays the estimated lane lines on the original road image.

### Input

```text
Road image/video frame
```

### Output

```text
Road image/video frame with detected lane lines
```

For better visualization, add your actual output screenshots here:

```markdown
![Lane Detection Result](output/result.png)
```

---

## 💡 Key Concepts

This project demonstrates practical applications of:

* Image preprocessing
* Edge detection
* Gaussian filtering
* Region-of-interest masking
* Hough Transform
* Line detection
* Image overlay and visualization
* Basic computer vision pipelines

---

## ⚠️ Limitations

This implementation is based on traditional image-processing techniques and therefore has some limitations:

* Performs best on **straight or relatively simple roads**
* Can struggle with **curved lane markings**
* Performance can be affected by poor lighting, shadows, rain or faded lane markings
* Fixed ROI parameters may not generalize to every camera angle
* Multiple lanes and complex road geometry may require a more advanced approach

More advanced implementations can use **perspective transformation, polynomial fitting, semantic segmentation or deep-learning-based lane detection**.

---

## 🚀 Future Improvements

Potential improvements include:

* [ ] Real-time lane detection from webcam
* [ ] Video-based lane tracking
* [ ] Curved lane detection
* [ ] Perspective transformation / bird's-eye view
* [ ] Lane departure warning
* [ ] Automatic ROI detection
* [ ] Deep-learning-based lane segmentation
* [ ] Robust detection under different lighting and weather conditions

---

## 📚 Reference

This project is based on the lane-detection implementation available on Kaggle:

**Lane Detection using Python OpenCV**
https://www.kaggle.com/code/farialmahmod/lane-detection-using-python-opencv

The underlying approach follows a classical OpenCV pipeline involving edge detection, ROI selection and Hough-based line detection.

---

## 👨‍💻 Author

**Thanesh Bisen**

If you found this project useful, consider ⭐ starring the repository!
