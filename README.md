# Lab 2: Country Schools: Anomaly Detection and Cluster Analysis

## Lab Description
This lab explores basic data preprocessing, anomaly detection, and cluster analysis using the Country Schools dataset. The aim is to identify unusual records and group counties according to their school installation patterns.

## Dataset
The dataset contains information about the number of schools, installed and pending schools, installation percentages, and installed LDDs and TDDs.

- **Original dataset:** 50 records and 8 columns
- **After preprocessing:** 48 records and 8 columns
- **Features used for analysis:** 6 numerical columns
- **Clustering records:** 47 counties, excluding the aggregate `TOTAL` record

## Methodology

### 1. Data Preprocessing
The dataset was inspected to understand its structure, data types, missing values, and duplicate records. Rows containing missing values were removed, and the `PercentageInstalled` column was converted to a numerical format. Identifier columns were excluded from the analysis, and the selected numerical features were standardized to support the machine learning experiments.

### 2. Anomaly Detection
Isolation Forest was used to identify records with unusual combinations of school installation features. The results were examined to distinguish potential anomalies from the other records.

### 3. Cluster Analysis
K-Means clustering was used to group counties into three clusters based on six numerical features. The clusters were compared using their average school totals, installation figures, pending schools, and installation percentages.

## Results and Interpretation

### Anomaly Detection
The Isolation Forest model identified **7 potential anomalies** and **41 normal records** among the 48 records analyzed. Some flagged records had particularly low installation rates or many pending schools, while others showed unusually high installation figures.

These results highlight records that may deserve further investigation. However, an anomaly is not necessarily a data error, and the results should be interpreted in the context of the original data.

### Cluster Analysis
The K-Means model grouped the 47 counties into three clusters:

| Cluster | Counties | Average Installation | General Pattern |
|---|---:|---:|---|
| Cluster 0 | 16 | 72.69% | Larger school systems with substantial installation progress |
| Cluster 1 | 17 | 80.36% | Higher completion rates and fewer pending schools |
| Cluster 2 | 14 | 33.92% | Lower installation progress and more pending schools relative to installed schools |

Cluster 1 had the highest average installation rate, while Cluster 2 had the lowest. The cluster labels are identifiers, not rankings; the groups are interpreted using their average feature values.

## Conclusion
This lab applied data preprocessing, Isolation Forest, and K-Means to explore school installation patterns across counties. The anomaly detection experiment highlighted 7 potentially unusual records, while clustering revealed three groups with different installation characteristics. These findings provide a clearer picture of installation progress and areas that may require further investigation, although additional analysis would be needed to explain the reasons behind the observed differences.

## Tools and Libraries
- Python
- Pandas and NumPy
- Matplotlib
- Scikit-learn
- Kaggle Notebooks
