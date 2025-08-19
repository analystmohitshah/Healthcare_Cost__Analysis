# Healthcare Expense Allocation & Analysis

## Project Overview
This project demonstrates how to transform transactional healthcare data into **analytical insights** by merging **expense** and **visit** datasets.  
The analysis focuses on:
- Calculating **expense per patient visit**
- Determining **average expense per functional health centre** (e.g., hospitals, long-term care, community services)

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

1. **Merge Datasets**  
   - Join `expenses` and `visits` on `organization_id` and `functional_centre_number`.  
   - Retain attributes: `organization_id`, `functional_centre_number`, `functional_centre_name`, `expenses`, and `visits`.  

2. **Calculate Expense Per Visit**  
   ```python
   merged_df["expense_per_visit"] = merged_df.apply(
       lambda row: row["expenses"]/row["visits"] if row["visits"] > 0 else 0, axis=1
   )s.

3. **Compute Average Expense Per health Centre**
- Group by `health_centre_number`, `health_centre_name`  
- Calculate the **mean expense per visit** for each centre  
- Store results in a summary table  

---

## Example Output

### Final Merged Table (sample)
| organization_id | functional_centre_number | functional_centre_name | expenses | visits | expense_per_visit |
|-----------------|---------------------------|-------------------------|----------|--------|-------------------|
| 101             | 5001                      | General Hospital        | 200000   | 400    | 500               |
| 102             | 5002                      | Long-term Care          | 150000   | 300    | 500               |

### Average Expense per Functional Centre
| functional_centre_number | functional_centre_name | average_expense_per_visit |
|---------------------------|-------------------------|----------------------------|
| 5001                      | General Hospital        | 520                        |
| 5002                      | Long-term Care          | 480                        |

---

## 📊 Visualization
**Matplotlib Bar Chat** for comparision on Function Unit (Health Centre)
**Seaborn Boxplot** to compare distributions of expenses per visit across healthcare centres:  

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

Data Cleaning & Preparation

Data Merging & Joining in Pandas

Feature Engineering (Derived Metrics)

Aggregation & Grouped Analysis

Healthcare Financial Analytics Use Case

---

## Future Improvements

Add more advanced visualizations (bar charts, heatmaps).

Implement KNN imputation for missing visit counts instead of defaulting to 0.

Extend analysis to cover regional expense allocations across healthcare authoritie

---

👤 Author: Mohit Shah
📍 Ottawa, Canada
🔗 LinkedIn

