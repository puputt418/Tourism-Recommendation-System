# Tourism-Recommendation-System
![image](https://github.com/user-attachments/assets/563ebcb8-98ea-4d33-bed2-e9f26ece8f46)
Indonesia is a country with more than 17,000 islands, each offering its own unique charm—from pristine beaches and towering mountains to historical sites and modern attractions.

While this diversity is a gift, it can also make choosing a destination overwhelming. Travelers often find themselves unsure about where to go, especially when information is scattered across various sources with inconsistent details. This challenge affects both domestic and international visitors alike.

## Problem Statement

Most tourism platforms in Indonesia still rely on generic recommendations that ignore crucial aspects like past travel experiences, evolving tourist trends, and individual user preferences.

## Project Objective

This project introduces the "Tourism Destination Recommendation System in Indonesia Using a Hybrid Filtering Approach" to address these challenges.

By applying two recommendation techniques:

- Content-Based Filtering: compares destination descriptions and categories.
- Collaborative Filtering: analyzes patterns in user ratings.

This dual strategy aims to provide personalized and relevant destination recommendations.

## Evaluation Metric

To assess the system’s effectiveness, the model will be evaluated using the Precision@5 metric. This ensures that the top five recommendations generated are meaningful and aligned with the user’s interests.

## Goal

The goal of this project is to make the experience of choosing a travel destination in Indonesia more straightforward, insightful, and enjoyable for users.

## Dataset Overview

This project utilizes two datasets:

### 1. Tourism Dataset

- **Number of Entries:** 437 rows  
- **Columns:** 13  

#### Key Features:
- `Place_Id` (int64): Unique identifier for each tourist destination.
- `Place_Name` (object): Name of the tourist destination.
- `Description` (object): Textual description of the destination.
- `Category` (object): Type of destination (e.g., cultural site, amusement park).
- `City` (object): City where the destination is located.
- `Price` (int64): Entry fee in Indonesian Rupiah (IDR).
- `Rating` (float64): User rating on a scale from 1 to 5.
- `Time_Minutes` (float64): Estimated time needed to explore the destination (many missing values).
- `Coordinate`, `Lat`, `Long` (object/float64): Geographic location details.
- `Unnamed: 11` (float64): Empty column, irrelevant and removed.
- `Unnamed: 12` (int64): Column with unclear purpose, further inspection required.

---

### 2. Rating Dataset

- **Number of Entries:** 10,000 rows  
- **Columns:** 3  

#### Key Features:
- `User_Id` (int64): Unique identifier for each user.
- `Place_Id` (int64): Matches the tourism dataset to link ratings with destinations.
- `Place_Ratings` (int64): Rating given by a user for a particular place (1–5 scale).

---

## Methodology

This project implements a hybrid recommendation system that combines content-based and collaborative filtering approaches to suggest tourism destinations in Indonesia.

### 1. Data Preprocessing
- Cleaned both the tourism and rating datasets.
- Removed irrelevant columns such as `Unnamed: 11` and `Unnamed: 12`.
- Handled missing values, particularly in the `Time_Minutes` column.

### 2. Content-Based Filtering
- Utilized `CountVectorizer` to extract features from `Category`, `City`, and `Description`.
- Calculated cosine similarity between destinations based on these text features.
- Generated recommendations by identifying the most similar destinations based on a selected item.

### 3. Collaborative Filtering
- Created a user-item matrix using rating data.
- Applied user-based collaborative filtering with cosine similarity.
- Recommended destinations based on preferences of users with similar rating patterns.

### 4. Hybrid Recommendation Logic
- Combined scores from content-based and collaborative filtering results.
- Returned top-N recommendations based on the hybrid ranking.

---

## How to Run the Project

### 1. Clone the Repository
```bash
git clone https://github.com/puputt418/Tourism-Recommendation-System.git
cd Tourism-Recommendation-System
```

### 2. Install Required Libraries

Ensure you have the following libraries installed:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

### 3. Run the Notebook
Use Jupyter Notebook to open and execute:
```bash
jupyter notebook recommended_system.ipynb
```

## Evaluation and Interpretation of Results
The model was evaluated using multiple metrics:

- Precision@5: 0.0114

- Mean Absolute Error (MAE): 0.60

- Mean Squared Error (MSE): 0.50

- R² Score: -3.58

## Interpretation
The model exhibits poor performance in identifying useful tourism recommendations, as indicated by the low Precision@5 score. Additionally, error metrics show a significant gap between predicted and actual ratings, and the R² score confirms that the model performs worse than a naive average predictor.

These outcomes highlight the limitations of:

- TF-IDF in capturing semantic content.

- Sparse user-item interaction data.

- Non-optimized weighting of hybrid components.

The distribution of predicted ratings also centers heavily around 3.0, suggesting difficulties in distinguishing between highly and poorly rated destinations.

## Future Improvements
To improve model performance, the following approaches are recommended:

- Implement more advanced text representation (e.g., Word2Vec, BERT).

- Use matrix factorization techniques (e.g., SVD) to handle data sparsity.

- Fine-tune hybrid weighting strategies for better integration.

- Enrich datasets with more user interaction data.

- Experiment with hyperparameter optimization to reduce prediction bias.

Final Notes
While the model's performance is currently suboptimal, this project demonstrates a full-cycle recommendation system development—from data preparation, filtering strategy implementation, to evaluation and reflection.

Rather than focusing solely on high accuracy, this project emphasizes understanding the limitations of real-world data, the challenges of building recommendation systems, and identifying meaningful next steps for improvement.

This foundation can be expanded into a more robust and production-ready recommendation system with further iteration and data collection.

---

