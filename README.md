# 📰 News Recommendation System

A **Content-Based News Recommendation System** that helps users discover relevant news articles based on the **content of the articles**.

The system uses the **headline and short description** of news articles to identify similar content. **TF-IDF (Term Frequency–Inverse Document Frequency)** is used to convert article text into numerical vectors, and **K-Nearest Neighbors (KNN)** with **Cosine Distance** is used to find and recommend the most similar news articles.

The project is developed using **Python and Flask**, with Pandas and Scikit-learn used for data processing and machine learning. The frontend is built using **HTML, CSS, JavaScript, and Bootstrap**.

---

## 🚀 Features

* 📰 Content-based news recommendations
* 🔍 Search-based news recommendations
* 🧠 TF-IDF text vectorization
* 🤖 K-Nearest Neighbors (KNN)
* 📐 Cosine distance-based similarity
* 📝 Uses headline and short description as article content
* 🏷️ News category analysis
* 📊 Category statistics
* 🎲 Random news article selection
* 🌐 Flask REST API
* 💻 Interactive web interface
* 📱 Responsive Bootstrap-based UI
* 🌙 Dark mode support

---

## 🛠️ Technologies Used

| Technology       | Purpose                                      |
| ---------------- | -------------------------------------------- |
| **Python**       | Core application and recommendation logic    |
| **Flask**        | Backend server and REST APIs                 |
| **Pandas**       | Loading, cleaning and processing the dataset |
| **NumPy**        | Numerical and data operations                |
| **Scikit-learn** | TF-IDF and KNN implementation                |
| **HTML**         | Web page structure                           |
| **CSS**          | Styling and UI customization                 |
| **JavaScript**   | Frontend logic and API communication         |
| **Bootstrap**    | Responsive web interface                     |
| **Kaggle**       | News dataset source                          |

---

## 📂 Project Structure

```text
News-Recommendation-system-main/
│
├── server/
│   ├── app.py
│   │   └── Flask application and REST APIs
│   │
│   ├── model.py
│   │   └── Data preprocessing and recommendation model
│   │
│   ├── static/
│   │   ├── main.js
│   │   │   └── Frontend logic and API communication
│   │   │
│   │   └── style.css
│   │       └── Application styling
│   │
│   └── templates/
│       └── index.html
│           └── Main web interface
│
├── requirements.txt
│   └── Required Python libraries
│
└── README.md
    └── Project documentation
```

---

# 🔄 System Workflow

```text
                  ┌──────────────────────┐
                  │   Kaggle News Dataset│
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │  Data Preprocessing  │
                  │  Missing Values      │
                  │  Remove Duplicates   │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Headline + Short     │
                  │ Description          │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │   TF-IDF Vectorizer  │
                  │    Text → Vectors    │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │      KNN Model       │
                  │   Cosine Distance    │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │   User Search Query  │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Query → TF-IDF Vector│
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Find Similar Articles│
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Top K Recommendations│
                  └──────────────────────┘
```

---

# 🧠 How the Recommendation System Works

The recommendation process is based on the **content of the news articles**.

### 1. Dataset Loading

The application downloads and loads the **News Category Dataset** from Kaggle.

The dataset contains information such as:

```text
Headline
Short Description
Category
Article Link
```

The dataset is loaded and processed using **Pandas**.

---

### 2. Data Preprocessing

Before building the recommendation model, the news data is cleaned.

The system:

* Handles missing headlines
* Handles missing descriptions
* Handles missing categories
* Converts text values into strings
* Combines headline and short description
* Removes empty articles
* Removes duplicate article content
* Creates a unique article ID

The article content is created using:

```text
Headline + Short Description
```

This combined content is used for the recommendation process.

---

### 3. TF-IDF Vectorization

The combined article content is converted into numerical vectors using **TF-IDF**.

The project uses:

```python
TfidfVectorizer(
    stop_words='english',
    max_features=5000,
    ngram_range=(1, 2),
    min_df=2,
    max_df=0.8
)
```

TF-IDF gives numerical importance to words based on their occurrence across the news articles.

The process is:

```text
Article Content
      ↓
Remove Stop Words
      ↓
Extract Words / Word Pairs
      ↓
Calculate TF-IDF
      ↓
Numerical Vector
```

---

