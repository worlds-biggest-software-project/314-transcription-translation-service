# Standards & API Reference

> Project: Transcription & Translation Service · Generated: 2026-05-03

---

## Industry Standards & Specifications

### ISO Standards

**ISO 639-1 / ISO 639-3**
- URL: https://www.iso.org/iso-639-language-codes.html
- Two-character (ISO 639-1) and three-character (ISO 639-3) language code standards. Every STT and translation API uses these codes to specify source and target languages. ISO 639-3 adds coverage for minority and extinct languages absent from ISO 639-1.

**ISO 27001 — Information Security Management Systems**
- URL: https://www.iso.org/standard/27001
- The internationally recognised certification for an organisation's ISMS. Enterprise B2B buyers evaluating voice and transcription vendors require ISO 27001 certification alongside SOC 2 Type II before signing data processing agreements. Particularly relevant given that audio recordings constitute personal data under GDPR.

**ISO/IEC 23009 (MPEG-DASH)**
- URL: https://www.iso.org/standard/83314.html
- Adaptive bitrate streaming standard for video/audio delivery over HTTP. Transcription pipelines that process streamed media (live broadcast, video on demand) must handle MPEG-DASH audio segment extraction before passing to STT engines.

---

### W3C & IETF Standards

**WebVTT — Web Video Text Tracks Format (W3C Recommendation)**
- URL: https://www.w3.org/TR/webvtt1/
- The W3C standard format for timed-text captions and subtitles in HTML5 `<video>` elements. Every transcription service is expected to export WebVTT alongside the raw transcript. Supports speaker labels via voice tags and CSS-based styling.

**TTML — Timed Text Markup Language (W3C Recommendation)**
- URL: https://www.w3.org/TR/ttml2/
- XML-based W3C standard for timed text used in professional broadcast and OTT delivery (Netflix IMSC profile, EBU-TT for European broadcast). A transcription service targeting media production workflows must support TTML export.

**SSML — Speech Synthesis Markup Language (W3C Recommendation)**
- URL: https://www.w3.org/TR/speech-synthesis/
- W3C standard markup language for controlling text-to-speech rendering. Relevant when a transcription–translation pipeline feeds translated text back into a TTS engine to produce voice output in the target language.

**SRGS — Speech Recognition Grammar Specification (W3C Recommendation)**
- URL: https://www.w3.org/TR/speech-grammar/
- W3C standard for defining grammars that constrain speech recognition to expected inputs (menus, commands, form fields). Applicable when building a voice-driven transcription workflow where domain-specific vocabulary must be enforced.

**WebRTC (W3C Recommendation / IETF RFCs)**
- W3C: https://www.w3.org/TR/webrtc/
- IETF RFCs: https://datatracker.ietf.org/wg/rtcweb/documents/
- Browser-native standard for real-time audio and video capture and peer-to-peer transport. The primary mechanism for capturing microphone audio in web-based transcription applications before streaming to cloud STT APIs.

**RFC 6455 — The WebSocket Protocol (IETF Internet Standard STD 34)**
- URL: https://datatracker.ietf.org/doc/html/rfc6455
- Full-duplex communication over a single TCP connection. All specialist STT streaming APIs (Deepgram, AssemblyAI, Gladia, Speechmatics, Azure AI Speech) use WebSocket as the transport for real-time audio streaming and incremental transcript delivery.

**RFC 3711 — SRTP: Secure Real-Time Transport Protocol**
- URL: https://datatracker.ietf.org/doc/html/rfc3711
- Encryption and authentication layer for RTP audio streams. Mandatory in WebRTC-based transcription pipelines and any SRTP/DTLS-secured call recording scenario.

**RFC 5764 — DTLS-SRTP**
- URL: https://datatracker.ietf.org/doc/html/rfc5764
- Defines the unified DTLS + SRTP key exchange profile used in WebRTC. Ensures that audio streams captured from browsers are encrypted during transit to transcription APIs.

**RFC 5646 / BCP 47 — Tags for Identifying Languages**
- URL: https://datatracker.ietf.org/doc/html/rfc5646
- The IETF Best Current Practice for language tags (e.g., `en-US`, `fr-FR`, `zh-Hant-TW`). All transcription and translation APIs use BCP 47 language codes in their request parameters and response payloads. Correctly implementing BCP 47 is required for multi-language pipeline routing.

