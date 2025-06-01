# HR--Analytics
## Problem Statement
The HR manager would like to better understand the working preferences of employess of the company whether remote or on-site, on which day of the week do employees prefer to work either on-site or remotely, the percentage of employees working on-site on a given day of the week, this insight will help with capacity planning i.e. rental space to save on infrasructure. To understand what percentage of employees take a sick leave on a given day as this might be an indication of an outbreak, seasonal flu, this insight will aid in the improvement of sanitation infrastructure of the company.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is in Excel worksheets.
- Step 2: Extract and transform data by combining data from multiple worksheets in the same Excel worksheet using Power Query in Power BI.
- Step 3: Create metrics using DAX(Data Analysis Expressions).
   #### i. % of Work from Home          
      * WFH Count = SUM('Final Data1'[WFH Count])
      * WFH % = DIVIDE([WFH Count], [Present Day], 0)
      * Total Working Days = var totalDays = COUNT('Final Data1'[Value])
         var nonworkdays = CALCULATE(COUNT('Final Data1'[Value]), 'Final Data1'[Value] in { "HO",        "WO"})
         RETURN totalDays-nonworkdays
  #### ii. % of sick leave
      * SL Count = SUM('Final Data1'[SL Count])
      * SL % = DIVIDE([SL Count],[Total Working Days], 0)
  #### iii. % of Employees Present (on-site) per Day 
      *Present Day = VAR Presentdays = CALCULATE(COUNT('Final Data1'[Value]), 'Final     Data1'[Value]="P")
         RETURN  Presentdays + [WFH Count]
      * Presence % = DIVIDE([Present Day], 'Measure Table'[Total Working Days], 0)
    
