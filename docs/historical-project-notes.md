# Historical project notes

These notes retain the useful descriptions from the README introduced in
`9fc73e5c42e933db643b8bbe5c0d3f444bdc51d2`. They describe the intended app;
the repository contains no source that verifies these claims or controls.
The original browser-side API-key instructions are replaced with the credential
guidance in the [recovery guide](recovery.md).

## Described features

- Real-time speech-to-text through the Web Speech API and automatic “aura”
  analysis of whether speech sounds tough and confident in TikTok terms.
- Speaker recognition for Person 1, Person 2, and Person 3, using simple voice
  fingerprinting and a live speech display with speaker labels.
- A history table of aura readings with speaker identification.
- A chat window for interacting with an AI assistant and a debug panel for
  monitoring application state.
- Optional ElevenLabs voice synthesis and spoken analysis results.
- React and TypeScript, a responsive mobile/desktop design, and Google's Gemini
  2.0 API. The README specifically named `gemini-2.0-flash-lite`; this is a
  historical model reference, not a claim of current service availability.

## Described use

1. Click **Start Speaking** and grant microphone access.
2. Speak; analysis is described as automatic while speaking.
3. The app is described as identifying the speaker and analyzing each person
   separately.
4. Results are announced if text-to-speech is enabled, and recorded in the
   history table with speaker labels.

## Described speaker training

1. In **Speaker Recognition**, choose a profile (Person 1, 2, or 3).
2. Click **Train Voice** and speak clearly for about 15–30 seconds.
3. Click **Stop Training**; repeat for each person.

The README said identification was simplified, worked best in quiet conditions,
and improved with more training samples. No accuracy measurements or training
implementation are available here.

## Described premium text-to-speech controls

The original instructions described enabling **Text-to-Speech**, checking
**Use Premium Text-to-Speech**, selecting a voice, and clicking **Test Voice**.
They said an ElevenLabs API key was required and mentioned a free tier, without
evidence of current pricing or availability. Provider credentials must stay on
a server; do not follow the old instruction to insert a key into `src/App.tsx`.

The original setup used `npm install`, then `npm start` and
`http://localhost:3000`. Source recovery is now the prerequisite; see the
[recovery guide](recovery.md) for the gated setup steps.
