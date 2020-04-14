# Toxic Text Classification Report
Link to Report: https://docs.google.com/document/d/1fKOzErfzN-hjsj542BrOv3S-YGs-LaEKKYYcSyLIOTc/edit?usp=sharing

Link to Google Colab Notebook (view-only):
https://colab.research.google.com/drive/1GukAgm5Hgtz-qiZhYtrJQRSOluJ2croE

# About the Project

Since the objective is simply to identify the percentage of how toxic a piece of text is, the the only feature column that is needed is "toxic". The pieces of texts that are classified as True for any of the other forms of toxicity are also classified as True under Toxic. This means that if a piece of text is classified as "severe_toxic" or "threat", it is also classified as True for "Toxic".

## Model Architectures

### Simple LSTM


### Bi-LSTM with MaxPooling



## Next Steps
- https://arxiv.org/pdf/1611.06639.pdf#page=10&zoom=100,89,636
- Training on Upsampling
- Denser networks
- Grid Search Parameter tuning across all models
