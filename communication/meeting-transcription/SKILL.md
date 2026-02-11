---
name: meeting-transcription
description: A skill to transcribe meeting audio and generate summaries.
license: MIT
---

## Workflow

This skill transcribes audio from meetings and generates a concise summary. The process is as follows:

1.  **Audio Input**: The user provides a path to an audio file of a meeting. Supported formats include MP3, WAV, and M4A.
2.  **Transcription**: The skill utilizes a speech-to-text engine to convert the spoken words in the audio file into a text document.
3.  **Summarization**: The generated transcript is then processed by a large language model to produce a summary. This summary highlights key discussion points, action items, and decisions made during the meeting.
4.  **Output**: The skill outputs both the full transcription and the summary as separate text files in a specified output directory.

## Usage

To use this skill, you need to provide the path to the audio file you want to transcribe and an output directory where the results will be saved.

```bash
meeting-transcription --input <path-to-audio-file> --output <path-to-output-directory>
```

## Example

Here is an example of how to use the skill:

```bash
meeting-transcription --input /home/ubuntu/recordings/project-kickoff.mp3 --output /home/ubuntu/transcripts
```

This command will transcribe the `project-kickoff.mp3` audio file and save the transcription and summary in the `/home/ubuntu/transcripts` directory.
