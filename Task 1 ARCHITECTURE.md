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
