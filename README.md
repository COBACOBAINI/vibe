[![Releases](https://img.shields.io/github/v/release/COBACOBAINI/vibe?style=flat-square&logo=github&logoColor=white)](https://github.com/COBACOBAINI/vibe/releases)

# vibe: Fast Cross-Platform Desktop Transcription Tool with Whisper and OpenAI

Topics: ai, cross-platform, desktop, openai, rust, transcribe, whisper

Here you find a self-contained desktop solution for transcribing audio on your own machine. vibe focuses on privacy, performance, and an honest approach to transcription. It runs on Windows, macOS, and Linux, and it ships with a straightforward interface for both casual use and power users. The project blends open source speech models with a robust, native application surface to deliver quick, accurate transcripts without sending data to external services by default.

Images and visuals tell part of the story. The vibe UI aims to be calm and efficient, offering clear controls and fast feedback as you work with audio files, recordings, or live input. This README explains what vibe is, how it works, how to install it from the official releases, and how to get the most out of transcription tasks. It also covers how the project is built, how you can contribute, and how to extend it for your own workflows.

Table of contents
- Quick overview
- How vibe works
- Core features
- Supported platforms
- How to install from releases
- Build from source
- How to transcribe
- Transcription options
- Privacy and data handling
- Performance and resource usage
- Architecture and code map
- Development guide
- Testing and quality
- Troubleshooting
- Security considerations
- FAQ
- Roadmap
- License and credits

Quick overview
vibe is a cross-platform desktop app designed to help you transcribe audio files and recordings on your own machine. It leverages Whisper models for offline transcription and can optionally use an OpenAI backend if you provide your API key. The app is built with Rust for speed and safety, and it uses a lightweight UI layer that feels native on all major desktop platforms. The goal is to give you reliable transcripts without needing to rely on cloud services by default, while still offering flexible options for those who want to access more capable AI models through OpenAI when privacy is acceptable and the user consents.

The app focuses on:
- Privacy by design: transcripts stay on your device unless you choose to upload or send data.
- Speed and responsiveness: fast startup, smooth playback, and quick results on typical laptop hardware.
- Accessibility: clear typography, keyboard shortcuts, and easy navigation so transcription tasks don’t slow you down.
- Extensibility: a clean codebase and clear contribution paths so others can adapt vibe to their needs.

How vibe works
At its core, vibe is a desktop front-end that coordinates audio input, model inference, and transcript rendering. The runtime uses Rust to manage processes and memory efficiently, while the user interface presents a straightforward workflow for loading audio, choosing transcription models, and saving transcripts. Whisper models provide offline transcription options, with accuracy trade-offs based on model size. If you opt to use the OpenAI pathway, vibe can route transcripts through the API when you supply an API key, allowing access to larger or more capable models for complex audio.

Key design choices:
- Local-first processing: most transcription runs occur locally, with optional online processing.
- Simple file handling: open an audio file, select a transcription model, run, and save.
- Model selection: pick a Whisper model that balances speed and accuracy for your audio type.
- Language support: specify the input language to improve transcription accuracy and alignment.
- Output formats: save transcripts in plain text, SRT, VTT, or JSON for downstream use.

Core features
- Audio loading and playback: load common audio formats, preview, and scrub through the waveform.
- Transcription engine options: offline Whisper models, with optional OpenAI integration for higher accuracy on demanding audio.
- On-device privacy: no data leaves your machine unless you opt in.
- Multi-language support: detect or set the transcription language to improve accuracy.
- Subtitles and captions: export SRT and VTT files for video workflows.
- Time-stamped transcripts: precise word timing data for editor tools.
- Keyboard-centric operation: fast shortcuts for common tasks, enabling focus on the content.
- Progress indicators: real-time status updates during transcription.

Supported platforms
- Windows (x64)
- macOS (Intel and Apple Silicon)
- Linux (most major distributions with a supported desktop environment)

The goal is to support a broad user base without forcing a specific platform. The build and packaging pipeline are designed to adapt to new OS variants as they appear and to keep the user experience consistent across environments.

Install from official releases
The recommended way to start with vibe is to download a released installer or package from the official releases page. Because the link includes a path, the release page hosts assets that you can download and run directly on your OS. You should go to the page and grab the appropriate installer for your system, then run it to install vibe on your computer. The releases page includes installers for different architectures and operating systems, along with checksums and notes about model versions.

- Release link: https://github.com/COBACOBAINI/vibe/releases
- How to proceed:
  - Open the releases page.
  - Identify the asset that matches your platform (Windows, macOS, or Linux) and your architecture (x86_64, arm64, etc.).
  - Download the installer or package with a name that indicates the OS and architecture.
  - Run the downloaded file and follow the on-screen prompts to install vibe.
  - After installation, launch vibe from your applications or start menu.

If you encounter issues with the installer, check the release notes for known issues, and verify your system meets the minimum requirements listed in the release page. The release page provides guidance on prerequisites and common setup steps, and it often includes post-install instructions such as how to authorize optional OpenAI API use or how to select a transcription model in the first run.

Note: The link above is the official releases page. It is the correct source for installable assets. If you cannot access it or if it changes, you should check the same page in the Releases section of the repository to locate the latest assets and instructions.

Build from source
If you prefer to build vibe from source, you will need a suitable toolchain and dependencies. The project is written in Rust and integrates a UI layer that interacts with audio input and model inference components. To build from source, you will typically need:

- Rust toolchain (rustup, cargo)
- A C toolchain and system libraries for audio handling and audio decoding
- Optional OpenAI client libraries if you plan to enable online transcription
- A modern operating system with a compatible toolchain and build environment

Typical steps:
- Clone the repository
- Install Rust and cargo
- Resolve platform-specific dependencies
- Build the project in release mode
- Run the built binary and verify the app starts

The source tree is organized to separate core logic from the user interface, so you can explore the transcription engine, model loading, and audio processing modules independently if you want to extend vibe.

How to transcribe
Transcribing with vibe is designed to be simple. After you install vibe, you can load an audio file, select a transcription model, and start the transcription. The transcript appears in the main editor with timestamps and optional speaker labeling if you enable that feature. You can edit, review, and export transcripts in several formats.

- Load an audio file: supported formats include common audio formats such as WAV, MP3, FLAC, and Ogg Vorbis.
- Choose a model: Whisper-based models come in various sizes; smaller models run faster with lower resource usage, while larger models yield higher accuracy on challenging audio.
- Set language: specify the language if you know it, or let the system auto-detect to guide the model toward the right transcription conventions.
- Start transcription: the app processes the audio and displays the transcript as it runs.
- Edit and fine-tune: you can correct transcription errors and adjust timing to match your needs.
- Export options: save as TXT, SRT, VTT, or JSON for further processing, video synchronization, or content indexing.

Transcription options
- Whisper offline mode: run Whisper models locally for privacy and speed.
- OpenAI backend: optional, if you provide API credentials, vibe can use OpenAI models for more nuanced transcriptions on difficult audio.
- Language hints: supply a language hint or let detection run to improve accuracy.
- Punctuation and formatting: control how punctuation is applied in the transcript and whether to include speaker labels.
- Time alignment: adjust transcript timing to improve match with the audio track.
- Custom vocabularies: add terms that appear in your transcripts to improve recognition of names, places, or jargon.

Privacy and data handling
vibe emphasizes privacy. Transcripts generated on your machine are stored locally by default. If you opt in to use an online API, only the data you send is transmitted, and you can review the terms of service and data usage for the provider before enabling it. You control what data is uploaded and when. The app stores user settings locally, and any exported transcripts remain under your control.

Performance and resource usage
- Memory and CPU usage scale with the model size and audio duration.
- Whisper models offer a range of trade-offs between speed and accuracy.
- The UI remains responsive during transcription, thanks to asynchronous processing and careful resource management.
- On modern laptops, you can expect smooth performance for typical speech-length audio files.

Architecture and code map
- Frontend: a native-like user interface that runs on all major desktop platforms. It handles file I/O, progress reporting, and user interactions.
- Transcription engine: a Rust component that manages model loading, audio decoding, and text generation. It runs offline by default.
- Model management: a module that selects and loads Whisper models, adjusts processing parameters, and returns transcripts with timing information.
- Optional API layer: an optional path that routes transcription requests to an online OpenAI service when configured.
- Data handling: modules responsible for saving transcripts, exporting formats, and managing user preferences.

Development guide
- If you want to contribute, start by forking the repository and creating a feature branch.
- Follow the project’s coding conventions and maintain clear, well-documented changes.
- Add tests that cover new features and ensure existing behavior remains stable.
- Update documentation for any user-facing changes.

Release notes and updates
- Re-releases may include model updates, performance improvements, or bug fixes.
- Each release includes assets appropriate to target platforms and versions, along with notes about changes and how they affect users.
- Check the Releases section for details and download links for the latest builds.

Contributing
- We welcome contributions from developers and researchers alike.
- If you want to contribute code, write tests for new functionality and ensure that changes align with the project’s goals of privacy, reliability, and simplicity.
- For documentation improvements, provide examples that help users accomplish common transcription tasks quickly.

Licensing
- vibe uses a permissive license that allows you to run, study, modify, and distribute the software. The license encourages open collaboration while protecting the rights of users and contributors.

Roadmap
- Improve model loading speed on low-end hardware.
- Expand language support and improve detection accuracy for multi-speaker audio.
- Enhance the OpenAI integration with flexible cost controls and usage monitoring.
- Improve offline playback features and waveform visualization for easier editing.
- Add batch processing for longer transcription tasks and project-based workflows.

FAQ
- Can I use vibe entirely offline? Yes. You can run Whisper models locally and export transcripts without sending data to external services.
- Do I need an OpenAI account to use vibe? No. The OpenAI path is optional and only used if you provide credentials and choose to enable it.
- What happens to data I export? Exported transcripts stay with you. You decide where to store them and how to share them.

Security considerations
- The app avoids transmitting data by default.
- If you enable online transcription, API calls happen over secure channels with standard authentication practices.
- Regular updates reduce exposure to known vulnerabilities and keep the tool current with security fixes.

Changelog (high level)
- Version tokens correspond to stable releases. Each release includes notes on new features, fixes, and known issues.
- For historical changes, refer to the Releases page in the repository.

Troubleshooting
- If the app fails to start after installation, verify system requirements and ensure you downloaded the correct asset for your platform.
- If transcription results look incorrect, try a larger Whisper model or adjust the language hints and vocabulary settings.
- If you see audio playback issues, check your system audio drivers and confirm the selected audio device is correct.

Other resources
- Documentation: the project wiki and official docs live alongside the repository.
- Community discussions: participants share tips, scripts, and workflows to optimize transcription projects.
- Related projects: explore related tools in the ecosystem for transcription, captioning, and audio analysis.

Release assets and installation details
Because the official releases page hosts platform-specific assets, download an installer or package that matches your operating system and architecture, then run it to install vibe. The page often includes additional notes about model versions, dependencies, and post-install steps. If you are unsure which asset to pick, look for the label that matches your OS (for example, Windows x64, macOS arm64, or Linux x86_64) and a file type you recognize (installer, package, or AppImage). If you run into any issues, the release notes typically provide troubleshooting steps and contact information for the maintainers.

Releases link usage
- Link to releases page: https://github.com/COBACOBAINI/vibe/releases
- This link should be used to obtain the official installer assets. It is the definitive source for the current builds and release notes.
- If the link changes, search the repository’s Releases section to locate the latest assets and follow the same download and run procedure described here.

Appendix: sample workflows
- Quick transcript for a short audio clip:
  - Launch vibe.
  - Load audio file.
  - Select a Whisper model sized for speed versus accuracy.
  - Run transcription.
  - Review and correct any errors.
  - Export to TXT or SRT for adding captions to a video.

- Batch transcription:
  - Prepare a folder with multiple audio files.
  - Use vibe’s batch mode (if available) or a scripted workflow to process each file.
  - Save transcripts to a project folder with consistent naming.
  - Use the JSON export to feed transcripts into a downstream data pipeline if needed.

- OpenAI integration workflow:
  - In settings, enable OpenAI transcription path and provide the API key.
  - Choose a model and language hint suitable for your audio.
  - Run transcription and review results with the editor.
  - Save the transcript locally or apply it to a larger video project.

Example usage scenarios
- Academic research: transcribe lecture audio, label speakers, and export captions for accessibility.
- Media production: generate draft transcripts for quick editing, then refine grammar and style.
- Accessibility support: create captions and transcripts to help a wider audience engage with multimedia content.
- Personal projects: archive voice notes or interviews with time-stamped transcripts for future searchability.

Design considerations
- Privacy-first approach keeps you in control of your data.
- Cross-platform support ensures broad usability without compromising performance.
- Pluggable architecture enables future integrations and feature expansions.
- Clear export options help you align transcripts with your existing workflows.

A note on naming and branding
The vibe project emphasizes simplicity and speed. The name is concise and easy to remember, with a brand image focused on calm, efficient transcription work. The user interface prioritizes readability and ease of use, enabling you to focus on the content of transcripts rather than the tool's quirks.

Community and governance
- The project welcomes input from users and developers.
- Contributions should be aligned with the goals of privacy, reliability, and simplicity.
- Major changes go through a review process to maintain code quality and compatibility across platforms.

Notes on assets and visuals
- The README uses a mix of emojis and visuals to convey ideas quickly.
- Emphasis on practical steps helps users move from discovery to productive use with minimal friction.
- Visuals are intended to complement the text, not overwhelm it.

Appendix: glossary
- Transcription: converting spoken audio into written text.
- Whisper: an open-source speech recognition model family.
- OpenAI: a provider that offers more advanced language models via API.
- AppImage: a portable Linux package format.
- SRT/VTT: subtitle formats that pair text with time codes.

End user experience
- vibe aims to be reliable in everyday scenarios: recording lectures, interviews, and media soundtracks.
- The application is designed to reduce friction and deliver transcripts that you can trust with minimal post-processing.

Developer notes
- The codebase is modular, allowing for experimentation with different models and interfaces.
- The build system supports cross-compilation and platform-specific packaging strategies.
- Documentation is a priority, with inline comments and external docs available to help contributors.

Licensing and credits
- The project is distributed under a permissive license to encourage use, adaptation, and collaboration.
- Credits are given to contributors, model maintainers, and the broader open-source community that supports speech recognition research and tooling.

Legal and compliance
- Users should review licensing terms for any models employed by vibe, especially when using online APIs.
- Ensure you have rights to the audio you transcribe and the transcripts you produce.

Final notes
- The official release assets provide the smoothest path to getting vibe up and running quickly.
- If you prefer to build from source, the repository contains the necessary code and instructions to guide you through the process.
- For questions, issues, or feature requests, use the repository’s issue tracker and contribution guidelines to start a discussion with the maintainers and community.

Releases note re-emphasis
- The official releases page is the primary source for download assets and update notes. If you need to install vibe today, follow the link provided above and choose the asset that matches your environment. The same link will appear again in the installation section to remind you where the official, up-to-date builds live: https://github.com/COBACOBAINI/vibe/releases

End of document
