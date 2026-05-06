# Transcription & Translation Service — Feature & Functionality Survey

> Candidate #314 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Deepgram | STT API / SaaS | Commercial (pay-as-you-go) | https://deepgram.com |
| AssemblyAI | STT + Audio Intelligence API | Commercial (pay-as-you-go) | https://www.assemblyai.com |
| Gladia | STT API / SaaS | Commercial (pay-as-you-go, free tier) | https://www.gladia.io |
| Rev.ai | STT API + Human fallback | Commercial (pay-as-you-go) | https://www.rev.ai |
| Speechmatics | Enterprise STT + Translation API | Commercial (custom pricing) | https://www.speechmatics.com |
| Whisper (OpenAI) | Open-source STT model | MIT / open-source (self-host) or managed API | https://github.com/openai/whisper |
| Google Cloud Speech-to-Text (Chirp 3) | Managed cloud STT + Translation | Commercial (pay-as-you-go) | https://cloud.google.com/speech-to-text |
| Amazon Transcribe | Managed cloud STT | Commercial (pay-as-you-go) | https://aws.amazon.com/transcribe |
| Azure AI Speech | Managed cloud STT + Translation | Commercial (pay-as-you-go) | https://azure.microsoft.com/en-us/products/ai-services/speech |
| Otter.ai | Consumer/SMB meeting assistant SaaS | Commercial (freemium, Pro $16.99/month) | https://otter.ai |
| DeepL API | Text + Voice Translation API | Commercial (free tier + Pro) | https://www.deepl.com/en/products/api |
| Pyannote | Open-source speaker diarization library | MIT / open-source (self-host); pyannoteAI managed | https://github.com/pyannote/pyannote-audio |

---

## Feature Analysis by Solution

### Deepgram

**Core features**
- Real-time streaming transcription via WebSocket with Nova-3 model
- Batch transcription via REST API for pre-recorded files
- Speaker diarization: per-word speaker labels in real-time and batch
- 45+ language support with automatic language detection
- Smart formatting: automatic punctuation, capitalisation, number normalisation
- Filler word detection (um, uh, etc.)
- Utterance segmentation and word-level timestamps
- Keyterm prompting (custom vocabulary boost without retraining)
- PII redaction (redacts personal identifiers from transcripts)
- On-premises and private cloud deployment options

**Differentiating features**
- Nova-3 Medical model: domain-adapted acoustic model for clinical audio
- Flux model: purpose-built for conversational voice-agent speech (interruptions, overlaps)
- Sub-300 ms streaming latency — fastest in class for voice-agent pipelines
- Self-serve acoustic model customisation without ML expertise

**UX patterns**
- Developer-first documentation with interactive playground in browser
- SDKs for Python, Node.js, Go, .NET, Ruby, Rust
- No consumer app surface; purely API/SDK delivery
- Pricing calculator available on dashboard; volume discounts automatic

**Integration points**
- REST API and WebSocket for streaming
- Official SDKs: Python, JavaScript/TypeScript, Go, .NET, Ruby, Rust
- Webhook callbacks for async jobs
- Compatible with LiveKit, Liveblocks, Vapi, Bolna voice-agent frameworks
- Zapier and Make connectors for no-code integration

**Known gaps**
- No built-in translation (STT only; translation requires separate API call)
- No consumer or SaaS front-end; pure developer API
- Limited post-processing AI (no summarisation or action-item extraction built in)
- Speaker identification (recognising a named speaker) not yet in production

**Licence / IP notes**
- Proprietary SaaS; no open-source components exposed. Models are not licensable for offline use on lower tiers.

---

### AssemblyAI

**Core features**
- Universal-3-Pro model: 93.3% word accuracy, 99 languages with code-switching
- Real-time streaming via WebSocket (~300 ms latency)
- Batch transcription via REST API
- Speaker diarization with per-word labels
- Sentiment analysis per utterance
- Auto chapters / topic detection
- Entity detection (people, places, organisations, dates)
- PII redaction
- Content safety labels (violence, profanity, etc.)
- Summarisation using LeMUR (LLM post-processing layer)

