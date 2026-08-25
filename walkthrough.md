# Grievance Redressal AI Portal - Walkthrough

## What was built
I have built a web portal where users can record their complaints in regional languages, and the AI (mocked for now, but ready for real API keys) will automatically categorize the complaint and assign it to a specific government department in India. 

### Features:
1. **Speech Recognition**: The frontend uses the browser's built-in Web Speech API (`SpeechRecognition`) configured for Hindi (`hi-IN`) as an example regional language. This translates spoken words directly into a transcript.
2. **AI Translation & Routing**: The Python FastAPI backend receives the transcript. Our simulated AI layer translates the text and uses keyword analysis to route it to the appropriate department:
   - *Water Board*
   - *Electricity Department*
   - *Police Department*
   - *Municipal Corporation*
   - *General Administration*
3. **Database Integration**: All complaints and their statuses are saved in a local SQLite database (`complaints.db`).
4. **Helpline Directory**: Once a complaint is routed, the UI immediately displays the relevant department's helpline number so the citizen knows who to call if they need urgent assistance.

## How to test it
1. Open your web browser and navigate to: **[http://localhost:8000/](http://localhost:8000/)**
2. Click the "**🎤 Start Recording**" button. You will be prompted to allow microphone access.
3. Speak a complaint in Hindi (e.g., "*Sadak par kachra pada hai*" or "*Bijli chali gayi hai*").
4. Click **Stop Recording**, then **Submit Complaint**.
5. You will see the AI assign a Complaint ID, route it to the correct department (e.g. Municipal Corporation), and display the department's helpline number!

## Future Improvements
To make it production-ready:
- Replace the browser Speech API with a robust regional AI speech model (like Bhashini API).
- Replace the mock text classification in `backend/ai_service.py` with the Gemini or OpenAI API to achieve deep semantic understanding of complaints.
- Upgrade the database to PostgreSQL.
