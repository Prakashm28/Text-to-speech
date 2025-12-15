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
