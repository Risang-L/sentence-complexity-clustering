# Sentence Complexity Clustering on L2 Texts

This project explores unsupervised clustering of L2-written sentences based on syntactic and lexical complexity features.  
The goal is to discover sentence-level writing patterns across proficiency levels using clustering and visualization techniques.

---

## Project Motivation

This work was developed as part of a personal NLP research portfolio to showcase data preprocessing, feature engineering, and unsupervised learning skills on real-world L2 language data.  
The project builds on previous research into syntactic complexity in second language writing.

---

## Methodology

The pipeline includes:
1. **Data Cleaning & Sentence Splitting**  
2. **Feature Engineering**  
   - Sentence length
   - Type-Token Ratio (TTR)
   - POS ratios (noun, verb, adjective)
   - Syntactic depth (dependency distance)
3. **Feature Correlation Analysis**
4. **Dimensionality Reduction**
   - PCA
   - t-SNE (for visualization)
5. **Clustering**
   - KMeans clustering of sentence features
6. **Interpretation**
   - Example sentences + feature averages per cluster

All steps were implemented manually in Python without external linguistic toolkits (like TAASSC) to demonstrate full control over feature engineering.

---

## Data

This project uses all 5600 samples in Written Essays (WE) from the [ICNALE corpus](https://language.sakura.ne.jp/icnale/), a publicly available collection of English essays written by second language users.  

**Note:**  
The ICNALE dataset is **not included** in this repository due to licensing restrictions.  
To reproduce the full pipeline, please request access and download the dataset from the official ICNALE website linked above.  
Once obtained, place the dataset files in `data/raw/` as described in `data/raw/README.md`.

---

## Results

Two main visualizations were created:
1. ![PCA Plot](outputs/figures/pca_plot.png)
The PCA plot shows the global structure of sentence complexity clusters across two principal components.  
A large distinct yellow cluster (Cluster 4) represents sentences that differ greatly (likely longer or more complex sentences), while a dense purple core (Cluster 0) suggests short or simple sentence structures.


2. ![t-SNE Plot](outputs/figures/tsne_plot.png)  
The t-SNE plot focuses on local structure and reveals tighter, well-separated neighborhood clusters.  
Distinct shapes and densities suggest subtle syntactic and lexical variation across learner sentence groups.

---
## Cluster Interpretation Method
The clusters were interpreted using a two-step process combining qualitative review and quantitative feature analysis.

First, a sample of sentences from each cluster was reviewed. This provided initial qualitative impressions of the sentence types based on length, grammatical structure, and writing style. Example observations included short, awkward beginner sentences (e.g., "I agree this statement.") and very long, complex argumentative sentences with hedging and multi-clause structures.

Second, sentence-level linguistic features were analyzed numerically across clusters. Key features included sentence length (num_tokens), type-token ratio (ttr), and part-of-speech ratios (noun_ratio, verb_ratio, adj_ratio). These values provided objective evidence to refine and validate the initial hypotheses.

Both methods consistently revealed five distinct sentence types:

Cluster 0: Short, simple sentences with high verb density; typical of beginner writers.

Cluster 1: Medium-length factual statements with dense noun phrases; often used for general explanations.

Cluster 2: Longer opinion sentences mixing simple and compound structures; associated with transitional learners.

Cluster 3: Short sentences with high adjective use; descriptive or comparative structures.

Cluster 4: Very long, complex argumentative sentences; characteristic of advanced L2 writers attempting native-like syntax.

The agreement between qualitative and quantitative approaches strongly suggests that sentence complexity features can meaningfully group learner writing styles without prior labels. This validates the effectiveness of the feature design and unsupervised clustering approach.

