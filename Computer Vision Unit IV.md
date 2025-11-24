
---

## 1. Introduction to Image Gradients

1. **What is a gradient in an image?**
    
    - Gradient = **rate of change of intensity** (brightness) in an image.
        
    - It tells us **how quickly** pixel values change and in **which direction** they change.
        
2. **Why do we need gradients?**
    
    - Edges in an image appear where intensity changes **suddenly**.
        
    - Gradients help to:
        
        - Detect **edges**.
            
        - Highlight **object boundaries**.
            
        - Prepare for **segmentation**, **classification**, **object detection**, etc.
            
3. **Mathematical idea (simple)**
    
    - For a grayscale image (I(x, y)):
        
        - Horizontal change ≈ (G_x = \frac{\partial I}{\partial x})
            
        - Vertical change ≈ (G_y = \frac{\partial I}{\partial y})
            
    - Gradient **magnitude**:  
        (|G| = \sqrt{G_x^2 + G_y^2}) → strength of edge.
        
    - Gradient **direction**:  
        (\theta = \tan^{-1}(\frac{G_y}{G_x})) → orientation of edge.
        
4. **Concept in practice**
    
    - We don’t compute derivatives directly.
        
    - We use **filters (kernels)** that approximate derivative using **convolution**.
        

---

## 2. First Order Derivative Filters

### 2.1 Concept

1. **First-order derivative**
    
    - Measures **how fast intensity changes** in one direction.
        
    - Large derivative = strong edge.
        
    - Used for **basic edge detection**.
        
2. **Idea in discrete images**
    
    - Approximate derivative by **difference between neighboring pixels**:
        
        - Example: (G_x \approx I(x+1,y) - I(x-1,y))
            

### 2.2 Common First-Order Filters

1. **Roberts Cross Operator**
    
    - Very small **2×2 kernels**.
        
    - Detects edges along diagonals.
        
    - Kernels:
        
        - (G_x = \begin{bmatrix}+1 & 0 \ 0 & -1\end{bmatrix})
            
        - (G_y = \begin{bmatrix}0 & +1 \ -1 & 0\end{bmatrix})
            
    - **Pros**: Simple, fast.
        
    - **Cons**: Very sensitive to noise, not much smoothing.
        
2. **Prewitt Operator**
    
    - Uses **3×3 kernels**.
        
    - Computes gradient with **average differences**.
        
    - Kernels (one version):
        
        - (G_x = \begin{bmatrix}-1 & 0 & 1 \ -1 & 0 & 1 \ -1 & 0 & 1\end{bmatrix})
            
        - (G_y = \begin{bmatrix}-1 & -1 & -1 \ 0 & 0 & 0 \ 1 & 1 & 1\end{bmatrix})
            
    - **Pros**: Better than Roberts, some smoothing.
        
    - **Cons**: Less accurate than Sobel.
        
3. **Sobel Operator**
    
    - Most commonly used simple gradient operator.
        
    - Adds **more weight to center** row/column (smoothing + derivative).
        
    - Kernels:
        
        - (G_x = \begin{bmatrix}-1 & 0 & 1 \ -2 & 0 & 2 \ -1 & 0 & 1\end{bmatrix})
            
        - (G_y = \begin{bmatrix}-1 & -2 & -1 \ 0 & 0 & 0 \ 1 & 2 & 1\end{bmatrix})
            
    - **Pros**:
        
        - Smoother results.
            
        - More robust to noise.
            
    - **Cons**:
        
        - Still a simple approximation.
            
4. **Scharr Operator (advanced)**
    
    - Variation of Sobel with better rotational symmetry.
        
    - Used when **precise gradient** is needed.
        

### 2.3 General Steps to Apply First-Order Filters

1. Convert image to **grayscale**.
    
2. Optionally apply **smoothing** (like Gaussian blur) to reduce noise.
    
3. Convolve image with **Gx kernel** → get horizontal gradient image.
    
4. Convolve image with **Gy kernel** → get vertical gradient image.
    
5. Compute:
    
    - Gradient magnitude (|G|).
        
    - Gradient direction (\theta).
        
6. Use (|G|) to detect **edges** (e.g., thresholding on (|G|)).
    

---

## 3. Second Order Derivative Filters

### 3.1 Concept

1. **Second-order derivative**
    
    - Measures **change of the first derivative**.
        
    - Highlights places where intensity changes **very sharply**.
        
    - Often used to find **exact edge locations** (zero-crossings).
        
2. **Properties**
    
    - Much more **sensitive to noise** than first-order.
        
    - Usually **combine with smoothing**.
        

### 3.2 Laplacian Operator

1. **What is Laplacian?**
    
    - Sum of second derivatives in x and y directions:  
        (\nabla^2 I = \frac{\partial^2 I}{\partial x^2} + \frac{\partial^2 I}{\partial y^2})
        
    - Detects areas where intensity changes **in all directions**.
        
