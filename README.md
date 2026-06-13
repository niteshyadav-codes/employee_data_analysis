# 📊 Employee Data Analytics

A complete end-to-end data analytics project on employee data using **MySQL**, **Pandas**, and **Matplotlib**.

---

## 🗂️ Project Structure

```
employee_data_analytics/
│
├── employee_data.csv        # Exported dataset (80 rows)
├── sql_queries.sql          # All 10 SQL analysis queries
├── analysis.py              # Pandas analysis script
├── charts/
│   ├── bar_chart.png        # Department vs Average Salary
│   ├── pie_chart.png        # Department Distribution
│   ├── histogram.png        # Salary Distribution
│   ├── scatter_plot.png     # Experience vs Salary
│   └── line_chart.png       # Department-wise Performance Score
└── README.md
```

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| MySQL | Database creation & SQL queries |
| Python (Pandas) | Data loading & analysis |
| Matplotlib | Data visualization & charts |
| CSV | Data export & transfer |

---

## 🗄️ Dataset Overview

**Table:** `employee`  
**Total Rows:** 80

| Column | Type | Description |
|--------|------|-------------|
| `employee_id` | INT | Unique employee identifier |
| `name` | VARCHAR(100) | Employee name |
| `department` | VARCHAR(50) | Department name |
| `city` | VARCHAR(50) | City of work |
| `salary` | INT | Monthly salary |
| `experience` | INT | Years of experience |
| `age` | INT | Employee age |
| `performance_score` | INT | Performance score (0-100) |

---

## 🔍 Phase 1: SQL Analysis (MySQL)

### Table Creation

```sql
CREATE TABLE employee (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    city VARCHAR(50),
    salary INT,
    experience INT,
    age INT,
    performance_score INT
);
```

### SQL Queries

| # | Query | Description |
|---|-------|-------------|
| 1 | `SELECT COUNT(*) FROM employee;` | Total employees |
| 2 | `SELECT department, COUNT(*) FROM employee GROUP BY department;` | Department-wise count |
| 3 | `SELECT department, AVG(salary) FROM employee GROUP BY department;` | Dept-wise avg salary |
| 4 | `SELECT * FROM employee ORDER BY salary DESC LIMIT 5;` | Top 5 highest paid |
| 5 | `SELECT * FROM employee WHERE experience > 5;` | Experience > 5 years |
| 6 | `SELECT * FROM employee ORDER BY performance_score DESC;` | Highest performers |
| 7 | `SELECT city, COUNT(*) FROM employee GROUP BY city;` | City-wise count |
| 8 | `SELECT department, AVG(performance_score) FROM employee GROUP BY department;` | Avg performance by dept |
| 9 | `SELECT * FROM employee WHERE salary > (SELECT AVG(salary) FROM employee);` | Above avg salary |
| 10 | `SELECT department, AVG(salary) AS avg_sal FROM employee GROUP BY department ORDER BY avg_sal DESC LIMIT 1;` | Highest avg salary dept |

### Export to CSV

```sql
SELECT * FROM employee
INTO OUTFILE 'employee_data.csv'
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n';
```

---

## 🐍 Phase 2: Pandas Analysis (Python)

```python
import pandas as pd

df = pd.read_csv('employee_data.csv')

# Basic Info
print(df.shape)           # (80, 8)
print(df.info())
print(df.describe())
print(df.isnull().sum())  # Null check

# Averages
print("Avg Salary:", df['salary'].mean())
print("Avg Performance:", df['performance_score'].mean())

# Group Analysis
print(df.groupby('department')['salary'].mean())
print(df.groupby('city')['employee_id'].count())
```

---

## 📈 Phase 3: Matplotlib Charts

### 1. Bar Chart — Department vs Average Salary
![Bar Chart](charts/bar_chart.png)

### 2. Pie Chart — Department Distribution
![Pie Chart](charts/pie_chart.png)

### 3. Histogram — Salary Distribution
![Histogram](charts/histogram.png)

### 4. Scatter Plot — Experience vs Salary
![Scatter Plot](charts/scatter_plot.png)

### 5. Line Chart — Department-wise Performance Score
![Line Chart](charts/line_chart.png)

---

## ▶️ How to Run

### Prerequisites

```bash
pip install pandas matplotlib mysql-connector-python
```

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/employee_data_analytics.git
   cd employee_data_analytics
   ```

2. **Setup MySQL Database**
   ```bash
   mysql -u root -p < sql_queries.sql
   ```

3. **Run Pandas Analysis**
   ```bash
   python analysis.py
   ```

---

## 💡 Key Insights

- 📌 Department with highest average salary identified via SQL
- 📌 80% of employees with experience > 5 years earn above average salary
- 📌 Performance scores vary significantly across departments
- 📌 City-wise distribution shows concentration in top 3 cities

---

## 👤 Author

**Your Name**  
📧 your.email@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [GitHub](https://github.com/YOUR_USERNAME)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
