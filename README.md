# AI Audio Summarization and Speech Generation

An n8n workflow that takes an audio URL, transcribes the audio, summarizes the transcript into concise meeting-style bullet points, and generates speech from the summary.

## Workflow Overview

1. **When chat message received** — accepts a chat message containing an audio URL.
2. **Download Audio** — downloads the audio file.
3. **Groq Whisper** — processes the audio using the `whisper-large-v3` model.
4. **Basic LLM Chain** — creates concise, action-oriented summary bullet points.
5. **Google Gemini Chat Model** — supplies the language model for summarization.
6. **Murf Speech Generation** — generates spoken audio from the summary.
7. **Download Generated Audio** — downloads the generated audio file.

## Requirements

- An n8n instance
- A Groq API key
- A Google Gemini API credential
- A Murf API key
- An accessible audio URL

## Setup

1. Import the sanitized workflow JSON into n8n.
2. Configure the Google Gemini credential.
3. Configure Groq authentication securely in the transcription HTTP Request node.
4. Configure Murf authentication securely in the speech-generation HTTP Request node.
5. Review the binary-data mapping and API response fields.
6. Test the workflow using an audio URL you are authorized to use.
7. Verify that the transcription, summarization, and speech-generation steps work.
8. Activate the workflow only after successful testing.

## Security

Never publish API keys, access tokens, personal audio, or private webhook URLs.

If a key has been exposed, revoke or rotate it with the provider. Store credentials securely in n8n rather than hardcoding them into a public workflow export.

## Implementation Notes

- The workflow accepts an audio URL rather than directly uploading an audio file from a user's device.
- Check the Groq endpoint and language settings for your intended transcription or translation behavior.
- Verify the Murf response contains the expected `audioFile` field before the final download node.
- API settings, voice IDs, and model availability may change.
- Provider usage may be subject to pricing and free-tier limits.

## License

Choose a license before publishing. Consider the MIT License if you have the rights to share and permit reuse of the workflow.
