Hand HUD — palm-anchored kinematic dashboard

This project captures webcam input, detects a hand using MediaPipe, and draws a white, mechanical-style kinematic HUD over the hand (palm-centered radial UI, finger bones, rotation readout, small 3D cube and grid) similar to the reference images.

## Files

- `requirements.txt` — Python dependencies
- `main.py` — application entrypoint and webcam loop
- `hand_overlay.py` — functions for drawing the HUD and computing kinematics
- `utils.py` — small helpers (smoothing, geometry)

## How to run (Windows PowerShell)

1. Create and activate a virtual environment (optional but recommended):

   python -m venv .venv; .\.venv\Scripts\Activate.ps1

2. Install dependencies:

   pip install -r requirements.txt

3. Run:

   python main.py

## How to run (Mac OS)

If you're having issues with MediaPipe installation on your Mac, follow these steps:

## Solution for MediaPipe on Mac OS

### 1. First, check your Python version
```bash
python --version
```

MediaPipe has compatibility issues with Python 3.13. If you're using Python 3.13, you'll need to downgrade.

### 2. Install MediaPipe for Apple Silicon
Try these specific installation methods:

**Option A: Install from specific wheel**
```bash
pip install mediapipe --no-cache-dir
```

**Option B: Try the silicon-specific package**
```bash
pip install mediapipe-silicon
```

**Option C: Use conda-forge (if you have conda)**
```bash
conda install -c conda-forge mediapipe
```

### 3. If the above doesn't work, create a new environment with Python 3.11
```bash
# Deactivate current environment
deactivate

# Create new environment with Python 3.11
python3.11 -m venv ml_env
source ml_env/bin/activate

# Now install packages
pip install --upgrade pip
pip install -r requirements.txt
```

### 4. If you don't have Python 3.11 installed, install it first:
```bash
# Using pyenv (recommended)
brew install pyenv
pyenv install 3.11.9
pyenv global 3.11.9

# Or using Homebrew
brew install python@3.11
```

### 5. Alternative: Install packages individually
If the requirements.txt still fails, install packages one by one:
```bash
pip install opencv-python
pip install numpy
pip install mediapipe
pip install pyautogui
# Add any other packages from your requirements.txt
```

### 6. Check your requirements.txt file
Make sure your `requirements.txt` doesn't have any typos. It should look something like:
```
mediapipe>=0.10.1
opencv-python>=4.5.0
numpy>=1.19.0
```

### 7. If you're still having issues, try forcing the architecture:
```bash
# For Apple Silicon Macs
GRPC_PYTHON_BUILD_SYSTEM_OPENSSL=1 GRPC_PYTHON_BUILD_SYSTEM_ZLIB=1 pip install mediapipe
```

### 8. Verify installation
```bash
python -c "import mediapipe; print(mediapipe.__version__)"
python -c "import cv2; print(cv2.__version__)"
```

The most likely solution is **using Python 3.11** since MediaPipe often has compatibility issues with the very latest Python versions. Try option 3 first, as it resolves the issue in most cases.

Which step would you like to try first, or would you like me to help you check your current Python version?

## Notes

- Works with a single hand in frame. For multi-hand, toggle a flag in `main.py`.
- Tweak smoothing and drawing constants in `hand_overlay.py`.
- If you want recording/output images, I can add that next.

## Copyright & Attribution

This repository is published publicly by the original creator

You are welcome to fork, clone, and contribute to this project. If you reuse substantial parts of the code or publish derivative works, please give clear credit to the original author. A suggested credit line is:


Please keep a copy of this README and the `LICENSE` file in redistributed or forked versions so attribution remains visible.

## License

This project is released under the MIT License — see the `LICENSE` file included in this repository. The MIT License permits reuse, modification, and redistribution; please preserve the copyright notice and give credit to the original author when distributing or republishing the work.

If you'd prefer a license that explicitly requires attribution (for example, Creative Commons Attribution 4.0), let me know and I can switch the license file.

## Contributing

Contributions are welcome. To contribute:

1. Open an issue to discuss proposed changes or file a bug report.
2. Create a branch for your changes and open a pull request with a clear description.
3. Keep changes focused and include tests or usage notes when appropriate.

By submitting a pull request you agree that your contribution will be made under the repository's license (MIT by default).

