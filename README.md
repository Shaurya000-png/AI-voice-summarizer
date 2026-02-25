# AI Voice Summarizer

AI Voice Summarizer is a full-stack prototype that turns voice notes into transcripts, concise summaries, action items, and playable audio summaries.

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

## Environment Variables

| Variable | Location | Purpose |
| --- | --- | --- |
| `OPENAI_API_KEY` | `backend/.env` | Authenticates requests to OpenAI APIs |

Do not commit `.env`; only the `.env.example` template belongs in the repository.

## Troubleshooting

- If recording fails, check browser microphone permissions and use `localhost` or HTTPS.
- If uploads fail, confirm the FastAPI server is running on port `8000`.
- If AI processing fails, verify that `OPENAI_API_KEY` is set in `backend/.env`.
- If audio playback is missing, check that the `backend/generated/` folder can be created.

## Cost Note

Each recording uses transcription, chat completion, and speech generation APIs. Short tests are inexpensive, but usage depends on audio length and current provider pricing.

## Development Commands

| Command | Directory | Description |
| --- | --- | --- |
| `npm run dev` | `frontend/` | Start the Vite dev server |
| `npm run build` | `frontend/` | Build frontend assets |
| `npm run lint` | `frontend/` | Run ESLint |
| `uvicorn main:app --reload` | `backend/` | Start the FastAPI API |

## Current Limitations

- Audio files are processed per request and generated summaries are stored locally.
- There is no user account system or persistent history yet.
- The frontend currently targets the local backend URL directly.

## Roadmap

- Save previous transcripts and summaries in a local or cloud database
- Support uploaded audio files in addition to browser recording
- Add summary length controls and meeting-style templates
- Add deployment configuration for a hosted frontend and backend

## License

MIT License. This project is intended for learning and portfolio demonstration.
