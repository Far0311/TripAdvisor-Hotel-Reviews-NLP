# TripAdvisor-Hotel-Reviews-NLP
This assignment explores NLP techniques using the TripAdvisor Hotel Reviews dataset. It covers data preprocessing, sentiment classification using Logistic Regression, CNN, and BERT models, and text clustering with LDA, NMF, KMeans, and Agglomerative Clustering to analyze and group customer opinions effectively.

# Summary of Performance Across Tasks
| Task                                | Model / Technique        | Accuracy | Macro F1 | Silhouette Score | Calinski-Harabasz | Davies-Bouldin | Notable Insights |
|-------------------------------------|---------------------------|----------|----------|------------------|-------------------|----------------|------------------|
| Text Classification + Sentiment Analysis | **CNN**                   | 0.96     | 0.96     | –                | –                 | –              | Best performance overall; excellent at identifying all classes, particularly Neutral with F1 = 0.95 |
| Text Classification + Sentiment Analysis | **Logistic Regression**   | 0.91     | 0.91     | –                | –                 | –              | Strong performance and well-balanced; slightly weaker for Neutral (F1 = 0.88) |
| Text Classification + Sentiment Analysis | **BERT**                  | 0.88     | 0.83     | –                | –                 | –              | Good for Positive class (F1 = 0.94); struggles with Neutral (F1 = 0.74) |
| Text Classification + Sentiment Analysis | **VADER (Lexicon-based)** | 0.80     | 0.48     | –                | –                 | –              | Biased toward Positive; fails at Neutral (F1 = 0.01); recall for Negative is low (0.41) |
| Clustering                          | **LDA + KMeans**          | –        | –        | 0.4801           | 18007.6279        | 0.7151         | Best cluster quality across all metrics; well-defined, compact, and distinct clusters |
| Clustering                          | **LDA + Agglomerative**   | –        | –        | 0.4091           | 13352.2827        | 0.8528         | Good cohesion and separation; slightly weaker than KMeans on all metrics |
| Clustering                          | **NMF + KMeans**          | –        | –        | 0.3007           | 8470.7654         | 1.0749         | Lower performance; less compact clusters and poorer separation |
| Clustering                          | **NMF + Agglomerative**   | –        | –        | 0.2364           | 7186.5672         | 1.5570         | Weakest clustering results; high overlap and poor cohesion between clusters |

## Text Classification + Sentiment Analysis

- **CNN** outperformed all other models with the highest **accuracy (0.96)** and **macro F1-score (0.96)**. It demonstrated excellent precision and recall across all sentiment classes, especially for the Neutral class. *Random oversampling* was applied during training to address class imbalance.
- **Logistic Regression** showed strong and balanced performance (**accuracy = 0.91**, **macro F1 = 0.91**), though slightly weaker on the Neutral class (F1 = 0.88). To mitigate class imbalance, **SMOTE (Synthetic Minority Oversampling Technique)** was used.
- **BERT** performed particularly well for the Positive class (F1 = 0.94), but struggled with Neutral (F1 = 0.74). It had an overall **accuracy of 0.88**. To enhance training on limited data, **data augmentation** was applied during preprocessing.
- **VADER**, a lexicon-based method, yielded the weakest results with a **macro F1-score of 0.48**, heavily biased toward Positive sentiment and extremely poor at identifying Neutral (F1 = 0.01).

<hr>


## Clustering

- **LDA + KMeans** was the top performer among clustering models:
  - **Silhouette Score**: 0.4801 (indicating well-separated clusters),
  - **Calinski-Harabasz Index**: 18007.63 (suggesting compact and distinct clusters),
  - **Davies-Bouldin Index**: 0.7151 (lower is better, showing strong performance).
- **LDA + Agglomerative** was the next best, with reasonably good clustering structure but slightly lower quality than KMeans.
- **NMF-based approaches** underperformed across all metrics:
  - Less compact clusters (lower Calinski-Harabasz),
  - More overlapping (higher Davies-Bouldin),
  - Poorer cohesion and separation (Silhouette Score as low as 0.2364 for NMF + Agglomerative).

<hr>
