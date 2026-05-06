# Transcription & Translation Service

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source transcription and translation pipeline that unifies streaming STT, speaker diarization, translation, and LLM post-processing in a single deployable service.

Transcription & Translation Service is a developer-oriented platform for converting audio into structured, multilingual, speaker-attributed text. It targets engineering teams, media producers, contact centres, and regulated enterprises who currently chain together two to four separate APIs (STT, diarization, translation, summarisation) and want a single open-source artifact instead.

---

## Why Transcription & Translation Service?

- Incumbents force pipeline fragmentation: Deepgram and AssemblyAI omit translation, while Amazon Transcribe requires chaining Amazon Translate separately. No single API delivers transcription, diarization, translation, and summarisation end-to-end.
- Cloud-only architectures lock out regulated sectors: most specialist APIs (Deepgram, AssemblyAI, Gladia) offer no on-premises option, blocking adoption in healthcare, legal, and other GDPR/HIPAA-bound contexts.
- Pricing for high-accuracy paths is prohibitive: Rev.ai's human fallback at $1.50–$1.99/min is roughly 597x its AI cost, and real-time low-latency APIs run 2–4x batch pricing.
- Coverage beyond the top 50 languages degrades sharply, leaving mid-range languages (Tagalog, Swahili, Bengali, Tamil) underserved by specialist APIs.
- Open-source foundations are mature enough to compete: Whisper (MIT, 99 languages) and Pyannote 3.1 (11–19% DER on AMI benchmark) provide a credible base for a self-hostable alternative with no known IP barriers.

---

## Key Features

### Transcription Core

- Audio ingestion via REST batch upload and WebSocket real-time streaming
- STT powered by Whisper large-v3-turbo (self-hosted or via managed API)
- Word-level timestamps with speaker labels
- Smart formatting: automatic punctuation and capitalisation
- Multi-format audio input (MP3, MP4, WAV, OGG, M4A)

### Speaker Intelligence

- Speaker diarization via Pyannote integration
- Speech activity detection and overlapped speech detection
- Per-word speaker labels in batch and (where supported) streaming modes
- Optional named speaker identification through voice biometrics enrolment (backlog)

### Translation

- Translation of transcripts to one or more target languages, integrating DeepL API or a Speechmatics-style unified call pattern
- Structured JSON output containing transcript, speaker segments, and translated segments
- WebVTT and SRT subtitle export for captioned video workflows

### LLM Post-Processing

- Auto-summary, action-item extraction, and key-topic tagging
- PII redaction for names, phone numbers, and email addresses
- Custom vocabulary and keyterm boosting
- Confidence scores per word or segment to drive downstream review logic

### Developer Experience

- REST API with Python and Node.js SDKs
- Webhook callbacks for async job completion
- Structured JSON outputs designed for downstream automation

---

## AI-Native Advantage

Where incumbents expose raw transcripts and leave higher-level reasoning to the integrator, this project treats meeting and audio intelligence as a single structured output: transcription, diarization, action-item extraction, sentiment scoring, and topic tagging emerge from one pipeline. Domain-adapted acoustic models address jargon mis-transcription in medical, legal, and engineering audio. Real-time translation preserves speaker tracks, and a privacy-preserving on-device mode using compact Whisper-class models keeps sensitive audio off the network for regulated industries.

---

## Tech Stack & Deployment

The recommended stack combines Whisper large-v3-turbo for STT, Pyannote for diarization, and DeepL or Speechmatics-style unified translation for multilingual output. Deployment modes are intended to span fully self-hosted (whisper.cpp for CPU-only or edge environments), private cloud, and managed cloud — mirroring the deployment flexibility offered by Speechmatics and Azure Speech containers. Standard transports are WebSocket (RFC 6455) for streaming and REST for batch, with WebVTT/SRT subtitle output and ISO 639-1 / BCP 47 language codes. SDKs are planned for Python and JavaScript/TypeScript first.

---

## Market Context

The global speech and voice recognition market exceeded $22 billion in 2025 and is forecast to surpass $55 billion by 2030, with machine and hybrid translation adding a further $7–9 billion addressable layer. AI transcription APIs cluster at $0.004–$0.02 per audio minute at scale; consumer SaaS apps charge $10–$20/month; human transcription runs $1–$2/minute. Primary buyers include enterprise legal and compliance teams, media and podcast producers, healthcare providers, contact-centre QA teams, and global enterprises needing simultaneous translation for internal meetings.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context. Note that the recommended foundational components (Whisper, Pyannote, faster-whisper) are MIT-licensed with no identified patent concerns, leaving licence selection open.
