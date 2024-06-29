# HR-Data-Analysis-Project

<div style="text-align: center;">
  <img src="https://github.com/Gimhana123/HR-Data-Analysis-Project/blob/main/Screenshot%20(1062).png?raw=true">
</div>
<br><br>
This repository contains the code and resources for a comprehensive HR data analysis project. The project involves data analysis and cleaning using MySQL and the development of various SQL queries to answer key questions related to employee demographics and metrics.

## Features

- **Gender Breakdown**: Analyze the gender distribution of employees in the company.
- **Race/Ethnicity Breakdown**: Determine the racial/ethnic composition of the workforce.
- **Age Distribution**: Understand the age distribution of employees.
- **Work Location Analysis**: Compare the number of employees working at headquarters versus remote locations.
- **Employment Duration**: Calculate the average length of employment for terminated employees.
- **Gender Distribution Across Departments**: Examine how gender distribution varies across different departments and job titles.
- **Job Title Distribution**: Analyze the distribution of various job titles across the company.
- **Turnover Rate**: Identify the department with the highest turnover rate.
- **Geographic Distribution**: Determine the distribution of employees across various locations by city and state.
- **Employee Count Over Time**: Track changes in the company's employee count over time based on hire and termination dates.
- **Tenure Distribution**: Analyze the tenure distribution for each department.

## Data Processing

- **Data Cleaning**: Performed extensive data cleaning using MySQL to ensure data quality and consistency.
- **Data Analysis**: Analyzed the cleaned data in MySQL to derive key metrics and insights.

## SQL Queries

1. **Gender Breakdown of Employees**
    ```sql
    SELECT gender, COUNT(*) AS count
    FROM employees
    GROUP BY gender;
    ```

2. **Race/Ethnicity Breakdown of Employees**
    ```sql
    SELECT race_ethnicity, COUNT(*) AS count
    FROM employees
    GROUP BY race_ethnicity;
    ```

3. **Age Distribution of Employees**
    ```sql
    SELECT age, COUNT(*) AS count
    FROM employees
    GROUP BY age
    ORDER BY age;
    ```

4. **Employees at Headquarters vs Remote Locations**
    ```sql
    SELECT location, COUNT(*) AS count
    FROM employees
    GROUP BY location;
    ```

5. **Average Length of Employment for Terminated Employees**
    ```sql
    SELECT AVG(DATEDIFF(termination_date, hire_date)) AS avg_length
    FROM employees
    WHERE termination_date IS NOT NULL;
    ```

6. **Gender Distribution Across Departments and Job Titles**
    ```sql
    SELECT department, job_title, gender, COUNT(*) AS count
    FROM employees
    GROUP BY department, job_title, gender
    ORDER BY department, job_title, gender;
    ```

7. **Distribution of Job Titles**
    ```sql
    SELECT job_title, COUNT(*) AS count
    FROM employees
    GROUP BY job_title
    ORDER BY count DESC;
    ```

8. **Department with the Highest Turnover Rate**
    ```sql
    SELECT department, COUNT(*) AS terminations
    FROM employees
    WHERE termination_date IS NOT NULL
    GROUP BY department
    ORDER BY terminations DESC
    LIMIT 1;
    ```

9. **Distribution of Employees Across Locations by City and State**
    ```sql
    SELECT city, state, COUNT(*) AS count
    FROM employees
    GROUP BY city, state
    ORDER BY state, city;
    ```

10. **Company's Employee Count Over Time**
    ```sql
    SELECT YEAR(hire_date) AS year, COUNT(*) AS hires
    FROM employees
    GROUP BY YEAR(hire_date)
    UNION ALL
    SELECT YEAR(termination_date) AS year, -COUNT(*) AS terminations
    FROM employees
    WHERE termination_date IS NOT NULL
    GROUP BY YEAR(termination_date)
    ORDER BY year;
    ```

11. **Tenure Distribution for Each Department**
    ```sql
    SELECT department, DATEDIFF(CURDATE(), hire_date) AS tenure, COUNT(*) AS count
    FROM employees
    GROUP BY department, tenure
    ORDER BY department;


    ## Conclusion

### Summary of Findings
- **Employee Demographics**: The analysis revealed a predominantly [male/female] workforce composition with [percentage]% male and [percentage]% female employees. The racial/ethnic breakdown indicated [insights]. Age distribution highlighted [trends].
  
- **Operational Insights**: Location analysis showed [insights]. The average employment duration for terminated employees was [average length], suggesting [implications]. Departments like [department name] exhibited the highest turnover rate at [rate]%.

- **Organizational Structure**: Job title distribution indicated [observations]. Geographic distribution across [cities/states] revealed [patterns].

### Recommendations
- **Diversity and Inclusion**: Implement initiatives to enhance gender and racial diversity based on the demographic insights.
- **Retention Strategies**: Develop targeted plans for departments with high turnover rates to improve employee retention.
- **Operational Efficiency**: Optimize workforce distribution based on location insights to enhance operational efficiency and support remote work policies.
- **Career Development**: Align job title distribution with career growth opportunities to foster employee engagement and satisfaction.


This comprehensive analysis provides valuable insights into our workforce demographics, operational efficiencies, and organizational structure. By implementing these recommendations and exploring future directions, we aim to strengthen our workforce strategies and support organizational growth.

