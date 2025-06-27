# HR-Analytics-Dashboard-Power-Query-Excel
This project presents a comprehensive HR analytics dashboard built with Excel, leveraging Power Query for data cleaning and preparation. The dashboard integrates three key datasets—Employee Data, Employee Engagement Survey, and Training Data—along with a visual dashboard and key insights
## Data Sources & Structure

### 1. `employee_data`
- **Columns:**  
  `EmpID`, `FirstName`, `LastName`, `StartDate`, `Title`, `Supervisor`, `EmployeeType`, `TerminationType`, `DepartmentType`, `Division`, `DOB`, `State`, `JobFunctionDescription`, `GenderCode`, `MaritalDesc`, `Performance Score`, `Current Employee Rating`, `age`, `Age Group`

### 2. `survey_data`
- **Columns:**  
  `Employee ID`, `Survey Date`, `Engagement Score2`, `Satisfaction Score2`, `Work-Life Balance Score`

### 3. `training_data`
- **Columns:**  
  `Employee ID`, `Training Date`, `Training Program Name`, `Training Type`, `Training Outcome`, `Location`, `Trainer`, `Training Duration(Days)`, `Training Cost2`

### 4. `dashboard`
- Contains KPIs, summary tables, pivot charts, and slicers for interactive analysis.

---

## Data Preparation Steps (Power Query)

- **Raw Data Downloaded:** All three sheets imported as raw data.
- **Cleaning & Standardization:**
  - Trimmed whitespace and standardized column formats.
  - Formatted all dates to a consistent structure.
  - Checked for and confirmed absence of null values or duplicates.
  - Capitalized text fields for consistency (e.g., names, departments).
- **All data transformations were performed in Power Query before analysis.**

---

## Dashboard Components

### KPIs
- **Employee Count**
- **Average Satisfaction Level**
- **Average Work-Life Balance**
- **Average Engagement Score**
- **Average Training Cost**

### Summary Table
- **Male/Female Count:**  
  Using formulas like `=COUNTIF(employee_data[GenderCode],"female")`

### Pivot Charts
1. **Pie Chart:** Employee count by Age Group.
2. **Bar Chart:** Employee count by Department Type.
3. **Bar Chart:** Employee count by Termination Type.
4. **Bar Chart:** Training Results (Employee count by Training Outcome).

### Slicers
- Marital Status (`MaritalDesc`)
- Performance Score
- Employee Type
- Training Type
- Gender Code

---

## Key Insights & Formulas

### Resignation Analysis
- **% of Employees Resigned with 5 Work-Life Balance:**  
  `=COUNTIF(employee_engagement_survey_data__2[Work-Life Balance Score],5)/3000`
- **% Resigned with 5 Engagement Score:**  
  Similar formula as above, using `Engagement Score2`.
- **% Resigned with 5 Satisfaction Score:**  
  Similar formula as above, using `Satisfaction Score2`.

### Training Cost Analysis
- **Total Cost for Completed/Incomplete/Failed Training:**  
  `=SUMIF(training_and_development_data[Training Outcome], "Completed", training_and_development_data[Training Cost2])`

### Employee Training Cost Extremes
- **Employee with Highest Training Cost:**
  ```excel
  =LET(
    maxCost, MAX(training_data!I2:I3001),
    empID, XLOOKUP(maxCost, training_data!I2:I3001, training_data!A2:A3001),
    firstName, XLOOKUP(empID, employee_data!A2:A3001, employee_data!B2:B3001),
    lastName, XLOOKUP(empID, employee_data!A2:A3001, employee_data!C2:C3001),
    firstName & " " & lastName
  )
  ```
- **Employee with Lowest Training Cost:**  
  (Similar formula using `MIN`.)

---

## How to Use

1. **Open `employee_data`, `survey_data`, and `training_data` sheets to view raw and cleaned data.**
2. **Navigate to the `dashboard` sheet for KPIs, charts, and slicers.**
3. **Review the `key insights` sheet for calculated analytical insights and formulas.**

---

## Tools Used

- **Power Query:** Data cleaning, standardization, and transformation.
- **Excel:** Formulas, pivot charts, dashboards, slicers, and summary analysis.

---

## Notes

- All data preparation is reproducible in Power Query.
- All insights are calculated with standard Excel formulas for transparency.

---

Feel free to reach out if you have questions or suggestions!
