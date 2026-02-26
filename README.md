# 🎓 Student Performance Data Cleaning Project

This project focuses on structured **data preprocessing and cleaning** of a student performance dataset using Python and Pandas. The objective is to transform raw academic data into a clean, consistent, and analysis-ready dataset.

---

## 📁 Project Structure

├── main.ipynb  
├── student_performance_prediction.csv  
├── cleaned_student_performance.csv  
└── README.md  

- `main.ipynb` → Contains the complete data cleaning workflow  
- `student_performance_prediction.csv` → Raw dataset (input)  
- `cleaned_student_performance.csv` → Final cleaned dataset (output)  

---

## 📌 Project Objective

The notebook performs systematic data preprocessing steps including:

- 📥 Loading raw CSV data  
- 🔎 Inspecting dataset structure and data types  
- ❌ Handling invalid values  
- 🧹 Treating missing data  
- 🔁 Removing duplicate records  
- 💾 Exporting the cleaned dataset  

This ensures the dataset becomes reliable and ready for further analysis or machine learning tasks.

---

## 🛠️ Technologies Used

- 🐍 Python 3.x  
- 📓 Jupyter Notebook  
- 🐼 Pandas  
- 📦 NumPy  

---

## 🔍 Complete Data Cleaning Workflow (Code Overview)

```python
import pandas as pd
import numpy as np

# Load dataset
df = pd.read_csv("student_performance_prediction.csv")

# Basic inspection
print(df.info())
print(df.shape)
print(df.describe())
print(df.isnull().sum())

# Handle invalid values
df.loc[df["Study Hours per Week"] < 0, "Study Hours per Week"] = np.nan
df.loc[(df["Attendance Rate"] < 0) | (df["Attendance Rate"] > 100), "Attendance Rate"] = np.nan
df.loc[(df["Previous Grades"] < 0) | (df["Previous Grades"] > 100), "Previous Grades"] = np.nan

# Fill missing values
for col in df.select_dtypes(include=np.number).columns:
    df[col] = df[col].fillna(df[col].median())

for col in df.select_dtypes(include="object").columns:
    df[col] = df[col].fillna(df[col].mode()[0])

# Remove duplicates
df = df.drop_duplicates()

# Save cleaned dataset
df.to_csv("cleaned_student_performance.csv", index=False)

print("Data cleaning completed successfully ✅")
```

---

## 🎯 Key Highlights

✔ Structured preprocessing workflow  
✔ Logical validation of academic metrics  
✔ Median-based numerical imputation  
✔ Mode-based categorical imputation  
✔ Duplicate removal for data integrity  
✔ Export-ready cleaned dataset  

---

## 🚀 Future Improvements

- Add Exploratory Data Analysis (EDA)  
- Implement Machine Learning model  
- Perform Feature Engineering  
- Deploy as a mini ML project  

---

## 👨‍💻 Author

**Jatin Vishwakarma**  
Aspiring Data Scientist | Python Developer  

---

⭐ If you found this project helpful, consider giving it a star!