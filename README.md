Project Title :- Multimodal LLM Framework for Cyber Threat Detection on Mobile Devices

This project presents a multimodal cyber threat detection system that integrates machine-learning models across four different cybersecurity domains—network intrusion, phishing URLs, malware images, and audio spoofing—and combines them with an LLM-based explanation layer to generate human-readable security reports.

The goal is to build an interpretable, mobile-friendly threat detection pipeline capable of analyzing multiple attack vectors and providing users with clear, actionable insights.

Project Overview:- 
1.Modern cybersecurity attacks are increasingly complex and often span multiple data types (network flows, URLs, images, audio). Traditional systems rely on a single modality and fail to detect multi-stage or evolving threats.
2.This project introduces a hybrid ML + LLM architecture where:
3.Four independent ML models classify threats in their respective domains.
4.A lightweight LLM (TinyLlama-1.1B-Chat) converts model predictions, risk scores, and confidence levels into human-readable reports.
5.The entire pipeline is designed with low computational overhead, making it suitable for mobile or lightweight deployment contexts.
6.Each modality has its own preprocessing pipeline and threat classifier.

System Architecture:- The framework has four main layers:

1.Data Preprocessing

2.Embedding Generation (Feature Extraction)

3.Threat Detection Layer (ML Models)

4.Risk Reporting Layer (LLM)

Datasets Used:- 
1.CICIDS2017 — Network Intrusion Detection= ~2.3M network flow records, 
15 classes (benign + 14 attack types)
Preprocessing: merging 8 CSV files, cleaning features, label encoding
Model: Feed-forward neural network with learned embeddings

2.Phishing & Malicious URL Dataset- Combined two phishing datasets
Purely numerical URL features (no raw text)
Model: Feed-forward neural network for binary phishing detection

3.Malimg Dataset — Malware Image Classification= 9,342 grayscale malware images across 25 families
Image preprocessing: resize to 64×64, normalize
Model: Lightweight CNN with Global Average Pooling
Output: Malware family classification

4.ASVspoof 2019 — Audio Spoofing Detection= 20k+ training samples
Extracted MFCC features (mean + STD)
Model: Feed-forward neural network for binary classification (bonafide vs spoof)

Threat Detection Pipeline
For each dataset, the ML model outputs: Predicted Label, Confidence Score, Base Risk Value
These predictions are standardized and passed to the LLM layer.

LLM-Based Explanation Layer:- 
A lightweight LLM — TinyLlama-1.1B-Chat-v1.0 — is used to generate:
1.Human-readable security reports
2.Practical explanations of the threat
3.Severity rating (1–10)

This adds interpretability and makes the results accessible to non-experts.

Example Output (High-Level)
Module: Network Intrusion
Predicted Label: DDoS
Confidence: 0.98
Risk Score: 9.0 (Critical)

Explanation:
This flow pattern shows extremely high traffic bursts with repetitive packet sequences,
indicating a Distributed Denial of Service attack. Immediate mitigation is recommended.

Key Contributions
1.Unified multimodal threat detection across 4 data types
2.Lightweight LLM used for interpretability
3.Mobile-friendly architecture
4.High accuracy models (CNN, FFNN, MFCC-based classifiers)
5.Unified risk scoring system
6.Complete ML + LLM pipeline for cybersecurity

Technologies Used:- 
1.Python
2.TensorFlow
3.PyTorch
4.Scikit-learn
5.Librosa (Audio Feature Extraction)
6.TinyLlama-1.1B-Chat
7.NumPy / Pandas
8.Matplotlib / Seaborn


How to Run
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

Conclusion

This project successfully integrates multimodal ML models with an LLM explanation layer, providing a comprehensive and interpretable cybersecurity solution. The architecture is lightweight, extensible, and suitable for real-world applications, especially mobile threat detection.

Future Work
1.Add real-time streaming support
2.Mobile deployment (TensorFlow Lite / ONNX)
3.Add more modalities (logs, emails, images)
4.Expand LLM to generate actionable remediation steps
