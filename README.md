# DL_ASSIGNMENT2_148
#QUESTION1
# Dakshina Transliteration with Seq2Seq (Keras)

This project demonstrates a character-level sequence-to-sequence (seq2seq) transliteration model using LSTM networks to convert **Latin-script ** text into **Devanagari** script, trained on the [Dakshina dataset](https://github.com/google-research-datasets/dakshina).


## Features

- Downloads and extracts the Dakshina dataset
- Prepares and one-hot encodes training data
- Trains a seq2seq LSTM model to perform transliteration
- Saves and reloads the model for inference
- Provides an interactive CLI to test transliteration

---

## Dataset

We use the `hi.translit.sampled.train.tsv` file from the Dakshina dataset, which contains tab-separated lines with the format:

Only the first two columns are used.

## Model Architecture

- **Encoder**: LSTM processes input Latin characters
- **Decoder**: LSTM generates Devanagari characters, character by character


## Setup Instructions

1. **Clone the repository**:
   bash
   git clone https://github.com/your-username/dakshina-transliteration.git
   cd dakshina-transliteration
2.**After training, the script launches an input prompt**:
Latin word: namaste
Devanagari transliteration: नमस्ते
Type 'exit' to quit the translator.
3.**Training Details**
Epochs: 200

Batch size: 64

Latent dimensions: 256

Validation split: 20%

Uses RMSprop optimizer and categorical crossentropy

