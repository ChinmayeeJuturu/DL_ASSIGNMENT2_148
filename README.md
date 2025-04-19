# DL_ASSIGNMENT2_148
#QUESTION1
# Dakshina Transliteration with Seq2Seq (Keras)

This project demonstrates a character-level sequence-to-sequence (seq2seq) transliteration model using LSTM networks to convert **Latin-script ** text into **Devanagari** script, trained on the [Dakshina dataset](https://github.com/google-research-datasets/dakshina)


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
a)To compute the total number of computations done by the network in the described LSTM-based seq2seq architecture
Embedding size = m

Hidden size = k (same for encoder and decoder)

Sequence length = T (same for input and output)

Vocabulary size = V (same for source and target)

1-layer LSTM for both encoder and decoder

Using one-hot encoding , so effectively input size = V

Total computations = per timestep LSTM cost × T × number of sequences
T = max_encoder_seq_length = 15

V = num_encoder_tokens = num_decoder_tokens =80
k = latent_dim = 256
**Total Computations Formula**
Total=T*(9Vk+8k2+V)=15*(9*80*256+8*256*256+80)=10,630,320
b)the total number of parameters in my network:
latent_dim = 256 (hidden size k)

num_encoder_tokens = 80 

num_decoder_tokens = 80 
LSTM params=4×[(input_dim×hidden_dim)+(hidden_dim×hidden_dim)+hidden_dim]
1. Encoder LSTM (Input dim = num_encoder_tokens = 80)
   =4×[(80×256)+(256×256)+256]=345088parameters
2.Decoder LSTM (Input dim = num_decoder_tokens = 80)
   =4×[(80×256)+(256×256)+256]=345088parameters
3.Dense Output Layer (256 → 80 softmax)
   =256×80+80= 20480+80=20560 parameters
4.Total Parameters:
Total=345088+345088+20560=
710736 trainable parameters
c)The accuracy on the test set:
Test Accuracy: 88.45%
Sample predictions:
Latin: priyanka → Predicted: प्रियांका
Latin: bharat → Predicted: भारत 
Latin: kumar → Predicted: कुमार 
Latin: delhi → Predicted: दिल्ली 
Latin: ashok → Predicted: अशोक
**Comparision**
compare to simple RNN LSTM gave good accuracy

#QUESTION2:
# GPT-2 Fine-Tuning for Song Lyric Generation

This project fine-tunes OpenAI's GPT-2 language model on a custom dataset of song lyrics to generate original lyrics based on any input prompt. It uses the Hugging Face Transformers and Datasets libraries for model training and inference.

## Overview

- Fine-tunes GPT-2 (`gpt2`) on a custom `lyrics.txt` file.
- Generates lyrics from user input using Hugging Face pipelines.
- Runs seamlessly on Google Colab or locally with Python.

## Requirements

- Python 3.7+
- torch
- transformers
- datasets
- google.colab (if using Colab)

Install dependencies with:

!pip install transformers datasets

Model Settings
Model: gpt2

Max token length: 128

Batch size: 4

Epochs: 3

Loss: Causal Language Modeling (no masked tokens)
How It Works
The notebook loads and tokenizes your .txt file.

GPT-2 is fine-tuned using Hugging Face's Trainer API.

The model is saved and used with the pipeline API for lyric generation.
Sample Output
Prompt: dancing in the moonlight
output:
dancing in the moonlight, feeling like I'm free
stars above are singing just for me...




