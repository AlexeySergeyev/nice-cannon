# Lightning Distance Analysis: Nice Midday Cannon

## Overview
This project analyzes video and audio recordings to calculate the distance to a lightning strike using the time difference between the visual flash and thunder sound. The analysis uses footage captured during a lightning event that coincided with the famous Nice Midday Cannon tradition in Nice, France.

The Nice Midday Cannon ("le canon de midi") is a beloved tradition dating back to 1863, where a loud boom is heard precisely at noon every day. This project leverages modern digital signal processing and computer vision techniques to demonstrate the classic "flash-to-thunder" distance calculation method with scientific precision.

![Lightning Analysis](figs/output.png)

The notebook implements a comprehensive lightning distance analysis that combines:

## Methodology

1. **Audio Extraction and Processing**:
   - Extract audio track from MP4 video file using MoviePy
   - Load audio signal using Librosa for detailed waveform analysis
   - Identify thunder sound by detecting peak amplitudes in the audio signal
   - Precisely time the thunder occurrence to millisecond accuracy

2. **Video Frame Analysis**:
   - Process video frames to detect the lightning flash
   - Analyze RGB color channel intensities across time windows
   - Identify the frame with maximum blue channel intensity (characteristic of lightning)
   - Calculate exact timing of the visual flash

3. **Timing Synchronization**:
   - Calculate the time difference between lightning flash and thunder sound
   - Account for the instantaneous nature of light vs. sound propagation
   - Apply error analysis for measurement precision

4. **Distance Calculation**:
   - Use physics formula: **Distance = Time Delay × Speed of Sound**
   - Apply temperature-corrected speed of sound (~340 m/s at 15°C)
   - Provide results in multiple units (meters, kilometers, feet)
   - Include uncertainty analysis and error margins

## Physics Background
The speed of sound in air varies with temperature: v = 331.3 × √(1 + T/273.15)
- At 15°C: ~340 m/s
- At 20°C: ~343 m/s

Since light travels much faster than sound (~3×10⁸ m/s), we can assume the lightning flash is seen instantaneously while thunder arrives later. This time difference directly correlates to distance.

## Features
- **Audio Signal Processing**: Extract and analyze audio from MP4 video files using MoviePy and Librosa
- **Thunder Detection**: Precise timing analysis of audio waveforms to identify thunder peaks
- **Video Frame Analysis**: Computer vision techniques to detect lightning flash in video sequences
- **Color Channel Analysis**: RGB intensity analysis to pinpoint lightning occurrence
- **Distance Calculation**: Physics-based calculation using speed of sound and time difference
- **Interactive Visualizations**: Comprehensive plots for waveforms, intensity analysis, and frame inspection
- **Error Analysis**: Uncertainty quantification and measurement precision assessment
- **Multi-unit Results**: Distance output in meters, kilometers, and feet
- **Professional Documentation**: Complete methodology explanation and physics background

## Technical Capabilities
- Handles MP4 video files with synchronized audio
- Frame-by-frame video analysis with customizable regions of interest
- High-precision audio sampling and waveform analysis
- Temperature-corrected speed of sound calculations
- Matplotlib-based scientific visualizations
- Interactive Jupyter notebook environment

## Repository Structure
```
nice-cannon/
├── cannon.ipynb              # Main Jupyter notebook with lightning distance analysis
├── README.md                 # Project documentation and usage guide
├── requirements.txt          # Python package dependencies
├── data/                     # Input data files
│   ├── video_2022-11-08_08-31-43.mp4  # Original lightning video recording
│   └── audio.wav             # Extracted audio file for processing
└── figs/                     # Output visualizations and figures
    └── output.png            # Sample analysis output visualization
```

## Dependencies
- **Python**: 3.8+ (tested with Python 3.12.3)
- **Jupyter**: Notebook or JupyterLab environment
- **FFmpeg**: Required for video/audio processing (system dependency)
- **Python Libraries**: See requirements.txt for complete list
- Required Python libraries (listed in `requirements.txt`):
  - imageio>=2.31.0
  - moviepy==1.0.3
  - numpy>=1.24.0
  - matplotlib>=3.7.0
  - librosa>=0.10.0
  - ipython>=8.0.0
  - jupyter>=1.0.0

