# AR Lung Model Renderer

This Python script allows you to render a 3D lung model using a live camera feed and ArUco markers. The `AR_render` class uses OpenGL to display the 3D lung model on a background captured from the camera. You can control the size and position of the lung model using keyboard inputs.

## Prerequisites

- Python 3.6 or later
- PyOpenGL: Download the appropriate PyOpenGL accelerate wheel file from [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyopengl) based on your Python version and operating system. Add the downloaded file to the working folder and install it using:
```
pip install name-file.whl

```

## Installation

Install the required dependencies by running:
```
pip install -r requirements.txt
```


## Running the Script

1. Ensure that you have Python 3.6 or later installed.
2. Download the PyOpenGL accelerate wheel file from the provided link and add it to the working folder. Install it using the command mentioned in the prerequisites.
3. Run the following command to install other required dependencies:

```
pip install -r requirements.txt
```

4. Execute the script using:
```
python AR_entrance.py
```

## Usage

Once the script is running, a live camera feed will appear, and the 3D lung model will be rendered on ArUco markers. You can control the size and position of the model using the following keyboard inputs:

- Increase model size: `=`
- Decrease model size: `-`
- Move model left: `a`
- Move model right: `d`
- Move model up: `w`
- Move model down: `s`

## Credits

- The code is inspired by the example available [here]([https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyopengl](https://github.com/BryceQing/OPENCV_AR/tree/master)).

## Future Work

The current implementation allows for basic interaction with the 3D lung model.
Future work includes implementing hand gesture recognition for more intuitive control.
Additionally, the code can be optimized to run on NVIDIA GPU for improved performance.

