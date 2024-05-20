# Data Analysis of HR data using Power BI

This project aims to analyze HR data using Power BI, transforming sample raw data from an Excel sheet into meaningful insights through data analysis and visualizations. The results of the analysis are documented for comprehensive understanding


## Common Power BI terms

Measure:
A measure is a dynamic calculation used to analyze and aggregate data. Measures are created using Data Analysis Expressions (DAX), a formula language for creating custom calculations in Power BI, Excel, and other data analysis tools. Measures are typically used to calculate sums, averages, minimum or maximum values, counts, or more complex calculations that can't be directly achieved with simple aggregation functions.
In other words a measure is basically a variable that we will be creating in order to create my own formulas and expressions according to requirements.

## All the measures used in this Data Analysis
  1. Headcount = countrows(staff)
  2. Average Salary = AVERAGE(staff[Salary])
  3. Minimum Salary = min(staff[Salary])
  4. Maximum Salary = MAX(staff[Salary])
  5. Cumulative Headcount = 
          VAR currentDate = LASTDATE(staff[Date of Join])
      RETURN
          CALCULATE([Headcount], ALL(staff[Date of Join]), staff[Date of Join]<=currentDate)
  6. Average Leave Balance = AVERAGE(staff[Leave Balance])
  7. LBL over 20 days = CALCULATE([Headcount], staff[Leave Balance]>20)


## The provided schema consists of the following fields, each containing specific information about employees:

1. Name: The name of the employee.
2. Emp ID: The unique identifier for the employee.
3. Gender: The gender of the employee.
4. Education Qualification: The educational qualification of the employee.
5. Date of Join: The date when the employee joined the organization.
6. Job Title: The job role or title of the employee.
7. Salary: The salary of the employee.
8. Age: The age of the employee.
9. Leave Balance: The remaining leave balance for the employee. 


## Types on Analysis, I will be performing on sample data :

1. How many people are in each job?
2. Gender Break down of the staff
3. Age spread of the staff
4. Which jobs pay more?
5. Top earner in each job
6. Qualification versus salary
7. Staff growth trend over time
8. Employees filter starting letter
9. Leave balance analysis
10. Quck HR dashboard


# HR DashBoard Overview

  ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/79d9a877-ed6d-4c1b-b5f7-6775ecb8bd90)


# Process

1.  First step is to load our HR data in to POWER BI
    ![1](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/1bbc5009-8eea-401c-8fd1-65e0ee4d69d8)


2. Transform the data according to our adjustment - changed the headers to first columns and names the table as staff from data
    ![2](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/ea6425a2-ff32-479e-9cf6-5941c77da1fe)

3.Performing analysis

1. How many people are in each job?
  create a headcount , Headcount = countrows(staff) 
  create a bar chart visualization with Job title on Y axis and Headcount on X axis
    ![3](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/c96c3d2e-b8f6-4eba-a7cd-2a6f7112e223)

through this visualization we can see Packagin associate has most number of staff and while marketing specialist has lowest

2. Gender breakdown Analysis
  according to pie chart we can see there are 73 males 43.34% and 88 females 54.66%
    ![4](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/99af2d9c-cafd-43d5-ac14-8050731e8b53)

    ![5](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/7f8e4459-d5c8-4d0c-9f0d-493eb9c9ebf2)

  adding slicer with job field in the title we can analyze how many males and females work in each department

3. Age spread Analysis

   -For analysis of age spread we will use column chart.
   -on X-axis i will put age
   -on y-axis i will headcount
   -create a age bin with 5 years age spread, for better visualization.
   -breaking it down in gender - putting gender in legend
   -according to analyzation of charts we can see there is 1 female in 2025 age categpry while most of the majority life between 35-45 with females 44 and male 41.
   -overall distribution of age between genders looks almost same but headcount of female is more

