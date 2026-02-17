# AI Voice Summarizer

AI Voice Summarizer is a full-stack app that records voice notes, transcribes them, summarizes the text, extracts action items, and generates a spoken summary.

![Status](https://img.shields.io/badge/status-working_prototype-brightgreen)
![Stack](https://img.shields.io/badge/stack-React_%2B_FastAPI-blue)

## Features

- Browser-based voice recording with microphone permission handling
- Audio transcription through OpenAI Whisper
- AI summary generation using GPT-4o-mini
- Action item extraction from meetings, lectures, and notes
- Text-to-speech output for listening to the generated summary
- Clean React interface with loading, result, and playback states

## Tech Stack

- Backend: FastAPI, Python, Pydantic, python-multipart
- Frontend: React, Vite, Tailwind CSS
- AI APIs: Whisper, GPT-4o-mini, and TTS-1

## Requirements

- Node.js 18 or newer
- Python 3.8 or newer
- OpenAI API key with access to transcription, chat, and speech models

## Quick Start

```bash
git clone <repo-url>
cd AI-voice-summarizer
```

### Backend

```bash
cd backend
python -m venv venv
.\\venv\\Scripts\\activate
pip install -r requirements.txt
```

Create `backend/.env` from the example file and add your key:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

Run the API server:

```bash
uvicorn main:app --reload
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

- Backend: `http://localhost:8000`
- Frontend: `http://localhost:5173`

## API Overview

`POST /api/process-audio` accepts a multipart audio file under the `file` field.

The endpoint transcribes the audio, summarizes the transcript, extracts action items, creates an MP3 summary, and returns JSON.

### Example Response

```json
{
  "transcript": "Full transcription text",
  "summary": "Short generated summary",
  "action_items": ["Follow up with the team"],
  "audio_summary_url": "/generated/summary_file.mp3"
}
```

## Usage

1. Open the frontend in the browser and allow microphone access.
2. Start recording and stop when the voice note is complete.
3. Wait for the backend to transcribe, summarize, and generate audio output.
4. Review the transcript, summary, action items, and audio playback.

For best results, record in a quiet room and keep the note focused on one topic.

## Project Structure

```text
backend/
  main.py           FastAPI app and `/api/process-audio` endpoint
  services.py       OpenAI transcription, summary, and speech helpers
  models.py         Pydantic response schemas
  requirements.txt  Python dependencies

frontend/
  src/App.jsx                         Main page and upload workflow
  src/components/AudioRecorder.jsx    Microphone capture and upload
  src/components/SummaryView.jsx      Transcript, summary, and actions UI
  src/index.css                       Tailwind entry styles
```