## Installation

### Prerequisites
Ensure you have Python 3.8+ and FFmpeg installed on your system:

**FFmpeg Installation:**
- **Ubuntu/Debian**: `sudo apt update && sudo apt install ffmpeg`
- **macOS**: `brew install ffmpeg`
- **Windows**: Download from https://ffmpeg.org/ and add to PATH

### Setup Instructions

1. **Clone the repository:**
```bash
git clone https://github.com/AlexeySergeyev/nice-cannon.git
cd nice-cannon
```

2. **Create and activate a virtual environment (recommended):**
```bash
python -m venv .venv

# On Linux/macOS:
source .venv/bin/activate

# On Windows:
.venv\Scripts\activate
```

3. **Install Python dependencies:**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

4. **Verify installation:**
```bash
python -c "import moviepy.editor, librosa, numpy, matplotlib; print('All packages installed successfully!')"
```
## Usage

### Running the Analysis

1. **Start Jupyter Notebook:**
```bash
jupyter notebook cannon.ipynb
```
   Or use JupyterLab:
```bash
jupyter lab cannon.ipynb
```

2. **Execute the notebook sections in order:**

   **Section 1: Setup and Imports** (Cells 1-4)
   - Import required libraries (MoviePy, Librosa, NumPy, Matplotlib)
   - Configure visualization settings
   - Verify all dependencies are working

   **Section 2: File Input and Verification** (Cells 5-7)
   - Define input video file path
   - Verify file existence and properties
   - Display file information

   **Section 3: Audio Extraction** (Cells 8-9)
   - Extract audio track from MP4 video using MoviePy
   - Save audio as WAV file for processing
   - Load audio with Librosa for analysis

   **Section 4: Audio Analysis** (Cells 10-16)
   - Visualize audio waveform in time windows
   - Interactive audio playback for verification
   - Detailed waveform analysis to detect thunder peaks
   - Precise timing calculation for thunder occurrence

   **Section 5: Video Processing** (Cells 17-19)
   - Load video for frame-by-frame analysis
   - Display sample frames and regions of interest
   - Extract video metadata (FPS, duration, dimensions)

   **Section 6: Lightning Detection** (Cells 20-26)
   - Analyze video frames in lightning time window
   - Calculate RGB color channel intensities
   - Identify maximum blue channel intensity (lightning flash)
   - Verify detection with detailed frame inspection

   **Section 7: Distance Calculation** (Cells 27-29)
   - Calculate time difference between flash and thunder
   - Apply physics formula with temperature-corrected speed of sound
   - Display comprehensive results with error analysis

   **Sections 8-9: Results and Conclusion** (Cells 30-31)
   - Summary of methodology and key findings
   - Accuracy considerations and conclusions

### Expected Results
The analysis will produce:
- **Audio Visualizations**: Waveform plots highlighting thunder detection
- **Video Analysis**: Frame intensity plots showing lightning flash
- **Timing Measurements**: Precise timestamps for both events
- **Distance Calculation**: Final result in multiple units with error margins

**Sample Output:**
```
=== LIGHTNING DISTANCE ANALYSIS ===

Timing measurements:
  Flash detected at:  39.XXX s
  Thunder detected at: 50.XXX s
  Time difference:     XX.XXX ± 0.016 s

Physics calculation:
  Speed of sound:      340 m/s (at ~15°C)
  Distance formula:    Distance = Time × Speed

=== FINAL RESULT ===
Lightning distance: XXXX ± XX meters
                   = X.XX ± 0.XX km
                   = XXXX ± XX feet
```

## Troubleshooting

### Common Issues and Solutions

#### MoviePy Import Errors
**Problem**: `ModuleNotFoundError: No module named 'moviepy.editor'`

**Solutions**:
1. Ensure you're using the correct MoviePy version:
   ```bash
   pip uninstall moviepy
   pip install moviepy==1.0.3
   ```
