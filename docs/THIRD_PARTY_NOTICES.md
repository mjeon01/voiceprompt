# Third-party notices

VoicePrompt application source is not published. Third-party components retain their own licenses and rights.
Copies of the relevant license texts are in the adjacent `licenses` directory (or `../licenses` in the documentation repository).

| Component | Use | License / source |
|---|---|---|
| Whisper / model weights | Local speech recognition | MIT — https://github.com/openai/whisper |
| Argmax WhisperKit / ArgmaxCore 1.1.1 | macOS Core ML inference | MIT — https://github.com/argmaxinc/argmax-oss-swift |
| swift-transformers portions in ArgmaxCore | Tokenizer and model utilities | Apache-2.0 — https://github.com/huggingface/swift-transformers ; see Argmax NOTICES |
| swift-argument-parser 1.7.0 | macOS dependency | Apache-2.0 with Swift Runtime Library Exception — https://github.com/apple/swift-argument-parser |
| Whisper.net / CPU Runtime 1.9.1 | Windows local inference | MIT — https://github.com/sandrohanea/whisper.net |
| whisper.cpp / ggml | Native CPU inference | MIT — https://github.com/ggml-org/whisper.cpp |
| NAudio.Core / NAudio.WinMM 2.2.1 | Windows microphone capture | MIT — https://github.com/naudio/NAudio |
| .NET runtime / Windows Desktop runtime | Windows app runtime | MIT plus bundled third-party notices — https://github.com/dotnet/runtime and https://github.com/dotnet/wpf |
| Microsoft.Extensions.AI.Abstractions 10.2.0 | Whisper.net dependency | MIT — https://github.com/dotnet/extensions |

Models are downloaded separately, not included in the app ZIP. macOS conversions come from
https://huggingface.co/argmaxinc/whisperkit-coreml ; Windows GGML models come from
https://huggingface.co/ggerganov/whisper.cpp . Their upstream notices still apply.

The Windows Visual C++ redistributable is not bundled; obtain it from Microsoft if required.
NAudio 2.2.1 is deliberately pinned to the WinMM API used by this app; newer major NAudio releases require separate compatibility work.

Architecture references, without application source copied: VoxPrompt (https://github.com/charle-com/voxprompt),
VoiceInk (https://github.com/Beingpax/VoiceInk), WhisperDictation (https://github.com/JoshPetrenko/WhisperDictation),
KeyboardShortcuts (https://github.com/sindresorhus/KeyboardShortcuts).
