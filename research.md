# Transcription & Translation Service

> Candidate #314 · Researched: 2026-05-02

## Existing Products and Software Packages

| Tool | Description | Type | Pricing | Strengths / Weaknesses |
|------|-------------|------|---------|------------------------|
| Deepgram | Developer-first STT API; Nova-3 model optimised for real-time voice agents | API / SaaS | Pay-as-you-go from $0.0043/min | Best accuracy for real-time streaming; no human fallback |
| Gladia | Multilingual STT API with native code-switching, diarization, NER, and sentiment | API / SaaS | Pay-as-you-go; free tier 10h/month | Richest audio intelligence bundle; 100+ languages |
| Speechmatics | Enterprise STT with high accuracy across accents and noisy environments | API / Enterprise | Custom pricing | Strong accent coverage; complex enterprise sales cycle |
| Rev.ai | AI transcription with optional routing to human transcriptionists via same API | API / SaaS | $0.02/min AI; $1.50/min human | Human fallback option is unique; premium cost for humans |
| AssemblyAI | Full audio intelligence API: transcription, summarisation, topic detection | API / SaaS | Pay-as-you-go from $0.37/hr | Rich post-processing features; US-centric language support |
| Whisper (OpenAI) | Open-source model supporting 99 languages, widely self-hosted | Open-source model | Free (self-host) | Excellent multilingual; requires infra to operate at scale |
| Google Cloud Speech-to-Text | Hyperscaler managed STT with streaming and batch modes | Managed cloud service | From $0.006/15-sec chunk | Broad language support; latency higher than specialist APIs |
| Otter.ai | Consumer/SMB transcription and meeting notes app with speaker labels | SaaS app | Free; Pro $16.99/month | Easy to use; limited API surface |
| Pyannote | Open-source speaker diarization library (v3.1) | Open-source library | Free (self-host) | Best-in-class diarization DER; research-grade integration effort |
| Soniox | Low-latency streaming STT focused on voice agent and call centre use cases | API / SaaS | Custom pricing | Extremely low latency; narrower language coverage |

## Relevant Industry Standards or Protocols

- **WebSocket (RFC 6455)** — primary transport for real-time streaming audio to cloud STT APIs
- **WebRTC** — browser-native audio capture standard underpinning real-time transcription in web apps
- **SRTP / DTLS** — secure media transport for WebRTC streams requiring encrypted audio pipelines
- **SRT (Secure Reliable Transport)** — low-latency streaming protocol used in broadcast and live captioning workflows
- **VTT / SRT subtitle formats** — standard output formats for captioned video; any transcription service must export these
- **ISO 639-1 / BCP 47** — language code standards used to specify source and target languages in multilingual pipelines
- **GDPR / HIPAA** — data-processing regulations that heavily influence architecture choices for audio containing personal or health data

## Available Research Materials

1. Gladia (2026). *Best Speech-to-Text APIs in 2026*. gladia.io. <https://www.gladia.io/blog/best-speech-to-text-apis>
2. BrassTranscripts (2026). *Best AI Transcription Services 2026*. brasstranscripts.com. <https://brasstranscripts.com/blog/best-ai-transcription-services-2026>
3. BrassTranscripts (2026). *Best Speaker Diarization Models Compared [2026]*. brasstranscripts.com. <https://brasstranscripts.com/blog/speaker-diarization-models-comparison>
4. Reverie (2026). *8 Best Speech-to-Text APIs in 2026: A Complete Comparison Guide*. reverieinc.com. <https://reverieinc.com/blog/speech-text-api-comparison/>
5. Speechmatics (2026). *Best speech-to-text AI guide: APIs, platforms and services compared*. speechmatics.com. <https://www.speechmatics.com/company/articles-and-news/best-speech-to-text-ai-guide-apis-platforms-and-services-compared>
6. NextLevel.ai (2026). *Best Speech to Text Models 2026: Real-Time Agent Comparison*. nextlevel.ai. <https://nextlevel.ai/best-speech-to-text-models/>
7. Soniox (2025). *Soniox vs Speechmatics Speech-to-Text: Accuracy, Features, Pricing*. soniox.com. <https://soniox.com/compare/soniox-vs-speechmatics>

## Market Research

**Market Size:** The global speech and voice recognition market exceeded $22 billion in 2025 and is forecast to surpass $55 billion by 2030. The translation services sub-segment (machine and hybrid) adds a further $7–9 billion addressable layer.

**Funding:** Deepgram raised $85 M Series B (2022). AssemblyAI raised $50 M Series B (2022). Rev (parent of Rev.ai) is profitable and bootstrapped. Speechmatics raised £62 M Series B (2022).

**Pricing Landscape:** AI transcription APIs cluster at $0.004–$0.02 per audio minute at scale. Consumer SaaS apps charge $10–$20/month for moderate usage. Human transcription falls in the $1–$2/minute range. Real-time low-latency APIs command a premium of 2–4x batch pricing.

**Key Buyer Personas:** Enterprise legal and compliance teams needing verbatim records; media and podcast producers requiring fast turn-around captions; healthcare providers transcribing clinical consultations; call centres requiring QA analytics over agent conversations; global enterprises needing simultaneous translation of internal meetings.

**Notable Trends:** Speaker diarization accuracy has improved dramatically; Pyannote 3.1 achieves 11–19% DER on standard benchmarks. LLM post-processing now cleans transcripts, inserts punctuation, and generates structured summaries in the same pipeline. Real-time translation latency has fallen below 500 ms for major language pairs, enabling live multilingual meetings without perceptible lag.

## AI-Native Opportunity

- **End-to-end meeting intelligence** — transcription, diarization, action-item extraction, sentiment scoring, and topic tagging delivered as a single structured output rather than raw text.
- **Domain-adapted acoustic models** — fine-tuning on industry-specific vocabulary (medical, legal, engineering) to eliminate jargon mis-transcription that standard models produce.
- **Real-time translation with speaker preservation** — translating each speaker's words in real time while maintaining separate speaker tracks and voice style cues in the output.
- **Privacy-preserving on-device processing** — running compact Whisper-class models locally so sensitive audio never leaves the user's device, unlocking regulated industries that block cloud audio.
- **Proactive summary and follow-up generation** — automatically producing meeting minutes, open questions, and calendar follow-up events from the transcript without any post-meeting effort.
