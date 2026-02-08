# 🛍️ Product Recommendation System  
### Popularity & Rating-Based Collaborative Filtering

## 📌 Project Overview
This project implements a **robust baseline recommendation system** using real-world Amazon product ratings data.  
Instead of relying on complex similarity matrices or matrix factorization, the system focuses on **scalable, explainable, and production-safe logic**.

The recommender suggests products based on **overall popularity and rating quality**, while excluding items already interacted with by the user.

---

## 📊 Dataset
Amazon product ratings dataset with the following columns:

- **UserId** – Unique reviewer identifier  
- **ProductId** – Amazon product ASIN  
- **Rating** – User rating (1–5)  
- **Timestamp** – Unix timestamp of the review  

---

## 🔍 Exploratory Data Analysis

### Rating Distribution
- Ratings are highly skewed toward **4 and 5 stars**
- Indicates a strong positivity bias typical of e-commerce platforms
- Explains why similarity-based collaborative filtering can struggle due to sparsity

---

## 🧠 Recommendation Strategy

### Why Not Traditional Collaborative Filtering?
- User–item matrix is extremely sparse
- Item–item similarity computation is memory-intensive
- Many users and products have very few interactions

### Chosen Approach: Weighted Popularity-Based Recommender

Each product is scored using:
score = average_rating × log(1 + rating_count)
This balances:
- **Rating quality** (how well a product is rated)
- **User engagement** (how many users rated it)

---

## ⚙️ Recommendation Logic

1. Compute product-level statistics (rating count & average rating)
2. Calculate a weighted popularity score
3. Rank products by score
4. Recommend top products **excluding items already rated by the user**
5. Automatically handles cold-start users

---

## ✅ Example Output

```python
['B001MA0QY2', 'B000ZMBSPF', 'B0043OYFKU', 'B0009V1YR8', 'B001A0OWCG']

