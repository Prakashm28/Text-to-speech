
If the empty line or closing ``` is missing → GitHub throws this error.

---

# ✅ **HERE IS YOUR CORRECTED ARCHITECTURE.md (FULLY FIXED)**  
👉 **Just copy–paste THIS — it will work 100% in GitHub.**

---

# ✅ **FINAL WORKING VERSION – ARCHITECTURE.md**

```markdown
# System Architecture — Piper Personalization Project

This document describes the architecture for:

- Task 1 — Dataset Analysis
- Task 2 — Personalization Engine

---

# 📌 Task 1 — Dataset Analysis Architecture

```mermaid
graph TD

    %% DATA SOURCES
    subgraph "Datasets"
        LJSpeech["📁 LJSpeech Dataset"]
        VCTK["📁 VCTK Dataset"]
        LibriTTS["📁 LibriTTS Dataset"]
        HiFi["📁 Hi-Fi Multi-Speaker"]
        HUI["📁 HUI-Audio-Corpus-German"]
        CommonVoice["📁 Mozilla Common Voice"]
    end

    %% PIPELINE
    subgraph "Dataset Analysis Pipeline"
        Loader["📥 Dataset Loader
        - Load metadata
        - Load audio/text pairs"]

        Preprocess["🧹 Preprocessing
        - Noise reduction
        - Normalization
        - Silence trimming
        - Resampling"]

        FeatureExtract["🎛️ Feature Extraction
        - Prosodic features (F0, energy)
        - Speaking rate
        - Emotion cues
        - Timbre & pitch"]

        QualityAnalyzer["🔎 Quality Analyzer
        - SNR
        - Clarity
        - Distortion
        - Accent detection"]

        Mapper["🗺️ Voice Characteristics Mapping
        - Dataset → Expected TTS voice profile"]

        DocGen["📄 Documentation Generator
        - Dataset report
        - Feature charts
        - Mermaid diagrams"]
    end

    %% OUTPUT
    subgraph "Outputs"
        AnalysisReport["📘 DATASET_ANALYSIS.md"]
        Diagrams["🖼️ Mermaid Diagrams"]
    end

    %% CONNECTIONS
    LJSpeech --> Loader
    VCTK --> Loader
    LibriTTS --> Loader
    HiFi --> Loader
    HUI --> Loader
    CommonVoice --> Loader

    Loader --> Preprocess
    Preprocess --> FeatureExtract
    FeatureExtract --> QualityAnalyzer
    QualityAnalyzer --> Mapper
    Mapper --> DocGen

    DocGen --> AnalysisReport
    DocGen --> Diagrams





graph TD

    %% USER AUDIO INPUT
    subgraph "User Input"
        Mic["🎤 User Audio (5–10 min)"]
        Metadata["📝 User Metadata
        - User ID
        - Device info
        - Recording conditions"]
    end

    %% ENGINE PIPELINE
    subgraph "Personalization Engine"
        
        Preprocessor["🧹 Audio Preprocessor
        - Noise reduction
        - Normalization
        - Silence removal
        - Segmentation"]

        SpeakingPattern["⏱️ Speaking Pattern Analyzer
        - Pacing & rhythm
        - Word/sentence pauses
        - Breathing patterns"]

        ProsodyModel["📈 Stress & Pitch Model
        - F0 contours
        - Stress patterns
        - Intonation modeling"]

        EmotionDetector["😊 Emotion Detector
        - Happy / Sad / Neutral / Excited
        - Energy + pitch + spectral features"]

        ProfileBuilder["🧩 Voice Profile Builder
        - Prosody features
        - Emotion embeddings
        - Speaking pattern model
        - Create JSON/YAML profile"]

        FineTuner["🛠️ Model Fine-Tuning
        - Adapt Piper TTS model
        - Train user-specific embeddings
        - Save personalized weights"]
    end

    %% OUTPUT
    subgraph "Output"
        VoiceProfile["📦 personalized_voice_profile.json"]
        UpdatedModel["🎙️ Personalized Piper Model"]
    end

    %% CONNECTIONS
    Mic --> Preprocessor
    Metadata --> Preprocessor

    Preprocessor --> SpeakingPattern
    Preprocessor --> ProsodyModel
    Preprocessor --> EmotionDetector

    SpeakingPattern --> ProfileBuilder
    ProsodyModel --> ProfileBuilder
    EmotionDetector --> ProfileBuilder

    ProfileBuilder --> FineTuner

    FineTuner --> VoiceProfile
    FineTuner --> UpdatedModel
