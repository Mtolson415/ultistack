# Corrected release-candidate stack

Architecture selected for implementation planning, November 10, 2026. No deployment or benchmark result is claimed.

| Tier | Selected roles / candidates |
|---|---|
| Heavy, exclusive | llama-swap with Qwen3.6-35B-A3B APEX-I-Quality + matching projector, or Qwen3-Coder-Next APEX-I-Quality; target 262K native context after validation |
| Knowledge | Qwen3 embeddings 0.6B for code and 4B for notes, separate Qdrant collections; 0.6B reranker; OCR candidate; Qwen3-4B-Instruct-2507 for anonymization, compression and note assistance |
| Privacy/routing | Presidio, detect-secrets, Piiranha; supplementary guard and classifier; deterministic gateway, reversible mappings, SQLite provider-model-task ledger and independent tests |
| Utilities | Qwen ASR/TTS candidates versus Whisper/Kokoro, supported NPU runtime independently selected; on-demand image-generation candidate |
| Cloud | FCC behind the privacy gateway; verified free NVIDIA NIM/Groq/OpenRouter options subject to account quotas; bounded retries and local fallback |

## Corrections carried into the design

- All service memory, cache, cold/warm speed and shared-bandwidth assumptions require device measurements. Support models stay warm only when capacity permits. File-cache warming does not guarantee instant swaps.
- Preserve maximum-context goals while scheduling competing work and measuring responsiveness.
- No implementation-specific NPU artifact or backend is selected. Model names do not establish compatible formats or execution hardware.
- TTS remains a separate selection; do not silently omit it when selecting dictation.
- Piiranha needs overlapping chunks for its documented input limit and review of its noncommercial/no-derivatives license before redistribution or commercial use. See its [model card](https://huggingface.co/iiiorg/piiranha-v1-detect-personal-information).
- DeepInfra has [paid pricing](https://deepinfra.com/pricing); it is outside the automatic free-only pool without applicable verified credits and explicit spend policy.
- Guard models supplement detection and policy. Complete-request coverage, execution isolation, deterministic restoration, and independent tests remain mandatory design elements.
- Configure actual endpoint addresses, model IDs, queues, cancellation and recovery; no promise of uninterrupted completion during every outage.

Heavy artifacts: [daily model](https://huggingface.co/mudler/Qwen3.6-35B-A3B-APEX-GGUF) and [coding model](https://huggingface.co/mudler/Qwen3-Coder-Next-APEX-GGUF). Exact revisions and byte sizes are recorded in private engineering notes. No model files are redistributed here.