**RFC 7235 / RFC 6750 — HTTP Authentication & Bearer Token Usage**
- RFC 7235: https://datatracker.ietf.org/doc/html/rfc7235
- RFC 6750: https://datatracker.ietf.org/doc/html/rfc6750
- Baseline HTTP authentication framework and the specification for OAuth 2.0 Bearer Token usage in Authorization headers. Applies to all REST-based transcription API calls.

---

### Data Model & API Specifications

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://spec.openapis.org/oas/v3.1.0.html
- The standard machine-readable format for describing RESTful APIs. An AI-native transcription service should publish an OpenAPI 3.1 specification to enable auto-generated SDKs, interactive documentation, and contract testing. OAS 3.1 is fully compatible with JSON Schema Draft 2020-12.

**JSON Schema (Draft 2020-12)**
- URL: https://json-schema.org/specification
- The vocabulary for annotating and validating JSON documents. Used to define the schema of transcription API request bodies (audio URL, language, options) and response payloads (transcript, speaker segments, confidence scores, translations).

**SRT (SubRip Text) — de facto standard subtitle format**
- No formal standards body; de facto format with broad toolchain support. All transcription services export SRT for compatibility with video editors (Premiere Pro, DaVinci Resolve, Final Cut Pro) and video platforms (YouTube, Vimeo). SRT uses `HH:MM:SS,mmm --> HH:MM:SS,mmm` timestamp notation.

**JSON Lines (JSONL)**
- URL: https://jsonlines.org/
- A de facto standard for streaming structured output one JSON object per line. Widely used by transcription APIs to stream incremental transcript segments over HTTP chunked transfer or Server-Sent Events (SSE).

---

### Security & Authentication Standards

**OAuth 2.0 (RFC 6749)**
- URL: https://oauth.net/2/
- The industry standard authorisation framework. Applicable when a transcription service needs to support user-delegated access (e.g., allowing a third-party meeting bot to transcribe on behalf of a user). Authorization Code + PKCE flow is recommended for public clients.

**OpenID Connect 1.0 (OIDC)**
- URL: https://openid.net/connect/
- Identity layer on top of OAuth 2.0 for user authentication. Relevant when building an end-user-facing SaaS transcription product that supports SSO with enterprise identity providers (Google Workspace, Azure AD, Okta).

**JWT — JSON Web Tokens (RFC 7519)**
- URL: https://datatracker.ietf.org/doc/html/rfc7519
- Compact, self-contained token format for authentication claims. Used by most transcription APIs for short-lived access tokens in client-side or WebSocket connection scenarios where embedding a long-lived API key would be a security risk.

**TLS 1.2 / 1.3 (RFC 8446)**
- URL: https://datatracker.ietf.org/doc/html/rfc8446
- Minimum transport security requirement for all audio streaming and API calls. Both GDPR and HIPAA compliance guidelines for voice data require TLS 1.2 or higher with AES-256 encryption.

**GDPR — EU General Data Protection Regulation**
- URL: https://gdpr-info.eu/
- EU privacy law that treats audio recordings and transcripts as personal data. Requires explicit consent before recording, lawful basis for processing, data minimisation, and the ability to honour right-to-erasure requests for voice recordings and transcripts. Maximum penalty: €20 million or 4% of global annual turnover.

**HIPAA — Health Insurance Portability and Accountability Act (US)**
- URL: https://www.hhs.gov/hipaa/index.html
- US healthcare regulation governing Protected Health Information (PHI). Clinical transcription services must implement BAAs with all processors, enforce role-based access controls, maintain detailed audit logs, and encrypt PHI at rest (AES-256) and in transit (TLS 1.2+). Penalty: $100–$50,000 per violation.

**AICPA SOC 2 Type II**
- URL: https://www.aicpa-cima.com/resources/landing/system-and-organization-controls-soc-suite-of-services
- US-centric audit attestation for SaaS security controls across the five Trust Service Criteria (Security, Availability, Processing Integrity, Confidentiality, Privacy). Enterprise B2B buyers in the US require SOC 2 Type II reports before onboarding third-party transcription vendors.

**OWASP API Security Top 10 (2023)**
- URL: https://owasp.org/API-Security/editions/2023/en/0x00-header/
- OWASP's definitive reference for API security vulnerabilities. Critical for a transcription API handling sensitive audio: broken object-level authorisation (BOLA), broken authentication, excessive data exposure, and rate-limiting failures are all directly applicable.

---

### MCP Server Specifications

