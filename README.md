# News2Video-AI  - Text-to-Video News Generator

This project converts written news text into a narrated video complete with AI-generated images, audio narration, and synchronized video output. The workflow is designed to run in Google Colab and uses state-of-the-art diffusion models along with text-to-speech and video processing libraries.

## Features

* Automatically splits news text into sentences.
* Generates an AI image for each sentence using a diffusion model.
* Produces corresponding audio narration using Google Text-to-Speech (gTTS).
* Creates a frame-based video with OpenCV.
* Merges all audio and video segments into a final MP4 video using FFmpeg.

## Requirements

The following Python libraries and system packages will be installed automatically in Colab:

* `torch`
* `diffusers`
* `transformers`
* `accelerate`
* `gTTS`
* `pydub`
* `opencv-python-headless`
* `numpy`
* `ffmpeg` (system package)

## Project Structure

The script automatically creates folders to store generated media:

```
/content/images/   # Stores generated images
/content/audio/    # Stores generated audio clips
/content/final_news_video.mp4  # Final output video
```

## How It Works

### 1. Install Dependencies

The notebook installs all required packages and FFmpeg.

### 2. Input Your Text

Provide your news text inside the `news_text` variable. The script splits your input into individual sentences.

### 3. Generate Images

Each sentence is used as a prompt for the diffusion model to generate an image.

### 4. Generate Audio

The same sentence is fed into gTTS to produce an audio narration clip.

### 5. Build Video Frames

OpenCV compiles each AI-generated image into video frames, repeating frames based on audio duration.

### 6. Merge Audio and Video

All audio segments are combined, then merged with the generated video using FFmpeg.

### 7. Display Output

The final MP4 video is displayed directly inside Colab.

## Model Used

The project loads a diffusion model from:

```
common-canvas/CommonCanvas-S-NC
```

This model generates relevant visual content from each sentence.

## Example Snippet

Here is the core logic to load the model and generate an image:

```python
pipe = DiffusionPipeline.from_pretrained(
    "common-canvas/CommonCanvas-S-NC",
    dtype=torch.float16,
    device_map=device
)
img = pipe(sent).images[0]
img.save(img_path)
```

## Output

Your final rendered video is saved as:

```
/content/final_news_video.mp4
```

You can download it directly from Colab.

## Notes

* GPU runtime in Colab is recommended for faster image generation.
* The pipeline may take several minutes depending on the number of sentences.

---

This README is ready to be added to your GitHub repository to explain the Text-to-Video News Project clearly and professionally.
