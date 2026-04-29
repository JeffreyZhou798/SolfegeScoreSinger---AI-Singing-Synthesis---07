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

Visit my ModelScope Space for instant access:  
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
4. Note: You can download the generated audio by clicking the **download icon** in the upper right corner of the preview window.

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

### Single Voice Example

| Score | Description | Output |
|-------|-------------|--------|
| **Twinkle Twinkle Little Star (Solo)** | Simple melody, single voice | `output twinkle-twinkle-little-star（Solo）.wav` |

### Multi-Voice Examples

| Score | Description | Output |
|-------|-------------|--------|
| **Lightly Row (Piano)** | Piano piece with multiple voices | `output lightly-row-Piano.wav` |
| **Twinkle Twinkle Little Star (Broken Chord)** | Broken chord accompaniment pattern | `output Twinkle Twinkle Little Star（broken chord）.wav` |
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

## ⚠️ Copyright Notice

© 2026 Jeffrey Zhou. All rights reserved.

This repository and its contents are protected by copyright law.  
No part of this project may be copied, reproduced, modified, or distributed without prior written permission from the author.

Commercial use is strictly prohibited.


*Built with ❤️ for music education*


# SolfegeScoreSinger - AI 歌唱合成系统

[![ModelScope](https://img.shields.io/badge/ModelScope-Space-blue)](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)
[![Python 3.10](https://img.shields.io/badge/Python-3.10-green)](https://www.python.org/)
[![Gradio](https://img.shields.io/badge/Gradio-6.2.0-orange)](https://gradio.app/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

**🎵 立即体验：[https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)**

---

## 📖 项目简介

SolfegeScoreSinger 是一款 AI 驱动的歌唱合成系统，能够将乐谱转化为使用唱名（Do/Re/Mi/Fa/Sol/La/Ti）演唱的自然人声。本系统采用零样本声音克隆技术——用户只需录制 7 个唱名样本，AI 即可学习其音色，从而演唱任意乐谱。

### 核心功能

- **🎙️ 零样本声音克隆**：仅需录制 7 个唱名（Do/Re/Mi/Fa/Sol/La/Ti），AI 即可习得您的音色
- **🎼 多格式乐谱支持**：支持上传 MIDI（.mid）或 MusicXML（.mxl、.musicxml）格式乐谱
- **🎭 首调 & 固定调**：同时支持首调唱名法与固定调唱名法
- **🎹 多声部合成**：可处理多声部乐谱（钢琴、合奏等）并进行声部混合
- **🌍 中英文界面**：界面简洁直观
- **🔊 可选降噪**：提供降噪前后的 A/B 对比，以保真为优先
- **⚡ CPU 优化**：可在免费 CPU 配置下运行，无需 GPU
- **🌐 云端部署**：支持在 ModelScope Spaces 或 Hugging Face Spaces 上部署

---

## 🎯 应用场景

- **音乐教育**：教师可为学生生成演唱示例
- **视唱练习**：生成视唱练习的人声演示
- **音乐制作**：从乐谱生成人声小样
- **合唱训练**：多声部合成，助力合唱排练
- **无障碍辅助**：帮助视障音乐人聆听乐谱内容

---

## 🚀 快速开始

### 在线体验（推荐）

访问 ModelScope Space 即可立即使用：  
**👉 [https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07](https://www.modelscope.cn/studios/JeffreyZhou2026/Solfege-Score-Singer-07)**

### 使用方法

#### 第一步：录制声音样本

1. 点击 **"录制样本"** 标签页
2. 对每个唱名（Do、Re、Mi、Fa、Sol、La、Ti）依次操作：
   - 点击 **"播放参考音"** 聆听标准音高
   - 点击 **"录制 [唱名]"** 开始录音
   - 清晰地演唱该唱名
   - 录制完成后点击 **"停止录音"**
   - 如需重录，点击 **"重新录制"**
3. 也可直接上传预先录制的音频文件
4. 注意：可点击预览窗口右上角的**下载图标**下载生成的音频。

**内置音色选项**：不想录音？可直接使用系统内置的儿童音色（`DefaultVoice_Child`）。

#### 第二步：上传乐谱

1. 点击 **"上传乐谱"** 标签页
2. 上传 MIDI 或 MusicXML 文件（.mid、.mxl、.musicxml）
3. 系统将自动：
   - 检测调号
   - 将音符转换为唱名
   - 显示解析后的乐谱表格
   - 估算生成所需时间

#### 第三步：配置参数（可选）

- **音色模式**：选择使用您录制的声音或默认音色
- **唱名模式**：选择首调唱名法或固定调唱名法
- **调号校正**：如有需要，可手动调整检测到的调号
- **唱名校正**：如 AI 识别有误，可手动修改单个唱名

#### 第四步：生成音频

1. 点击 **"生成音频"**
2. 观察进度条（CPU 环境下每秒音频约需 8 分钟生成）
3. 在音频播放器中预览结果
4. 可选择开启降噪并进行 A/B 对比
5. 以 WAV 或 MP3 格式下载

---

## 📊 示例输出

### 单声部示例

| 乐谱                        | 说明             | 输出文件                                           |
| --------------------------- | ---------------- | -------------------------------------------------- |
| **小星星（独唱）**          | 简单旋律，单声部 | `output twinkle-twinkle-little-star（Solo）.wav`   |

### 多声部示例

| 乐谱                          | 说明                 | 输出文件                                                   |
| ----------------------------- | -------------------- | ---------------------------------------------------------- |
| **轻轻划（钢琴版）**          | 含多声部的钢琴曲     | `output lightly-row-Piano.wav`                             |
| **小星星（琶音版）**          | 分解和弦伴奏型       | `output Twinkle Twinkle Little Star（broken chord）.wav`   |
| **小星星（钢琴双声部）**      | 双手钢琴编曲         | `output twinkle-twinkle-little-star-piano-2-voicing.wav`   |

所有示例可在 `Generated example/` 目录中找到。

---

## ⚙️ 技术规格

### 系统要求

- **Python**：3.10+
- **PyTorch**：2.1.0+
- **Gradio**：6.2.0（ModelScope SDK）
- **硬件**：CPU（支持免费配置）
- **内存**：建议 4GB 以上

### 支持的乐谱格式

| 格式     | 扩展名      | 说明                         |
| -------- | ----------- | ---------------------------- |
| MIDI     | `.mid`      | 标准 MIDI 文件               |
| MusicXML | `.mxl`      | 压缩 MusicXML（MuseScore 导出）|
| MusicXML | `.musicxml` | 未压缩 MusicXML              |

### 调号检测

系统支持全部 24 个大小调：
- **大调**：C、G、D、A、E、B、F#、C#、F、Bb、Eb、Ab、Db、Gb、Cb
- **小调**：a、e、b、f#、c#、g#、d#、a#、d、g、c、f、bb、eb、ab

### 唱名模式

#### 首调唱名法
- 主音始终为"Do"
- 唱名随调号变化
- 示例：D 大调中，D→Do、E→Re、F#→Mi
- 支持转调处理

#### 固定调唱名法
- 无论何种调号，C 始终为"Do"
- 唱名在所有调中保持不变
- 示例：D 大调中，D→Re、E→Mi、F#→Fa

---

## 🔧 高级功能

### 多声部合成

系统可处理多声部乐谱（钢琴、合奏、合唱等）：

- **声部分离**：自动从乐谱中分离各声部
- **独立生成**：各声部分别独立合成
- **混合选项**：支持求和、平均或加权混合方式
- **音量归一化**：确保输出音量均衡

### 降噪处理

提供可选降噪功能，支持 A/B 对比：

- **保守策略**：默认保留原始音质
- **A/B 测试**：可并排对比原始版与降噪版
- **用户决定**：由您选择保留哪个版本

### 音高移调

系统智能处理不同谱号：

- **高音谱号 & 次中音谱号**：下移一个八度，适应舒适人声音域
- **中音谱号 & 低音谱号**：按实际音高演唱

---

## 🏗️ 项目架构

```
SolfegeScoreSinger/
├── app.py                    # Gradio 主应用
├── backend/                  # 核心处理模块
│   ├── config.py             # 配置与模型管理
│   ├── score_parser.py       # 乐谱解析与调号检测
│   ├── metadata_generator.py # 元数据生成
│   ├── multi_voice_engine.py # 多声部合成引擎
│   ├── audio_mixer.py        # 声部混合
│   ├── denoise.py            # 降噪处理
│   └── i18n.py               # 国际化（英文）
├── locales/                  # 界面翻译文件
│   └── en.json               # 英文文本
├── DefaultVoice_Child/       # 内置儿童音色样本
│   ├── Do.wav
│   ├── Re.wav
│   ├── Mi.wav
│   ├── Fa.wav
│   ├── Sol.wav
│   ├── La.wav
│   └── Ti.wav
├── soulxsinger/              # AI 合成引擎
└── preprocess/               # 音频预处理工具
```

---

## 🚢 部署说明

### 部署至 ModelScope Spaces

1. **创建 Space**：
   - 访问 [modelscope.cn](https://www.modelscope.cn/)
   - 新建 Space → 选择"Gradio SDK"
   - 选择"CPU basic"（免费配置）

2. **上传文件**：
   - 上传 `modelscope-deploy/` 目录下的所有文件
   - 或使用 Git：`git clone https://www.modelscope.cn/YOUR_USERNAME/YOUR_SPACE.git`

3. **等待构建**：
   - 首次构建约需 2-3 分钟
   - 模型下载：约 5-10 分钟（1.5GB，自动完成）

4. **访问应用**：
   - Space 状态显示"Running"后即可访问
   - 点击提供的链接即可使用

### 部署至 Hugging Face Spaces

Hugging Face 的部署流程类似：
- 选择"Docker SDK"或"Gradio SDK"
- 选择"CPU basic"（免费配置）
- 上传 `huggingface-space/` 目录下的文件

---

## ⚠️ 注意事项

### CPU 性能说明

- **生成速度**：每秒音频约需 8 分钟
- **多声部**：时间成倍增加（2 个声部 = 2 倍时间）
- **建议**：先生成 15 秒的预览版本
- **队列机制**：同一时间只处理一个任务（concurrency_limit=1）

### 录音技巧

为获得最佳效果：
- ✅ 在安静环境中录音
- ✅ 每个唱名发音清晰
- ✅ 与参考音高保持一致
- ✅ 保持音量稳定
- ❌ 避免背景噪音
- ❌ 不要哼唱或含糊演唱

### 乐谱限制

- ✅ 支持任意时长
- ✅ 支持多声部乐谱
- ✅ 支持转调处理
- ⚠️ 复杂装饰音可能被简化
- ⚠️ 极快速的音符（<0.2 秒）可能需要手动校正

---

## 🛠️ 开发指南

### 本地安装

```bash
# 克隆仓库
git clone https://github.com/YOUR_USERNAME/SolfegeScoreSinger.git
cd SolfegeScoreSinger

# 安装依赖
pip install -r requirements.txt

# 本地运行
python app.py
```

### 主要依赖

```
torch>=2.0.0
gradio==6.2.0
music21>=9.0.0
librosa>=0.10.0
transformers==4.35.2
modelscope>=1.10.0
```

---

## 📚 文档资料

- [部署指南](modelscope-deploy/DEPLOYMENT_GUIDE.md) - 详细部署说明
- [API 参考](docs/API.md) - 后端模块文档
- [架构说明](docs/ARCHITECTURE.md) - 系统设计详情

---

## 🤝 参与贡献

欢迎贡献代码！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解相关规范。

---

## 📝 开源许可

本项目采用 Apache License 2.0 许可证，详情请见 [LICENSE](LICENSE) 文件。

---

## 🙏 致谢

- 使用 Gradio 构建 Web 界面
- 使用 music21 进行乐谱解析与乐理分析
- 采用 AI 声音合成技术实现自然人声生成
- 部署于 ModelScope Spaces，提供云端访问

---

## 📧 联系方式

如有问题或反馈，欢迎在 GitHub 提交 Issue，或在 ModelScope Space 页面留言。

---

## ⚠️ 版权声明

© 2026 Jeffrey Zhou。保留所有权利。

本仓库及其内容受版权法保护。  
未经作者书面授权，不得以任何形式复制、转载、修改或传播本项目的任何内容。

严禁商业使用。


*用 ❤️ 为音乐教育而生*

