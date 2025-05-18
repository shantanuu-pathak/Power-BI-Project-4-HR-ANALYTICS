# Power BI Project #3: HR Report

## Problem Statement

I recently completed a project focused on demystifying common HR metrics. The project provides insights into employee headcount, retention, and turnover trends. This will be a valuable tool for anyone interested in workforce analytics. Big shout out to Sean Chandler for the excellent resources and guidance!


### Steps followed 

#### Modeling

- Step 1 : The dataset is loaded in the Power BI and the root file is .csv
- Step 2 : After the dataset is loaded, the original file is hidden from the front end using the disbale load option.
- Step 3 : A reference is created for the above original file, and named with the suffix "people_data_source", so that the original file is not affected by the cleaning transformations.
- Step 4: Creation of Fact and Dimension tables: A fact and 8 dimension tabels are created. On the dimension tables, transformations such as removing duplicates, adding index column and creating a merge between the fact and dimension tables are performed. Other additional transformations like rounding off values and unpivot columns is also done as required and necessary.
            
#### Evaluation
- Step 1 : Following Dax measures are created:

            All Employees = DISTINCTCOUNT(people_fact[employee_id])

            Departing Employees = CALCULATE([All Employees], FILTER(people_fact,people_fact[term_date]>=FIRSTDATE('Date'[Date]) && people_fact[term_date]<=LASTDATE('Date'[Date])))

            Ending Headcount = CALCULATE([All Employees], FILTER(people_fact, people_fact[hire_date]<FIRSTDATE('Date'[Date]) && (people_fact[term_date]=BLANK() || people_fact[term_date]>=LASTDATE('Date'[Date]))))

            Headcount = CALCULATE([All Employees],FILTER(people_fact,people_fact[hire_date]<=LASTDATE('Date'[Date]) && (people_fact[term_date]>LASTDATE('Date'[Date]) || people_fact[term_date]=BLANK())))

            Retention = DIVIDE([Ending Headcount],[Starting Headcount])

	    Turnover % = DIVIDE([Departing Employees],[Avg # of Employees])


- Step 2: Following visuals are created overall

            Card (new)
            Clustered Bar chart
            Line and Stacked column charts
            Clustered Column chart
            100% Stacked Bar Chart
            Map
	    Slicer
	    Card (new)
	    Matrix
            Key influencers

Snapshots of the Dashboard:

![image](https://github.com/user-attachments/assets/1838d679-93b8-4660-99b3-669c6b3731be)

![image](https://github.com/user-attachments/assets/b277ccdd-68ad-4a29-9cc0-296f217f8ae4)

![image](https://github.com/user-attachments/assets/31cbd85f-d6b4-46d1-810a-417309ebedd4)

![image](https://github.com/user-attachments/assets/5297600d-3bb0-4b55-82e0-de227f16a4d5)

           
#### Integration of Buttons, Custom Slicer Panel and Tooltip

Power point is used to design the background, logos and images for buttons. The colour scheme for the theme for power bi is also imported.

Buttons and slicer panel is integrated and utilised for the better user navigation.


Tooltip is used on the maps to give users a better understanding of the different geolocational aspects.

Snapshot of the tooltip

![image](https://github.com/user-attachments/assets/c062e053-72ea-4965-8fbf-89c563af7ced)


#### Cover page

A cover page is created to give the user some details on what to expect in the report and, subsequently different tabs are created to let the user jump to different views.
