

# Product Category Clustering

Using a hybrid approach, where K-Means helps discover patterns, but the final categories are assigned using a combination of the cleaned product names and the primaryCategories column. 
This is much more robust and easier to explain in a report.

<br>

--- 

## Workflow


Raw Product Name
        │
        ▼
Text Cleaning
(lowercase, remove punctuation, stopwords, stemming/lemmatization)
        │
        ▼
106 Unique Clean Product Names
        │
        ├───────────────┐
        │               │
        ▼               ▼
TF-IDF Features    primaryCategories
        │               │
        ▼               │
K-Means Clustering       │
        │               │
        └──────┬────────┘
               ▼
Interpret clusters
               ▼
Rule-based mapping
               ▼
5 Final Meta-Categories


<br>

---

## Why use this hybrid approach?


| Method                   | Advantages                                                                         | Disadvantages                                          |
| ------------------------ | ---------------------------------------------------------------------------------- | ------------------------------------------------------ |
| TF-IDF + K-Means only    | Finds hidden patterns automatically                                                | Cluster labels are arbitrary and may vary between runs |
| Rule-based only          | Fully interpretable and reproducible                                               | Requires manual effort to define rules                 |
| **Hybrid (recommended)** | Leverages data-driven discovery while producing consistent, explainable categories | Requires a one-time review of clusters                 |


<br>

---


## Conclusion

Product categorization was performed using a hybrid methodology. First, TF-IDF vectorization and K-Means clustering were applied to the 106 unique cleaned product names to identify semantically similar groups. The resulting clusters were then interpreted and refined using the primaryCategories field, which, although incomplete, provided reliable category information where available. Finally, explicit rule-based mappings were created to assign each product to one of five business-oriented meta-categories. This approach combines the exploratory strengths of unsupervised learning with the consistency and interpretability of rule-based classification.

