# Toxic Text Classification Report
{Objective} percentages of toxicity

## Data, Preprocessing, Constants, Resources
Google Colab GPU usage

- Data shape
- Data columns ---> Data sliced
- Upsampling vs Downsampling
- Keras tokenizer
- Texts_to_sequences
- Padding
- Glove with 300D

max_features=
maxlen=
embed_size=


{link to Google Colab (view only)}


## Model Architecture


### Simple LSTM (Baseline)

### LSTM with MaxPooling

### LSTM with Attention
Andrew NG ATNN: https://www.youtube.com/watch?v=SysgYptB198
ATTN: https://www.youtube.com/watch?v=oaV_Fv5DwUM
debugging: https://github.com/keras-team/keras/issues/4962


### C-LSTM

Paper on C-LSTM: https://arxiv.org/abs/1511.08630


### CNN
- http://www.davidsbatista.net/blog/2018/03/31/SentenceClassificationConvNets/
- Globalmaxpooling vs maxpooling layer https://stats.stackexchange.com/questions/257321/what-is-global-max-pooling-layer-and-what-is-its-advantage-over-maxpooling-layer



## Parameter Tuning


## Next Steps
- https://arxiv.org/pdf/1611.06639.pdf#page=10&zoom=100,89,636
- HAN
- toxicity challenge best model Medium search
- Training on Upsampling
- Denser networks
- Grid Search Parameter tuning across all models
