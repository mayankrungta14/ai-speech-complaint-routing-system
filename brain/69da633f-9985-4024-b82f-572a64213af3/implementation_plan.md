# Grievance Redressal AI Portal

## Goal
Build a web application where users can voice their complaints in Indian regional languages. The system will recognize the speech, translate it, analyze the content to categorize it into the correct Indian government department, provide the department's helpline details, and track the status of the complaint.

## User Review Required
> [!IMPORTANT]
> **API Key Requirements**: This project will require API keys for:
> 1. An AI model (like Google Gemini or OpenAI) for processing text and determining the department.
> 2. A Speech-To-Text API (like Google Cloud Speech API, Bhashini, or AssemblyAI) that supports Indian regional languages.
> 
> Let me know if you have preferences for these services or if you want to use mock services for the initial prototype.

## Open Questions
> [!WARNING]
> 1. **Tech Stack**: I propose **Next.js (React)** for the frontend and **Python (FastAPI)** for the backend. Does this stack work for you?
> 2. **Database**: Should we start with a simple local database (SQLite) for rapid prototyping, or would you prefer something else?
> 3. **Speech-to-Text**: Do you want to use browser-based built-in speech recognition (free, but browser-dependent language support) or record audio and send it to a dedicated AI backend service (highly accurate for regional languages, but requires API setup)?

## Proposed Architecture

- **Frontend**: Next.js app with an audio recording interface.
- **Backend**: FastAPI server to handle audio files, call AI APIs, and manage the database.
- **AI Processing Layer**:
  - **Speech-to-Text**: Transcribe regional audio to text.
  - **Translation & Classification**: Use an LLM to translate the transcript (if needed) and classify it into departments (e.g., Police, Electricity, Water, Municipal Corporation, etc.).
- **Database**: Store complaints (Audio URL, Transcript, Translation, Assigned Department, Status, Timestamps).

### [Backend Setup]

#### [NEW] backend/main.py
FastAPI application entry point. Handles routing for creating complaints, fetching status, and listing departments.

#### [NEW] backend/ai_service.py
Integration with AI models for Speech-to-Text, translation, and text classification.

#### [NEW] backend/database.py
Database models and connection setup using SQLAlchemy.

### [Frontend Setup]

#### [NEW] frontend/app/page.tsx
Main landing page with a microphone interface to record complaints.

#### [NEW] frontend/app/complaint/[id]/page.tsx
Complaint tracking page showing the current status, department details, and helpline numbers.

#### [NEW] frontend/components/AudioRecorder.tsx
React component to capture audio from the user's microphone.

## Verification Plan

### Manual Verification
- Start the Next.js frontend and FastAPI backend locally.
- Record a sample voice complaint in a regional language via the UI.
- Verify the system transcribes, translates, and assigns the correct department.
- Navigate to the complaint tracking page to ensure status and helpline details are correctly displayed.