**Differentiating features**
- LeMUR: embed GPT-class LLM queries directly against the transcript without exporting data
- Universal-3-Pro delivers 53.2% better accuracy than prior generation at same price
- 99 language support with automatic code-switching between English and other languages
- Audio intelligence bundle covers the widest range of NLU tasks in a single API

**UX patterns**
- API-first; rich documentation and guided tutorials
- SDKs: Python, JavaScript/TypeScript, Java, Go, C#, Ruby
- Real-time playground in developer portal
- LeMUR prompting via natural language on top of transcript objects

**Integration points**
- REST API and WebSocket (Universal-Streaming)
- SDKs: Python, Node.js, Java, Go, Ruby, C# (.NET)
- Langflow integration for AI pipeline builders
- Webhooks for async job completion
- Compatible with LangChain, LlamaIndex as a data source

**Known gaps**
- Translation is not a built-in feature (transcription → separate translation API required)
- Real-time LeMUR analysis not yet available (LeMUR works on completed transcripts only)
- Speaker identification (named speakers) absent
- No on-premises deployment option

**Licence / IP notes**
- Proprietary SaaS; models proprietary. SDKs are Apache-2.0 licensed open source.

---

### Gladia

**Core features**
- Solaria-1 model: 94% word accuracy, 110+ languages, native code-switching
- Real-time streaming with 103 ms partial latency
- Batch transcription
- Speaker diarization bundled at no extra cost
- Word-level timestamps
- Named entity recognition (NER) and topic detection
- Sentiment analysis
- In-API translation: one call returns transcript + translation in one or more target languages
- Automatic language detection

**Differentiating features**
- Native code-switching: seamlessly handles mid-sentence language switches without routing overhead
- Translation bundled in same API response — avoids latency of chaining a second API
- $0.55/hour flat rate, all features included (no per-feature surcharges)
- 110+ language coverage, widest of the specialist APIs

**UX patterns**
- Developer-first; clean REST and WebSocket documentation
- SDKs: Python, JavaScript/TypeScript
- Free tier of 10 hours/month lowers onboarding friction
- Meeting-bot builder guides showing end-to-end patterns

**Integration points**
- REST API and WebSocket for real-time
- Vapi voice-agent framework integration
- Webhooks for async completion
- Meeting-bot frameworks (Recall.ai)

**Known gaps**
- LLM post-processing (summarisation, action items) not built in; requires external call
- Speaker identification (named speakers) not available
- No on-premises or private cloud deployment
- Translation quality for low-resource language pairs not independently benchmarked

**Licence / IP notes**
- Proprietary SaaS. No open-source model weights published.

---

### Rev.ai

**Core features**
- AI transcription (Reverb model) at $0.003/min
- Human transcription fallback at $1.99/min via network of 14,000+ professional transcriptionists
- 57+ language support
- Speaker diarization
- Sentence-level timestamps and word-level timestamps
- Automatic punctuation and capitalisation
- Custom vocabulary
- PII redaction
- Translation (available as add-on)
- Sentiment analysis and topic extraction

**Differentiating features**
- Seamless AI-to-human escalation via the same API endpoint: developers set accuracy thresholds and human review is triggered automatically
- 99%+ accuracy guarantee available with human review for legal, medical, compliance-critical use cases
- Integration with Recall.ai for automated meeting-bot capture

**UX patterns**
- Dual-audience documentation: developer API guide and consumer app onboarding
- SDKs: Python, Node.js, Java, Ruby
- Async job model with webhook callbacks
- Confidence scores surfaced so downstream logic can route to human review

**Integration points**
- REST API (async) and WebSocket (real-time streaming)
- SDKs: Python, Node.js, Java, Ruby
- Recall.ai partnership for meeting capture
- Webhook callbacks for async completion

