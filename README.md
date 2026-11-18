# ArUco Augmented Reality

**A 3D lung model anchored to a live camera feed.**

[Setup](#setup) · [Controls](#controls) · [Implementation](#implementation) · [Portfolio](https://github.com/badredddineazzaz)

This Python prototype combines OpenCV marker detection with an OpenGL renderer. It estimates an ArUco marker’s pose, converts camera and pose matrices for rendering, and draws the bundled OBJ lung model over the webcam image.

## Features

- Detection and pose estimation for markers in the `DICT_6X6_250` dictionary.
- Live camera background and textured OBJ model loading.
- Camera projection and model-view transformations.
- Keyboard control of model scale and translation offsets.

## Setup

This is a legacy prototype, not a verified one-command installation. The dependency file pins OpenCV 4.1.1.26, NumPy 1.16.5 and Pillow 6.2.0. These old versions may require an older Python environment and compatible wheels. A working Python/OS combination has not been revalidated.

1. Clone the repository and enter its root directory:

```bash
git clone https://github.com/badredddineazzaz/ARUCO-AR-3d.git
cd ARUCO-AR-3d
```

2. Create an isolated Python environment compatible with those pinned versions. The recorded dependency installation command is:

```bash
python -m pip install -r requirements.txt
```

3. The entry point also imports **PyOpenGL** and **imutils**, which are missing from `requirements.txt`. Install compatible versions in that environment. OpenGL/GLUT must be available on the host. The file lists both `opencv-python` and `opencv-contrib-python`; they share the `cv2` namespace, so the dependency list needs reconciliation before claiming a reproducible setup.
4. Connect a webcam and prepare a `DICT_6X6_250` marker. The code opens camera index **1**, uses a marker size of **0.06** in the rendering call, and contains fixed camera calibration values. These must match your hardware and marker for meaningful pose estimation. They are source constants, not command-line options.
5. From the repository root, the entry point is:

```bash
python AR_entrance.py
```

The model path is relative to the working directory: `Models/lungLast/lung.obj`. Camera capture and rendering were not executed during this documentation review.

## Controls

Give the OpenGL window keyboard focus.

| Key | Effect implemented in the callback |
| --- | --- |
| `=` | Increase scale by 0.01 |
| `-` | Decrease scale by 0.01 |
| `w` / `s` | Decrease / increase `translate_x` |
| `a` / `d` | Decrease / increase `translate_y` |

The renderer currently passes `translate_y` to both the Y and Z translation arguments. The table describes the actual variables rather than promising independent screen-space movement.

## Implementation

| File | Purpose |
| --- | --- |
| [AR_entrance.py](AR_entrance.py) | Camera capture, ArUco pose estimation, OpenGL rendering and controls |
| [MatrixTransform.py](MatrixTransform.py) | Camera and pose matrix conversions |
| [Filter.py](Filter.py) | Pose update filtering |
| [objloader.py](objloader.py) | OBJ/material loading |
| [Models/lungLast](Models/lungLast) | Bundled model assets |

## Status and next steps

The prototype uses legacy ArUco APIs and fixed device parameters. Reproducible dependencies, configurable calibration and camera selection deserve attention before a modernized release. Hand-gesture control and NVIDIA GPU optimization were ideas in the original README; they are not implemented features.

## Credits

Inspired by [BryceQing/OPENCV_AR](https://github.com/BryceQing/OPENCV_AR/tree/master), as credited in the original documentation.
