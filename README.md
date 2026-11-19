# LogFiT: End-to-End Parallel Log Anomaly Detection System
### Parallel Computing Project — OpenMP Version

Based on: **LogFiT: Log Anomaly Detection Using Fine-Tuned Language Models** *(IEEE Transactions on Network and Service Management, Vol. 21, No. 2, April 2024)*

---

### Pipeline Overview
1. **Real Data Pipeline:** Loads real HDFS logs from LogHub / system log streams and groups them into log paragraphs.
2. **Real Model Inference:** Runs Hugging Face `roberta-base` to generate prediction logits over its 50,265-token vocabulary.
3. **Parallel Acceleration:** Uses **OpenMP** to parallelize the top-k rank verification across CPU threads.
4. **Full Anomaly Classification:** Evaluates per-paragraph anomaly predictions using Precision, Recall, F1 Score, and Specificity.


# LogFiT: End-to-End Parallel Log Anomaly Detection System
### Parallel Computing Project - Cuda Version
Based on: **LogFiT: Log Anomaly Detection Using Fine-Tuned Language Models** *(IEEE Transactions on Network and Service Management, Vol. 21, No. 2, April 2024)*

---
### Pipeline Overview:
1. **Real Data Pipeline:** Loads real HDFS logs from LogHub / system log streams and groups them into log paragraphs.
2. **Real Model Inference:** Runs Hugging Face `roberta-base` to generate real prediction logits over its **50,265**-word vocabulary.
3. **Parallel Acceleration (Your Novel Contribution):** Replaces the sequential top-$k$ verification bottleneck with a **2-Level Hierarchical GPU Reduction Kernel** (1 CUDA Block per blank, 256 coalesced threads per block, register warp-shuffles).
4. **Full Anomaly Classification:** Evaluates per-paragraph accuracy, computing **Precision, Recall, F1 Score, and Specificity** as in Table III of the paper.