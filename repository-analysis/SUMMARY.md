# Voice Recorder

## Overview

Voice Recorder is a small personal Android experiment for recording voice on a phone. Its interface has one record/stop button and a label showing the most recently saved filename.

## My Contributions

The repository contains a Kotlin recording flow using Android’s `AudioRecord` API, runtime microphone permission handling, timestamped file naming, and WAV output. Later commits refine the button’s placement and change its color to indicate recording state. Standard project scaffolding and an unused native example are separate from this recording implementation.

## Architecture

A single activity owns the interface, microphone recorder, and background writer thread. It captures 44.1 kHz mono, 16-bit PCM audio into a temporary file. After recording stops, the writer creates a WAV file with a manually constructed 44-byte header, copies the audio into it, and deletes the temporary file. Files are stored in a `Recordings` directory under app-specific external storage.

## Technical Challenges

The implementation handles conversion of raw audio into a WAV container by encoding the sample format and audio lengths in the header. Audio reads and file writing run on a separate thread, with the saved filename posted back to the interface. Thread shutdown and activity lifecycle handling remain incomplete.

## Results and Current State

This is an inactive prototype with a recording-to-file implementation, rather than a finished recording utility. Successful recording on a device has not been independently verified. It has no playback, recording browser, sharing controls, or automated tests of audio behavior; the included tests are template examples.

## Development History

All four observed commits are dated October 20, 2024. The first already contains the recording implementation; subsequent commits adjust IDE configuration, center the button and filename label, and add recording-state colors. Actual project start and abandonment dates are unknown.