**Known gaps**
- Human fallback pricing (597x AI cost) makes it impractical for volume use cases
- No LLM post-processing built in (summarisation, action items require external API)
- Streaming latency higher than Deepgram or Gladia
- Translation feature is an add-on, not natively integrated

**Licence / IP notes**
- Proprietary SaaS. Human transcriptionist network operates under work-for-hire agreements; transcripts are client-owned.

---

### Speechmatics

**Core features**
- Real-time and batch transcription across 55+ languages
- Unified speech-translation API: send audio once, receive transcript + translation together
- Speaker diarization (per-word speaker labels)
- Custom vocabulary (boost accuracy for proper nouns, acronyms, domain terms)
- No data logging as standard (privacy-first architecture)
- On-premises, private cloud, and edge deployment support
- Sub-500 ms real-time latency
- Automatic language detection

**Differentiating features**
- Unified STT + translation in a single API call — reduces pipeline complexity and eliminates round-trip latency
- Accent and dialect inclusivity: training deliberately targets underrepresented accents; outperforms Google on German, French, Swedish, Japanese
- Partial and final translation results delivered separately for real-time display scenarios
- On-premises deployment with no data leaving customer infrastructure — critical for regulated sectors

**UX patterns**
- Enterprise sales model with dedicated onboarding
- REST API and WebSocket documentation at docs.speechmatics.com
- SDKs: Python, JavaScript; C++ available for edge deployment
- CLI tool for batch processing and testing

**Integration points**
- REST API (batch) and WebSocket (real-time)
- On-premises Docker/Kubernetes containers
- Microsoft Azure Marketplace listing
- Webhook callbacks

**Known gaps**
- No consumer SaaS front-end; purely B2B/enterprise
- LLM post-processing (summarisation, action items) not included
- Speaker identification (named speakers) not available
- Custom acoustic model fine-tuning requires enterprise contract
- Price transparency requires sales engagement

**Licence / IP notes**
- Proprietary enterprise software. On-premises deployment available under commercial licence.

---

### Whisper (OpenAI) / WhisperX

**Core features**
- Open-source multilingual STT model supporting 99 languages
- Speech translation: transcribes non-English audio directly to English text
- Available in five model sizes (tiny → large-v3-turbo)
- Word-level timestamps (with WhisperX extension)
- Speaker diarization when combined with Pyannote (via WhisperX)
- Self-hostable on consumer or cloud GPU hardware
- Available as managed API via OpenAI (whisper-1) at $0.006/min
- GPT-4o-transcribe (streaming) available as next-generation managed option

**Differentiating features**
- MIT-licensed open-source weights — usable for on-device privacy-preserving transcription
- Foundation for the majority of downstream transcription tools (Otter.ai, Descript, Fireflies, etc.)
- Large-v3-turbo: 5.4x faster than Large-v2 with minimal accuracy loss
- Speech-to-English translation built into the model architecture (no separate translation step)

**UX patterns**
- CLI and Python library interface; no consumer UI
- Broad community ecosystem: WhisperX, faster-whisper, whisper.cpp (C++ port for CPU inference)
- Hugging Face Hub for model downloads and fine-tuned variants
- OpenAI Playground for managed API testing

**Integration points**
- Python library (self-hosted)
- OpenAI REST API (whisper-1, gpt-4o-transcribe)
- Hugging Face Transformers pipeline
- LangChain and LlamaIndex document loaders
- AWS SageMaker for scalable batch inference
- Local deployment via whisper.cpp (no Python required)

**Known gaps**
- No real-time streaming in base open-source implementation (batch only)
- No built-in diarization (requires WhisperX + Pyannote)
- Hallucination on silent or near-silent audio segments (known bug)
- Requires GPU for practical inference with large models; CPU inference too slow for production
- No PII redaction, sentiment, or audio intelligence features

**Licence / IP notes**
- MIT licence for model weights and code. No patent claims identified. Commercially usable, including for closed-source products. GPT-4o-transcribe is proprietary.

---

### Google Cloud Speech-to-Text (Chirp 3)

