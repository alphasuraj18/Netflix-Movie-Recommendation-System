# Netflix-Movie-Recommendation-System



A **content-based movie recommender system** built using the **TMDB 5000 Movie Dataset**. This project mimics how platforms like Netflix recommend similar movies to users based on movie content and metadata such as genres, cast, director, and plot overview.

---

## 📌 Project Highlights

- 🔍 **Content-Based Filtering**  
  Uses movie metadata to recommend similar movies.

- 🧠 **Natural Language Processing**  
  Tokenizes and vectorizes movie data using `CountVectorizer` from `scikit-learn`.

- 🤝 **Merged Datasets**  
  Combines movie details and credits for enriched recommendations.

- 📊 **Similarity Computation**  
  Calculates **cosine similarity** between movie vectors to find nearest neighbors.

---

## 🗂️ Dataset

Used the **TMDB 5000 Movies Dataset**:
- `tmdb_5000_movies.csv`
- `tmdb_5000_credits.csv`

Merged using the `title` column and filtered on relevant fields:
- `movie_id`
- `title`
- `overview`
- `genres`
- `keywords`
- `cast`
- `crew`

---

## 🔧 Features Used

| Feature    | Description |
|------------|-------------|
| `overview` | Movie plot summary |
| `genres`   | Movie genres (Action, Drama, etc.) |
| `keywords` | Tagline concepts |
| `cast`     | Top 3 actors |
| `crew`     | Director |

All these features are merged into a single `tags` column for vectorization.

---

## 🛠️ Tech Stack

- 🐍 Python
- 📦 Pandas, NumPy
- 📚 scikit-learn (CountVectorizer, cosine_similarity)
- 🔍 ast (for safe evaluation of JSON-like strings)
- 💻 Jupyter Notebook

---

## 🧠 How It Works

1. **Data Cleaning & Preprocessing**  
   JSON strings parsed into Python lists. Nulls handled. Text tokenized and merged into one field (`tags`).

2. **Feature Engineering**  
   `tags` column created by combining `overview`, `genres`, `keywords`, `cast`, and `crew`.

3. **Vectorization**  
   Bag-of-Words model applied using `CountVectorizer` (top 5000 words, stopwords removed).

4. **Similarity Matrix**  
   Cosine similarity computed between all movies.

5. **Recommendation Function**  
   Based on user input (movie title), returns top 5–10 most similar movies.

---

## 🚀 Sample Recommendation Function

```python
def recommend(movie):
    index = data[data['title'] == movie].index[0]
    distances = sorted(list(enumerate(similarity[index])), reverse=True, key=lambda x: x[1])
    for i in distances[1:6]:
        print(data.iloc[i[0]].title)
```

---

## 📊 Future Improvements

- Add **user-based collaborative filtering**
- Integrate **movie posters** using TMDB API
- Deploy using **Streamlit or Flask**
- Support **fuzzy title matching** with `difflib` or `fuzzywuzzy`

---

## 📁 How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/alphasuraj18/netflix-movie-recommender.git
   cd netflix-movie-recommender
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

---

## 👨‍💻 Author

**Suraj Kumar**  
B.Tech CSE (AI & ML), Galgotias University
