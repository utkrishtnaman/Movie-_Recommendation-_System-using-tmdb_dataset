# 🎬 Movie_Recommendation_System using tmdb dataset 🎬

An end-to-end Machine Learning project that recommends movies based on content similarity. The application features a sleek web interface built with Streamlit and fetches real-time movie posters using the TMDB API.

---

## 🚀 Overview
This project implements a **Content-Based Recommender System**. Unlike collaborative filtering, which depends on user ratings, this system suggests movies by analyzing metadata—such as **genres, keywords, cast, and directors**—to find the most similar matches within a 5,000-movie dataset.

## 🛠️ Technical Stack
* **Language:** Python 3.9+
* **Machine Learning:** Scikit-learn (`CountVectorizer`, `Cosine Similarity`)
* **NLP:** NLTK (`PorterStemmer`)
* **Data Handling:** Pandas, NumPy
* **Web Framework:** Streamlit
* **API:** TMDB API (The Movie Database)

## 🧠 Core Logic

### 1. Data Cleaning & Feature Engineering
* **Merging:** Combined the `tmdb_5000_movies` and `tmdb_5000_credits` datasets.
* **Feature Selection:** Kept `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, and `crew`.
* **Entity Extraction:** Extracted only the top 3 actors and the director from the credits.
* **Transformation:** Removed spaces from strings (e.g., "Johnny Depp" → "JohnnyDepp") to ensure the vectorizer treats names as unique tokens.

### 2. Vectorization & Similarity
* **Stemming:** Applied NLTK's `PorterStemmer` to reduce words to their root form (e.g., "activities" → "activ").
* **Bag of Words:** Converted the combined `tags` column into 5,000-dimensional vectors using `CountVectorizer`, excluding English stop words.
* **Cosine Similarity:** Calculated the similarity between movie vectors using the cosine of the angle between them.

### 3. Visuals
* **Posters:** The app uses the TMDB API to fetch high-resolution posters dynamically based on the unique `movie_id`.

## 💻 Installation & Setup

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/your-username/movie-recommender-system.git](https://github.com/your-username/movie-recommender-system.git)
    cd movie-recommender-system
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **TMDB API Key**
    * Sign up at [The Movie Database](https://www.themoviedb.org/).
    * Generate an API Key from your account settings.
    * Paste your key into the `fetch_poster` function in `app.py`.

4.  **Run the App**
    ```bash
    streamlit run app.py
    ```

## 📂 Project Structure
* `movie_recommender.ipynb`: Data preprocessing and model training.
* `app.py`: Main Streamlit application file.
* `movie_dict.pkl`: Serialized movie data dictionary.
* `similarity.pkl`: Pre-calculated similarity matrix.
* `Procfile` & `setup.sh`: Deployment configurations for Heroku.

## 🎯 Usage
1.  Search or select a movie from the dropdown.
2.  Click **Recommend**.
3.  View the top 5 recommended movies with their titles and posters.

---
