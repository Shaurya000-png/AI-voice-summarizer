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
