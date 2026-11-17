# Computer Vision Assignment 01

This repository contains code, datasets, and observation reports for **Assignment 01** of the Computer Vision course (ITEC0424-002). The project explores fundamental image processing and computer vision techniques, ranging from intensity thresholding to edge detection, distance transforms, and non-linear filtering.

---

## Repository Structure

```text
├── data/                       # Contains input images (digits, building, dolphin, shapes)
├── Assignment01_CV.ipynb       # Main Jupyter Notebook with complete implementation
└── README.md                   # Project documentation
```

# Topics Covered & Summary of Observations
1. **Intensity Thresholding (digits.png)**
- Binary & Inverse Binary Thresholding: Evaluated the effect of varying global thresholds ($T = 55, 129, 200$). Demonstrated how proper threshold placement isolates specific digits based on foreground/background intensity differences, while intermediate thresholds can cause digits to merge invisibly into complex soft-disc backgrounds.
- Window Thresholding: Tested narrow intensity windows (e.g., $55 < I < 90$, $90 < I < 129$, $129 < I < 200$) to isolate targets.
- Limitation Analysis: Highlighted the constraint of intensity-based thresholding—because pixel intensity alone cannot separate objects sharing identical grey levels (e.g., digit '3' and the ring disc both sharing $I = 130$), spatial algorithms are required.
2. **Image Denoising (Smoothing Filters)**
- Average (Box) Filters: Analyzed the trade-off across kernel sizes ($3\times3$ up to $9\times9$). While larger kernels successfully attenuate independent noise (reducing noise standard deviation roughly by $\sqrt{N}$), they lead to significant edge blurring.
- Gaussian Filters: Tested Gaussian windows ($9\times9$) across varying values of $\sigma$ ($0.5$ to $4.0$).
- Optimal Selection: Determined that a Gaussian filter with a $9\times9$ window and $\sigma = 0.5$ yields the best balance by preserving structural details while eliminating excessive noise.
3. **Canny Edge Detection (dolphin.png)**
- Hyperparameter Analysis: Investigated the influence of the blur kernel size ($K$), low threshold ($L$), and high threshold ($H$) across a 27-parameter grid search.
- Optimal Configuration: Evaluated outputs using precision and recall (2-pixel tolerance) against ground truth, achieving a peak performance with $(K, L, H) = (11, 150, 200)$ yielding a precision of $\approx 0.934$. Larger kernel sizes effectively suppress complex water/sun-glitter textures while preserving the dolphin's main silhouette.
4. **Chamfer Distance & Matching**
- Distance Transform (Manhattan Metric): Implemented forward ($O(hw)$) and backward passes to generate precise distance maps from binary feature boundaries.
- Chamfer Matching: Performed template matching by overlaying a triangle edge template onto a scene's distance map, successfully localizing the target shape at the optimal minimum coordinate match.
5. **Median Filtering & Linearity**
- Algorithm Steps: Detailed padding, sliding window collection, sorting, and median extraction.
- Non-Linearity Proof: Demonstrated mathematically and via counter-example that the median filter violates additivity ($F(A+B) \neq F(A) + F(B)$), proving it is non-linear and cannot be represented via standard convolution—explaining its unique capability to remove salt-and-pepper noise while preserving sharp boundaries.

# Getting Started
  1. **Clone the repository**:
     - git clone [https://github.com/Likithna/ComputerVision01.git](https://github.com/Likithna/ComputerVision01.git)
  2. **Navigate to the directory and launch Jupyter Notebook**:
     - cd ComputerVision01
     
       jupyter notebook Assignment01_CV.ipynb
  3. Ensure your images are stored inside the data/ directory so the notebook paths resolve correctly.
Author
Likith N A (Student ID: 2024017879)
