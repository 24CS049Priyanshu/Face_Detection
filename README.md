# AI Face Detection Laboratory 🔬

An interactive web-based face detection application that demonstrates real-time computer vision with comprehensive mathematical explanations. This educational project combines practical AI implementation with theoretical foundations to help understand how face detection algorithms work.

## Features

- **Real-time Face Detection**: Detects multiple faces simultaneously using TensorFlow.js and BlazeFace model
- **Live Statistics**: Displays face count, confidence scores, and processing FPS
- **Mathematical Education**: Comprehensive explanations of the mathematical concepts behind face detection
- **Image Capture**: Download screenshots with face count overlay and detection boxes
- **Responsive Design**: Works on desktop and mobile devices
- **No Backend Required**: Runs entirely in the browser



## Mathematical Concepts Covered

This project explains the mathematical foundations of face detection including:

### 1. Image Matrix Representation
Digital images are represented as multi-dimensional matrices where each element represents pixel intensity (0-255).

**Grayscale Image:**
```
I_gray(x,y) = [p_1,1  p_1,2  ...  p_1,n]
              [p_2,1  p_2,2  ...  p_2,n]
              [  ⋮      ⋮    ⋱    ⋮  ]
              [p_m,1  p_m,2  ...  p_m,n]
```

**RGB Color Image:**
```
I_RGB = [I_R, I_G, I_B] where each channel is a 2D matrix
```

### 2. Convolution Operations
Convolution is the core mathematical operation for feature detection, sliding a filter (kernel) across the image.

**Convolution Formula:**
```
(I * K)(x,y) = Σ Σ I(x+m, y+n) · K(m,n)
               m n
```

**Edge Detection Kernel Example:**
```
K_edge = [-1  -1  -1]
         [-1   8  -1]
         [-1  -1  -1]
```

### 3. Neural Network Predictions
The network uses activation functions to convert raw scores into probabilities.

**Sigmoid Activation:**
```
σ(z) = 1 / (1 + e^(-z)) where z = Σ w_i x_i + b
```

**Face Probability:**
```
P(face|x) = σ(W · φ(x) + b)
```
Where φ(x) represents the learned feature representation of input x.

### 4. Bounding Box Mathematics
Face detection models predict bounding box coordinates and dimensions.

**Bounding Box Representation:**
```
B = (x_center, y_center, width, height, confidence)
```

**Corner Coordinates:**
```
x_min = x_center - width/2
y_min = y_center - height/2
x_max = x_center + width/2
y_max = y_center + height/2
```

### 5. Non-Maximum Suppression (NMS)
NMS eliminates duplicate detections using Intersection over Union (IoU).

**IoU Calculation:**
```
IoU = Area of Intersection / Area of Union = |B_1 ∩ B_2| / |B_1 ∪ B_2|
```

**NMS Decision Rule:**
```
Keep box if: IoU < threshold OR confidence > max_confidence
```

### 6. Confidence Scoring
Confidence combines objectness score with classification probability.

**Confidence Formula:**
```
Confidence = P(Object) × P(Class|Object) × IoU_pred^truth
```

**Final Score:**
```
Final Score = σ(raw output) × 100%
```

### 7. Real-time Processing Mathematics
Frame rate calculation and optimization for real-time performance.

**FPS Calculation:**
```
FPS = 1 / Processing Time per Frame
```

**Total Processing Time:**
```
Processing Time = T_preprocessing + T_inference + T_postprocessing
```

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **AI/ML**: TensorFlow.js, BlazeFace model
- **Math Rendering**: MathJax for LaTeX formula display
- **Browser APIs**: WebRTC for camera access, Canvas API for rendering

## Installation and Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ai-face-detection-lab.git
   cd ai-face-detection-lab
   ```

2. **Serve the files**
   Since this uses camera access, you need to serve files over HTTPS or localhost:
   
   **Option A: Using Python**
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Python 2
   python -m SimpleHTTPServer 8000
   ```
   
   **Option B: Using Node.js**
   ```bash
   npx http-server -p 8000
   ```
   
   **Option C: Using Live Server (VS Code)**
   - Install Live Server extension
   - Right-click on `index.html` and select "Open with Live Server"

3. **Open in browser**
   Navigate to `http://localhost:8000` in your web browser

## Usage

1. **Allow Camera Permission**: Click "Start Detection" and grant camera access when prompted
2. **View Real-time Detection**: Watch as faces are detected and highlighted with bounding boxes
3. **Monitor Statistics**: Observe live face count, confidence scores, and FPS metrics
4. **Capture Images**: Use "Capture & Download" to save screenshots with face count overlay
5. **Learn Mathematics**: Scroll down to explore the mathematical concepts section

## File Structure

```
ai-face-detection-lab/
├── index.html          # Main HTML file with embedded CSS and JavaScript
├── README.md           # This file
└── LICENSE            # MIT License file
```

## Model Attribution and Credits

This project utilizes the **BlazeFace** model from Google's MediaPipe project, accessed through TensorFlow.js:

- **BlazeFace Model**: Copyright Google LLC, Apache License 2.0
- **TensorFlow.js**: Copyright Google LLC, Apache License 2.0
- **Model Source**: https://github.com/tensorflow/tfjs-models/tree/master/blazeface

### Important Notes on Model Usage

- The BlazeFace model is loaded directly from TensorFlow.js CDN
- No model files are redistributed in this repository
- All model weights and architecture remain under Google's copyright
- This project serves as an educational interface to demonstrate the model's capabilities

## Browser Compatibility

- **Chrome/Chromium**: Full support
- **Firefox**: Full support
- **Safari**: Full support (iOS 11+)
- **Edge**: Full support

**Requirements:**
- Modern browser with WebRTC support
- Camera access permission
- JavaScript enabled

## Privacy and Security

- **Local Processing**: All face detection happens locally in your browser
- **No Data Collection**: No images or data are sent to external servers
- **Camera Access**: Only used for real-time processing, not stored or transmitted
- **No Cookies**: This application doesn't use cookies or tracking

## Educational Purpose

This project is designed for educational purposes to demonstrate:

- Computer vision concepts and implementation
- Mathematical foundations of AI/ML algorithms
- Browser-based AI application development
- Real-time image processing techniques

## Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **Google/TensorFlow Team** for the BlazeFace model and TensorFlow.js
- **MathJax** for mathematical formula rendering
- **MediaPipe** project for computer vision research and development
- **Open source community** for making AI accessible to everyone

## Disclaimer

This is an educational project demonstrating face detection technology. The accuracy and performance may vary based on lighting conditions, camera quality, and browser capabilities. This project is not intended for production use in security or commercial applications.

## Support

If you encounter any issues or have questions:

1. Check the browser console for error messages
2. Ensure camera permissions are granted
3. Try refreshing the page
4. Open an issue on GitHub for technical problems

---

**Note**: This project uses third-party models and libraries. Please refer to their respective licenses and terms of use. All mathematical explanations are provided for educational purposes and represent commonly accepted formulations in computer vision literature.
