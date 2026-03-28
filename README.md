# Project VULCAN

![vulcan](https://github.com/ERC-BPGC/project-vulcan/assets/64892362/435007e0-b9ac-4111-8b91-9db8e8976c05)

A humanoid robot facial structure that can interact with humans — tracking faces, expressing emotions, hearing and speaking.

---

## Features

- **Eyes** — Independent 2-axis eyeball motion, eyelids, and gaze tracking via embedded cameras
- **Mouth** — Lip movement synced with speech and emotional expressions
- **Eyebrows** — Up/down motion to complement expressions
- **Neck** — 2-axis motion (horizontal 360° + vertical tilt)
- **Hearing & Speech** — Microphone array for sound localisation, speech recognition, and TTS output
- **Vision** — Face detection, gaze estimation, emotion recognition (FER), hand-wave detection
- **LLM Integration** — RAG-augmented responses via GPT

---

## Subsystems

### Mechanical
- [Eye, eyelid & eyebrow subsystem](https://www.youtube.com/watch?v=uqxhR49N3ws) — asymmetric eyeball motion with cameras, blinking, and brow movement
- [Mouth subsystem](https://www.youtube.com/watch?v=Ke2lJfY4haM) — lip articulation for speech and emotion
- [Neck subsystem](https://www.youtube.com/watch?v=GJRW8hP-Jcs) — full pan and tilt

### Software
- **`software/vision/`** — face detection, gaze estimation (`t_gaze.py`), emotion recognition (`m_model.py`, `m_expression.py`), hand-wave detection
- **`software/speech/`** — speech-to-text, TTS, voice selection
- **`software/llm/`** — GPT interface and RAG pipeline for context-aware responses
- **`software/core/`** — main driver (`vulcan.py`, `vulcan2.py`) coordinating all subsystems

### Electronics
- Servo PCB (ESP32 & Mega variants) — custom KiCad boards in `electronics/pcb/`
- ESP32-CAM firmware — `electronics/firmware/camera_esp/`
- Arduino servo firmware — `electronics/firmware/serial_arduino/`

---

## Repository Structure

```
project-vulcan/
├── docs/                   # Install guides (CUDA, OpenCV, dlib), diagrams
├── software/
│   ├── core/               # Main entry points
│   ├── vision/             # CV modules
│   ├── speech/             # STT / TTS
│   ├── llm/                # GPT + RAG pipeline
│   │   └── rag/
│   ├── data/               # Knowledge base files for RAG
│   ├── utils/              # Shared helpers
│   ├── tools/              # Diagnostic scripts (check mic, list cameras)
│   ├── experiments/        # Prototypes and WIP scripts
│   ├── models/             # Model weights (gitignored — see models/README.md)
│   ├── archive/            # Deprecated code
│   └── requirements.txt
├── electronics/
│   ├── pcb/                # KiCad projects
│   ├── firmware/           # Arduino / ESP32 sketches
│   └── scripts/            # Python hardware-communication scripts
└── mechanical/             # CAD files (SolidWorks, Fusion, Blender, STL)
    ├── Eye_subsystem/
    ├── Mouth_Subsystem/
    ├── Head Structure/
    ├── Neck Base/
    └── base_holder/
```

> **Model weights** are not tracked in git — see [`software/models/README.md`](software/models/README.md) for download links.  
> **Install guides** for CUDA, OpenCV, and dlib are in [`docs/`](docs/).

---

## Getting Started

```bash
# Install Python dependencies
pip install -r software/requirements.txt

# Download model weights (see software/models/README.md), then run
python software/core/vulcan2.py
```

---

## Built With

- [Python](https://www.python.org/)
- [OpenCV](https://opencv.org/)
- [dlib](http://dlib.net/)
- [LangChain](https://www.langchain.com/) / [OpenAI](https://openai.com/)
- [KiCad](https://www.kicad.org/)
- [ROS](https://www.ros.org/)

## Limitations

- The robot covers only the structure above the neck — no full-body mobility.

## Papa

- [Parth Shah](https://github.com/Parth-Shah-Tool-Kit)
- [Ritwik Sharma](https://github.com/Maker-Rat)
