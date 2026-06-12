# Recommendation Systems for Personalized Content Discovery

A large-scale movie recommendation system built using the Netflix Prize Dataset. This project compares traditional collaborative filtering methods with Matrix Factorization and evaluates recommendation quality using both rating prediction and ranking metrics.

---

## Project Overview

The objective of this project is to:

* Learn user preferences from historical movie ratings.
* Predict ratings for unseen movies.
* Generate personalized Top-K movie recommendations.
* Compare multiple recommendation approaches.
* Evaluate recommendation quality using RMSE and MAP@10.

The project was developed as part of an academic recommendation systems challenge using the Netflix Prize Dataset.

---

## Dataset

### Netflix Prize Dataset

Dataset Statistics:

| Metric       |       Value |
| ------------ | ----------: |
| Users        |     480,189 |
| Movies       |      17,770 |
| Ratings      | 100,480,507 |
| Rating Scale |         1–5 |

Additional metadata:

* Movie Title
* Release Year
* Rating Timestamps

Dataset characteristics:

* Extremely sparse user-item matrix
* Long-tail movie popularity distribution
* Large-scale collaborative filtering problem

---

## Repository Structure

```text
Netflix-Recommendation-System/
│
├── Dataset_Preparation.ipynb
├── Recommendation_System_Development.ipynb
│
├── report/
│   └── Technical_Report.pdf
│
├── presentation/
│   └── Presentation.pdf
│
├── images/
│   ├── user_activity_distribution.png
│   ├── movie_popularity_distribution.png
│   ├── rating_distribution.png
│   └── long_tail_distribution.png
│
├── requirements.txt
└── README.md
```

---

## Data Processing Pipeline

The preprocessing pipeline performs:

1. Parsing raw Netflix movie files.
2. Converting records into tabular format.
3. Data type optimization for memory efficiency.
4. Integration of movie metadata.
5. User filtering and sparsity reduction.
6. Train/Validation/Test split generation.

Final filtered dataset:

| Metric       |      Value |
| ------------ | ---------: |
| Active Users |     54,404 |
| Ratings      | 47,092,231 |
| Movies       |     17,770 |

---

## Exploratory Data Analysis

The following analyses were performed:

* User activity analysis
* Movie popularity analysis
* Rating distribution analysis
* Sparsity analysis
* Long-tail popularity analysis

Key findings:

* User activity is highly skewed.
* Movie popularity follows a long-tail distribution.
* Ratings are concentrated around 3–5 stars.
* Dataset sparsity exceeds 98%.

---

## Recommendation Models

### Baseline Models

* Global Mean
* User Mean
* Movie Mean

### Collaborative Filtering

#### User-Based Collaborative Filtering

* Cosine Similarity
* Top-50 Neighbors

#### Item-Based Collaborative Filtering

* Cosine Similarity
* Top-50 Similar Items

### Matrix Factorization (Primary Model)

Implemented using PyTorch.

Model components:

* User Embeddings
* Movie Embeddings
* User Bias
* Movie Bias
* Global Rating Bias

Training Configuration:

| Parameter      |   Value |
| -------------- | ------: |
| Latent Factors |      64 |
| Optimizer      |    Adam |
| Batch Size     | 262,144 |
| Epochs         |      15 |
| Device         |     GPU |

---

## Evaluation Methodology

### Train / Validation / Test Split

| Split      | Ratio |
| ---------- | ----: |
| Train      |   80% |
| Validation |   10% |
| Test       |   10% |

### Metrics

#### RMSE

Measures rating prediction accuracy.

#### MAP@10

Measures recommendation ranking quality.

Relevance definition:

```text
Rating >= 3.5
```

Top-10 recommendations are generated for each user and compared against relevant items in the test set.

---

## Results

### RMSE Comparison

| Model                |       RMSE |
| -------------------- | ---------: |
| Global Mean          |     1.0725 |
| Movie Mean           |     0.9976 |
| User Mean            |     0.9789 |
| User-CF              |     1.0340 |
| Item-CF              |     1.0137 |
| Matrix Factorization | **0.8135** |

### Recommendation Metrics

| Metric   |       Value |
| -------- | ----------: |
| MAP@10   | **0.04965** |
| Coverage |   **9.45%** |

---

## Example Recommendations

### User History

* Streets of Fire
* Amadeus
* Dangerous Liaisons
* Moonlighting: The Pilot
* The Ninth Gate

### Recommended Movies

* Independence Day
* The Silence of the Lambs
* Pretty Woman
* The Lord of the Rings: The Fellowship of the Ring
* The Green Mile

---

## Key Findings

* Matrix Factorization significantly outperformed neighborhood-based methods.
* Latent factor models effectively captured user preferences.
* Recommendation quality improved substantially over baseline approaches.
* The system successfully generated personalized Top-K movie recommendations.
* Popularity bias remains a challenge due to the long-tail nature of the dataset.

---

## Reproducing Results

### 1. Clone Repository

```bash
git clone <repository-url>
cd Netflix-Recommendation-System
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run Data Preparation

Execute:

```text
Dataset_Preparation.ipynb
```

This notebook:

* Parses raw Netflix files
* Creates processed datasets
* Performs train/validation/test splitting

### 4. Run Model Development Notebook

Execute:

```text
Recommendation_System_Development.ipynb
```

This notebook performs:

* EDA
* Baseline Modeling
* User-Based Collaborative Filtering
* Item-Based Collaborative Filtering
* Matrix Factorization Training
* Evaluation
* Recommendation Generation

---

## Future Improvements

* Hybrid Recommendation Systems
* Cold-Start User Handling
* Content-Based Features
* Ranking-Aware Optimization
* Diversity-Aware Recommendations

---
