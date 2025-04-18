# Aura Tracker

This application uses speech recognition and Google's Gemini AI to analyze your speech and determine your "aura" in TikTok terms (whether you sound tough and confident or not) in real-time, with speaker recognition capabilities.

## Features

- Real-time speech-to-text conversion using the Web Speech API
- Speaker recognition to identify different people (Person 1, Person 2, Person 3)
- Premium text-to-speech using ElevenLabs API for high-quality voice synthesis
- Automatic aura analysis while you speak
- History table that tracks all aura readings with speaker identification
- Chat window to interact with the AI assistant
- Live speech display with speaker labeling
- Debug panel to monitor the application state

## How to Use

1. Click on "Start Speaking" to begin recording your speech
2. Speak into your microphone - analysis happens automatically as you speak
3. The app will attempt to identify which person is speaking
4. Each person's aura is analyzed separately
5. Results are announced through text-to-speech (if enabled)
6. Your analysis history is shown in the table with speaker labels

## Speaker Recognition

To train the app to recognize different speakers:

1. In the "Speaker Recognition" section, find the profile you want to train (Person 1, 2, or 3)
2. Click the "Train Voice" button for that profile
3. Start speaking clearly for about 15-30 seconds
4. Click "Stop Training" when you're done
5. Repeat for each person who will use the app

The system will then attempt to identify who is speaking during normal use and label their aura analysis accordingly.

## Premium Text-to-Speech

For higher quality voice synthesis:

1. Add your ElevenLabs API key in the src/App.tsx file 
   ```typescript
   const ELEVENLABS_API_KEY = "your-api-key-here";
   ```
2. Enable Text-to-Speech in the settings
3. Check "Use Premium Text-to-Speech"
4. Select your preferred voice from the dropdown
5. Click "Test Voice" to hear a sample

## Technical Details

- Built with React and TypeScript
- Uses the Web Speech API for speech recognition
- Simple voice fingerprinting for speaker identification
- Uses Google's Gemini 2.0 API for aura analysis
- Optional ElevenLabs integration for premium TTS
- Performs real-time analysis while you're speaking
- Responsive design for mobile and desktop

## Getting Started

1. Clone the repository
2. Install dependencies:
   ```
   npm install
   ```
3. If using ElevenLabs, add your API key to src/App.tsx
4. Start the development server:
   ```
   npm start
   ```
5. Open [http://localhost:3000](http://localhost:3000) to view it in the browser

## Notes

- This application requires microphone access
- Speaker recognition is simplified and works best in quiet environments
- The more samples you provide during training, the better the recognition
- ElevenLabs API key is required for premium TTS (free tier available)
- The application uses the gemini-2.0-flash-lite model for quick responses