2. Restart your Jupyter kernel: **Kernel → Restart & Clear Output**
3. Check your virtual environment is activated
4. Verify installation: `python -c "import moviepy.editor; print('MoviePy working!')"`

#### FFmpeg Related Issues
**Problem**: FFmpeg not found or codec errors

**Solutions**:
1. Verify FFmpeg installation: `ffmpeg -version`
2. Reinstall imageio-ffmpeg: `pip install --upgrade imageio-ffmpeg`
3. On Windows, ensure FFmpeg is in your system PATH
4. Try alternative installation: `conda install ffmpeg` (if using Conda)

#### Audio Processing Issues
**Problem**: Cannot extract or process audio

**Solutions**:
1. Verify video file exists: `ls -la data/video_2022-11-08_08-31-43.mp4`
2. Check video has audio track: `ffprobe data/video_2022-11-08_08-31-43.mp4`
3. Ensure sufficient disk space for audio.wav file
4. Check file permissions: `chmod 644 data/*`

#### Librosa/Audio Library Issues
**Problem**: Audio analysis fails or produces errors

**Solutions**:
1. Update librosa: `pip install --upgrade librosa`
2. Install additional audio dependencies: `pip install soundfile`
3. Clear any corrupted audio files: `rm data/audio.wav` and re-run extraction
4. Check sample rate compatibility in the notebook

**Solutions**:
1. Restart kernel: **Kernel → Restart & Clear Output**
2. Check memory usage (large video files can consume significant RAM)
3. Run cells individually rather than "Run All"
4. Update Jupyter: `pip install --upgrade jupyter`

#### Visualization Problems
**Problem**: Plots don't display or show incorrectly

**Solutions**:
1. Ensure matplotlib backend: `%matplotlib inline` in a cell
2. Update matplotlib: `pip install --upgrade matplotlib`
3. Clear output and re-run: **Cell → All Output → Clear**
4. Check display settings in your Jupyter environment

## Scientific Background

This project demonstrates practical applications of:

### Digital Signal Processing (DSP)
- **Audio Signal Analysis**: Time-domain waveform analysis for event detection
- **Sampling Theory**: Working with audio sampling rates and temporal resolution
- **Signal Peak Detection**: Identifying thunder signatures in noisy audio environments

### Computer Vision
- **Frame Analysis**: Sequential video frame processing and analysis
- **Color Space Analysis**: RGB channel intensity analysis for lightning detection
- **Temporal Analysis**: Time-series analysis of visual intensity changes

### Applied Physics
- **Acoustics**: Sound propagation speed calculation with temperature corrections
- **Wave Physics**: Understanding the fundamental differences between light and sound propagation
- **Measurement Theory**: Error analysis and uncertainty quantification

### Mathematical Methods
- **Statistical Analysis**: Peak detection algorithms and intensity measurements
- **Numerical Computing**: Array processing and mathematical operations with NumPy
- **Data Visualization**: Scientific plotting and result presentation

## Educational Value
This notebook serves as an excellent example for:
- **STEM Education**: Combining physics, mathematics, and computer science
- **Data Science**: Real-world application of signal processing techniques
- **Scientific Computing**: Using Python for scientific analysis and visualization
- **Research Methods**: Systematic approach to data collection, analysis, and presentation

## Contributing
We welcome contributions! Areas for improvement include:
- Enhanced detection algorithms
- Additional visualization features
- Performance optimizations
- Documentation improvements
- Test data sets
- Educational materials

Please feel free to submit issues or pull requests.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- **Nice Tourism Office**: For the historical context of the Nice Midday Cannon
- **Open Source Community**: For the excellent Python libraries that make this analysis possible
- **Scientific Community**: For the foundational physics and signal processing knowledge

## Citation
If you use this code for research or educational purposes, please cite:
```
Sergeyev, A. (2025). Lightning Distance Analysis: Nice Midday Cannon. 
GitHub repository: https://github.com/AlexeySergeyev/nice-cannon
```

## Contact
- **Author**: Alexey Sergeyev
- **GitHub**: [@AlexeySergeyev](https://github.com/AlexeySergeyev)

For questions, suggestions, or collaboration opportunities, please don't hesitate to reach out!
