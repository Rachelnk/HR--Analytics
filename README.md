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
        var nonworkdays = CALCULATE(COUNT('Final Data1'[Value]), 'Final Data1'[Value]          in { "HO", "WO"})
        RETURN totalDays-nonworkdays
  #### ii. % of sick leave
      * SL Count = SUM('Final Data1'[SL Count])
      * SL % = DIVIDE([SL Count],[Total Working Days], 0)
  #### iii. % of Employees Present (on-site) per Day 
      *Present Day = VAR Presentdays = CALCULATE(COUNT('Final Data1'[Value]), 'Final     Data1'[Value]="P")
         RETURN  Presentdays + [WFH Count]
      * Presence % = DIVIDE([Present Day], 'Measure Table'[Total Working Days], 0)
  - Step 3 : Create a chart with the target months, April, May, June .
  - Step 4 : Add three visual cards to show work from home(WFH), (in office)presence,sick leave(SL) percentages.
  - Step 5 : Add five tables showing:
    * Each employee's work from home, presence and sick leave percentages.
    * Each employee's daily attendance(from the month of April to June) whether they took a sick leave, worked from home or from the office.
    * Work from home, (work from office) Presence, Sick leave overall daily percentages. 
- Step 6 : Add three combo charts to show sick leave by date, work from home by date and presence by date.
  
### Dashboards
Click on the month chart to see the insights i.e. percentage of sick leave, work from home etc. 

             
![1000020673](https://github.com/user-attachments/assets/98dde122-8641-4660-a4f2-77768d68e3c7)


    
![1000020672](https://github.com/user-attachments/assets/f39bfac3-ea93-42c8-ac9f-1f1e989d6fd0)
