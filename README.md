# Custom Semantic Search Engine

A document search and summarization system built in Python that combines **Word2Vec embeddings**, **cosine similarity ranking**, and **BART-based AI summarization** to answer natural language queries over research documents.

---

## Demo Output

```
Query: What is the significance of the STS movement in the paper?
Summary: Sit to stand capacity is a key factor and marker in practical autonomy.
         Execution of sit to stand brings about physiological changes from a stable
         sitting position to a less stable standing position.
```

---

## How It Works

```
.docx file on Google Drive
        │
        ▼
  Extract full text
        │
        ▼
  Train Word2Vec embeddings     ← each word becomes a 100-number vector
        │
        ▼
  Build document vectors        ← average word vectors per document
        │
        ▼
  Cosine similarity search      ← rank documents by query relevance
        │
        ▼
  BART summarization            ← generate concise AI summary of top result
        │
        ▼
  Return query → summary pairs
```

---

## Features

- Load `.docx` research papers directly from Google Drive
- Semantic search using **Word2Vec** (gensim) and **cosine similarity** (scikit-learn)
- AI-powered summarization using **facebook/bart-large-cnn** via Hugging Face Transformers
- Handles multiple queries in a single run
- Input validation and error handling for edge cases (empty text, short text, oversized input)
- Fully interactive teaching notebook with embedded explanations, diagrams, mini quizzes, and coding challenges

---

## Tech Stack

| Component | Library / Model |
|-----------|----------------|
| Document parsing | `python-docx` |
| Text preprocessing | `gensim.utils.simple_preprocess` |
| Word embeddings | `gensim.models.Word2Vec` |
| Similarity ranking | `sklearn.metrics.pairwise.cosine_similarity` |
| Summarization | `facebook/bart-large-cnn` via `transformers.pipeline` |
| Numerical ops | `numpy` |
| Runtime | Google Colab |

---

## Project Structure

```
custom-search-engine/
├── Custom_Search_Engine.ipynb   # Main notebook (interactive lesson + full pipeline)
└── README.md
```

---

## Getting Started

### Prerequisites

- Google Account with Google Drive access
- Google Colab (free tier works fine)
- A `.docx` document stored in your Google Drive

### Steps

1. **Open the notebook in Google Colab**
   - Upload `Custom_Search_Engine.ipynb` to your Google Drive
   - Open it with Google Colab

2. **Place your document in Google Drive**
   ```
   My Drive / STS paper.docx
   ```
   Update the file path in `mount_and_load()` if your file has a different name or location:
   ```python
   file_path = "/content/drive/MyDrive/YOUR_FILE_NAME.docx"
   ```

3. **Run all cells top to bottom** (`Runtime → Run all`)

4. **View results** — each query prints its AI-generated summary

---

## Notebook Modules

The notebook is structured as a self-contained interactive lesson:

| Module | Topic |
|--------|-------|
| Module 1 | Imports — the toolbox |
| Module 2 | Loading documents from Google Drive |
| Module 3 | Word2Vec embeddings — turning words into numbers |
| Module 4 | Cosine similarity search |
| Module 5 | BART AI summarization |
| Module 6 | Final end-to-end workflow |
| Module 7 | Try It Yourself challenges |

Each module includes:
- Concept explanations with analogies
- Annotated code walkthroughs
- ASCII diagrams
- Mini quizzes with hidden answers
- Interactive demo cells

---

## Known Limitations

| Issue | Root Cause | Suggested Fix |
|-------|-----------|---------------|
| All queries return the same summary | Corpus has only 1 document — nothing to rank | Split document into paragraphs as separate corpus entries |
| Summarizer always returns the intro | Truncation limit of 1024 chars ≈ only ~256 tokens | Increase to `text[:4000]` or use a tokenizer |
| Word2Vec trained on single doc | Small vocabulary, weak semantic signal | Use a pre-trained model like `sentence-transformers` |

---

## Challenges (from the notebook)

| # | Challenge | Difficulty |
|---|-----------|-----------|
| 1 | Add 3 more custom queries | Easy |
| 2 | Split document into paragraphs for real search | Medium |
| 3 | Fix the character/token truncation bug | Medium |
| 4 | Print similarity scores alongside summaries | Easy |

---

## Author

**Khadija Zaman**
- GitHub: [@KhadijaZaman](https://github.com/KhadijaZaman)

---

## License

This project is open source and available under the [MIT License](LICENSE).
