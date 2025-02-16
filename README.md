# Prompt-Based Video Analytics

A powerful video analysis tool that uses the Qwen2-VL vision-language model to analyze video content based on natural language prompts. The system can process videos frame by frame and provide both temporal analysis and summary insights.

## Direct Kaggle Links:
- Without GUI : https://www.kaggle.com/code/pavansai25/prompt-based-video-analytics-solution
- With GUI : https://www.kaggle.com/code/pavansaibheemisetty/vlmint1
Open the link and just run the ipynb file. GUI one may take more time to execute

## Features

- Supports multiple Qwen2-VL model sizes (2B, 7B, 72B)
- Adaptive analysis based on prompt type
- Timestamp-specific analysis for temporal queries
- Comprehensive video summaries for general queries
- GPU acceleration with CPU fallback support
- Configurable frame sampling rate

## Prerequisites

- Python 3.8+
- CUDA-capable GPU (optional but recommended)



## Dependencies

```txt
torch
transformers
opencv-python
pillow
matplotlib
```

## Usage

1. Basic usage:
```python
from video_analyzer import VideoAnalyzer


analyzer = VideoAnalyzer(model_size="7b")


results = analyzer.process_video(
    video_path="path/to/video.mp4",
    prompt="Describe the main activities in this video",
    frame_interval=30  # Optional: adjust frame sampling rate
)


for result in results:
    print(f"Timestamp: {result['timestamp']}")
    print(f"Analysis: {result['analysis']}")
```

2. Example prompts:

```python

prompt = "When do people appear in the video?"

prompt = "Describe the overall scene and activities in this video"

prompt = "Track the movement of vehicles in this video"
```

## Configuration

The `VideoAnalyzer` class supports different model sizes:

- `2b`: Lightweight model suitable for quick testing
- `7b`: Balanced model for general use (recommended)
- `72b`: Largest model for maximum accuracy

Select the model size during initialization:
```python
analyzer = VideoAnalyzer(model_size="7b")  # or "2b" or "72b"
```

## Output Format

The system provides results in two formats based on the prompt type:

1. Temporal Analysis:
```python
[
    {
        'timestamp': 1.23,  
        'analysis': 'Description of the frame...'
    },
    # ... more frames
]
```

2. Summary Analysis:
```python
[
    {
        'timestamp': 'Full Video',
        'analysis': 'Comprehensive summary of the video...'
    }
]
```

## Performance Considerations

- GPU acceleration is automatically used when available
- Frame interval can be adjusted to balance between processing speed and analysis granularity
- Memory usage scales with video length and frame sampling rate

## Limitations

- Processing time depends on video length and frame sampling rate
- GPU memory requirements increase with larger model sizes
- Analysis quality may vary based on video quality and content complexity

