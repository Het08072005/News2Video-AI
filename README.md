# News2Video-AI
A lightweight AI tool that converts any news headline or short article text into a 30–60 second video using script generation and Hugging Face–based image/video models. The project automates the pipeline from text input to a fully rendered video with scenes, images, and text overlays.

This repository includes the full source code, Colab notebook, generation pipeline, and sample outputs.

---

## 🚀 Features

- Converts **headlines or article text** into a short video.  
- Automatically generates a **script**, **scene descriptions**, and **text overlays**.  
- Uses Hugging Face models for **image/video generation**.  
- Assembles final output using **MoviePy** or a similar tool.  
- Includes a ready-to-run **Google Colab notebook**.  
- Can be extended to scrape **trending news topics** automatically.

---

## 🛠️ How It Works (Pipeline)

1. **User Input**
   - User enters a news headline or article text.

2. **Script Generation**
   - A text generation model (Hugging Face transformer model like GPT-2 / FLAN-T5) creates a short 3–6 line script suitable for a 30–60 sec video.

3. **Scene Generation**
   - The script is divided into scenes.
   - For each scene, an image or short video is generated using a Hugging Face diffusion/video model.

4. **Video Assembly**
   - All scenes are merged.
   - Text overlays are added on top of each clip.
   - Background music can optionally be added.

5. **Output**
   - Final MP4 video is saved to `/outputs/videos/`.

---
