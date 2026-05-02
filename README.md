# 🚀 ECG Classification using CNN–BiLSTM with Explainable AI (XAI)

## 📌 Overview
This project presents a deep learning framework for **multi-label ECG classification** using a hybrid CNN–BiLSTM architecture, enhanced with Explainable AI (XAI).

Unlike traditional black-box models, this system not only predicts cardiac abnormalities but also provides **clinically meaningful interpretations** by identifying important ECG signal regions such as **P-waves, QRS complexes, and ST-T segments**.

The model is trained and evaluated on the **PTB-XL dataset**, a large-scale, clinically annotated ECG dataset.

---

## 🎯 Objectives
- Develop an accurate model for multi-label ECG classification  
- Capture both **spatial (morphological)** and **temporal** features  
- Improve model interpretability using XAI  
- Align model explanations with clinical ECG knowledge  

---

## 🧪 Contributions
- Hybrid **CNN–BiLSTM architecture** for ECG classification  
- Integration of **Grad-CAM, Integrated Gradients, and Saliency maps**  
- Clinical interpretation of model attention regions  
- End-to-end pipeline (preprocessing → training → evaluation → XAI → deployment)  

---

## 🧠 Key Features
- 📊 ECG signal preprocessing and normalization  
- 🏷️ Multi-label classification (NORM, MI, STTC, CD, HYP)  
- 🧩 CNN for feature extraction  
- 🔁 BiLSTM for temporal sequence learning  
- 📈 Performance evaluation using standard metrics  
- 🔍 Explainable AI (Grad-CAM, Integrated Gradients, Saliency)  
- 📉 Visualization of ECG signals and model outputs  
- 🌐 Streamlit web application for interactive inference

---

## 🏗️ Model Architecture
**CNN → BiLSTM → Fully Connected + Sigmoid Layer**

- **CNN (Convolutional Neural Network):** Extracts morphological features from ECG signals
- **BiLSTM (Bidirectional LSTM):** Captures temporal dependencies in ECG sequences
- **Sigmoid Layer:** Enables multi-label classification  

---

## 📂 Project Structure
```
├── outputs/                    # Outputs
│   ├── evaluation_plots/
│   ├── xai_plots/
│   ├── final_plots/
│   ├── reports/
│   └── README.md
├── app.py                      # Streamlit web app
├── inference.py                # Model inference script
├── run_all.py                  # Run full pipeline
├── part1_load_preprocess.py    # Data loading and preprocessing
├── part2_label_mapping.py      # Label mapping and encoding
├── part3_data_split.py         # Train/validation/test split
├── part4_dataset.py            # PyTorch dataset implementation
├── part5_baseline_cnn.py       # Baseline CNN model
├── part6_cnn_bilstm.py         # CNN-BiLSTM hybrid model
├── part7_train.py              # Training loop
├── part8_evaluate.py           # Model evaluation
├── part9_xai.py                # Explainable AI implementation
├── part10_save_and_plot.py     # Results saving and visualization
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
```

---

## ⚙️ Installation

```bash
git clone https://github.com/MridulSharma02/ECG-Arrhythmia-Detection
cd ECG-Arrhythmia-Detection
pip install -r requirements.txt
```

---

## 📁 Dataset

This project uses the **PTB-XL dataset**, a large publicly available ECG dataset provided by PhysioNet.

### 🔗 Download Dataset
https://physionet.org/content/ptb-xl/1.0.3/

### 📦 Dataset Details
- ~21,000 clinical 12-lead ECG records
- 71 diagnostic labels
- Expert annotations by cardiologists
- Multiple diagnostic classes

### ⚠️ Important Note
The dataset is **not included in this repository** due to size limitations.

### 📂 Setup Instructions
1. Download the dataset from the link above
2. Extract the files
3. Place them inside a folder named `data/` in the project root

*(Optional)* You may include a small subset of ECG samples in `sample_ecgs/` for quick testing.

---

## ▶️ Usage

### 🔹 Run Complete Pipeline
```bash
python run_all.py
```

### 🔹 Run Inference
```bash
python inference.py
```

### 🔹 Launch Web App
```bash
streamlit run app.py
```

---

## 📊 Results

### 🔹 Overall Performance
- **Macro F1-score:** 0.7194  
- **Macro AUROC:** 0.9071  
- **Macro Average Precision:** 0.7756  

👉 CNN–BiLSTM slightly outperforms baseline CNN, showing the importance of temporal modeling.

---

### 🔹 Per-Class Performance

| Class | F1 Score |
|-------|----------|
| NORM  | 0.8529   |
| MI    | 0.7524   |
| STTC  | 0.7582   |
| CD    | 0.7568   |
| HYP   | 0.4765   |

- ✅ Best: NORM  
- 📈 Improved: MI, CD  
- ⚠️ Challenging: HYP (class imbalance)  

---

## 🔍 Key Findings
- Temporal modeling improves classification performance  
- Model achieves high discriminative ability (AUROC > 0.90)  
- Slight overfitting observed after later epochs  
- Performance gap exists vs benchmark models  

---

## 🧠 XAI Insights (Core Contribution)
The model focuses on clinically relevant ECG regions:

- **QRS Complex → Myocardial Infarction (MI)**  
- **RR Intervals → Conduction Disorders (CD)**  
- **ST-T Segments → STTC**  

👉 These results **suggest** that the model learns clinically meaningful patterns.

### XAI Techniques Used
- **Grad-CAM:** Visualizes class-discriminative regions
- **Integrated Gradients:** Attributes predictions to input features
- **Saliency Maps:** Highlights important signal regions

---

## 📊 Detailed Evaluation Results
All model outputs, evaluation metrics, and XAI visualizations are available in the [`outputs/`](./outputs/) directory.

### 📁 What's Included:
- **[Model Comparison](./outputs/final_plots/model_comparison.png)** - Performance comparison between models
- **[Training Curves](./outputs/final_plots/)** - Training history and convergence
- **[Evaluation Plots](./outputs/evaluation_plots/)** - Confusion matrices, ROC curves, PR curves
- **[XAI Visualizations](./outputs/xai_plots/)** - GradCAM, attention maps, saliency maps
- **[Performance Reports](./outputs/reports/)** - Detailed metrics and analysis

For complete documentation, see [outputs/README.md](./outputs/README.md) 

### 📁 Includes:
- Confusion matrices  
- ROC curves  
- Precision-Recall curves  
- XAI visualizations  
- Training curves
- Final plots and reports

---

## 📈 Evaluation Metrics
- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**
- **AUROC (Area Under ROC Curve)**
- **Average Precision**

---

## ⚠️ Limitations
- Class imbalance affects HYP performance
- No external clinical validation
- XAI methods provide approximations, not causal explanations

---

## 🔮 Future Work
- Improve performance on minority classes (HYP)
- Apply data balancing techniques (SMOTE, focal loss)
- Explore deeper architectures (Transformers, ResNets)
- Clinical validation with real-world data
- Multi-center validation studies

---

## 🛠️ Requirements
See `requirements.txt` for full dependencies.

Main dependencies include:
- PyTorch
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Streamlit
- Captum (for XAI)

---

## 👨‍💻 Authors
- **Mridul Sharma**
- **Harshit Mahajan**
- **Harsh Raj**
- **Khalid Raza Khan**
- **Tejas Verma**

---

## ⭐ Acknowledgments
- PhysioNet for providing the PTB-XL dataset
- Open-source community for tools and libraries
- Medical professionals for domain expertise

---

## 📧 Contact
For questions or collaborations, please reach out via GitHub issues or pull requests.

---

**⭐ If you find this project helpful, please consider starring the repository!**
