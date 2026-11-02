# Licences

Oriel is free to use during the beta. Oriel's own code is not open source (all rights reserved); the libraries and
models it uses keep their own licences, listed here. Oriel downloads the models from their official pages; the only
model inside the installer is TransNetV2 (shot detection, MIT).

## AI models

| Model | What Oriel uses it for | Licence | Commercial use |
|---|---|---|---|
| SigLIP2 so400m (Google) — `google/siglip2-so400m-patch14-384` | visual search (required) | Apache-2.0 | yes |
| TransNetV2 (bundled) | shot detection | MIT | yes |
| opus-mt es-en (Helsinki-NLP) | translating Spanish searches into English | CC-BY-4.0 | yes, with attribution |
| Qwen3-ASR 1.7B / 0.6B (Qwen) | speech transcription | Apache-2.0 | yes |
| Qwen3-VL 4B Instruct (Qwen) | attributes, logos and text on screen, descriptions (NVIDIA only) | Apache-2.0 | yes |
| Qwen3-VL Embedding 2B / Reranker 2B (Qwen) | optional search models | Apache-2.0 | yes |
| Whisper large-v3 turbo / base (OpenAI; faster-whisper conversions) | optional transcription | MIT | yes |
| Parakeet TDT 0.6B v3 (NVIDIA; ONNX conversion) | optional transcription | CC-BY-4.0 | yes, with attribution |
| Silero VAD | voice detection | MIT | yes |
| distilbart CNN 12-6 | optional English summaries | Apache-2.0 | yes |
| pyannote speaker-diarization community-1 | optional speakers (needs a free Hugging Face account and accepting its terms) | CC-BY-4.0 | yes, with attribution |
| **insightface buffalo_l** | optional face groups | **non-commercial research only** | **no** |

**The face model.** insightface's code is MIT, but its pre-trained models (buffalo_l) may only be used for
non-commercial research. In Oriel the face model is **optional and off by default**: the wizard and
Settings › Face analysis ask you to read and accept its licence before downloading it or turning faces on. If your use
is commercial, leave faces off.

## Libraries (installed by the installer from the Python package index)

Permissive licences (MIT, BSD, Apache-2.0, ISC, PSF, HPND/MIT-CMU), commercial use allowed: PyTorch, torchvision,
torchaudio, transformers, accelerate, huggingface_hub, safetensors, tokenizers, sentencepiece, timm, open_clip,
sentence-transformers, ctranslate2, faster-whisper, onnx, onnxruntime, onnx-asr, qwen-asr, qwen-vl-utils, OpenCV,
NumPy, SciPy, pandas, scikit-learn, scikit-image, Pillow, PyAV, librosa, soundfile, pydub, numba, matplotlib, Flask,
Flask-SocketIO, Werkzeug, Jinja2, FastAPI, uvicorn, starlette, httpx, requests, aiohttp, pydantic, SQLAlchemy,
OpenTimelineIO (and its FCP / CMX adapters), pywebview, pythonnet, psutil, insightface (code), pyannote.audio (code),
lightning, gradio, nagisa, PyYAML, rich, tqdm and their dependencies.

Weak copyleft (commercial use allowed; changes to these libraries themselves must be shared): `certifi`, `bidict`,
`tqdm`, `orjson` (MPL-2.0); `soxr` (LGPL-2.1).

Strong copyleft: `soynlp` (GPL-3.0), pulled in by the speech package for Korean text. Oriel does not ship it inside
the installer; pip installs it on your PC.

The interface: Svelte, SvelteKit and Vite (MIT); the Manrope font (SIL Open Font License 1.1).

## Programs the installer may install

- **Python 3.12** (PSF licence), through `winget`.
- **ffmpeg** (GPL build from gyan.dev), through `winget`. Oriel runs it as a separate program; it is not part of
  Oriel's installer.

## Attribution

Oriel uses opus-mt (© Helsinki-NLP, CC-BY-4.0), Parakeet TDT (© NVIDIA, CC-BY-4.0) and pyannote speaker-diarization
community-1 (© pyannoteAI, CC-BY-4.0).
