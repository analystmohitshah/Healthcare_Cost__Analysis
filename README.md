# 📊 Healthcare Expense Allocation & Analysis

## 📌 Project Overview
This project demonstrates how to transform transactional healthcare data into **analytical insights** by merging **expense** and **visit** datasets.  
The analysis focuses on:
- Calculating **expense per patient visit**
- Determining **average expense per functional centre** (e.g., hospitals, long-term care, community services)

This type of analysis is crucial for **healthcare financial management**, enabling better:
- Budget allocation
- Resource planning
- Performance monitoring across institutions  

---

## 🗂️ Data Sources
- **Expenses Dataset** → Contains total healthcare expenses per organization and functional centre.  
- **Visits Dataset** → Contains the number of patient visits per organization and functional centre.  

Both datasets share the keys:
- `organization_id` → unique identifier for each healthcare organization  
- `functional_centre_number` → unique identifier for each functional centre  

---

## 🔑 Key Steps

### 1️⃣ Merge Datasets
- Join the **expenses** and **visits** tables on  
  `organization_id` + `functional_centre_number`  
- Retain key attributes:  
  `organization_id`, `functional_centre_number`, `functional_centre_name`, `expenses`, `visits`

### 2️⃣ Calculate Expense Per Visit
Create a derived column:  

\[
\text{expense\_per\_visit} = \frac{\text{expenses}}{\text{visits}}
\]

⚠️ If `visits = 0`, set `expense_per_visit = 0` to avoid division errors.

### 3️⃣ Compute Average Expense Per Functional Centre
- Group by `functional_centre_number`, `functional_centre_name`  
- Calculate the **mean expense per visit** for each centre  
- Store results in a summary table  

---

## 📈 Example Output

### 🔹 Final Merged Table (sample)
| organization_id | functional_centre_number | functional_centre_name | expenses | visits | expense_per_visit |
|-----------------|---------------------------|-------------------------|----------|--------|-------------------|
| 101             | 5001                      | General Hospital        | 200000   | 400    | 500               |
| 102             | 5002                      | Long-term Care          | 150000   | 300    | 500               |

### 🔹 Average Expense per Functional Centre
| functional_centre_number | functional_centre_name | average_expense_per_visit |
|---------------------------|-------------------------|----------------------------|
| 5001                      | General Hospital        | 520                        |
| 5002                      | Long-term Care          | 480                        |

---

## 📊 Visualization

Using **Seaborn Boxplot** to compare distributions of expenses per visit across healthcare centres:  

```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10,6))
sns.boxplot(
    data=merged_df,
    x='functional_centre_name',
    y='average_expense_per_visit'
)
plt.xticks(rotation=45)
plt.title("Expense per Visit Distribution by Functional Centre")
plt.show()

---
✅ Interpretation:

Hospitals show higher variability in expenses per visit.

Long-term care centres demonstrate more consistency in cost per visit.

Outliers suggest potential inefficiencies or special cases (e.g., specialized treatments).

---
🛠️ Tech Stack

Python (Pandas, NumPy)

Jupyter Notebook (for data cleaning & analysis)

Visualization: Matplotlib / Seaborn / Power BI

---

🚀 How to Run

Clone the repository:

git clone https://github.com/yourusername/healthcare-expense-analysis.git
cd healthcare-expense-analysis


Install dependencies:

pip install -r requirements.txt


Run the notebook:

jupyter notebook healthcare_expense_analysis.ipynb

---
## Skills Demonstrated ##

Data Cleaning & Preparation

Data Merging & Joining in Pandas

Feature Engineering (Derived Metrics)

Aggregation & Grouped Analysis

Healthcare Financial Analytics Use Case

---
📌 Future Improvements

Add more data visualizations (bar charts, heatmaps)

Implement KNN imputation for missing visit counts

Extend analysis to cover regional expense allocations across healthcare authorities

