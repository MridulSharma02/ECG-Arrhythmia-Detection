# Model Outputs

This directory contains all the outputs from the ECG Arrhythmia Detection models.

## 📁 Directory Structure

### `evaluation_plots/`
Model evaluation visualizations comparing Baseline CNN and CNN-BiLSTM architectures:
- Confusion matrices
- ROC curves
- Precision-Recall curves
- Probability distributions
- Performance metrics (CSV files)
- Metrics bar charts

### `xai_plots/`
Explainable AI (XAI) visualizations showing what the models learned:
- **GradCAM** - Class activation maps highlighting important regions
- **Attention Maps** - BiLSTM attention weights across time steps
- **Saliency Maps** - Input gradient-based feature importance
- **Integrated Gradients** - Attribution scores for model predictions
- **Per-lead Irregularities** - Lead-wise contribution analysis
- **Case Studies** - Three representative cases (MI, CD, STTC)
- Text reports for each case study

### `final_plots/`
Summary visualizations:
- Model comparison across all metrics
- Training curves for both architectures

### `reports/`
Aggregated performance metrics:
- All models metrics (CSV)
- Performance report card (visual summary)

## 🔍 Quick Links

- [Model Comparison](./final_plots/model_comparison.png)
- [Baseline CNN Training](./final_plots/baseline_cnn_training_curves.png)
- [CNN-BiLSTM Training](./final_plots/cnn_bilstm_training_curves.png)
- [All Models Metrics](./reports/all_models_metrics.csv)

## 📊 Sample XAI Cases

- **Case 0:** Myocardial Infarction (MI) - [All visualizations](./xai_plots/case0_all_classes_panel.png)
- **Case 1:** Conduction Disturbance (CD) - [All visualizations](./xai_plots/case1_all_classes_panel.png)
- **Case 2:** ST/T Change (STTC) - [All visualizations](./xai_plots/case2_all_classes_panel.png)