2. **Common Laplacian kernel (3×3)**
    
    - Example kernel:  
        [  
        \begin{bmatrix}  
        0 & -1 & 0 \  
        -1 & 4 & -1 \  
        0 & -1 & 0  
        \end{bmatrix}  
        ]
        
    - Or:  
        [  
        \begin{bmatrix}  
        -1 & -1 & -1 \  
        -1 & 8 & -1 \  
        -1 & -1 & -1  
        \end{bmatrix}  
        ]
        
3. **Use**
    
    - Highlights **edges and fine details**.
        
    - Often used with smoothing to avoid noise.
        

### 3.3 Laplacian of Gaussian (LoG)

1. **Idea**
    
    - First apply **Gaussian blur** (smoothing).
        
    - Then apply **Laplacian**.
        
    - Combined into one filter called **LoG**.
        
2. **Reason**
    
    - Reduce noise with Gaussian.
        
    - Then detect sharp intensity changes with Laplacian.
        
3. **Zero-crossings**
    
    - Edges are often taken where **LoG output changes sign** (positive → negative or vice versa).
        

### 3.4 Difference of Gaussian (DoG)

1. **Idea**
    
    - Approximate LoG by subtracting two Gaussian-blurred images:
        
    - (DoG = G_{\sigma_1} * I - G_{\sigma_2} * I) (with different (\sigma)).
        
2. **Use**
    
    - Cheaper than LoG.
        
    - Used in feature detection (e.g., SIFT).
        

### 3.5 Steps to Use Second-Order Filters

1. Convert to **grayscale**.
    
2. Apply **Gaussian blur** (important to reduce noise).
    
3. Apply **Laplacian** or **LoG/DoG** filter.
    
4. Detect **zero-crossings** or threshold on response to find edges.
    

---

## 4. Edge Detection

### 4.1 What is an Edge?

1. Edge = boundary where pixel intensity **changes sharply**.
    
2. Example: boundary between object and background.
    

### 4.2 Why Edge Detection?

1. Reduces data by keeping only **important structure**.
    
2. Used before:
    
    - **Segmentation**
        
    - **Object recognition**
        
    - **Object detection**
        

### 4.3 General Steps in Edge Detection

1. **Noise reduction**
    
    - Use Gaussian blur to smooth image.
        
2. **Compute gradients**
    
    - Use first-order (Sobel, Prewitt) or second-order (Laplacian) filters.
        
3. **Find edge strength**
    
    - Use gradient magnitude or filter response.
        
4. **Thresholding**
    
    - Only keep pixels with magnitude above some value.
        
5. **Post-processing**
    
    - Thinning edges, connecting broken edges.
        

### 4.4 Types of Edge Detection Methods

1. **Gradient-based**
    
    - Use first-order derivatives.
        
    - Examples: Roberts, Prewitt, Sobel.
        
2. **Laplacian-based**
    
    - Use second-order derivatives.
        
    - Examples: Laplacian, LoG, DoG.
        
3. **Canny Edge Detector (most famous advanced method)**
    
    **Steps of Canny:**
    
    1. **Noise reduction**
        
        - Apply Gaussian blur.
            
    2. **Gradient calculation**
        
        - Use Sobel to find (G_x), (G_y), magnitude, and direction.
            
    3. **Non-maximum suppression**
        
        - For each pixel, check neighbors **along gradient direction**.
            
        - Keep only local maxima → **thin edges**.
            
    4. **Double thresholding**
        
        - Use **high** and **low** threshold.
            
        - Strong edges: magnitude > high threshold.
            
        - Weak edges: between low and high threshold.
            
    5. **Edge tracking by hysteresis**
        
        - Keep weak edges that are connected to strong edges.
            
        - Remove isolated weak edges (noise).
            

---

## 5. Image Segmentation and Recognition

### 5.1 Image Segmentation

1. **Definition**
    
    - Process of dividing an image into **regions** that have similar properties.
        
    - Aim: Separate **objects** from background.
        
2. **Goals**
    
    - Simplify the image.
        
    - Identify meaningful **regions** (e.g., sky, road, person).
        
3. **Types / Methods of Segmentation**
    
    1. **Threshold-based Segmentation**
        
        - Use intensity value to separate foreground and background.
            
        - Example: Otsu’s method to find best threshold automatically.
            
    2. **Region-based Segmentation**
        
        - Start from a **seed** pixel and grow region by adding similar neighbors.
            
        - Methods: Region growing, region splitting and merging.
            
    3. **Edge-based Segmentation**
        
        - First detect edges, then combine edges to form **closed boundaries**.
            
        - Uses **edge detectors** as first step.
            
    4. **Clustering-based Segmentation**
        
        - Group pixels based on similarity in color/intensity/position.
            
        - Example: **k-means clustering** to group pixels into k clusters.
            
    5. **Graph-based / Advanced methods**
        
        - Treat image as graph (pixels = nodes).
            
        - Cut graph by minimizing some cost (e.g., Normalized Cuts).
            
    6. **Deep Learning-based Segmentation**
        
        - **Semantic segmentation** using CNNs (e.g., U-Net, FCN).
            
        - Output: class label for every pixel.
            
4. **General Steps in Traditional Segmentation**
    
    1. Preprocess: smoothing, noise removal.
        
    2. Choose method: thresholding / region / edge / clustering.
        
    3. Apply algorithm to divide image into regions.
        
    4. Post-process: merge small regions, remove noise.
        

