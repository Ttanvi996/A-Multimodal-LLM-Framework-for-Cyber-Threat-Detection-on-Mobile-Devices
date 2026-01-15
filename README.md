**Project Title :- Multimodal LLM Framework for Cyber Threat Detection on Mobile Devices**

This project presents a multimodal cyber threat detection system that integrates machine-learning models across four different cybersecurity domains—network intrusion, phishing URLs, malware images, and audio spoofing—and combines them with an LLM-based explanation layer to generate human-readable security reports.

The goal is to build an interpretable, mobile-friendly threat detection pipeline capable of analyzing multiple attack vectors and providing users with clear, actionable insights.

2.Project Overview:- 
 + Modern cybersecurity attacks are increasingly complex and often span multiple data types (network flows, URLs, images, audio). Traditional systems rely on a single modality and fail to detect multi-stage or evolving threats.
 + This project introduces a hybrid ML + LLM architecture
 + Four independent ML models classify threats in their respective domains.
 + A lightweight LLM (TinyLlama-1.1B-Chat) converts model predictions, risk scores, and confidence levels into human-readable reports.
 + The entire pipeline is designed with low computational overhead, making it suitable for mobile or lightweight deployment contexts.
 + Each modality has its own preprocessing pipeline and threat classifier.

3.System Architecture:- 

The framework has four main layers: Data Preprocessing, Embedding Generation (Feature Extraction), Threat Detection Layer (ML Models) and Risk Reporting Layer (LLM)

4.Datasets Used:- 

 + CICIDS2017 — Network Intrusion Detection= ~2.3M network flow records,  15 classes (benign + 14 attack types)
   Preprocessing: merging 8 CSV files, cleaning features, label encoding
   Model: Feed-forward neural network with learned embeddings

 + Phishing & Malicious URL Dataset- Combined two phishing datasets
   Purely numerical URL features (no raw text)
   Model: Feed-forward neural network for binary phishing detection

 + Malimg Dataset — Malware Image Classification= 9,342 grayscale malware images across 25 families
   Image preprocessing: resize to 64×64, normalize
   Model: Lightweight CNN with Global Average Pooling
   Output: Malware family classification

 + ASVspoof 2019 — Audio Spoofing Detection= 20k+ training samples
   Extracted MFCC features (mean + STD)
   Model: Feed-forward neural network for binary classification (bonafide vs spoof)

5.Threat Detection Pipeline:-

For each dataset, the ML model outputs: Predicted Label, Confidence Score, Base Risk Value
These predictions are standardized and passed to the LLM layer.

6.LLM-Based Explanation Layer:- 

A lightweight LLM — TinyLlama-1.1B-Chat-v1.0 — is used to generate:
 + Human-readable security reports
 + Practical explanations of the threat
 + Severity rating (1–10)
 + This adds interpretability and makes the results accessible to non-experts.


Example Output :- 
Module: Network Intrusion
Predicted Label: DDoS
Confidence: 0.98
Risk Score: 9.0 (Critical)

Explanation:-
This flow pattern shows extremely high traffic bursts with repetitive packet sequences,
indicating a Distributed Denial of Service attack. Immediate mitigation is recommended.

7.Key Contributions:-

 + Unified multimodal threat detection across 4 data types
 + Lightweight LLM used for interpretability
 + Mobile-friendly architecture
 + High accuracy models (CNN, FFNN, MFCC-based classifiers)
 + Unified risk scoring system
 + Complete ML + LLM pipeline for cybersecurity


Technologies Used:- 
 + Python
 + TensorFlow
 + PyTorch
 + Scikit-learn
 + Librosa (Audio Feature Extraction)
 + TinyLlama-1.1B-Chat
 + NumPy / Pandas
 + Matplotlib / Seaborn


How to Run:-
1. Install dependencies
pip install -r requirements.txt

2. Train individual ML models
python train_network_model.py
python train_url_model.py
python train_malware_model.py
python train_audio_model.py

3. Run the unified threat detection pipeline
python multimodal_pipeline.py

4. Generate an LLM-based report
python generate_report.py

8.Conclusion:-

This project successfully integrates multimodal ML models with an LLM explanation layer, providing a comprehensive and interpretable cybersecurity solution. The architecture is lightweight, extensible, and suitable for real-world applications, especially mobile threat detection.

9.Future Work:-

 + Add real-time streaming support
 + Mobile deployment (TensorFlow Lite / ONNX)
 + Add more modalities (logs, emails, images)
 + Expand LLM to generate actionable remediation steps
