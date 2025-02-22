# 📊 Heart Disease Analysis Dashboard – Power BI

## 📌 Overview
This Power BI dashboard provides an in-depth analysis of **heart disease risk factors**, including age, blood pressure, cholesterol levels, smoking habits, exercise patterns, and other health indicators. The dataset is used to create **interactive visualizations and key insights** to help medical professionals and data analysts understand trends in heart disease.

## 🚀 Features
- **📈 KPI Cards**: Display crucial metrics like heart disease prevalence, smoking percentage, and average sleep hours.
- **📊 Visualizations**: Interactive charts showing relationships between health indicators and heart disease.
- **⚙ DAX Calculations**: Custom DAX measures for percentage calculations, age group segmentation, and sleep analysis.
- **🔍 Filters & Slicers**: Heart disease status, age groups, smoking, and stress level filters for data-driven insights.


## 📊 Dashboard Pages
### **📌 Page 1: Summary Dashboard**
- **KPI Cards**: Heart Disease % | Avg Sleep Hours | Smoking % | Alcohol % | Avg Cholesterol  
- **Visuals**:
  - Heart Disease Count by Age Group
  - Smoking & Alcohol Consumption vs. Heart Disease (Stacked Column Chart)
  - Stress Level vs. Heart Disease (Bar Chart)
  - Exercise Habits & Heart Disease (Clustered Bar Chart)
  - Sleep Hours vs. Heart Disease (Gauge Chart)
![1](https://github.com/user-attachments/assets/87137604-38d1-46d9-849c-54845f6d796d)

### **📌 Page 2: Age, Gender & Heart Disease**
- Heatmap showing age distribution and heart disease occurrence.
- Gender-wise heart disease prevalence.
![2](https://github.com/user-attachments/assets/6da1000d-3851-4795-8284-8fe7430e69ed)

### **📌 Page 3: Smoking, Alcohol & Heart Disease**
- Stacked column chart: Smoking & Alcohol impact on heart disease.
- Bar chart showing smoking trends by age.
![3](https://github.com/user-attachments/assets/6f3f4a55-4d28-493a-82b4-f59b5129a3ec)

### **📌 Page 4: Sleep, Stress & Heart Disease**
- Gauge Chart: Avg Sleep Hours of heart disease patients.
- Stress Level vs. Heart Disease (Stacked Column Chart).
- Sugar Consumption & Heart Disease.
![4](https://github.com/user-attachments/assets/21772c50-26c0-4340-bf73-6b6d0337dd9b)

### **📌 Page 5: Blood Pressure, Cholesterol & Heart Disease**
- Scatter plot: Cholesterol vs. Heart Disease.
- Blood Pressure Distribution among heart disease patients.
![5](https://github.com/user-attachments/assets/31437a47-52b9-4723-971a-8bdbd46c7f47)

## ⚙ **DAX Measures**
### **1️⃣ Age Group Classification**
```DAX
Age Group = 
SWITCH(
    TRUE(),
    'heart_disease'[Age] >= 18 && 'heart_disease'[Age] <= 30, "18-30 (Young Adults)",
    'heart_disease'[Age] >= 31 && 'heart_disease'[Age] <= 45, "31-45 (Middle-Aged)",
    'heart_disease'[Age] >= 46 && 'heart_disease'[Age] <= 60, "46-60 (Older Adults)",
    'heart_disease'[Age] >= 61 && 'heart_disease'[Age] <= 80, "61-80 (Seniors)"
)
% of Smokers = 
IF([Total Individuals] = BLANK(), BLANK(),
IF([No of Smokers] = BLANK(), BLANK(),
DIVIDE([No of Smokers], [Total Individuals])))

Avg Sleep Hours (Heart Disease) = 
CALCULATE(AVERAGE('heart_disease'[Sleep Hours]), 
    'heart_disease'[Heart Disease Status] = "Yes")
