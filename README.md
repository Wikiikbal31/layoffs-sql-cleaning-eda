# 🚀 layoffs-sql-cleaning-eda – Data Cleaning & EDA Project

Hi! I'm currently learning to become a **Data Analyst**, and this is one of the hands-on projects I worked on to apply what I've learned so far. I followed guidance from **Alex The Analyst’s** YouTube SQL tutorials and used MySQL to clean and explore a dataset about global tech layoffs.

This project helped me improve my understanding of real-world data problems: messy values, missing entries, inconsistent formatting—and how to deal with them using SQL.

---

## 🎯 Project Goals

- Practice **SQL for real-world data cleaning**
- Apply **window functions and CTEs**
- Explore patterns and insights from layoff trends
- Show my ability to turn messy data into meaningful information

---

## 📌 Skills Demonstrated

✅ Handling duplicates and null values  
✅ Standardizing inconsistent data (text, dates, etc.)  
✅ Creating clean, query-ready tables  
✅ Using `ROW_NUMBER()`, `DENSE_RANK()`, `GROUP BY`, and subqueries  
✅ Generating business-relevant insights (top companies, trends, timelines)

---

## 📁 Files in This Project

```
layoffs-sql-cleaning-eda/
├── data_cleaning_in_mysql.sql             # Data cleaning steps (raw → clean)
├── exploratory_data_analysis.sql          # SQL queries to explore key insights
└── README.md                              # Project overview and documentation
```

---

## 🧼 Data Cleaning (MySQL)

Here’s a summary of what I did in the cleaning phase:

- Removed duplicates using `ROW_NUMBER()` and CTEs
- Trimmed extra whitespace in company and country names
- Standardized values (e.g., 'United States.' → 'United States')
- Converted date strings into proper `DATE` format
- Deleted rows with incomplete key information

🔍 **Example logic**:
```sql
DELETE
FROM layoffs_staging2
WHERE total_laid_off IS NULL
AND percentage_laid_off IS NULL;
```

---

## 📊 Exploratory Data Analysis (EDA)

After cleaning, I explored the dataset to uncover trends:

- 📅 Total layoffs per month (including rolling totals)
- 🏢 Companies with the highest layoffs each year
- 💰 Layoffs by funding stage
- 🌎 Patterns across time, company, and region

📌 **Key EDA Snippet**:
```sql
WITH Company_Year AS (
  SELECT company, YEAR(date) AS year, SUM(total_laid_off) AS total_laid_off
  FROM layoffs_staging2
  GROUP BY company, year
),
Company_Year_Rank AS (
  SELECT *, DENSE_RANK() OVER (PARTITION BY year ORDER BY total_laid_off DESC) AS ranking
  FROM Company_Year
)
SELECT * FROM Company_Year_Rank WHERE ranking <= 5;
```

---

## 💡 What I Learned

This project gave me a stronger foundation in SQL. I realized that **data cleaning is just as important as analysis**, and that understanding the business context makes insights more meaningful.

I also got more confident writing **organized queries**, using **CTEs**, and thinking like a data analyst—not just coding, but asking “what does the data really say?”

---

## 👋 About Me

I’m currently building my skills to become a **junior data analyst**. I have a background in business and administration, and I'm actively learning SQL, Excel, Python, and visualization tools. This project is one of many in my self-learning journey.

---

## 📬 Contact

- 📧 Email: wikiikbal05@gmail.com  
- 💼 LinkedIn: https://www.linkedin.com/in/wikiikbal31  
- 🐱 GitHub: https://github.com/Wikiikbal31

Thanks for checking out my project!
