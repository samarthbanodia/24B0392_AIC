# BERT Text Classification - Q1

In this project, we fine-tuned a pre-trained BERT model on a dataset (`train.csv`) containing text data and 43 categories.

## Local Setup and Requirements: 

- pip install tensorflow transformers datasets pandas spacy nltk scikit-learn
- Ensure youu have cuda installed as training requires quite alot hardware resources
- https://www.tensorflow.org/install/pip - for cuda install
- just run the the python notebook jupyter notebook Q1.ipynb or python3 Q1.py
- ensure train.csv is in the same folder as file


## About BERT

BERT (Bidirectional Encoder Representations from Transformers) is a large language model developed by Google. It’s pre-trained on large datasets like Wikipedia and BookCorpus. BERT uses a multi-layer bidirectional transformer encoder to represent the input text in high-dimensional space, taking into account the entire context of words in sentences.

- **BERT Base**: 12 layers / 110M parameters / 768 token length  
- **BERT Large**: 24 layers / 340M parameters (computationally more intensive)

In this project, I used the 'bert-base-uncased' model, which is not case-sensitive.

### BERT Architecture

- Stacked Transformer encoders
- Each encoder includes:
  - A self-attention layer
  - A feed-forward layer

### Input Requirements

BERT expects a sequence of tokens with two special tokens:
- **[CLS]**: Classification token at the start
- **[SEP]**: Separator token, used mainly for next sentence prediction or question answering tasks

Each token is embedded into a 768-dimensional vector (for BERT-base). These embeddings are used for various NLP tasks such as:
- Text classification
- Next Sentence Prediction (NSP)
- Question answering

**Model Outputs**:
- last_hidden_state
- pooler_output

**Tokenization**:
- Uses the **WordPiece** algorithm developed by Google Research

---

## Workflow

I used TFAutoModel and AutoTokenizer from Hugging Face’s transformers library to load the BERT model and tokenizer.

### Preprocessing Steps:
1. Convert text to lowercase
2. Remove special characters and non-alphabetic characters
3. Lemmatize text using SpaCy
4. Remove stopwords using NLTK

### Tokenizing and Building Model:
- Convert category labels to numeric encodings
- Split data into train, validation, and test sets
- Tokenize the text to get encodings
- Create a BERT classification model using `keras.Model`, followed by a dense layer for classification

### Train and test the model 
 - Get performance metrics

---

## Experiments & Resources : Taking 5 epocs , batch size of 4 and learning rate = 1e-5 i got ,
- Got an accuracy of 88.9%
- Precision of 89.3%
- Accuracy of 88.9%
- Recall of 88.8&


### Resources Used:(mainly medium articles and yt and some of keras website)
- [YouTube Guide](https://www.youtube.com/watch?v=IzbjGaYQB-U&t=558s)
- [Fine-tuning BERT (Medium)](https://medium.com/@heyamit10/fine-tuning-bert-for-classification-a-practical-guide-b8c1c56f252c)
- [Understanding BERT (Medium)](https://medium.com/@shaikhrayyan123/a-comprehensive-guide-to-understanding-bert-from-beginners-to-advanced-2379699e2b51)
- [Text Classification with BERT (Medium)](https://medium.com/@khang.pham.exxact/text-classification-with-bert-7afaacc5e49b)

### Errors Faced:
- Initially tried manual data handling but faced errors due to numpy 2.0 incompatibility with model.fit. Switched to using tf.data.Dataset pipeline for smoother integration.
- Faced confusion in generating a classification report and evaluating predictions. Resolved this by referring to [Keras Metrix Doc](https://keras.io/api/metrics/classification_metrics/#precision-class).
- Couldnt get GPU utilisation for due to version mismatch in drivers or something - isntalled cuda from starting.
[image]

---