**Core features**
- Chirp 3 model: latest-generation multilingual STT for 85+ languages
- Batch and streaming transcription
- Speaker diarization and word-level timestamps
- Model adaptation (custom vocabulary)
- Speech translation (via Chirp 2/3 and integration with Cloud Translation API)
- Subtitle export (SRT, VTT formats)
- Integration with Cloud Storage for large-scale batch workloads
- Automatic punctuation

**Differentiating features**
- Deep integration with Google Cloud ecosystem (Translation API, Natural Language API, BigQuery)
- Chirp 3 supports direct speech-to-text translation in a single model inference
- Scalable managed infrastructure; no provisioning required
- Available via Vertex AI for enterprise ML platform workflows

**UX patterns**
- Google Cloud Console with sample audio playground
- SDKs: Python, Java, Node.js, Go, C#, PHP, Ruby
- Cloud Shell and gcloud CLI for quick testing
- Broad tutorials and Colab notebooks

**Integration points**
- REST API and gRPC
- Cloud Storage triggers for automated batch transcription pipelines
- Integration with Pub/Sub for streaming event pipelines
- Google Workspace (Docs, Meet) live captions
- Vertex AI pipelines

**Known gaps**
- Higher latency than specialist APIs for real-time streaming
- Pricing is more complex (per 15-second chunk model)
- No built-in LLM post-processing (summarisation requires separate Natural Language or Vertex AI call)
- Diarization quality lags behind Pyannote-based solutions

**Licence / IP notes**
- Proprietary Google Cloud service. Customer data subject to Google Cloud DPA. No open-source model weights.

---

### Amazon Transcribe

**Core features**
- Batch and streaming (real-time) transcription
- Medical transcription (Transcribe Medical sub-service)
- Call Analytics: sentiment, talk-time, non-talk-time, speaker labels for contact-centre use
- Custom vocabulary and custom language models
- PII redaction
- Speaker diarization
- Automatic language identification
- Toxic content detection
- Integration with Amazon Translate for translation via chained API calls
- HealthScribe: clinical note generation from patient-provider conversations

**Differentiating features**
- HealthScribe: the only STT API with built-in clinical note structuring (SOAP notes, clinical insights)
- Call Analytics: deepest contact-centre QA feature set of any cloud STT provider
- Custom language model fine-tuning available via the console without ML expertise
- Tight integration with AWS ecosystem (S3, Lambda, Comprehend, Polly, Translate)

**UX patterns**
- AWS Console with guided wizard for batch jobs
- SDKs: .NET, Go, Java, JavaScript, PHP, Python, Ruby
- CloudFormation templates for infrastructure-as-code deployment
- IAM-controlled access consistent with AWS security model

**Integration points**
- REST API and WebSocket streaming
- S3 input/output for batch jobs
- Lambda event triggers for automated pipelines
- Amazon Translate (for translation)
- Amazon Polly (for text-to-speech round-trip)
- Amazon Comprehend (NLU)

**Known gaps**
- Translation is not native; requires chaining Amazon Translate separately
- Real-time streaming latency not competitive with Deepgram or Gladia for voice-agent use
- Lock-in to AWS ecosystem limits portability
- No consumer front-end; purely cloud-service oriented

**Licence / IP notes**
- Proprietary AWS service. Customer data subject to AWS DPA and customer controls. No open-source model weights.

---

### Azure AI Speech

**Core features**
- Real-time speech-to-text and batch transcription
- Speech translation: real-time translation into 60+ target languages in one API call
- Text-to-speech (TTS) with neural voices
- Speaker recognition and diarization
- Custom speech: acoustic and language model fine-tuning
- Conversation transcription: multi-channel audio with per-speaker transcript
- Pronunciation assessment
- Keyword detection
- Edge deployment via Azure Speech containers (offline/on-premises)

