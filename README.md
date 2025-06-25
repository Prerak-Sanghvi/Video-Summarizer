# Video Scene Segmentation & Summary Generator

This project automatically processes long videos (like lectures or tutorials), breaks them into scenes, transcribes the audio, summarizes each part, and generates a clean HTML report with timestamps, keyframes, and summaries.

---

## Project Goal

The goal was to build an end-to-end pipeline that could:

- Detect scene changes in a video
- Extract keyframes for each detected scene
- Transcribe audio using a speech-to-text model
- Generate a summary for each scene
- Output a structured HTML report with all relevant information

---

## What I Was Asked To Do (And What I Built)

| **Requirement**                        | **Implementation**                                               |
|----------------------------------------|------------------------------------------------------------------|
| Shot boundary detection                | Used PySceneDetect with content-based thresholding               |
| Keyframe extraction                    | Captured keyframes at scene start using OpenCV                   |
| Audio transcription (optional task)    | Used OpenAI Whisper for accurate speech-to-text conversion       |
| Text summarization using Transformers  | Applied BART (`facebook/bart-large-cnn`) on each transcript chunk|
| Redundancy filtering (optional task)   | Merged similar summaries using cosine similarity with Sentence-BERT |


---

## Additional Features I Added

To make the project more robust, I added:

- Scene-aware transcript splitting using timestamp alignment
- Sub-chunking of long scenes to avoid memory errors during summarization
- CPU-safe configuration: optimized everything to run smoothly on CPU (no GPU needed)
- Merged similar summaries to reduce repetition using cosine similarity
- Graceful fallback: when no scenes are detected, it treats the whole video as one scene
- Image embedding: keyframes are embedded into the HTML using base64 for easy sharing
- Clean HTML output: well-structured, visually scannable report
- All built and tested using Google Colab on CPU (no external dependencies or GPUs)

---

## How It Works

Just run the pipeline and upload any `.mp4` video file. The script automatically:

1. Detects scenes in the video
2. Extracts a keyframe for each scene
3. Transcribes the audio using Whisper
4. Aligns the transcript with scene timestamps
5. Summarizes each transcript chunk using BART
6. Merges any redundant summaries
7. Generates a report in `summary.html`

---

## What You Can Do With This

Once you run the pipeline, you'll be able to:

- Upload any `.mp4` file
- Automatically detect visual scene transitions
- Generate a clean, scrollable HTML summary
- View each scene's start/end time, keyframe, and summary
- Download the report instantly

---

## Sample Output (summary.html)

Each section of the report includes:

- Start and end timestamps for the scene
- A visual keyframe taken from the scene
- A short summary based on transcribed audio

The report is saved as `summary.html` and can be downloaded or shared directly.

---

## Skills Demonstrated

- Scene detection and segmentation using video analysis
- Audio transcription using Whisper
- Natural language processing and summarization with transformers
- Cosine similarity for redundancy removal
- HTML generation and base64 image embedding
- Resource-efficient engineering: CPU-only implementation

---

## Technical Stack

- Python (Colab)
- PySceneDetect
- OpenCV
- Whisper (OpenAI)
- HuggingFace Transformers (BART)
- Sentence-BERT for similarity detection
- MoviePy
- HTML and Base64 for report generation

---

## Platform and Environment

This entire project was developed and tested on **Google Colab**, using **CPU only**. No GPUs or external hardware were required, making it lightweight and accessible.

---

## How to Run It

1. Upload the `.mp4` video file when prompted.
2. The pipeline runs automatically, step-by-step.
3. At the end, a downloadable file named `summary.html` is generated.

---

## Proof of Work

uploaded `summary.html`



