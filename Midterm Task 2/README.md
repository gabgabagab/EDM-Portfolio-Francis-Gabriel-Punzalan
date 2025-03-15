 Midterm Lab Task 2 – Data Cleaning and Transformation

 Step 1: Load Data into Power Query  
1. Download Uncleaned_DS_jobs.csv.  
2. Open Excel → `Data` → `Get Data` → `From File` → `From Text/CSV`.  
3. Click Load and open Power Query Editor.  
4. Duplicate the raw data (Right-click the query → `Duplicate`).  



 Step 2: Data Cleaning Tasks  

2.1 Clean Salary Estimate Column  
- Extract text before `(` using `Transform` → `Extract` → `Text Before Delimiter`.  

2.2 Create Min and Max Salary Columns  
- Select `Salary Estimate` → `Add Column` → `Column from Examples`.  
- Manually enter Min/Max Salary for the first row and let Power Query fill the rest.  
- Rename columns as Min Sal and Max Sal.  

2.3 Create Role Type Column  
- Add a Custom Column and use the formula to classify job roles:  
  ```powerquery
  if Text.Contains([Job Title], "Data Scientist") then "Data Scientist"
  else if Text.Contains([Job Title], "Data Analyst") then "Data Analyst"
  else if Text.Contains([Job Title], "Data Engineer") then "Data Engineer"
  else if Text.Contains([Job Title], "Machine Learning") then "Machine Learning Engineer"
  else "Other"
  ```
- Change data type to Text.  

2.4 Clean Location Column  
- Create a Custom Column to standardize locations (e.g., `"New Jersey" → ", NJ"`).  
- Split the column using `,` as a delimiter.  
- Rename Location Correction 2 to State Abbreviation.  
- Replace incorrect values (`Anne Rundell → MA`).  

2.5 Split Company Size Column  
- Select `Size` column → `Transform` → `Split Column by Delimiter` (`-`).  
- Rename new columns MinCompanySize and MaxCompanySize.  

2.6 Handle Negative Values  
- Filter out:  
  - `-1` in Competitors and Industry.  
  - `0` in Revenue.  

2.7 Clean Company Name  
- Remove ratings (numbers) after company names using `Replace Values`.  

2.8 Remove Unnecessary Columns  
- Delete Description column.  

2.9 Save Cleaning Steps  
- Go to Home → `Advanced Editor` → Copy the M Code for documentation.  



 Step 3: Reshape and Group the Data  

3.1 Create Salary by Role Type Table  
1. Duplicate raw data (`Right-click → Duplicate`).  
2. Rename as Sal By Role Type dup.  
3. Choose Columns: `Role Type`, `Min Sal`, `Max Sal`.  
4. Convert salary columns to currency and multiply by `1000`.  
5. Group By Role Type and calculate average Min/Max Salary.  

3.2 Create Salary by Company Size Table  
1. Create a reference (`Right-click → Reference`).  
2. Rename as Sal By Role Size ref.  
3. Choose Columns: `Size`, `Min Sal`, `Max Sal`.  
4. Convert salary columns to currency and multiply by `1000`.  
5. Group By Company Size and calculate average Min/Max Salary.  

3.3 Map State Names  
1. Load State Mapping table (`New Query → Open Workbook`).  
2. Merge State Abbreviation from `Uncleaned DS Jobs` with the mapping table.  
3. Rename merged column as State Full Name.  
4. Filter out null or blank values.  

3.4 Create Salary by State Table  
1. Create a reference (`Right-click → Reference`).  
2. Rename as Sal By State ref.  
3. Choose Columns: `State Full Name`, `Min Sal`, `Max Sal`.  
4. Convert salary columns to currency and multiply by `1000`.  
5. Group By State and calculate average Min/Max Salary.  



 Step 4: Verify Queries and Dependencies  
1. Go to View → Click `Query Dependencies`.  
2. Ensure the following queries exist:  
   - Sal By Role Type dup  
   - Sal By Size ref  
   - State Mapping  
   - Sal By State ref  
   - Uncleaned DS Jobs  



Final Insights You Can Generate:  
- Highest & Lowest Paying Roles → from `Sal By Role Type dup`.  
- Best Paying Company Sizes → from `Sal By Role Size ref`.  
- Best & Worst Paying States → from `Sal By State ref`.  