**Differentiating features**
- Real-time speech translation to 60+ languages natively in the Speech SDK — tightest latency of the hyperscaler offerings
- Conversation Transcription API designed for multi-device conference room scenarios
- Pronunciation Assessment: unique feature for language-learning applications
- Full on-premises container deployment with offline capability

**UX patterns**
- Azure Portal with Speech Studio for no-code testing
- SDKs: C#, C++, Java, JavaScript, Python, Go, Swift, Objective-C
- Speech Studio for custom model training via browser UI
- Azure Cognitive Search integration for transcript indexing

**Integration points**
- REST API and Speech SDK (gRPC + WebSocket internally)
- Azure Event Hubs and Service Bus for streaming pipelines
- Power Platform connectors for no-code/low-code integration
- Teams and Office 365 integration for enterprise meeting workflows
- Azure OpenAI integration for LLM post-processing

**Known gaps**
- Complex pricing tiers (standard, custom, conversation) create billing uncertainty
- Custom model training requires significant annotated audio data
- Vendor lock-in to Azure; no portable open-source path
- LLM post-processing (summarisation) requires separate Azure OpenAI call

**Licence / IP notes**
- Proprietary Microsoft service. Customer data subject to Microsoft DPA. Speech container images are licensable for on-premises under Azure consumption model.

---

### Otter.ai

**Core features**
- Real-time meeting transcription with speaker labels
- Auto-generated meeting summary and action items
- AI Chat: query the transcript in natural language post-meeting
- OtterPilot: automated meeting bot joins Zoom, Teams, Google Meet
- Collaborative editing: highlight, comment, assign action items
- Vocabulary customisation per workspace
- Search across all meeting transcripts
- Integrations: Slack, Zoom, Salesforce, Google Drive, Jira, Notion
- MCP Server (2026): exposes transcript archive to LLM agents

**Differentiating features**
- Consumer-grade UX: zero-setup meeting recording for non-technical users
- MCP Server integration (2026) allows Claude, ChatGPT, and other agents to query meeting archives
- Institutional knowledge graph: builds a searchable knowledge base from ongoing meetings
- Salesforce integration: auto-populates CRM fields from meeting transcripts

**UX patterns**
- Web app and mobile app (iOS, Android) — no installation required for basic use
- Onboarding in under 2 minutes; auto-join calendar-linked meetings
- Progressive disclosure: summary and action items shown above full transcript
- Suggested prompts in AI Chat to guide users unfamiliar with LLM querying

**Integration points**
- Zapier and Make for no-code workflow automation
- Slack (share summaries), Zoom (auto-join), Google Meet, Teams
- Salesforce CRM, HubSpot
- Google Drive, Notion, Jira
- MCP Server for LLM agent access
- REST API (limited; aimed at enterprise tier)

**Known gaps**
- API surface is very limited compared to developer-focused STT APIs
- Video recording only available on Enterprise plan
- English-centric; multilingual support is limited vs. Gladia or Speechmatics
- No translation features
- No on-premises or self-hosted option

**Licence / IP notes**
- Proprietary SaaS. No open-source components. Transcripts stored on Otter servers unless Enterprise.

---

### DeepL API

**Core features**
- Neural machine translation across 33 languages
- Document translation (Word, PowerPoint, PDF, HTML, text files) preserving formatting
- Glossary support: enforce custom terminology at scale
- XML/HTML tag-aware translation (preserves markup structure)
- Formality control (formal/informal register per language)
- Writing improvement (DeepL Write): style and grammar suggestions
- Voice-to-voice translation suite (launched April 2026): meeting, mobile, web, and group conversation modes
- SDKs: Python, .NET, Node.js, PHP, Ruby, Java

**Differentiating features**
- Consistently top-ranked for translation quality in human evaluation benchmarks, especially European language pairs
- Voice-to-voice translation API (2026): first-class audio translation pipeline for custom integrations
- Formality control is unique among major translation APIs — essential for languages with T/V distinction (German, French, Spanish, etc.)
- Document translation with layout preservation removes need for reformatting

