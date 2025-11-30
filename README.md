🎧 Aggression Risk Detection from Voice

A complete end-to-end prototype for detecting emotions and estimating aggression risk from speech.

This project explores how voice tone, emotional patterns, and acoustic features can help estimate an Aggression Risk Score (0–100) and classify a speaker’s emotional state using deep learning.

The system is built as a technical prototype (PoC) — it is not a real-world security tool.
Its goal is to show that aggression detection from audio is feasible using modern AI techniques.

🚀 Overview

This project takes an audio signal → processes it → extracts emotional features → and predicts:

🎭 Emotion label (8 classes from RAVDESS)

🔥 Aggression Risk Score (0–100)

💬 Optional textual interpretation

The full pipeline includes:

Audio preprocessing

Mel-spectrogram generation

CNN + LSTM (CRNN) model

Speaker-independent train/val/test split

Evaluation metrics

Real voice testing (record your own audio)

Everything is implemented in a single well-structured Colab notebook.

🧠 Model Architecture (CRNN)

This project uses a CRNN (Convolutional Recurrent Neural Network):

🟦 CNN block

Extracts local features from mel-spectrograms
→ frequency patterns, voice texture, tone

🟧 LSTM block

Captures how the voice evolves over time
→ emotional progression, intensity

🟩 Dense layers

Outputs probabilities for 8 emotions

🔥 Custom post-processing

Emotion → Aggression score (0–100)

This hybrid architecture is commonly used in speech-emotion-recognition tasks.

🎛 Features

✔ End-to-end audio-to-emotion pipeline
✔ Mel-spectrogram extraction
✔ Data augmentation
✔ CRNN model
✔ Training, validation, testing
✔ Final evaluation on held-out speakers
✔ Real-time prediction from recorded audio
✔ Visualization of emotion probabilities
✔ Aggression score interpretation

🎧 Dataset

RAVDESS – Ryerson Audio-Visual Database of Emotional Speech
Kaggle link:
https://www.kaggle.com/datasets/uwrfkaggler/ravdess-emotional-speech-audio

Emotions included:

neutral

calm

happy

sad

angry

fearful

disgust

surprised

We use a speaker-independent split:

16 actors → training

4 actors → validation

4 actors → testing

This is much harder than random splitting (and more realistic).

📊 Results
Metric	Score
Train Accuracy	~70%
Validation Accuracy	~50%
Test Accuracy	~43%

These results are normal for RAVDESS without pretraining, and align with published baselines.

The model performs well on emotional categories with strong acoustic patterns (happy, angry, surprised).

📥 Installing the RAVDESS Dataset

To download the dataset in Google Colab, you need a Kaggle API key (kaggle.json).

🔒 IMPORTANT:
Do NOT upload kaggle.json to GitHub.
It contains private credentials and must remain secret.

How to set it up
1. Get your Kaggle API Token

Go to your Kaggle account settings

Scroll to “API”

Click Create New Token

A file named kaggle.json will download

2. Upload it to Colab
from google.colab import files
files.upload()  # upload kaggle.json manually

3. Move it to the correct directory
!mkdir -p ~/.kaggle
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json


You can now download the dataset:

!kaggle datasets download -d uwrfkaggler/ravdess-emotional-speech-audio

▶️ Running the Model

The full workflow is available in:

Aggression_Risk_Detection_from_Voice_structured3.0.ipynb

It includes:

Data loading

Feature extraction

Model training

Model evaluation

Saving/loading the trained model

Recording a voice sample

Real-time prediction

To test your own voice:

Run the recording cell

Speak normally, happily, angrily, etc.

The notebook visualizes:

Emotion probabilities

Predicted label

Aggression score

Interpretation message

🧪 Example Output
Audio file: recorded.wav  
Emotion: angry  
Aggression Score: 78 / 100  
Interpretation: High aggression detected. Intense vocal tone and elevated stress markers.

🧰 Tech Stack

Python

PyTorch

Torchaudio

NumPy

Matplotlib

Google Colab

Kaggle API

📂 Repository Structure
├── Aggression_Risk_Detection_from_Voice_structured3.0.ipynb
├── README.md
└── (model weights can be saved locally after training)

👤 Author

Mohammad SWAYDAN
Double-degree student — ENSTA  & ULFG
Systems Observation & Artificial Intelligence
📧 mohammad.swaydan@ensta.fr

⭐ If you like this work

Feel free to star the repo or connect on LinkedIn!
This project is part of my learning journey in speech emotion recognition and deep learning.
