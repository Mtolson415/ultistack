# Linux voice: NPU-preferred recognition, measured selection

Research decision, November 10, 2026. Not installed or benchmarked on the project device.

- **Recognition:** prioritize evaluating Whisper Large-v3 Turbo through FastFlowLM on the XDNA2 NPU. Retain CPU/Vulkan fallback.
- **Speech output:** keep Kokoro CPU provisionally. No supported Linux NPU Kokoro path was established in this review; replacements remain eligible when validated.
- **Goal:** preserve GPU availability for large-context inference while maintaining English/Spanish quality, responsiveness, and offline use. NPU hardware utilization alone is not the success criterion.

FastFlowLM documents [Linux Strix Halo support](https://fastflowlm.com/docs/install_lin/) and [standalone ASR in release notes](https://github.com/ROCm/FastFlowLM/releases). AMD's separate [whisper.cpp NPU route](https://ryzenai.docs.amd.com/en/1.8/whisper_cpp.html) remains Windows-only in the reviewed documentation. These are different runtime paths. The [Lemonade backend matrix](https://github.com/lemonade-sdk/lemonade/blob/main/docs/dev/backends-reference.md) lists Linux CPU Kokoro.

Selection requires device-execution evidence, matching language/accuracy checks, end-to-end microphone and playback, load tests alongside GPU inference, and disconnected/reboot recovery. Power or latency gains remain unmeasured. The speech model family may survive migration while its runtime and packaged artifacts change.
