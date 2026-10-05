# Uzbek YouTube Video Transcription (Free and open source)

This repository provides a Google Colab notebook designed to download audio from YouTube videos, process it into a normalized format, and transcribe it into timed Uzbek subtitles (SRT format) using the specialized (BuzzASR/uzbek)[https://huggingface.co/BuzzASR/uzbek] automatic speech recognition model from HuggingFace.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bedilbek/uzbek-youtube-transcriber/blob/main/youtube_uzbek_subtitles.ipynb)

## ☑️ Features
- **Automated Download**: Uses `yt-dlp` alongside an isolated Node 22 JavaScript runtime to bypass modern bot detection systems.
- **Audio Normalization**: Downmixes audio to 16 kHz mono PCM (`wav`) for optimal model performance.
- **Specialized ASR Model**: Powered by the **BuzzASR/uzbek** model, leveraging PyTorch and Hugging Face's `transformers` with sequential long-form decoding to maintain context.
- **Caption Validation**: Validates generated timestamps and formats a clean UTF-8 `.srt` file wrapped beautifully to fit common screen constraints.
- **Secure Credentials Integration**: Optional Netscape cookie parser strictly isolated within your private runtime environment.

## ⚙️ Getting Started

1. **Open the Notebook**:
   Click the **Open In Colab** badge above or upload your notebook file directly to [Google Colab](https://colab.research.google.com/).

2. **Configure GPU Runtime**:
   Go to **Runtime** → **Change runtime type** and select a hardware accelerator (e.g., **GPU T4**, **A100**, or **L4**).

3. **Set Settings**:
   - Set `SOURCE` to `"youtube"`, `"upload"`, or `"path"`.
   - Paste your target `YOUTUBE_URL`.
   - Enable `SAVE_TO_DRIVE` if you wish to back up outputs.

4. **Run Cells**:
   Execute the notebook sequentially from top to bottom (**Runtime → Run all**).

## ∑ Optional: Bypassing YouTube Access Restrictions
If YouTube restricts direct downloads from Colab's public IPs:
1. Run `yt-dlp` locally on your machine with your browser session credentials:
   ```sh
   uvx --from 'yt-dlp[default]' yt-dlp --js-runtimes node --cookies-from-browser chrome --no-playlist -f 'bestaudio/best' -o 'audio.ext' 'YOUR_YOUTUBE_URL'
   ```
2. Upload the downloaded file to Colab and choose `SOURCE="upload"`.

## 📄 Outputs
- `*.segments.json`: Raw model output containing transcript segments and precise durations.
- `*.srt`: Formatted SubRip Subtitle file downloaded directly to your computer.