### 4. KNN Model

After converting the article content into numerical vectors, the project uses **K-Nearest Neighbors (KNN)** to find similar articles.

The model uses **Cosine Distance** to compare the article vectors.

```text
Article Vectors
      ↓
KNN Model
      ↓
Cosine Distance
      ↓
Nearest Articles
```

---

### 5. Cosine Distance

Cosine distance is used to measure how different two text vectors are.

The project converts the distance into a similarity score using:

```text
Similarity = 1 - Cosine Distance
```

A smaller cosine distance indicates that the articles are more similar.

---

### 6. User Search Query

When the user enters a search query, the query is converted into a TF-IDF vector using the same vectorizer.

For example:

```text
User Query:

"artificial intelligence technology"
```

The process is:

```text
User Query
     ↓
TF-IDF Transformation
     ↓
Query Vector
     ↓
KNN Search
     ↓
Cosine Distance
     ↓
Top K Similar Articles
```

---

### 7. Recommendation Generation

The KNN model finds the nearest article vectors to the user's query vector.

The system then returns the top K similar articles.

For example:

```text
User Query
     ↓
Find Similar Articles
     ↓
Top 5 Articles
     ↓
Display Recommendations
```

The recommended articles contain information such as:

```text
Headline
Category
Short Description
Article Link
Similarity Score
```

---

# 🧠 TF-IDF Component

**TF-IDF** stands for **Term Frequency–Inverse Document Frequency**.

It is used to convert news article text into numerical vectors so that the text can be compared mathematically.

The project uses:

```python
TfidfVectorizer(
    stop_words='english',
    max_features=5000,
    ngram_range=(1, 2),
    min_df=2,
    max_df=0.8
)
```

### TF-IDF Process

```text
News Article
     ↓
Text Processing
     ↓
Remove Stop Words
     ↓
Calculate TF
     ↓
Calculate IDF
     ↓
TF × IDF
     ↓
Numerical Vector
```

The resulting vectors are used by KNN to find similar news articles.

---

# 🤖 KNN Recommendation

The project uses **K-Nearest Neighbors** to find the closest news articles to the user's search query.

The recommendation process is:

```text
User Query
     ↓
Convert Query to TF-IDF Vector
     ↓
Compare With Article Vectors
     ↓
Calculate Cosine Distance
     ↓
Find Nearest Neighbors
     ↓
Select Top K
     ↓
Recommended News
```

The default recommendation count is **5 articles**.

---

# 🏷️ Category Analysis

The system also provides information about the categories available in the dataset.

The category API returns:

```text
Total Articles
Total Categories
Category Name
Article Count
Percentage
```

This allows the application to display category statistics from the news dataset.

---

# 🎲 Random Articles

The application also provides a random article feature.

Random articles are selected from the processed dataset and displayed on the frontend.

```text
News Dataset
     ↓
Random Selection
     ↓
Random Articles
     ↓
Display on Web Page
```

This allows users to discover news articles without entering a search query.

---

# 🌐 Backend API

The backend is developed using **Flask**.

The Flask application provides REST APIs that connect the frontend with the recommendation model.

### Get Categories

```text
GET /api/categories
```

Returns category statistics and article information.

---

### Get Recommendations

```text
POST /api/recommend
```

Accepts a search query and returns similar news articles.

Example request:

```json
{
  "query": "artificial intelligence technology",
  "top_k": 5
}
```

---

### Get Random Articles

```text
GET /api/random_articles
```

Returns randomly selected news articles.

Example:

```text
/api/random_articles?n=6
```

---

# 🎨 User Interface

The application provides an interactive web interface built using:

* HTML
* CSS
* JavaScript
* Bootstrap 5

The interface includes:

* 🔍 Search box for news queries
* 📰 Recommended Articles section
* 🎲 Random Articles section
* 🏷️ News category information
* 🌙 Dark mode toggle
* 📱 Responsive design

When the user enters a search query, the frontend sends the query to the Flask backend. The backend processes the query using **TF-IDF and KNN**, finds similar articles, and returns the recommendations to the frontend.

---

# 🔗 Frontend–Backend Communication

The communication flow is:

```text
                    User
                      │
                      ▼
              Enter Search Query
                      │
                      ▼
             JavaScript Frontend
                      │
                      ▼
                Flask API
                      │
                      ▼
          Recommendation Engine
                      │
                      ▼
                 TF-IDF
                      │
                      ▼
               KNN + Cosine
                      │
                      ▼
             Similar Articles
                      │
                      ▼
              Flask Response
                      │
                      ▼
             JavaScript Frontend
                      │
                      ▼
          Display Recommendations
```

---

# 🛡️ Edge Cases

The system handles several common cases during recommendation.

### Empty Search Query

If the user enters an empty query, the recommendation process does not continue.

---

### Missing Dataset

If the dataset cannot be loaded or is empty, the application stops with an appropriate error message.

---

### Missing Values

Missing headlines, descriptions, and categories are handled during preprocessing.

---

### Duplicate Articles

Duplicate article content is removed during preprocessing to avoid repeated content in the recommendation dataset.

---

### Small Dataset

For smaller datasets, the system adjusts the maximum number of TF-IDF features to avoid unnecessary feature size.

---

# 📊 Dataset

The project uses the **News Category Dataset** from Kaggle.

The dataset contains information such as:

```text
Headline
Short Description
Category
Article Link
```

The recommendation system mainly uses:

```text
Headline + Short Description
```

as the article content.

---

# 🔮 Future Improvements

The current content-based recommendation system can be enhanced with:

* 🔹 User profiles and personalized recommendations
* 🔹 User recommendation history
* 🔹 Like/Dislike functionality
* 🔹 Collaborative filtering
* 🔹 Hybrid recommendation techniques
* 🔹 Advanced NLP techniques
* 🔹 More article text features
* 🔹 Recommendation accuracy evaluation
* 🔹 Real-time news updates
* 🔹 Online deployment

---

# 🎯 Project Highlights

* 📰 Developed a **Content-Based News Recommendation System**
* 🧠 Used **TF-IDF Vectorization** to represent news article content
* 🤖 Used **K-Nearest Neighbors (KNN)** to find similar articles
* 📐 Used **Cosine Distance** to measure article similarity
* 🔍 Implemented search-based news recommendations
* 📝 Used **headline and short description** as article content
* 🧹 Implemented data preprocessing and duplicate removal
* 🏷️ Implemented news category analysis
* 🎲 Added random article discovery
* 🌐 Developed REST APIs using Flask
* 💻 Built the frontend using HTML, CSS, JavaScript, and Bootstrap
* 🔄 Connected the machine-learning recommendation model with the web application

---

# 🧰 Technology Architecture

```text
                     News Recommendation System
                               │
                               ▼
                            Python
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
           Pandas        Scikit-learn          Flask
              │                │                │
              ▼                ▼                ▼
      Data Processing       TF-IDF          REST APIs
                               │
                               ▼
                              KNN
                               │
                               ▼
                       Cosine Distance
                               │
              ┌────────────────┴────────────────┐
              ▼                                 ▼
       Recommendation                      Web Interface
              │                                 │
              └────────────────┬────────────────┘
                               ▼
                         Similar News
                           Articles
```

---

# ▶️ How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-link>
```

### 2. Open the Project Directory

```bash
cd News-Recommendation-system-main
```

### 3. Install Required Libraries

```bash
pip install -r requirements.txt
```

### 4. Run the Flask Application

```bash
cd server
python app.py
```

### 5. Open the Application

Open the following URL in your browser:

```text
http://localhost:5000
```

---

# 🔗 Links

* **GitHub:** `<your-github-repository-link>`
* **Live Demo:** `<your-live-demo-link>`

---

# 📌 Project Summary

The **News Recommendation System** is a **Content-Based Recommendation System** that recommends similar news articles based on their textual content.

The system uses the **Kaggle News Category Dataset** and preprocesses the article data by handling missing values, removing duplicates, and combining the headline and short description.

The combined article content is converted into numerical vectors using **TF-IDF Vectorization**. The system then uses **K-Nearest Neighbors (KNN)** with **Cosine Distance** to find the most similar articles to a user's search query.

The recommendation model is integrated with a **Flask backend**, while the frontend is developed using **HTML, CSS, JavaScript, and Bootstrap**.

The project demonstrates how **Natural Language Processing, Machine Learning, REST APIs, and Web Development** can be combined to build a practical **content-based news recommendation application**.
