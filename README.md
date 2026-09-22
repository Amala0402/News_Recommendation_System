# 📰 News Recommendation System

A **Content-Based News Recommendation System** that helps users discover relevant news articles based on the **content of the articles**.

The system uses the **headline and short description** of news articles to identify similar content. **TF-IDF Vectorization** is used to convert the text into numerical vectors, and **K-Nearest Neighbors (KNN)** with **Cosine Distance** is used to find and recommend the most similar news articles.

The project is developed using **Python and Flask**, with Pandas and Scikit-learn used for data processing and machine learning. The frontend is built using **HTML, CSS, JavaScript, and Bootstrap**.


---

## 🚀 Features

* 📰 Personalized news discovery
* 👍 Like and 👎 Dislike based user interaction
* 🎯 Category-based personalized recommendations
* 🔄 Dynamic recommendation generation
* 🚫 Prevents previously rated articles from appearing again
* 📊 Category-based article selection
* 🧠 TF-IDF text vectorization
* 💾 Session-based preference tracking
* 📱 Interactive Streamlit web interface
* 🎨 Category-specific visual elements
* 🔁 Restart option when suitable recommendations are unavailable

---

## 🛠️ Technologies Used

| Technology       | Purpose                                           |
| ---------------- | ------------------------------------------------- |
| **Python**       | Core application and recommendation logic         |
| **Pandas**       | Loading, cleaning and processing the news dataset |
| **NumPy**        | Numerical and data operations                     |
| **Scikit-learn** | TF-IDF vectorization                              |
| **Streamlit**    | Interactive web application                       |
| **CSV**          | Storage of news article data                      |

---

## 📂 Project Structure

```text
News_Recommendation_System/
│
├── app.py
│   └── Main Streamlit application
│
├── news.csv
│   └── News article dataset
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
                  ┌──────────────────┐
                  │    News Dataset  │
                  │     news.csv     │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Data Processing  │
                  │ & Preparation    │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Initial Article  │
                  │    Selection     │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ User Interaction │
                  │   Like / Dislike │
                  └────────┬─────────┘
                           │
                    ┌──────┴──────┐
                    ▼             ▼
                  Like         Dislike
                    │             │
                    ▼             ▼
             Store Preference   Store Category
                    │             │
                    └──────┬──────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Preference       │
                  │ Analysis         │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Find Candidate   │
                  │ Articles         │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Remove Previously│
                  │ Rated Articles   │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Personalized    │
                  │ News Feed        │
                  └──────────────────┘
```

---

# 🧠 How the Recommendation System Works

The recommendation process is based mainly on **user preferences and news categories**.

### 1. Dataset Loading

The application loads the news dataset from `news.csv`.

The dataset contains information related to news articles, which is processed before being displayed to the user.

The data processing stage prepares the article information so that it can be used by the recommendation system.

---

### 2. Initial Article Selection

When the application starts, a set of news articles is selected for the user to evaluate.

The initial articles are selected from different categories so that the user gets exposure to different types of news.

For example:

```text
Technology → Article 1
Sports     → Article 2
Business   → Article 3
Science    → Article 4
Politics   → Article 5
```

This gives the recommendation system an initial understanding of the user's interests.

---

### 3. User Preference Collection

The user can interact with each article using:

```text
👍 Like
👎 Dislike
```

When an article is liked, the system records its information and identifies its category.

For example:

```text
User Likes:

Technology
Sports
Science
```

These categories become indicators of the user's current interests.

---

### 4. Preference Analysis

The system examines the categories associated with the articles liked by the user.

For example:

```text
Liked Articles
      ↓
Identify Categories
      ↓
Technology
Sports
Science
      ↓
Create Preference Set
```

This preference information is then used to identify suitable candidate articles.

---

### 5. Candidate Article Selection

The system searches the available news dataset for articles belonging to the user's preferred categories.

For example:

```text
Preferred Categories
        ↓
Technology + Sports + Science
        ↓
Search Dataset
        ↓
Find Matching Articles
```

Articles that match the user's preferred categories become recommendation candidates.

---

### 6. Filtering Previously Rated Articles

Articles that the user has already interacted with are excluded from the recommendation list.

This prevents the application from repeatedly showing the same articles during the current session.

```text
Candidate Articles
        ↓
Check Rated Articles
        ↓
Remove Previously Rated Articles
        ↓
Remaining Articles
```

---

### 7. Recommendation Generation

After filtering, the system selects suitable articles from the remaining candidates and displays them as the user's personalized news feed.

The recommendation process therefore follows:

```text
User Interaction
       ↓
Liked Categories
       ↓
Category Filtering
       ↓
Remove Rated Articles
       ↓
Generate Recommendations
```

---

# 🤖 TF-IDF Component