**UX patterns**
- Consumer web app at deepl.com (familiar reference point for evaluating quality)
- Developer portal with interactive API explorer
- Six official SDK libraries with consistent interface
- Free tier (500k characters/month) for prototyping

**Integration points**
- REST API (text, document, glossary endpoints)
- Voice translation API (REST, 2026)
- Official SDKs: Python, Node.js/TypeScript, Java, C# (.NET), PHP, Ruby
- CAT tool integrations: SDL Trados, memoQ, Phrase, Memsource
- Zapier connector
- Browser extensions and desktop apps (indirect integration path for enterprise)

**Known gaps**
- Only 33 languages supported — significantly narrower than Google Translate or Azure Translator
- No speech-to-text built in until 2026 voice API (still early stage)
- No speaker diarization or audio intelligence features
- No real-time streaming translation (voice API is turn-based)
- No open-source model or self-hosted option

**Licence / IP notes**
- Proprietary SaaS. Translation models are proprietary. SDK libraries are open source (MIT). API terms prohibit storing translations for model training purposes.

---

### Pyannote (pyannote-audio / pyannoteAI)

**Core features**
- Speaker diarization: automatic labelling of who spoke when
- Speech activity detection (VAD)
- Speaker change detection
- Overlapped speech detection
- Speaker embedding and verification
- STT orchestration (pyannoteAI managed): single API call returns speaker-attributed transcript using Whisper Large v3 Turbo
- Python SDK and TypeScript SDK (pyannoteAI)
- REST endpoint (pyannoteAI managed): no SDK required for basic use

**Differentiating features**
- State-of-the-art open-source diarization (11–19% DER on AMI benchmark)
- pyannoteAI Precision-2 model: 40% faster training pipeline, improved noisy audio performance vs. OSS 3.1
- Only solution with MIT-licensed open-source weights enabling fully offline, privacy-preserving diarization
- STT orchestration combines Whisper + Pyannote in one managed call

**UX patterns**
- Research-grade library requiring Python and GPU familiarity
- Hugging Face Hub for model distribution with licence-gated access
- pyannoteAI managed service provides REST endpoint for non-Python teams
- Changelog at pyannote.ai for tracking improvements

**Integration points**
- Python library (self-hosted)
- Hugging Face Transformers pipeline
- WhisperX (open-source STT + diarization pipeline)
- AWS SageMaker asynchronous endpoint (documented deployment pattern)
- pyannoteAI REST API and Python/TypeScript SDKs

**Known gaps**
- Real-time streaming diarization not available; batch-only
- Significant infrastructure effort for self-hosted production deployment
- Requires Hugging Face account and licence acceptance for gated models
- No consumer UX; purely developer/research tooling

**Licence / IP notes**
- pyannote-audio core: MIT licence. Pretrained model weights: available under Hugging Face model licence (requires acceptance). pyannoteAI managed service: proprietary. No patent concerns identified.

---

## Cross-Cutting Feature Themes

### Table-Stakes Features
- Accurate word-level transcription with punctuation and capitalisation
- Speaker diarization (who said what, when)
- Word-level timestamps
- Support for at least English and major European languages
- WebSocket streaming and REST batch API endpoints
- Custom vocabulary / keyword boosting
- Developer SDKs in at least Python and JavaScript/TypeScript
- Webhook callbacks for async job completion
- PII / sensitive-data redaction

### Differentiating Features
- Native code-switching within utterances (Gladia)
- Human transcription fallback with accuracy SLA (Rev.ai)
- Unified STT + translation in a single API response (Gladia, Speechmatics)
- Built-in LLM post-processing on transcripts without data export (AssemblyAI LeMUR)
- Clinical note generation from patient audio (Amazon Transcribe HealthScribe)
- On-premises / edge container deployment (Speechmatics, Azure AI Speech, Whisper)
- MIT-licensed self-hostable model weights (Whisper, Pyannote)
- Voice-to-voice translation (DeepL 2026, Azure AI Speech)
- Formality control in translation output (DeepL)
- MCP Server for LLM agent access to transcript archives (Otter.ai)

