# Voice Recorder

A small Android voice-recording prototype written in Kotlin. The app provides a single record/stop button and displays the filename after saving.

Implemented recording code captures microphone input as 44.1 kHz mono, 16-bit PCM and packages it into timestamped WAV files. Recordings are written to `Recordings` under the app-specific external files directory, rather than a public media folder.

## Open and run

Open the repository root in Android Studio and select the `app` module. The project uses Android SDK 34 (minimum device API 24), Android Gradle Plugin 8.7.1, Kotlin 1.9.24, and the included Gradle 8.9 wrapper. Java/Kotlin bytecode targets Java 11; the checked-in IDE configuration references JBR 21.

The build also configures CMake 3.22.1 and an Android NDK native build, although the native code is only an unused JNI greeting example. No NDK version is pinned. An Android SDK and the native build toolchain must be configured locally.

With the toolchain configured, the wrapper build command is:

```sh
./gradlew assembleDebug
```

This build command was checked against the project configuration but was not executed during repository analysis.

Launch the app on an Android device or emulator with microphone input, grant microphone permission, tap the microphone button to start, and tap the stop icon to finish. The filename label updates after WAV writing completes.

## Status and limitations

This is an unfinished personal experiment. The repository contains no verified build or device-recording results. There is no in-app playback, recording list, export, or sharing flow. Lifecycle cleanup, thread coordination, and error handling need further work before relying on it for recordings.

The included JUnit and Android instrumented tests check basic arithmetic and the application package name only; they do not exercise recording or WAV output.
