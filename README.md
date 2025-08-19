# Healthcare Expense Allocation & Analysis using Python

## Project Overview
This project demonstrates how to transform transactional healthcare data into **analytical insights** by merging **expense** and **visit** datasets.  
The analysis focuses on:
- Calculating **expense per patient visit**
- Determining **average expense per health centre** (e.g., hospitals, long-term care, community services)
- **Health centre** is the department or the unit in the organization.

This type of analysis is crucial for **healthcare financial management**, enabling better:
- Budget allocation
- Resource planning
- Performance monitoring across institutions  

---

## 🗂️ Data Sources 
- **Expenses Dataset**([path/to/datasets ](https://github.com/analystmohitshah/healthcare-expense-analysis/blob/main/datasets/expenses.csv)) → Contains total healthcare expenses per organization and health centre (department).  
- **Visits Dataset** (path/to/datasets) → Contains the number of patient visits per organization and health centre (department).  

Both datasets share the keys:
- `organization_id` → unique identifier for each healthcare organization  
- `functional_centre_number` → unique identifier for each health centre  

---

## 🔑 Key Steps

1. **Merge Datasets**  
   - Join `expenses` and `visits` on `organization_id` and `functional_centre_number`.  
   - Retain attributes: `organization_id`, `functional_centre_number`, `functional_centre_name`, `expenses`, and `visits`.  

2. **Calculate Expense Per Visit**  
   ```python
merged_df['expense_per_visit'] = merged_df.apply(
    lambda row: row['expenses'] / row['visits'] if row['visits'] > 0 else 0,
    axis=1
).round(2)```

3. **Compute Average Expense Per health Centre**
- Group by `health_centre_number`, `health_centre_name`  
- Calculate the **mean expense per visit** for each centre  
- Store results in a summary table  

---

## Example Output

### Final Merged Table (sample)
| organization_id | health_centre_number | health_centre_name             | expenses | visits  | expense_per_visit |
|-----------------|----------------------|--------------------------------|----------|---------|-------------------|
|   1             | 82                   | Mental Health Specialty Clinic | 500000.0 | 0.0     | 0.0               |
|   2             | 10                   | Medical Specialty Clinic       | 500000.0 | 10909.0 | 275.0             |



### Average Expense per health Centre
| health_centre_number | health_centre_name | average_expense_per_visit |
|----------------------|---------------------------|--------------------|
| 10                   | Medical Specialty Clinic  | 251.25             |
| 50                   | Diabetes Specialty Clinic | 480                |

---

## 📊 Visualization
**Matplotlib Bar Chat** for comparision on Function Unit (Health Centre)
![barchart](https://github.com/user-attachments/assets/7fdacf23-16cd-4cfd-ae1f-a1087a8cead4)

**Seaborn Boxplot** to compare distributions of expenses per visit across healthcare centres:  
![boxplot](https://github.com/user-attachments/assets/9351bef3-6251-4c70-a63d-a66df6019d2d)

---
# Interpretation:

Hospitals show higher variability in expenses per visit.

Long-term care centres demonstrate more consistency in cost per visit.

Outliers suggest potential inefficiencies or special cases (e.g., specialized treatments).

---
## 🛠️ Tech Stack

**Python** (Pandas, NumPy)

**Jupyter** Notebook (for data cleaning & analysis)

**Visualization** (Matplotlib, Seaborn )

---

## How to Run

Clone the repository:

git clone https://github.com/yourusername/healthcare-expense-analysis.git
cd healthcare-expense-analysis


Install dependencies:

pip install -r requirements.txt


Run the notebook:

jupyter notebook healthcare_expense_analysis.ipynb

---
## Skills Demonstrated

- Data Cleaning & Preparation

- Data Merging & Joining in Pandas

- Feature Engineering (Derived Metrics)

- Aggregation & Grouped Analysis

- Healthcare Financial Analytics Use Case

---

## Future Improvements

- Add more advanced visualizations (bar charts, heatmaps).

- Implement KNN imputation for missing visit counts instead of defaulting to 0.

- Extend analysis to cover regional expense allocations across healthcare authoritie

---

👤 Author: Mohit Shah
[GitHub](https://github.com/analystmohitshah)
[LinkedIn](https://www.linkedin.com/in/analystmohitshah/)

