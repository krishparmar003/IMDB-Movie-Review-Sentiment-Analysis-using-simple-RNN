# 🎬 IMDB Movie Review Sentiment Analysis using Simple RNN

A deep learning project that classifies IMDB movie reviews as **Positive** or **Negative** using a **Simple RNN** built with TensorFlow/Keras, served through an interactive **Streamlit** web app.

🔗 **Live Demo:** [[YOUR_STREAMLIT_APP_LINK](https://movie-review-sentiment-analysis-dl-rnn.streamlit.app/)]([YOUR_STREAMLIT_APP_LINK](https://movie-review-sentiment-analysis-dl-rnn.streamlit.app/))

---

## 📌 Overview

This project walks through the complete NLP pipeline for sentiment analysis, from understanding word embeddings to deploying a trained model:

1. **Embeddings** – converting word indices into dense vectors (`embedding.ipynb`)
2. **Model training** – training a Simple RNN on the IMDB dataset (`simplernn.ipynb`)
3. **Prediction** – loading the saved model and predicting on raw text (`prediction.ipynb`)
4. **Deployment** – a Streamlit app where anyone can type a review and get a sentiment (`main.py`)

---

## 🧠 Model Architecture

| Layer | Output Shape | Params |
|-------|--------------|--------|
| Embedding (vocab 10,000 → 128 dims) | (None, 500, 128) | 1,280,000 |
| SimpleRNN (128 units, ReLU) | (None, 128) | 32,896 |
| Dense (1 unit, Sigmoid) | (None, 1) | 129 |

**Total params:** 1,313,025 (~5.01 MB)

- Reviews are tokenized using the IMDB word index and padded/truncated to **500 tokens**.
- Output is a score between 0 and 1. A score **> 0.5** means **Positive**, otherwise **Negative**.

---

## 📂 Project Structure

```
IMDB-Movie-Review-Sentiment-Analysis-using-simple-RNN/
│
├── main.py                 # Streamlit web app
├── simple_rnn_imdb.h5      # Trained Simple RNN model
├── embedding.ipynb         # Word embedding walkthrough
├── simplernn.ipynb         # Model building and training
├── prediction.ipynb        # Loading the model and making predictions
├── requirements.txt        # Python dependencies
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

- **Python 3.10**
- **TensorFlow 2.15.0 / Keras**: model building and inference
- **NumPy, Pandas, scikit-learn, Matplotlib**: data handling and visualization
- **TensorBoard**: training visualization
- **Streamlit**: web app and deployment

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/krishparmar003/IMDB-Movie-Review-Sentiment-Analysis-using-simple-RNN.git
cd IMDB-Movie-Review-Sentiment-Analysis-using-simple-RNN
```

### 2. Create a virtual environment

> ⚠️ Python **3.10** is recommended, since `tensorflow==2.15.0` supports Python 3.9 to 3.11.

**Windows**
```bash
py -3.10 -m venv myenv
```

**macOS / Linux**
```bash
python3.10 -m venv myenv
```

### 3. Activate the virtual environment

**Windows (Command Prompt)**
```bash
myenv\Scripts\activate.bat
```

**Windows (PowerShell)**
```powershell
myenv\Scripts\activate
```

**macOS / Linux**
```bash
source myenv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Run the Streamlit app

```bash
streamlit run main.py
```

The app will open in your browser at `http://localhost:8501`.

---

## 💡 How to Use

1. Open the app (live link above, or locally).
2. Type or paste a movie review into the text box.
3. Click **Classify**.
4. The app shows the predicted **sentiment** along with the **prediction score**.

**Example**

```
Review: This movie was fantastic! The acting was great and the plot was thrilling.
Sentiment: Positive
Prediction Score: 0.838
```

---

## 📓 Notebooks

If you want to explore the learning process, run the notebooks with Jupyter:

```bash
jupyter notebook
```

| Notebook | What it covers |
|----------|----------------|
| `embedding.ipynb` | How word embeddings turn integer-encoded words into dense vectors |
| `simplernn.ipynb` | Loading IMDB data, building and training the Simple RNN, saving the `.h5` model |
| `prediction.ipynb` | Loading the saved model, preprocessing raw text and predicting sentiment |

---

## ⚠️ Limitations

- A Simple RNN struggles with long-term dependencies (vanishing gradients). **LSTM or GRU** would likely perform better.
- Preprocessing is basic: text is lowercased and split on spaces, so punctuation attached to words (e.g. `great!`) won't match the vocabulary.
- Words not in the IMDB vocabulary are not handled specially.

---

⭐ If you found this project helpful, consider giving it a star!
