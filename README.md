# VLM Multi-Object Tracking

A Visual Language Model (VLM) based multi-object tracking system that combines traditional computer vision tracking algorithms with modern Vision-Language Models for enhanced object tracking capabilities.

## Overview

This project implements a hybrid approach to multi-object tracking by integrating:
- Traditional OpenCV tracking algorithms (CSRT, KCF, MOSSE, MIL, Boosting, TLD, MedianFlow)
- Qwen 2.5-VL (Vision-Language Model) for intelligent object detection and analysis
- Real-time video processing capabilities

## Features

- **Multiple Tracking Algorithms**: Support for 7 different OpenCV tracking algorithms
- **VLM Integration**: Uses Qwen 2.5-VL-3B-Instruct model for advanced object understanding
- **Interactive Object Selection**: Click-to-select objects in the first frame
- **Real-time Processing**: Efficient frame-by-frame tracking with visual feedback
- **Flexible Input/Output**: Supports various video formats and saves tracked results

## Installation

### Prerequisites

```bash
pip install git+https://github.com/huggingface/transformers
pip install qwen-vl-utils
pip install openai
pip install flash-attn --no-build-isolation
pip install opencv-python
pip install torch
pip install pillow
```

### GPU Requirements

- CUDA-compatible GPU recommended
- Supports bfloat16 precision for memory efficiency

## Usage

### Quick Start

1. **Upload your video** to the Colab environment or specify the path:
```python
video_file = "/content/your_video.mp4"
```

2. **Run the tracking system**:
```python
if __name__ == "__main__":
    video_file = "/content/video.mp4"  # absolute path
    output_file = "/content/tracked_output.mp4"
    tracker_name = "csrt"  # or "kcf", "mosse", etc.
    
    track_objects_in_video(video_file, output_file, tracker_name)
```

### Supported Tracking Algorithms

- **CSRT** (Channel and Spatial Reliability Tracker) - Recommended for accuracy
- **KCF** (Kernelized Correlation Filters) - Good balance of speed and accuracy
- **MOSSE** (Minimum Output Sum of Squared Error) - Fastest option
- **MIL** (Multiple Instance Learning)
- **Boosting**
- **TLD** (Tracking-Learning-Detection)
- **MedianFlow**

### Interactive Object Selection

1. The system will display the first frame of your video
2. Click on objects you want to track
3. Press 'SPACE' to confirm selections
4. Press 'ESC' to start tracking

## Project Structure

```
├── VLM_object_tracking.ipynb    # Main implementation notebook
├── Result/                      # Output directory for tracked videos
└── README.md                   # This file
```

## Technical Details

### VLM Integration

The system uses Qwen 2.5-VL-3B-Instruct model for:
- Intelligent object detection
- Scene understanding
- Enhanced tracking decision making

### Performance Optimization

- **Device Mapping**: Automatic GPU allocation
- **Memory Management**: bfloat16 precision to reduce memory usage
- **Efficient Processing**: Frame-by-frame processing with minimal latency

## Links

- **Demo Notebook**: [Google Colab](https://colab.research.google.com/drive/1ykYKMwj9uwobXbj3zZJmLR9D7oMzQDf0?usp=sharing)
- **Source Code**: [GitHub Repository](https://github.com/Patrick-zhuyanxun/VLM-Multi-Object-Tracking.git)
- **Qwen 2.5-VL Documentation**: [Official Blog](https://qwenlm.github.io/blog/qwen2.5-vl/)

## Research References

- **CSRT Tracker**: [Discriminative Correlation Filter with Channel and Spatial Reliability](https://openaccess.thecvf.com/content_cvpr_2017/html/Lukezic_Discriminative_Correlation_Filter_CVPR_2017_paper.html)
- **Object Tracking Overview**: [Medium Article](https://medium.com/@khwabkalra1/object-tracking-2fe4127e58bf)

## Author

**朱彥勳 (Patrick Zhu)**  
Final Project Report - 2025

## License

This project is available for academic and research purposes. Please cite appropriately if used in academic work.

## Troubleshooting

### Common Issues

1. **CUDA Memory Error**: Reduce batch size or use CPU processing
2. **Model Loading Issues**: Ensure stable internet connection for model download
3. **Video Format Issues**: Convert to MP4 format for best compatibility

### Performance Tips

- Use CSRT for best tracking accuracy
- Use MOSSE for fastest processing
- Ensure sufficient GPU memory (8GB+ recommended)
- Process videos at lower resolution for faster results

## Contributing

Feel free to submit issues and enhancement requests through the GitHub repository.
