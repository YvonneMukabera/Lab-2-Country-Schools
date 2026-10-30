# Lab 2: Country Schools Data Analysis

## Lab Description

This lab explores data preprocessing, anomaly detection, and cluster analysis using the Country Schools dataset. The aim is to identify unusual records and group counties according to their school installation patterns.

## Dataset

The dataset contains information about the total number of schools, installed and pending schools, installation percentages, and installed LDDs and TDDs.

- **Original dataset:** 50 records and 8 columns
- **After preprocessing:** 48 records and 8 columns
- **Features used for analysis:** 6 numerical columns
- **Records used for clustering:** 47 counties, excluding the aggregate `TOTAL` record

## Methodology

### 1. Data Inspection

The dataset was examined to understand its structure, numerical summaries, data types, and feature distributions. Histograms were used to explore the distribution of numerical columns.

### 2. Data Preprocessing

Missing values and duplicate records were checked. The dataset contained 14 missing values and no duplicate records. Rows with missing values were removed, leaving 48 complete records.

The `PercentageInstalled` column was converted from text to a numerical format by removing percentage signs. Six numerical features were selected for analysis, while identifier columns were excluded. StandardScaler was then used to standardize the selected features.

### 3. Anomaly Detection

Isolation Forest was applied to identify records with unusual combinations of school installation features. The results were examined using the detected anomaly labels and a scatter plot.

### 4. Cluster Analysis

K-Means was used to group the 47 individual counties based on the six standardized numerical features. The Elbow Method was used to examine different cluster numbers, and the final analysis used **8 clusters**.

A scatter plot was used to visualize the county groups, while cluster counts and average feature values helped describe their characteristics.

## Results and Interpretation

### Anomaly Detection

The Isolation Forest model identified **7 potential anomalies** and **41 normal records** among the 48 records analyzed.

The flagged records included counties with very low installation rates, counties with high installation figures, and the aggregate `TOTAL` record. These records have unusual combinations of features compared with the rest of the dataset and may deserve further investigation.

An anomaly does not necessarily represent an error in the data.

### Cluster Analysis

The K-Means model grouped the 47 counties into eight clusters:

| Cluster | Number of Counties | Average Installation |
|---|---:|---:|
| 0 | 9 | 53.32% |
| 1 | 8 | 83.58% |
| 2 | 2 | 63.27% |
| 3 | 2 | 95.42% |
| 4 | 6 | 53.51% |
| 5 | 6 | 13.08% |
| 6 | 7 | 80.49% |
| 7 | 7 | 82.19% |

The results show differences in school installation progress across the groups. Cluster 3 had the highest average installation percentage, while Cluster 5 had the lowest. Some clusters also had relatively high numbers of pending schools.

The cluster labels are identifiers rather than rankings. Their characteristics are understood by comparing the average values of the selected features.

## Conclusion

This lab applied data preprocessing, Isolation Forest, and K-Means to explore school installation patterns across counties. Anomaly detection highlighted records with unusual school statistics, while cluster analysis revealed groups of counties with different levels of installation progress. Overall, the findings provide a clearer picture of the differences between counties and help identify areas that may need more attention.

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Kaggle Notebooks
