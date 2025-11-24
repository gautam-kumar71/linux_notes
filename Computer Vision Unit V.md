
---

# **UNIT V – Applications of Computer Vision (Detailed Notes)**

Topics: **Gesture Recognition, Motion Estimation, Object Tracking, Face Detection, Deep Learning with OpenCV**

---

# **1. Gesture Recognition**

### **Definition:**

Gesture recognition is a computer vision technique that allows a computer to **understand human movements** (like hand signs, body poses, finger movements) and interpret them as **commands**.

### **Detailed Points:**

- **Purpose:** To let humans interact with machines using natural body movements instead of keyboards or touch screens.
    
- **Common Gestures:**
    
    - Hand waves
        
    - Palm open/closed
        
    - Thumbs-up
        
    - Sign language symbols
        
    - Body pose like raising hands
        
- **How it Works (Steps):**
    
    1. **Detection:** Identify the hand or body region in the image or video.
        
    2. **Feature Extraction:** Extract key features (edges, contours, keypoints).
        
    3. **Tracking (optional):** Track the movement across frames.
        
    4. **Classification:** Use ML/DL to recognize which gesture it is.
        
    5. **Output:** Convert gesture → action (e.g., next slide, play/pause).
        
- **Techniques Used:**
    
    - CNNs for hand‐pose recognition
        
    - MediaPipe hand landmark detection
        
    - Skeleton detection (OpenPose)
        
    - Optical flow for movement direction
        
- **Applications:**
    
    - Touchless UI
        
    - Gaming (e.g., Kinect)
        
    - AR/VR
        
    - Robot control
        
    - Sign-language translation
        
    - Smart TVs (gesture-based volume change)
        

---

# **2. Motion Estimation**

### **Definition:**

Motion estimation is the process of **calculating how objects move between video frames**, including speed and direction.

### **Detailed Points:**

- **Purpose:** Understand movement patterns in videos.
    
- **How it Works:**
    
    - Analyse pixel changes from frame to frame.
        
    - Find where an object in frame 1 moved in frame 2.
        
- **Output:**
    
    - A **motion vector** (e.g., moved 10 pixels right, 5 pixels up).
        
- **Techniques:**
    
    1. **Optical Flow**
        
        - Tracks how brightness of pixels changes
            
        - Example: Lucas-Kanade method, Farneback method
            
    2. **Block Matching**
        
        - Divides the image into blocks
            
        - Finds similar blocks in the next frame
            
- **Applications:**
    
    - Video compression (e.g., MPEG, H.264)
        
    - Autonomous driving (detecting moving vehicles)
        
    - Robotics (path planning, collision avoidance)
        
    - Stabilizing shaky videos
        
    - Sports motion analysis
        
- **Challenges:**
    
    - Fast-moving objects
        
    - Motion blur
        
    - Camera shaking
        
    - Low light
        

---

# **3. Object Tracking**

### **Definition:**

Object tracking means **locating the same object continuously across video frames**, after detecting it once.

### **Detailed Points:**

- **Why Needed:**
    
    - To follow one or multiple objects as they move (cars, people, balls, animals).
        
- **Two Main Phases:**
    
    1. **Detection** – Find the object in the first frame
        
    2. **Tracking** – Follow it in all remaining frames
        
- **Types of Tracking:**
    
    - **Single Object Tracking (SOT)**
        
    - **Multiple Object Tracking (MOT)**
        
- **Popular Tracking Algorithms:**
    
    - **Kalman Filter** – predicts next position
        
    - **Meanshift / Camshift** – color-based tracking
        
    - **Optical Flow** – motion-based
        
    - **CSRT, KCF trackers** (OpenCV)
        
    - **Deep Learning Trackers**
        
        - SORT
            
        - DeepSORT
            
        - ByteTrack
            
- **Applications:**
    
    - Traffic surveillance
        
    - CCTV and security
        
    - Sports performance analysis
        
    - Drones following objects
        
    - Wildlife monitoring
        
- **Challenges:**
    
    - Object goes behind another object (occlusion)
        
    - Fast motion
        
    - Changing light
        
    - Object changes shape or direction suddenly
        

---

# **4. Face Detection**

### **Definition:**

Face detection is the process of **finding human faces in an image or video** and marking where the face is located.

### **Detailed Points:**

- **Goal:** Only detect the presence/location of face, not identify the person (that is “Face Recognition”).
    
- **How it Works:**
    
    - Detect patterns that look like human faces (eyes, nose, mouth arrangement).
        
- **Techniques Used:**
    
    1. **Haar Cascade Classifiers (OpenCV classic)**
        
        - Fast but old
            
        - Trained using many positive and negative face images
            
    2. **HOG + SVM**
        
        - Histogram of Oriented Gradients
            
        - Good for frontal faces
            
    3. **Deep Learning Based Face Detectors:**
        
        - DNN-based OpenCV face detector
            
        - SSD (Single Shot Detector)
            
        - MTCNN (Multi-task cascaded CNN)
            
        - RetinaFace (very accurate)
            
- **Applications:**
    
    - Phone face unlock
        
    - Attendance systems
        
    - CCTV
        
    - Face tracking
        
    - Face filters (Snapchat, Instagram)
        
    - Human-computer interaction
        
- **Challenges:**
    
    - Different face angles (profile view)
        
    - Low light
        
    - Wearing mask or glasses
        
    - Small/blurred faces
        
    - Crowded scenes
        

---

# **5. Deep Learning with OpenCV**

### **Definition:**

Deep learning with OpenCV means using **OpenCV’s DNN (Deep Neural Network) module** to run trained deep learning models for vision tasks.

### **Detailed Points:**

- **OpenCV DNN module:**  
    Supports deep learning model loading and inference.
    
- **Supported Model Formats:**
    
    - Caffe (.prototxt, .caffemodel)
        
    - TensorFlow (.pb)
        
    - ONNX (most common today)
        
    - Darknet (.cfg, .weights)
        
- **What Deep Learning Can Do in OpenCV:**
    
    - Object detection (YOLO, SSD)
        
    - Face detection & recognition
        
    - Pose estimation
        
    - Emotion detection
        
    - Image segmentation
        
    - Text detection (EAST)
        
    - Style transfer
        
- **Popular Deep Models Used in OpenCV:**
    
    - **YOLOv3/v4/v5/YOLO-NAS** for real-time detection
        
    - **OpenPose** for body keypoints
        
    - **DeepSORT + YOLO** for tracking
        
    - **MobileNet-SSD** for lightweight detection
        
    - **FaceNet/ArcFace** for face recognition
        
- **Workflow:**
    
    1. Load the trained DL model
        
    2. Preprocess image (resize, normalize)
        
    3. Pass through network
        
    4. Get output predictions
        
    5. Draw results (bounding boxes, labels)
        
- **Advantages:**
    
    - High accuracy
        
    - Works on complex tasks
        
    - Supports GPU acceleration
        
- **Applications:**
    
    - Autonomous vehicles
        
    - Healthcare diagnostics
        
    - Retail analytics
        
    - Smart city systems
        
    - Security systems
        
    - Gesture recognition
        
    - Industrial automation
        

---
