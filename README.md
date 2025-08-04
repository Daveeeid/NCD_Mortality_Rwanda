# NCD Mortality in Rwanda (2000–2021) – Capstone Project  
**NAMES:** Muhirwa David  
**ID:** 27436  
**AUCA**  

## Introduction

This project presents a detailed data analytics capstone study on Non-Communicable Disease (NCD) mortality trends in Rwanda between 2000 and 2021. The analysis uses clustering and visualization techniques to derive insights that support public health planning.

## 📊 Overview

Non-communicable diseases (NCDs) like cardiovascular conditions, cancer, and diabetes are leading causes of death worldwide. In Rwanda, this burden is rising. This project investigates:

- The trend of NCD mortality rates over time

- Differences by gender

- Risk segmentation using clustering (KMeans)

- Interactive dashboards for insight delivery using Power BI

## 📂 Dataset

**Source**: WHO Global Health ObservatoryOriginal Format: Kaggle ZIP ("WHO Non-communicable diseases")Filtered Dataset: rwanda_ncd_clustered.csv

Variables Included:  
| Column | Description |
|---|---|
| Year | Calendar year from 2000 to 2021. |
| FEMALE | Female NCD mortality rate (%). |
| MALE | Male NCD mortality rate (%). |
| TOTAL | Average of male and female mortality (%). |
| Cluster | Numeric cluster label from KMeans (0 = high risk). |
| Phase | Descriptive phase: High Risk, Transition, Low Risk. |

## 🔧 Tools & Technologies Used

- Python (Pandas, Matplotlib, Scikit-learn)

- Jupyter Notebook for preprocessing and modeling

- Power BI for interactive dashboard creation

- KMeans Clustering for phase segmentation

## 🧐 Methodology

**1. Sata Loading**  
![](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/data%20loading.jpg?raw=true)  
I started by loading the original dataset RELAY_WHS.csv, which contains non-communicable disease (NCD) mortality rates from the World Health Survey. Using pandas.read_csv(), we read the file into a DataFrame and preview its first few rows to understand the structure and column contents. This step helps identify which rows/columns are relevant for filtering Rwanda-specific data.

**2. Data Cleaning (Python)**

- Removed missing values and standard formatting errors

- Calculated TOTAL column as an average of FEMALE and MALE

![](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/drop.jpg?raw=true)
The .dropna() function removed any rows (years) where male or female mortality data was missing — a basic but effective data cleaning step.  
![](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/total.jpg?raw=true)  
This line created a new TOTAL column by averaging the FEMALE and MALE mortality rates — which is essential for later clustering and analysis.

**3. Exploratory Data Analysis**
- Generated summary statistics

- Visualized gender-wise and total mortality trends over time

![image alt](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/descriptive%20stats.jpg?raw=true)  
This block computes summary statistics (count, mean, min, max, std, etc.) of NCD mortality rates for both male and female groups individually using groupby(). It also generates overall descriptive statistics for the entire dataset, regardless of gender.

**These values help assess:**  

   Central tendency (mean, median)

   Spread (standard deviation, range)

   Differences in NCD mortality between males and females

This step sets the foundation for visualizing disparities and selecting appropriate clustering features.



**4. Machine Learning (Clustering)**

- Applied KMeans clustering (k=3)

- Clustered years into three groups based on TOTAL

- Named clusters: High Risk, Transition, Low Risk

![image alt](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/pivot.jpg?raw=true)  
This section applies KMeans clustering to segment Rwanda’s yearly NCD mortality rates into 3 meaningful risk phases:

1. Pivoting: Data is reshaped so each row is a year, with separate columns for male and female mortality.

2. Standardization: Values are scaled to ensure fair clustering regardless of original magnitude.

3. Clustering: Using KMeans (with k=3), we identify clusters representing High Risk, Transition, and Low Risk periods.

4. Silhouette Score: A metric to evaluate how well the data is clustered. Values closer to 1 indicate better-defined clusters.

This model-driven phase categorization enhances the depth and reliability of the final Power BI dashboard.

**5. Dashboard Design (Power BI)**

- Imported cleaned CSV

- Created line chart, bar chart, KPI cards, raw data table

- Added slicers for Phase and Year to enable interactivity

![image alt](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/dashboard.jpg?raw=true)

### 📊 Results & Insights  
| Phase | Years | Avg TOTAL (%) |
|---|---|---|
| High Risk | 2000-2001 | ~36.6% |
| Transition | 2002–2004 | ~29.8% |
| Low Risk | 2005–2021 | ~23.6% |

**Key Observations:**

- Male mortality consistently higher than female

- Major improvements occurred during 2002–2004 (transition period)

- Overall 14% drop in total NCD mortality over 21 years

![imag alt](https://github.com/Daveeeid/NCD_Mortality_Rwanda/blob/main/categories.jpg?raw=true)

## 📊 Power BI Dashboard Features

KPI Cards for Female, Male, and Total average rates

Line Chart: Gender-wise trends over time

Bar Chart: Avg mortality by risk phase

Table: Raw data view with conditional formatting

Slicers: Dynamic filters for Year and Phase

📷 Power BI Screenshot: Full dashboard overview with interactivity

## 🤖 Future Enhancements

- Expand the analysis to East African region (Kenya, Uganda)
- Integrate policy events and funding data to explain shifts
- Use time series models for forecasting future NCD rates
- Analyze additional indicators (e.g., blood pressure, obesity, smoking)



