# Audio — The Silence Beneath the Web

This directory is reserved for audio versions of the v2 novel.

## What lives here

Chapter-by-chapter audio narration of
[*The Silence Beneath the Web*](../novel.md). Formats and generation
tools are open — this is a container, not a spec.

## Conventions when files land

- One file per chapter, named by chapter number:
  `chapter-01.mp3`, `chapter-02.mp3`, etc.
- A `manifest.json` listing chapter → file mapping, duration, model /
  voice used, and hash.
- If multiple voice-model versions coexist, put them in per-voice
  subdirectories (e.g. `audio/xtts-v2/`, `audio/elevenlabs-rachel/`).

## Attribution

Whatever produces the audio should be credited alongside AIRowling in
the top-level README. TTS voice is a distinct authoring choice from
the prose; a voice model that produces something distinctive deserves
naming.
