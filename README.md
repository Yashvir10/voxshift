# VoxShift 🎙️

**AI-powered video dubbing pipeline** — upload a video, pick a target language, and get back a fully dubbed version with translated, natural-sounding voiceover and synced audio.

VoxShift automates the entire dubbing workflow: transcription → translation → speech synthesis → audio-video sync, wrapped in a simple web interface.

---

## ✨ Features

- 🎧 **Automatic transcription** of any video's speech using OpenAI Whisper
- 🌐 **Translation** into Hindi, Marathi, Tamil, Telugu, Bengali, or Gujarati
- 🗣️ **Natural neural voiceover** generation using Microsoft Edge TTS (native regional voices)
- ⏱️ **Timing-aware audio sync** — silence padding ensures the dubbed audio matches the original video's pacing
- 🎬 **Automatic merge** of the new audio track back onto the original video
- 🖥️ **Simple web UI** — upload, select language, track progress, and download the result

---

## 🧠 How It Works

1. **Speech-to-Text** — Whisper transcribes the input video's audio into timestamped subtitles (`.srt`)
2. **Translation** — Each subtitle line is translated into the target language via Deep Translator (Google Translate backend)
3. **Text-to-Speech** — Translated lines are converted into speech using Edge TTS, with a native voice model per language
4. **Sync** — FFmpeg inserts silence between segments so dubbed speech lines up with the original video's timing
5. **Merge** — The final audio track is combined with the original video, replacing the original audio track

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Speech-to-Text | OpenAI Whisper |
| Translation | Deep Translator (Google Translate) |
| Text-to-Speech | Microsoft Edge TTS |
| Media Processing | FFmpeg |
| Backend | Flask, Werkzeug, threading |
| Frontend | HTML, CSS, JavaScript |

---

## 📂 Project Structure

```
voxshift/
├── app.py                 # Flask web server
├── main.py                # Core dubbing pipeline (CLI-runnable)
├── templates/
│   └── index.html         # Web UI
├── uploads/                # Temporary uploaded videos (gitignored)
├── outputs/                 # Final dubbed videos (gitignored)
├── requirements.txt
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- [FFmpeg](https://ffmpeg.org/download.html) installed and available on your system PATH

### Installation

```bash
git clone https://github.com/<your-username>/voxshift.git
cd voxshift
pip install -r requirements.txt
```

### Run the web app

```bash
python app.py
```

Then open `http://localhost:5000` in your browser, upload a video, choose a target language, and download the dubbed output once processing completes.

### Run via CLI

```bash
python main.py <video_file> <language_code>
```

Supported language codes: `hi` (Hindi), `mr` (Marathi), `ta` (Tamil), `te` (Telugu), `bn` (Bengali), `gu` (Gujarati)

---

## 🗺️ Roadmap

- [ ] Add more target languages
- [ ] Real-time progress percentage during processing
- [ ] Support for longer videos with chunked processing
- [ ] Voice cloning option to preserve original speaker's tone
- [ ] Dockerize for easier deployment

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙋 Author

Built by **Yashvir Bhardwaj** — [GitHub](https://github.com/Yashvir10) · [LinkedIn](https://linkedin.com/in/yashvir-bhardwaj)
