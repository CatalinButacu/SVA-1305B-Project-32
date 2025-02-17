**Technical University "Gh. Asachi" | Faculty of Automation and Computer Science**  

--------------------------------------------------------------------------------  
### **Project Overview**  
This MATLAB application is designed to **automatically detect and blur human faces** in real-time video streams or uploaded images, addressing privacy concerns in digital media. Built using MATLAB’s App Designer and Computer Vision Toolbox, the tool combines real-time image acquisition, face detection algorithms, and customizable blurring techniques into an intuitive graphical interface.  

#### **Core Objectives**  
- Protect privacy by anonymizing faces in images/videos.  
- Demonstrate practical applications of computer vision (object detection, image processing).  
- Provide an interactive platform for users to experiment with blurring parameters and shapes.  

--------------------------------------------------------------------------------  
### **Technical Highlights**  

#### **1. System Architecture**  
The application follows a **pipeline workflow**:  
1. **Image Acquisition**:  
   - **Real-Time Mode**: Captures frames from a webcam/external camera using MATLAB’s `webcam` object.  
   - **Static Mode**: Processes uploaded images (JPG/PNG) or snapshots.  
2. **Face Detection**:  
   - Uses MATLAB’s `vision.CascadeObjectDetector` with the *FrontalFaceCART* model to identify faces.  
   - Converts frames to grayscale to optimize Haar feature-based detection.  
3. **Blurring Process**:  
   - Applies a **Gaussian filter** (`imgaussfilt`) to detected face regions.  
   - Supports **two blur shapes**:  
     - *Square*: Blurs the exact bounding box of the detected face.  
     - *Circle*: Creates a circular mask around the face center for natural blurring.  
4. **GUI Integration**:  
   - Live preview of original and processed images.  
   - Interactive controls for blur level (0–40), shape selection, and live mode toggling.  

#### **2. Key Algorithms & Functions**  
- **Real-Time Processing**:  
  - A `timer` object updates frames every **0.05 seconds** (20 FPS) in live mode, calling `updateLive` to refresh the GUI.  
  - The `photoProcessing` and `photoProcessing2` functions handle square/circular blurring, respectively.  
- **Circular Blur Logic**:  
  - Computes the face’s center coordinates and radius from the bounding box.  
  - Generates a circular mask using `meshgrid` and applies Gaussian blur only within the mask.  

#### **3. MATLAB Components Used**  
- **App Designer**: For building the GUI (buttons, sliders, image displays).  
- **Computer Vision Toolbox**: For `CascadeObjectDetector` and face detection workflows.  
- **Image Processing Toolbox**: For `rgb2gray`, `imgaussfilt`, and image masking.  

--------------------------------------------------------------------------------  
### **Application Workflow**  
1. **Launch the App**:  
   - Run `app.m` to initialize the GUI. The camera and timer start automatically.  
2. **Live Mode**:  
   - Toggle the **LIVE** switch to enable real-time blurring.  
   - Adjust the blur intensity with the slider and select a blur shape.  
3. **Static Image Processing**:  
   - **Capture**: Click **CAPTURE** to take a webcam snapshot.  
   - **Upload**: Click **UPLOAD** to process an existing image.  
4. **Exit**: Click **EXIT** to terminate the application and release hardware resources.  

--------------------------------------------------------------------------------  
### **Key Features**  
| Feature                | Description                                                                 |  
|------------------------|-----------------------------------------------------------------------------|  
| **Real-Time Blurring** | Process live video at ~20 FPS with adjustable blur intensity.               |  
| **Dual Blur Shapes**   | Choose between square (precise) or circular (natural-looking) blur effects. |  
| **Hardware Integration** | Supports default and external cameras (code-configurable).                |  
| **User-Friendly GUI**  | Intuitive controls with live previews and system time display.              |  

--------------------------------------------------------------------------------  
### **Setup & Requirements**  
1. **MATLAB Toolboxes**:  
   - *Computer Vision Toolbox* (mandatory for face detection).  
   - *Image Processing Toolbox* (for blur operations).  
   - *Webcam Support Package* (install via MATLAB Add-Ons).  
2. **Code Adjustments**:  
   - To use an external camera, modify `setupLiveAcquisition` in `app.m`:  
     ```matlab  
     app.Camera = webcam('ZV-E10'); % Replace with your camera name  
     ```  
3. **Performance Tips**:  
   - Lower blur levels (<20) for smoother real-time processing.  
   - Close background apps to reduce CPU load.  

--------------------------------------------------------------------------------  
### **Practical Applications**  
- **Privacy Protection**: Blur faces in public datasets, social media, or surveillance footage.  
- **Educational Tool**: Learn MATLAB’s App Designer, real-time image processing, and Haar cascades.  
- **Research Prototyping**: Extend the code to experiment with other detectors (e.g., eye, smile).  

--------------------------------------------------------------------------------  
### **Limitations & Future Work**  
- **Current Limitations**:  
  - Only detects frontal faces; side profiles or occluded faces may be missed.  
  - Circular blur may clip faces near image edges.  
- **Future Enhancements**:  
  - Add support for video file input/output.  
  - Implement multi-shape blurring (e.g., polygons).  
  - Integrate deep learning models (YOLO, SSD) for higher accuracy.  

--------------------------------------------------------------------------------  
**References**  

1. MathWorks, *Computer Vision Toolbox Documentation* [Online]. Available:  
   https://www.mathworks.com/help/vision/index.html  

2. MathWorks, *Face Detection and Tracking Using Live Video Acquisition* [Online]. Available:  
   https://www.mathworks.com/help/vision/ug/face-detection-and-tracking-using-live-video-acquisition.html  

3. MathWorks, *vision.CascadeObjectDetector System Object* [Online]. Available:  
   https://www.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-system-object.html 

**License:**
This project is for educational purposes. Use freely under MIT License. 
