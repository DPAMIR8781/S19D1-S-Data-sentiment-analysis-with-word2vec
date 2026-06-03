🎬 Sentiment Analysis with Word2Vec and Transfer Learning
📌 Project Overview

This project focuses on sentiment analysis of movie reviews using Natural Language Processing (NLP) techniques.

The objective is to classify IMDB movie reviews as positive or negative by utilizing:

Word2Vec Embeddings
Pretrained GloVe Embeddings (Transfer Learning)
LSTM Neural Networks
TensorFlow / Keras
Gensim

The project compares the performance of a custom-trained Word2Vec model against a pretrained embedding model to demonstrate the benefits of transfer learning in NLP applications.

🎯 Objectives
Load and preprocess IMDB review data
Train a custom Word2Vec embedding model
Convert text into numerical vector representations
Build an LSTM-based sentiment classifier
Evaluate model performance
Apply transfer learning using pretrained GloVe embeddings
Compare both approaches
📊 Dataset

Dataset: IMDB Reviews Dataset

Source: TensorFlow Datasets (TFDS)
Binary classification problem
Positive Reviews → 1
Negative Reviews → 0

For faster experimentation, only 10% of the dataset was used during training.

🛠 Technologies Used
Python
NumPy
TensorFlow
Keras
TensorFlow Datasets
Gensim
Word2Vec
GloVe Embeddings
📚 Project Workflow
1. Data Loading

The IMDB dataset was loaded using TensorFlow Datasets:

tfds.load("imdb_reviews")

Reviews were tokenized into word sequences.

2. Custom Word2Vec Training

A Word2Vec model was trained on the training dataset.

Configuration:

Word2Vec(
    sentences=X_train,
    vector_size=100,
    window=5,
    min_count=1,
    workers=4,
    sg=1
)

Parameters:

Parameter	Value
vector_size	100
window	5
min_count	1
architecture	Skip-Gram
3. Sentence Embedding

Each review was transformed into a sequence of embedding vectors.

Example:

["this", "movie", "was", "great"]

↓

[
 [0.12, 0.53, ...],
 [0.45, 0.77, ...],
 ...
]
4. Sequence Padding

Since reviews have different lengths, all sequences were padded to a fixed length.

pad_sequences(
    maxlen=200,
    padding='post'
)

Final shape:

(samples, 200, embedding_dimension)
5. LSTM Model

Neural Network Architecture:

Masking
↓
LSTM (20 units)
↓
Dense (10 units, ReLU)
↓
Dense (1 unit, Sigmoid)

Model compilation:

optimizer="rmsprop"
loss="binary_crossentropy"
metrics=["accuracy"]
6. Early Stopping

To avoid overfitting:

EarlyStopping(
    monitor="val_loss",
    patience=3,
    restore_best_weights=True
)
📈 Results
Baseline Accuracy

Majority class prediction:

50.6%
Custom Word2Vec + LSTM

Test Accuracy:

69.92%
Transfer Learning (GloVe) + LSTM

Pretrained model:

glove-wiki-gigaword-50

Vocabulary Size:

400,000 words

Embedding Dimension:

50

Test Accuracy:

73.56%
🏆 Performance Comparison
Model	Accuracy
Baseline	50.60%
Word2Vec + LSTM	69.92%
GloVe + LSTM	73.56%

Improvement gained from transfer learning:

+3.64%
🔍 Key Learnings

This project demonstrates that:

Word embeddings significantly improve NLP model performance.
Transfer learning can provide better semantic representations than training embeddings from scratch on limited data.
Pretrained GloVe embeddings improve classification accuracy.
LSTM networks effectively capture sequential information in text data.
🚀 Future Improvements

Possible enhancements:

Bidirectional LSTM
GRU Architecture
Attention Mechanisms
Transformer Models (BERT)
Hyperparameter Optimization
Full IMDB Dataset Training
Advanced Text Cleaning
📂 Repository Structure
.
├── notebooks/
│   └── sentiment_analysis.ipynb
├── README.md
├── requirements.txt
└── images/
👤 Author

Doruk Pamir

Aspiring Data Analyst & Data Scientist

Python
SQL
Machine Learning
Deep Learning
NLP
Generative AI
Data Visualization

GitHub:
https://github.com/DPAMIR8781