---

### 5.2 Image Recognition

1. **Definition**
    
    - Task of **identifying what is in the image** (e.g., “This is a cat”).
        
    - Often uses segmented regions or whole image.
        
2. **Pipeline (traditional approach)**
    
    1. **Preprocessing**
        
        - Resize, normalize, denoise.
            
    2. **Feature Extraction**
        
        - Extract key features like:
            
            - Edges (HOG – Histogram of Oriented Gradients),
                
            - Corners (Harris detector),
                
            - Local descriptors (SIFT, SURF).
                
    3. **Feature Representation**
        
        - Represent image as a **feature vector**.
            
    4. **Classification**
        
        - Use ML models:
            
            - k-NN
                
            - SVM
                
            - Decision Trees, Random Forest, etc.
                
    5. **Output**
        
        - Assign a **label** (e.g., “dog”, “car”).
            
3. **Modern Deep Learning-based Recognition**
    
    - Use a **Convolutional Neural Network (CNN)**.
        
    - CNN automatically learns features + classifier together.
        
    - Input: image.
        
    - Output: class probabilities.
        

---

## 6. Image Classification

1. **Definition**
    
    - Task of assigning a **single label** to an entire image.
        
    - Example: Given an image, classify as **cat/dog/car/person**.
        
2. **Difference from Segmentation & Detection**
    
    - **Classification**: one label for whole image.
        
    - **Segmentation**: label per pixel.
        
    - **Detection**: labels + bounding boxes.
        
3. **Traditional Classification Pipeline**
    
    1. **Preprocessing**
        
        - Resize, normalize intensity.
            
    2. **Feature Extraction**
        
        - Use descriptors:
            
            - HOG (edges and gradients).
                
            - SIFT/SURF (keypoints).
                
            - Color histograms.
                
    3. **Train a classifier**
        
        - Collect labeled images.
            
        - Train algorithm (SVM, kNN, logistic regression, etc.).
            
    4. **Prediction**
        
        - For a new image:
            
            - Extract features.
                
            - Feed into classifier.
                
            - Get predicted label.
                
4. **Deep Learning Classification (CNN)**
    
    1. **Convolution layers**
        
        - Learn filters to detect edges, textures, shapes.
            
    2. **Pooling layers**
        
        - Reduce size, keep important information.
            
    3. **Fully connected layers**
        
        - Act like normal neural networks for final decision.
            
    4. **Softmax layer**
        
        - Gives probability for each class.
            
    5. **Training**
        
        - Use large labeled dataset and backpropagation.
            
5. **Performance Measures**
    
    - Accuracy, Precision, Recall, F1-score.
        
    - Confusion matrix.
        

---

## 7. Object Detection

1. **Definition**
    
    - Find **what objects are present** AND **where** they are in the image.
        
    - Output:
        
        - **Class label** (e.g., “person”, “car”).
            
        - **Bounding box** around each object.
            
2. **Difference from Classification**
    
    - Classification: only “what”.
        
    - Detection: “what + where (location)”.
        
3. **Traditional Object Detection (before deep learning)**
    
    **Pipeline:**
    
    1. **Sliding window**
        
        - Move a window over the image at different positions and scales.
            
    2. **Feature extraction**
        
        - Compute features for each window:
            
            - HOG features (for humans, cars, etc.).
                
    3. **Classification**
        
        - Use a classifier (e.g., SVM) to say “object” or “no object”.
            
    4. **Non-Maximum Suppression (NMS)**
        
        - Several windows may detect same object.
            
        - Keep the one with highest score, remove overlapping ones.
            
4. **Deep Learning-based Object Detection**
    
    Two main families:
    
    1. **Two-stage detectors**
        
        - **R-CNN**:
            
            - Generate region proposals.
                
            - Extract features with CNN.
                
            - Classify each region.
                
        - **Fast R-CNN**:
            
            - Run CNN once for whole image.
                
            - Use region proposals on feature map.
                
        - **Faster R-CNN**:
            
            - Adds **Region Proposal Network (RPN)**.
                
            - End-to-end trainable, faster.
                
    2. **One-stage detectors**
        
        - **YOLO (You Only Look Once)**
            
        - **SSD (Single Shot Detector)**
            
        - Directly predict bounding boxes and class scores in **one pass**.
            
        - Faster, good for real-time.
            
5. **Generic Steps in Object Detection**
    
    1. **Input image**.
        
    2. **Feature extraction** using CNN.
        
    3. **Generate candidate boxes**
        
        - Using region proposals (two-stage) or dense grid (one-stage).
            
    4. **Predict**
        
        - For each box: class probabilities + box coordinates.
            
    5. **Post-process**
        
        - Apply Non-Maximum Suppression to remove duplicates.
            
    6. **Output**
        
        - Final set of bounding boxes with labels and confidence scores.
            

---

If you want, next I can turn **just this Unit IV** into a clean exam-focused **PDF-style outline with headings** for printing, but content-wise this covers the detailed points, steps, and types you’ll need to write answers like a topper.