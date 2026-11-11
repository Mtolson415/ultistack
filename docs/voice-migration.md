# Linux voice: NPU-preferred recognition, measured selection

Research decision, November 10, 2026. Not installed or benchmarked on the project device.

- **Recognition:** compare Qwen3-ASR-0.6B with Whisper Large-v3 Turbo; select the Linux NPU runtime independently. Retain supported CPU/GPU fallback.
- **Speech output:** compare Qwen3-TTS 0.6B candidates with Kokoro CPU; exact checkpoint, voices, and Linux NPU runtime remain to validate. Neither model is mandatory.
- **Goal:** preserve GPU availability for large-context inference while maintaining English/Spanish quality, responsiveness, and offline use. NPU hardware utilization alone is not the success criterion.

FastFlowLM documents [Linux Strix Halo support](https://fastflowlm.com/docs/install_lin/) and [standalone ASR in release notes](https://github.com/ROCm/FastFlowLM/releases). AMD's separate [whisper.cpp NPU route](https://ryzenai.docs.amd.com/en/1.8/whisper_cpp.html) remains Windows-only in the reviewed documentation. These are different runtime paths. The [Lemonade backend matrix](https://github.com/lemonade-sdk/lemonade/blob/main/docs/dev/backends-reference.md) lists Linux CPU Kokoro.

Selection requires device-execution evidence, matching language/accuracy checks, end-to-end microphone and playback, load tests alongside GPU inference, and disconnected/reboot recovery. Power or latency gains remain unmeasured. The speech model family may survive migration while its runtime and packaged artifacts change.
