# Toxic Text Classification Report
{Objective} percentages of toxicity
{link to Kaggle Competition}
{link to Google Colab Notebook (view only)}

## Data and Preprocessing
Google Colab GPU usage

- Data shape
Toxic: 15294
Non-Toxic: 144277

Feature Columns:
- toxic
- severe_toxic
- obscene
- threat
- insult
- identity_hate

Since the objective is simply to identify the percentage of how toxic a piece of text is, the the only feature column that is needed is "toxic". The pieces of texts that are classified as True for any of the other forms of toxicity are also classified as True under Toxic. This means that if a piece of text is classified as "severe_toxic" or "threat", it is also classified as True for "Toxic".


- Upsampling vs Downsampling

Since there is extreme class imbalance in the given dataset (15294(Toxic): 144277(Non-Toxic)), the data is in need of resampling. For the purpose of saving times the following model architectures were trained on a downsampled majority class as opposed to an upsampled minority class.

After downsampling the number of non-toxic texts and splitting the data into training and test partitions:

Class distribution: 11393:11393

Preprocessing pipeline used:
- Keras tokenizer
- Texts_to_sequences
- Padding (max_length = 150)
- Embedded words with Glove(300 Dimension): http://nlp.stanford.edu/data/glove.6B.zip


## Constants

max_features = 100,000 (maximum number of words to keep, based on word frequency)
maxlen = 150 (Max length of padded sequence)
embed_size = 300 (Glove word embedding dimension)
epochs = 5

## Model Architectures

### Simple LSTM

- 'f1_score': 0.9064493267186392
- 'precision_score': 0.9116179615110478
- 'recall_score': 0.9013389711064129
- 'roc_auc_score': 0.9072976772286174


### Bi-LSTM with MaxPooling

Relevant Paper: https://arxiv.org/pdf/1611.06639v1.pdf
- Paper mentions getting prior results from applying GlobalMaxPooling1D or an Attention layer after obtaining the contextual state from the Bi-Directional layer
- Paper mentions potential drawback that "applying 1D pooling operation over
the time-step dimension independently may destroy the structure of the feature representation"

Performance:
- 'f1_score': 0.892062918097993
- 'precision_score': 0.9160787226141849
- 'recall_score': 0.8692741367159972
- 'roc_auc_score': 0.895112759158978


### Bi-LSTM with Attention
Model implementation based on:
- Andrew NG : https://www.youtube.com/watch?v=SysgYptB198
- Shuyi Wang: https://www.youtube.com/watch?v=oaV_Fv5DwUM

![Attention Mechanism](https://www.tensorflow.org/images/seq2seq/attention_mechanism.jpg)
- source: https://www.tensorflow.org/tutorials/text/nmt_with_attention

Layers used:
TimeDistributed: This wrapper applies a layer to every temporal slice of an input.
https://keras.io/layers/wrappers/
Permute: Permutes the dimensions of the input according to a given pattern.
Repeat Vector: Repeats the input vector n times.
https://keras.io/layers/core/

Performance:
- 'f1_score': 0.9038933707471062
- 'precision_score': 0.8997905027932961
- 'recall_score': 0.9080338266384778


### CNN

![CNN-Convolution](http://www.davidsbatista.net/assets/images/2018-03-31-sentence_convolution-example.png)
- Sentence convolution image source: http://www.davidsbatista.net/blog/2018/03/31/SentenceClassificationConvNets/

![CNN-Architecture](https://miro.medium.com/max/2800/0*0efgxnFIaLTZ2qkY)
- CNN for text classification architecture image source: http://www.davidsbatista.net/blog/2018/03/31/SentenceClassificationConvNets/


- Globalmaxpooling vs maxpooling layer https://stats.stackexchange.com/questions/257321/what-is-global-max-pooling-layer-and-what-is-its-advantage-over-maxpooling-layer

Performance:
- 'f1_score': 0.8960787761561455
- 'precision_score': 0.8943488943488943
- 'recall_score': 0.897815362931642
- 'roc_auc_score': 0.89626689797509


### C-LSTM

The intuition behind a C-LSTM is that "a CNN may be able to pick out invariant features for good and bad sentiment. This learned spatial features may then be learned as sequences by an LSTM layer"

https://medium.com/@mrunal68/text-sentiments-classification-with-cnn-and-lstm-f92652bc29fd

Paper on C-LSTM: https://arxiv.org/abs/1511.08630

LSTM w/ CNN
- 'f1_score': 0.881525360977416
- 'precision_score': 0.9286271450858035
- 'recall_score': 0.8389711064129669
- 'roc_auc_score': 0.88748135593471




## Parameter Tuning


## Next Steps
- https://arxiv.org/pdf/1611.06639.pdf#page=10&zoom=100,89,636
- Training on Upsampling
- Denser networks
- Grid Search Parameter tuning across all models
