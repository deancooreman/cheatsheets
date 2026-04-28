# Video Download & Transcription Workflow

This guide covers the full process: from extracting hidden video links on protected platforms to generating high-accuracy AI transcripts.

---

## Installing the Tools

**Prerequisites:** Python 3.9+ ([python.org](https://www.python.org/downloads/) — check "Add to PATH") and ffmpeg:

```powershell
winget install ffmpeg
```

**yt-dlp:**
```powershell
pip install yt-dlp          # or: winget install yt-dlp
```

**Whisper:**
```powershell
pip install openai-whisper
```

> **Note:** The first time you run a model (e.g. `medium`), Whisper downloads it automatically. Subsequent runs use the cached version.

---

## Step 1: Extracting the Video Link (DevTools)

Most educational platforms hide their direct video files. You must find the **Master Manifest**.

1. **Open Video:** Load the video in your browser (Firefox, Chrome, or Edge).
2. **Open DevTools:** Press `F12` (or right-click -> **Inspect**).
3. **Network Tab:** Click on the **Network** tab at the top.
4. **Filter:** In the search box, type `master.m3u8`.
5. **Copy URL:** Right-click the result and select **Copy** -> **Copy URL**.
   * *If multiple links appear, they represent different streams (e.g., slides vs. camera).*

---

## Step 2: Downloading the Video (yt-dlp)

Use `yt-dlp` to download the stream. We use your browser's cookies to bypass login (SSO) and a "referer" to prevent 403 errors.

```powershell
yt-dlp --cookies-from-browser firefox --referer "https://your-platform.com/" -o "Lecture_01.mp4" "PASTE_M3U8_URL_HERE"
```

* **Browser:** Change `firefox` to `chrome` or `edge` if necessary.
* **Referer:** The base URL of the site — prevents "403 Forbidden" errors.
* **`-o`:** Output filename. Omit for an auto-generated name.

---

## Step 3: Transcribing the Video (Whisper)

Convert your downloaded `.mp4` into a text document using OpenAI's Whisper.

```powershell
python -m whisper "filename.mp4" --language English --model medium
```

* **Filename:** Use the **Tab** key to auto-complete long filenames.
* **`--language`:** Set to your spoken language (e.g. `English`, `French`, `German`). Omit to let Whisper auto-detect.
* **Model:** `medium` is the sweet spot for accuracy in technical/academic content.
* **Output:** Whisper saves `.txt` (plain text), `.srt` (subtitles), and `.vtt` in the same folder.

---

## Cheatsheet

### yt-dlp

| Goal | Command |
| :--- | :--- |
| **Basic download** | `yt-dlp "URL"` |
| **Bypass login/SSO** | `yt-dlp --cookies-from-browser firefox "URL"` |
| **Bypass login + referer** | `yt-dlp --cookies-from-browser firefox --referer "https://your-platform.com/" "URL"` |
| **Custom filename** | `yt-dlp -o "Lecture_01.mp4" "URL"` |
| **Download as MP3** | `yt-dlp -x --audio-format mp3 "URL"` |
| **List available formats** | `yt-dlp -F "URL"` |
| **Pick a specific format** | `yt-dlp -f 22 "URL"` |
| **Cookies from file** | `yt-dlp --cookies cookies.txt "URL"` |

### Whisper

| Goal | Command |
| :--- | :--- |
| **Specific language** | `python -m whisper "file.mp4" --language English --model medium` |
| **Fastest (draft)** | `python -m whisper "file.mp4" --model base` |
| **High accuracy** | `python -m whisper "file.mp4" --model large-v3` |
| **Translate to English** | `python -m whisper "file.mp4" --task translate` |
| **Plain text only** | `python -m whisper "file.mp4" --output_format txt` |
| **Save to folder** | `python -m whisper "file.mp4" --output_dir ./transcripts` |

### Whisper Model Reference

| Model | Size | Speed | Best for |
| :--- | :--- | :--- | :--- |
| `tiny` | 39 MB | Fastest | Quick drafts, English only |
| `base` | 74 MB | Fast | Short clips, testing |
| `small` | 244 MB | Moderate | Good balance |
| `medium` | 769 MB | Slow | Technical/academic content |
| `large-v3` | 1.5 GB | Slowest | Maximum accuracy |
