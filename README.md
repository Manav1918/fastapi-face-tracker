<div align="center">
  <h1>📷 FastAPI Real-Time Face Tracker</h1>
  <p><i>A lightweight, high-performance real-time face detection streaming API built with FastAPI and OpenCV.</i></p>

  <p>
    <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
    <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV" />
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  </p>
</div>

---

## 📖 Overview

**FastAPI Real-Time Face Tracker** is an elegant and efficient application that captures your webcam's video stream, processes it frame-by-frame to detect human faces using OpenCV's Haar Cascade Classifiers, and serves the live annotated video feed over a web API using FastAPI's `StreamingResponse`. 

Whether you're looking to build a security camera web application, a smart mirror, or just learn how to stream video with FastAPI, this project is the perfect starting point!

## ✨ Features

- **⚡ Blazing Fast API:** Built on top of [FastAPI](https://fastapi.tiangolo.com/), ensuring high performance and asynchronous capabilities.
- **👁️ Real-Time Face Detection:** Utilizes OpenCV's robust `haarcascade_frontalface_default` to draw bounding boxes around faces instantaneously.
- **🎥 Live Video Streaming:** Streams MJPEG (Motion JPEG) seamlessly to any modern web browser without needing complex frontend code.
- **🧩 Minimal & Clean Codebase:** Easy to read, understand, and modify for your own custom computer vision tasks.

## 🚀 Getting Started

### Prerequisites

Make sure you have Python installed on your system. It is highly recommended to use a virtual environment.

### Installation

1. **Clone the repository** (if applicable) or download the source code:
   ```bash
   git clone https://github.com/Manav1918/fastapi-face-tracker.git
   cd "FastAPI cam"
   ```

2. **Create a Virtual Environment** (Optional but recommended):
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
   *The main dependencies include `fastapi`, `uvicorn`, and `opencv-python`.*

### Running the Application

Start the FastAPI development server by running `main.py` directly:

```bash
python main.py
```

*Alternatively, you can run it via Uvicorn:*
```bash
uvicorn main:app --reload
```

## 📡 API Endpoints

Once the server is running (default is `http://127.0.0.1:8000`), you can access the following endpoints:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET`  | `/`      | **Status Check:** Returns a JSON response indicating the app is live. |
| `GET`  | `/video` | **Video Stream:** Returns the live webcam feed with face detection bounding boxes. Open this endpoint directly in your browser! |

### Try it out!
1. Open your browser and go to: [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to check the status.
2. Go to: [http://127.0.0.1:8000/video](http://127.0.0.1:8000/video) to see your webcam feed with real-time face tracking.

## 🛠️ How it Works

1. **Capture:** `cv2.VideoCapture(0)` connects to your primary webcam.
2. **Process:** In the `generate_frames` generator, each frame is converted to grayscale, and `face_cascade.detectMultiScale` finds faces.
3. **Annotate:** `cv2.rectangle` draws blue boxes around detected faces.
4. **Stream:** Frames are encoded into `.jpg` bytes and yielded as a continuous `multipart/x-mixed-replace` stream.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
