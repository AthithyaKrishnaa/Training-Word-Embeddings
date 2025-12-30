# Skip-gram Word Embedding from Scratch

This project implements a **Word2Vec (Skip-gram)** model from scratch using TensorFlow/Keras. It demonstrates how a neural network can learn semantic relationships between words by predicting context from a target word, transforming raw text into meaningful 10-dimensional vectors.

## 📂 Project Structure

* `train_word_embedding.ipynb`: The main Jupyter notebook containing the preprocessing, model architecture, training loop, and visualization.
* `dataset.txt`: A sample text corpus used for training.

## 📝 Dataset Breakdown

The model uses a curated `dataset.txt` focusing on royal and familial relationships. Examples include:

* *"The future king is the prince"*
* *"Daughter is the princess"*
* *"Only a woman can be a queen"*

**Why this dataset?** It contains clear semantic analogies (King is to Man as Queen is to Woman) which makes it easy to verify if the word embeddings have actually learned "meaning."

## ⚙️ How it Works

1. **Preprocessing**: The text is lowercased, and punctuation is removed. A unique vocabulary is created, assigning every word a specific ID (e.g., `king -> 5`).
2. **Skip-gram Generation**: A sliding window moves across the text. For a `window_size=2`, it creates pairs of **(Target Word, Context Word)**.
* *Input*: "king" → *Target*: "prince", "future".


3. **The Neural Network**:
* **Embedding Layer**: Maps the word ID to a 10-dimensional vector.
* **Dense Layer**: Uses a Softmax activation to predict the probability of a context word appearing.


4. **Training**: The model runs for **500 epochs** using the Adam optimizer, minimizing the difference between its predictions and the actual context words.

## 📊 Visualizing Results

Since humans cannot see in 10 dimensions, the notebook uses **PCA (Principal Component Analysis)** to squash those 10D vectors into a **2D scatter plot**.

### How to read the result image:

* **Clustering**: Words that appear in similar contexts will be physically closer together on the graph.
* **Semantic Logic**: You should see "King" and "Prince" clustered near each other, while "Queen" and "Princess" form a separate cluster nearby.
* **Relationship Vectors**: In a successful run, the distance/direction between "Man" and "Woman" should be similar to the distance between "King" and "Queen."

## 🚀 Installation & Usage

1. **Clone the repo**:
```bash
git clone https://github.com/your-username/word2vec-from-scratch.git

```


2. **Install dependencies**:
```bash
pip install tensorflow numpy matplotlib scikit-learn

```


3. **Run the notebook**: Open `train_word_embedding.ipynb` in Jupyter or Google Colab and run all cells.