**Model Context Protocol (MCP) — Anthropic / open standard**
- Specification: https://modelcontextprotocol.io/specification/2025-11-25
- GitHub: https://github.com/modelcontextprotocol
- An open protocol for connecting LLM applications to external data sources and tools via JSON-RPC 2.0, using either stdio (local) or HTTP/SSE (remote) transports. By 2026, MCP has become the de facto open standard for AI tool integration. A transcription service exposing an MCP Server would allow LLM agents (Claude, ChatGPT, etc.) to invoke transcription, search transcript archives, and retrieve summaries without custom integration code. Otter.ai launched an MCP Server in 2026 as the first production example in this space.

---

## Similar Products — Developer Documentation & APIs

### Deepgram

- **Description:** Developer-first STT API with Nova-3 and Flux models optimised for real-time voice agents and low-latency streaming.
- **API Documentation:** https://developers.deepgram.com/reference/deepgram-api-overview
- **SDKs/Libraries:** Python (https://github.com/deepgram/deepgram-python-sdk), JavaScript/TypeScript (https://github.com/deepgram/deepgram-js-sdk), Go, .NET, Rust
- **Developer Guide:** https://developers.deepgram.com/home
- **Standards:** REST/JSON (batch), WebSocket (streaming), OpenAPI-documented endpoints
- **Authentication:** API Key (server-side); short-lived access tokens for client-side WebSocket connections

---

### AssemblyAI

- **Description:** STT + audio intelligence API combining transcription with LeMUR LLM post-processing, sentiment analysis, topic detection, and 99-language Universal-3-Pro model.
- **API Documentation:** https://www.assemblyai.com/docs/api-reference/overview
- **SDKs/Libraries:** Python (https://github.com/AssemblyAI/assemblyai-python-sdk), Node.js (https://github.com/AssemblyAI/assemblyai-node-sdk), Java, Go, C# (.NET), Ruby
- **Developer Guide:** https://www.assemblyai.com/docs
- **Standards:** REST/JSON (async batch), WebSocket (Universal-Streaming for real-time)
- **Authentication:** API Key passed in Authorization header

---

### Gladia

- **Description:** Multilingual STT API with Solaria-1 model, native code-switching across 110+ languages, bundled speaker diarization, and in-call translation — all in a single API response.
- **API Documentation:** https://docs.gladia.io/api-reference
- **SDKs/Libraries:** Python, JavaScript/TypeScript; also available via Vercel AI SDK (`@ai-sdk/gladia`)
- **Developer Guide:** https://www.gladia.io/blog/getting-started-with-gladia-how-to-build-with-our-stt-api-features
- **Standards:** REST/JSON (batch), WebSocket (real-time streaming)
- **Authentication:** API Key (`x-gladia-key` header)

---

### Speechmatics

- **Description:** Enterprise STT + unified speech-translation API across 55+ languages with on-premises deployment, no data logging, and best-in-class accent coverage.
- **API Documentation:** https://docs.speechmatics.com/api-ref
- **SDKs/Libraries:** Python (https://speechmatics.github.io/speechmatics-python/), JavaScript (community), C++ (for edge/on-prem)
- **Developer Guide:** https://docs.speechmatics.com/
- **Standards:** REST/JSON (batch jobs API), WebSocket (Realtime API)
- **Authentication:** JWT tokens (time-limited); API Key for batch job submission

---

### Rev.ai

- **Description:** STT API with optional routing to professional human transcriptionists via the same endpoint, offering 99%+ accuracy guarantees for legal, medical, and compliance use cases.
- **API Documentation:** https://www.rev.ai/docs
- **SDKs/Libraries:** Python, Node.js, Java, Ruby
- **Developer Guide:** https://www.rev.ai/docs
- **Standards:** REST/JSON (async), WebSocket (streaming); responses conform to a custom JSON transcript object format
- **Authentication:** API Key (`Authorization: Bearer <token>` header)

---

### OpenAI Whisper / GPT-4o Transcription

- **Description:** Open-source Whisper model (MIT) and managed GPT-4o-transcribe API for batch and streaming STT with 99-language support.
- **API Documentation:** https://platform.openai.com/docs/guides/speech-to-text
- **SDKs/Libraries:** Python (`openai` library), Node.js (`openai` npm package); whisper.cpp for C++ self-hosted inference
- **Developer Guide:** https://platform.openai.com/docs/guides/speech-to-text
- **Standards:** REST/JSON (file upload); WebSocket (Realtime API for gpt-4o-realtime-preview)
- **Authentication:** API Key (`Authorization: Bearer <token>` header); OAuth-style project tokens supported

---

### Google Cloud Speech-to-Text (Chirp 3)

- **Description:** Google's managed STT service with the latest Chirp 3 model, 85+ language support, direct speech translation, and deep integration with the Google Cloud ecosystem.
- **API Documentation:** https://cloud.google.com/speech-to-text/docs
- **SDKs/Libraries:** Python, Java, Node.js, Go, C#, PHP, Ruby (all via Google Cloud client libraries)
- **Developer Guide:** https://cloud.google.com/speech-to-text/docs/quickstarts
- **Standards:** REST/JSON and gRPC; OpenAPI-compatible REST interface; WebSocket-based streaming via gRPC bidirectional streaming
- **Authentication:** Google Cloud service account keys or Application Default Credentials (ADC); OAuth 2.0 for user-delegated access

---

### Amazon Transcribe

- **Description:** AWS managed STT service with specialised modes (Medical, Call Analytics, HealthScribe), PII redaction, and deep integration with the AWS ecosystem for translation (via Amazon Translate) and NLU (via Amazon Comprehend).
- **API Documentation:** https://docs.aws.amazon.com/transcribe/latest/APIReference/Welcome.html
- **SDKs/Libraries:** .NET, Go, Java, JavaScript, PHP, Python, Ruby (via AWS SDK)
- **Developer Guide:** https://docs.aws.amazon.com/transcribe/latest/dg/
- **Standards:** REST/JSON (batch) via AWS SDK; WebSocket (streaming); AWS Signature Version 4 for request signing
- **Authentication:** AWS IAM (Access Key + Secret Key + Session Token); IAM roles for EC2/Lambda

---

### Azure AI Speech

- **Description:** Microsoft's managed STT + real-time translation service with support for 85+ languages, native speech translation to 60+ target languages, pronunciation assessment, and full on-premises container deployment.
- **API Documentation:** https://learn.microsoft.com/en-us/azure/ai-services/speech-service/
- **SDKs/Libraries:** C#, C++, Java, JavaScript, Python, Go, Swift, Objective-C (via Azure Cognitive Services Speech SDK)
- **Developer Guide:** https://learn.microsoft.com/en-us/azure/ai-services/speech-service/get-started-speech-to-text
- **Standards:** Speech SDK (wraps gRPC + WebSocket internally); REST/JSON for batch transcription (OpenAPI specification available on GitHub at azure-rest-api-specs)
- **Authentication:** Azure subscription key (`Ocp-Apim-Subscription-Key` header) or Azure Active Directory (AAD) OAuth 2.0 token

---

### DeepL API

- **Description:** Neural machine translation API with the highest human-evaluated quality for European language pairs, formality control, document translation with layout preservation, and a new voice-to-voice translation API launched April 2026.
- **API Documentation:** https://developers.deepl.com/docs
- **SDKs/Libraries:** Python, Node.js/TypeScript, Java, C# (.NET), PHP, Ruby (all official DeepL libraries)
- **Developer Guide:** https://developers.deepl.com/docs/getting-started/about
- **Standards:** REST/JSON; responses include `detected_source_language` in BCP 47 format
- **Authentication:** API Key (`DeepL-Auth-Key` header); API Free and API Pro key types

---

## Notes

- **Emerging: Real-time voice-to-voice translation APIs.** DeepL's April 2026 launch of a voice translation API and Azure AI Speech's established real-time translation SDK represent a converging category. Neither exposes a full pipeline (STT + domain adaptation + translation + TTS) in a single open-standard interface.
- **MCP as integration layer.** MCP is evolving rapidly and may become the default mechanism for LLM agents to consume transcription results. Designing a transcription service with MCP Server support from day one would position it well for the agentic AI workflow ecosystem.
- **Streaming JSON schema.** There is no standardised schema for streaming transcript payloads. Each provider uses a proprietary JSON envelope. An open-source project adopting a published JSON Schema for streaming transcript events (interim/final word results, speaker labels, confidence scores) would meaningfully improve interoperability.
- **HIPAA BAA availability.** Of the APIs surveyed, AWS (Amazon Transcribe), Azure (AI Speech), and Google Cloud (Speech-to-Text) offer BAAs as part of their standard enterprise agreements. Deepgram, AssemblyAI, and Speechmatics offer BAAs under enterprise contracts. Gladia does not publicly advertise HIPAA compliance as of mid-2026.
