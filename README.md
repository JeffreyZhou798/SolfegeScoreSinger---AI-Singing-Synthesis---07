# SolfegeScoreSinger - AI Singing Synthesis System

[![ModelScope](https://img.shields.io/badge/ModelScope-Space-blue)](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)
[![Python 3.10](https://img.shields.io/badge/Python-3.10-green)](https://www.python.org/)
[![Gradio](https://img.shields.io/badge/Gradio-6.2.0-orange)](https://gradio.app/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

**🎵 Try it now: [https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)**

---

## 📖 Overview

SolfegeScoreSinger is an AI-powered singing synthesis system that converts musical scores into natural vocal performances using solfege syllables (Do/Re/Mi/Fa/Sol/La/Ti). The system uses zero-shot voice cloning technology - users only need to record 7 solfege samples once, and the AI will learn their voice timbre to sing any score.

### Key Features

- **🎙️ Zero-Shot Voice Cloning**: Record 7 solfege syllables (Do/Re/Mi/Fa/Sol/La/Ti) once, and the AI learns your voice
- **🎼 Multi-Format Score Support**: Upload MIDI (.mid) or MusicXML (.mxl, .musicxml) scores
- **🎭 Movable Do & Fixed Do**: Supports both movable do (首调唱名法) and fixed do (固定调唱名法) systems
- **🎹 Multi-Voice Synthesis**: Handles multi-part scores (piano, ensemble) with voice mixing
- **🌍 English Interface**: Clean and intuitive English interface
- **🔊 Optional Denoising**: A/B comparison for noise reduction with fidelity-first approach
- **⚡ CPU-Optimized**: Runs on free CPU tier (no GPU required)
- **🌐 Cloud Deployment**: Deploy on ModelScope Spaces or Hugging Face Spaces

---

## 🎯 Use Cases

- **Music Education**: Teachers can create singing examples for students
- **Sight-Reading Practice**: Generate vocal performances for sight-reading exercises
- **Music Production**: Create vocal demos from sheet music
- **Choral Training**: Multi-voice synthesis for choir practice
- **Accessibility**: Help visually impaired musicians hear sheet music

---

## 🚀 Getting Started

### Online Demo (Recommended)

Visit our ModelScope Space for instant access:  
**👉 [https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)**

### How to Use

#### Step 1: Record Your Voice Samples

1. Click the **"Record Samples"** tab
2. For each solfege syllable (Do, Re, Mi, Fa, Sol, La, Ti):
   - Click **"Play Reference Tone"** to hear the standard pitch
   - Click **"Record [Syllable]"** to start recording
   - Sing the syllable clearly
   - Click **"Stop Recording"** when done
   - Use **"Re-record"** if needed
3. You can also upload pre-recorded audio files instead

**Built-in Voice Option**: Don't want to record? Use the default child voice (`DefaultVoice_Child`) provided in the system.

#### Step 2: Upload Your Score

1. Click the **"Upload Score"** tab
2. Upload a MIDI or MusicXML file (.mid, .mxl, .musicxml)
3. The system will:
   - Detect the key signature automatically
   - Convert notes to solfege syllables
   - Show the parsed score table
   - Estimate generation time

#### Step 3: Configure Settings (Optional)

- **Voice Mode**: Choose between your recording or default voice
- **Solfege Mode**: Select Movable Do or Fixed Do
- **Key Correction**: Manually adjust detected key if needed
- **Solfege Correction**: Modify individual syllables if AI makes mistakes

#### Step 4: Generate Audio

1. Click **"Generate Audio"**
2. Watch the progress bar (generation takes ~8 minutes per second of audio on CPU)
3. Preview the result in the audio player
4. Optionally apply noise reduction with A/B comparison
5. Download as WAV or MP3

---

## 📊 Example Outputs

### Single Voice Examples

| Score | Description | Output |
|-------|-------------|--------|
| **Twinkle Twinkle Little Star (Solo)** | Simple melody, single voice | `output twinkle-twinkle-little-star（Solo）.wav` |
| **Lightly Row (Piano)** | Piano piece, single melody line | `output lightly-row-Piano.wav` |

### Multi-Voice Examples

| Score | Description | Output |
|-------|-------------|--------|
| **Twinkle Twinkle Little Star (Piano 2-Voice)** | Two-hand piano arrangement | `output twinkle-twinkle-little-star-piano-2-voicing.wav` |

All examples can be found in the `Generated example/` directory.

---

## ⚙️ Technical Specifications

### System Requirements

- **Python**: 3.10+
- **PyTorch**: 2.1.0+
- **Gradio**: 6.2.0 (ModelScope SDK)
- **Hardware**: CPU (free tier supported)
- **Memory**: 4GB+ RAM recommended

### Supported Score Formats

| Format | Extension | Notes |
|--------|-----------|-------|
| MIDI | `.mid` | Standard MIDI files |
| MusicXML | `.mxl` | Compressed MusicXML (MuseScore export) |
| MusicXML | `.musicxml` | Uncompressed MusicXML |

### Key Detection

The system supports all 24 major and minor keys:
- **Major Keys**: C, G, D, A, E, B, F#, C#, F, Bb, Eb, Ab, Db, Gb, Cb
- **Minor Keys**: a, e, b, f#, c#, g#, d#, a#, d, g, c, f, bb, eb, ab

### Solfege Modes

#### Movable Do (首调唱名法)
- The tonic note is always "Do"
- Syllables change based on the key signature
- Example: In D major, D→Do, E→Re, F#→Mi
- Supports key modulation (转调)

#### Fixed Do (固定调唱名法)
- C is always "Do" regardless of key
- Syllables remain constant across all keys
- Example: In D major, D→Re, E→Mi, F#→Fa

---

## 🔧 Advanced Features

### Multi-Voice Synthesis

The system can process multi-part scores (piano, ensemble, choir):

- **Voice Separation**: Automatically separates voices from the score
- **Independent Generation**: Each voice is synthesized separately
- **Mixing Options**: Combine voices using sum, average, or weighted mixing
- **Volume Normalization**: Ensures balanced output

### Noise Reduction

Optional denoising with A/B comparison:

- **Conservative Approach**: Default preserves original fidelity
- **A/B Testing**: Compare original vs. denoised side-by-side
- **User Control**: You decide which version to keep

### Pitch Transposition

The system handles different clefs intelligently:

- **Treble Clef & Tenor Clef**: Transposed down one octave for comfortable vocal range
- **Alto Clef & Bass Clef**: Sung at actual pitch

---

## 🏗️ Architecture

```
SolfegeScoreSinger/
├── app.py                    # Main Gradio application
├── backend/                  # Core processing modules
│   ├── config.py             # Configuration & model management
│   ├── score_parser.py       # Score parsing & key detection
│   ├── metadata_generator.py # Metadata creation
│   ├── multi_voice_engine.py # Multi-voice synthesis
│   ├── audio_mixer.py        # Voice mixing
│   ├── denoise.py            # Noise reduction
│   └── i18n.py               # Internationalization (English)
├── locales/                  # UI translations
│   └── en.json               # English texts
├── DefaultVoice_Child/       # Built-in child voice samples
│   ├── Do.wav
│   ├── Re.wav
│   ├── Mi.wav
│   ├── Fa.wav
│   ├── Sol.wav
│   ├── La.wav
│   └── Ti.wav
├── soulxsinger/              # AI synthesis engine
└── preprocess/               # Audio preprocessing tools
```

---

## 🚢 Deployment

### Deploy on ModelScope Spaces

1. **Create Space**: 
   - Visit [modelscope.cn](https://www.modelscope.cn/)
   - Create new Space → Select "Gradio SDK"
   - Choose "CPU basic" (free tier)

2. **Upload Files**:
   - Upload all files from `modelscope-deploy/` directory
   - Or use Git: `git clone https://www.modelscope.cn/YOUR_USERNAME/YOUR_SPACE.git`

3. **Wait for Build**:
   - First build takes ~2-3 minutes
   - Model download: ~5-10 minutes (1.5GB, automatic)

4. **Access Application**:
   - Space will show "Running" status
   - Click the provided URL to use

### Deploy on Hugging Face Spaces

Similar process for Hugging Face:
- Select "Docker SDK" or "Gradio SDK"
- Choose "CPU basic" (free tier)
- Upload `huggingface-space/` files

---

## ⚠️ Important Notes

### CPU Performance

- **Generation Speed**: ~8 minutes per second of audio
- **Multi-Voice**: Time multiplies (2 voices = 2× time)
- **Recommendation**: Generate 15-second previews first
- **Queue System**: One task at a time (concurrency_limit=1)

### Voice Recording Tips

For best results:
- ✅ Use a quiet environment
- ✅ Sing each syllable clearly
- ✅ Match the reference tone pitch
- ✅ Keep consistent volume
- ❌ Avoid background noise
- ❌ Don't hum or mumble

### Score Limitations

- ✅ Supports unlimited duration
- ✅ Works with multi-part scores
- ✅ Handles key changes
- ⚠️ Complex ornamentation may be simplified
- ⚠️ Extremely fast passages (<0.2s notes) may need manual correction

---

## 🛠️ Development

### Installation

```bash
# Clone repository
git clone https://github.com/YOUR_USERNAME/SolfegeScoreSinger.git
cd SolfegeScoreSinger

# Install dependencies
pip install -r requirements.txt

# Run locally
python app.py
```

### Key Dependencies

```
torch>=2.0.0
gradio==6.2.0
music21>=9.0.0
librosa>=0.10.0
transformers==4.35.2
modelscope>=1.10.0
```

---

## 📚 Documentation

- [Deployment Guide](modelscope-deploy/DEPLOYMENT_GUIDE.md) - Detailed deployment instructions
- [API Reference](docs/API.md) - Backend module documentation
- [Architecture](docs/ARCHITECTURE.md) - System design details

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 📝 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Built with Gradio for the web interface
- Uses music21 for score parsing and music theory analysis
- Employs AI voice synthesis technology for natural vocal generation
- Deployed on ModelScope Spaces for cloud accessibility

---

## 📧 Contact

For questions or feedback, please open an issue on GitHub or leave a comment on our ModelScope Space.

---

**🎵 Made with ❤️ for music education**