5. Which jobs Pay more

  To do this we have to create a new measure to calculate the average of all staff salaries.
  Average Salary = AVERAGE(staff[Salary])
  
  create a table with selecting job titles and average salary
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/cef72ccf-a462-4c5d-b9c4-54fdbe19f2a3)

  Through this table we can see that Product manager has the highest average salary $82,825 and Packagin Associate has the lowest average $33,409.
  But Average is not signicant because we cannot see the headcount of each employee.
  Adding headcount to the table.

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/e22ab379-653e-4ac5-81ea-e4781ce2e4ee)

  As we can see through our visualization, 16 people are working as Product Manager with average of 82,825 and Packaging Associate has 22 people Average is $33,409.
  Adding headcount to table represents the data better and making visualization justifiable. 

  Adding range to the table.
  create new measure minimum and maximum salary
  1. Minimum Salary = min(staff[Salary])
  2. Maximum Salary = MAX(staff[Salary])

  Add Minimum and Maximum measures salaries to the table:
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/156ac648-561d-4756-9b6c-10b9f1baea29)

  We can see the Maximum salary of an employee who is Packaging associate is $36,200 and minimum salary is $28,900.
  While the Maximum salary of an employee who is Product manager is $85,000 and minimum salary is $80,700.

  Through this easy visualization breakdown we got to analyze the range, headcount, and average salary of employees in their respect job.

  5. Top Earners in each job

     Create a headcount graph of job title and create a table selection titles of Name, Employee ID, Gender, and salary.
     Formate the table showing only top 3 people by their salary.

     ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/613e4551-ff01-42e1-a279-62c9c7e8c33e)

     These are the Top 3 People across the country with highest salary.

     We can select any titles from Job title graph and we can see top 3 people salary in that job.

     ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/cb82b5cc-bf0d-4025-99c7-8dfdd884fa96)
     Top 3 People of Packaging associate

     ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/bf8e911c-884d-4964-8099-e9f44a9010dc)
     Top 3 People of Profuction Operator

     ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/35c74e76-7a2c-43cc-a603-ac7caa33ca79)
     Top 3 People who are Production Manager
     


6. Qualification versus Salary

    So, we are going to look at employees qualication and how much they are paid. To see the trend whether is salary is correlated to their qualications.
  
    We are going to create a scatter plot in order to show the correlation between salary and qualification.
  
    Note: Scatter plot doesn't work with Non-numerical data, so we are going to transform qualification into Ranks
  
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/ca015281-e92c-481d-8645-425a3510d957)
  
    Transforming and assigning ranks to qualification.
  
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/e2a05146-e6ed-4ce4-aa96-f246f5ad3286)
  
    Assigned ranks
  
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/9003afba-376d-4ae2-8839-d42e776b97d6)
  
    We can see the salary spreads of different employees according to their qualifications.

  
7. Staff Growth trend over time

   To see a trend growth, A line chart perfect represents the growth over time. 

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/924e63a0-8c07-4ab2-a74e-0c5c6dbc41e1)

   We can see in our Line chart tread, one line shows on each date how many people joined and the other trend line shows cumulative headcount of all the employee till that date starting from starting.
   We can also see the surgest of growth between particular dates by hovering over the trend line for example, From September 2018 to December 2018 more than 10 people joined the company.


8. Employee filter by starting letter

   Goal is to search the employee through their starting letter of their name.

   First we need to transform the data by extracting first letter from their name.
   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/0c30d39d-ddc0-421e-a612-cd44b43cdba7)

   We will creating a slicer chart through which we can select employee first letter in order to sort them to see and analyze their details. And we are going to also add a table with employee details as follows:

    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/ac06c791-481d-4bd4-95e6-003e1556cd50)

   In this visualization we can see everybody with their Employee ID, Name, Job Title because we have not selected any letter in the slicer chart.

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/01bf336c-4adc-4ec9-b2de-3058e1a1c63e)

   Every employee with G starting letter.

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/1743647e-5b52-4e60-9cf0-b437ca419221)

   Every Employee with S starting letter.

   Making more visual changes by adding a card visual with headcount through which we will know how many people are their with the starting letter
   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/771873cf-0f2f-4edd-93ec-ae2160adff96)
   we can see there are 6 people with H starting letter.

   Through this we can select and analyze date more easily.

9. Leave balance Analysis

   We are going to analyze average leave balance aswell as to count the number of employees that have excess leave balance of certain amount.

   Create measure:
   Average Leave Balance = AVERAGE(staff[Leave Balance]), This measure calculates average leave balance
   LBL over 20 days = CALCULATE([Headcount], staff[Leave Balance]>20), This measure calculate the number of people having more than 20 leave balance.

   Create a bar graph showing average leave balance based on the Job title
   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/df94f13a-96bf-4b1a-a477-f6288ad014b4)

   Add the LBL over 20 days measure in the tooltip and if you hover over the bar chart and you can see the number of people in each job title with over 20 days Leave balance.

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/b321c0d8-6a63-4e0b-a5e8-f64e8ec0b11b)

   Add gender graph to see based on gender

   ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/3beb084a-e754-4422-92e2-e948f649eb24)

   Just by clicking on gender and hovering over the bar chart we can see more details based on gender and department.



10. Quick HR Dashboard


    Finally, we will create an HR Dashboard which represents visualizations of all the analysis of data based on Excel sheet.
    It has headcount, Average salary, Average leave balance, and other charts representing the overall analysis for better understanding the company employee structure and their details without looking at matrices.
    
    ![image](https://github.com/ankurcyb/HR-DataAnalysis/assets/141453942/4b60af57-335d-4ea4-8cf9-2d37b2f1b1e9)



# Acknowledgment

This Data Analysis and Power BI visualization is inspired through YouTube channel called [Chandoo](https://www.youtube.com/@chandoo_).
And sample HR data from Keggle.







   





     

     