The project also includes **TF-IDF Vectorization** using Scikit-learn.

TF-IDF stands for **Term Frequency–Inverse Document Frequency** and is commonly used to represent text as numerical vectors.

The project initializes a TF-IDF vectorizer to provide a foundation for text-based recommendation functionality.

```python
TfidfVectorizer(stop_words='english')
```

The TF-IDF component can be extended in future versions to calculate similarity between articles and provide more advanced content-based recommendations.

### Current Recommendation Approach

The main recommendation flow is based on:

```text
User Preference
      ↓
Liked Categories
      ↓
Category Filtering
      ↓
Article Selection
      ↓
Personalized Recommendations
```

Therefore, the current system should be described primarily as a **preference/category-based recommendation system**, with TF-IDF providing a foundation for future content-similarity improvements.

---

# 🛡️ Edge Cases

The system also considers situations where suitable recommendations may not be immediately available.

### User Dislikes Initial Articles

If the user dislikes the initially displayed articles, the system can use the interaction information to avoid unsuitable categories and provide another set of articles.

```text
Articles Disliked
       ↓
Identify Disliked Categories
       ↓
Avoid Unsuitable Articles
       ↓
Generate Another Selection
```

---

### No Suitable Recommendations

If suitable articles cannot be found for the user's preferences, the application provides an appropriate message and allows the user to restart the recommendation process.

This helps maintain a smooth user experience instead of leaving the recommendation section empty.

---

# 🎨 User Interface

The application is built using **Streamlit**, providing an interactive and easy-to-use interface.

The interface includes:

* 📰 News article display
* 👍 Like button
* 👎 Dislike button
* 📊 User interaction progress
* 🎯 Personalized recommendation section
* 🏷️ Category information
* 🎨 Custom styling
* 🔄 Restart functionality

The interface allows users to interact with news articles directly and receive recommendations without requiring complex input.

---

# 📊 Dataset

The project uses a CSV-based news dataset.

The dataset provides the information required for displaying articles and determining their categories.

Typical information used by the recommendation system includes:

```text
Article ID
Category
Subcategory
Headline
Summary
Article Link
```

The dataset is loaded and processed using **Pandas** before being used by the application.

---

# 🔮 Future Improvements

The current recommendation system can be enhanced further with more advanced recommendation techniques.

Possible improvements include:

* 🔹 Content similarity using article headlines and summaries
* 🔹 Cosine similarity between article vectors
* 🔹 User preference scoring
* 🔹 Weighted Like/Dislike preferences
* 🔹 Collaborative filtering
* 🔹 Hybrid recommendation techniques
* 🔹 Machine-learning-based ranking
* 🔹 Persistent user profiles
* 🔹 Recommendation accuracy evaluation
* 🔹 Article popularity analysis
* 🔹 Real-time news collection
* 🔹 More advanced personalization

A future version could represent each article using its **headline and summary**, convert the text into TF-IDF vectors, and calculate similarity to recommend articles that are more closely related to the user's interests.

---

# 🎯 Project Highlights

* 📰 Developed an interactive **personalized news recommendation system**
* 🎯 Uses user interactions to identify preferred news categories
* 👍 Implements Like/Dislike based preference collection
* 🔄 Generates recommendations dynamically
* 🚫 Prevents previously rated articles from being repeatedly recommended
* 🧠 Integrates TF-IDF vectorization as a foundation for advanced text-based recommendations
* 📊 Uses Pandas for efficient dataset processing
* 💻 Provides an interactive Streamlit interface
* 🎨 Focuses on simple and user-friendly news discovery

---

# 🧰 Technology Architecture

```text
                    News Recommendation System
                              │
                              ▼
                           Python
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
           Pandas          Scikit-learn    Streamlit
              │               │               │
              ▼               ▼               ▼
       Dataset Processing   TF-IDF        Web Interface
              │               │               │
              └───────────────┼───────────────┘
                              ▼
                    Recommendation Logic
                              │
                              ▼
                     Personalized News
```

---

# ▶️ How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/Amala0402/News_Recommendation_System.git
```

### 2. Open the Project Directory

```bash
cd News_Recommendation_System
```

### 3. Install Required Libraries

```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit Application

```bash
streamlit run app.py
```

### 5. Open the Application

After running the command, Streamlit will provide a local URL where the application can be accessed.

---

# 📌 Project Summary

The **News Recommendation System** provides a simple and interactive approach to personalized news discovery. Instead of showing the same news to every user, the system observes user interactions, identifies preferred categories, filters the available dataset, and generates a personalized set of articles.

The project combines **Python, Pandas, Scikit-learn and Streamlit** to demonstrate how user preferences can be incorporated into a recommendation workflow.

The current implementation focuses on category-based personalization while providing a foundation for future development of more advanced content-based and hybrid recommendation techniques.