### Underserved Areas / Opportunities
- **End-to-end pipeline as a single artifact**: Most solutions require chaining STT → diarization → translation → LLM post-processing across 2–4 separate APIs. No single open-source tool integrates all steps.
- **Low-resource language accuracy**: Coverage beyond the top 50 languages degrades sharply; mid-range languages (Tagalog, Swahili, Bengali, Tamil) remain underserved by specialist APIs.
- **Named speaker identification**: Distinguishing speakers by identity (not just "Speaker 1") requires custom integration work with voice biometrics; no API bundles this seamlessly.
- **Domain-adapted real-time translation**: Real-time translation with domain vocabulary preservation (legal, medical, technical) is unavailable as a single-call API.
- **Structured output formats**: Generating meeting minutes, agenda-matched summaries, or SOAP clinical notes directly from raw audio with no post-processing step.
- **Confidence-aware human escalation at granular level**: Sentence- or phrase-level confidence-triggered human review (not just job-level) is not offered by any current API.
- **Privacy-preserving cloud hybrid**: On-device pre-processing with cloud enrichment for regulated sectors remains architecturally unsupported by most vendors.

### AI-Augmentation Candidates
- **Post-processing LLM layer**: Rule-based punctuation and capitalisation restoration is already being replaced by LLM generation; the same pattern can extend to action-item extraction, summarisation, and classification.
- **Acoustic model fine-tuning from user feedback**: Rather than static custom vocabulary, an AI-native system can continuously fine-tune on corrections provided by users.
- **Dynamic routing**: AI can select the best STT/translation model for each audio segment based on detected language, noise level, and domain — rather than committing to a single provider at session start.
- **Real-time speaker context tracking**: LLMs can maintain cross-turn speaker context to resolve pronouns and fill gaps in diarization at a discourse level.
- **Intelligent confidence thresholding**: ML classifiers on confidence scores and audio features can route segments for human review more efficiently than flat accuracy thresholds.

---

## Legal & IP Summary

The dominant open-source components (Whisper, Pyannote, faster-whisper) are MIT-licensed and impose no restrictions on commercial use or closed-source integration. All major commercial APIs (Deepgram, AssemblyAI, Gladia, Rev.ai, Speechmatics, Google, AWS, Azure, DeepL) are proprietary SaaS services with standard developer API terms; their model weights are not accessible and their API output can be stored and used by customers per their respective data processing agreements. No patent concerns were identified for Whisper or Pyannote. DeepL's API terms prohibit using translated output to train competing models. An AI-native open-source project built on Whisper and Pyannote would face no known IP barriers.

---

## Recommended Feature Scope

**Must-have (MVP)**
- Audio ingestion: REST batch upload and WebSocket real-time streaming
- STT transcription powered by Whisper large-v3-turbo (self-hosted or via managed API)
- Speaker diarization via Pyannote integration
- Word-level timestamps with speaker labels
- Translation of transcripts to one or more target languages (DeepL API or Speechmatics unified call)
- Structured JSON output: transcript, speaker segments, translated segments
- REST API with Python and Node.js SDKs

**Should-have (v1.1)**
- LLM post-processing: auto-summary, action-item extraction, key-topics tagging
- PII redaction (names, phone numbers, email addresses)
- Custom vocabulary / keyterm boosting
- WebVTT and SRT subtitle export
- Confidence scores per word or segment
- Webhook callbacks for async job completion
- Multi-format audio input (MP3, MP4, WAV, OGG, M4A)

**Nice-to-have (backlog)**
- Named speaker identification (voice biometrics enrolment + recognition)
- Domain-adapted vocabulary packs (legal, medical, engineering)
- Human review escalation queue with confidence-threshold routing
- On-device / edge inference mode using whisper.cpp for privacy-critical deployments
- MCP Server endpoint exposing transcript archive to LLM agents
- Pronunciation assessment (language-learning applications)
