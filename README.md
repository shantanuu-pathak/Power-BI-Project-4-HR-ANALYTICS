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

            ![Image](https://github.com/user-attachments/assets/9f7f6d30-ab8d-48bf-a1aa-56bfe171a32d)
	    
	    ![Image](https://github.com/user-attachments/assets/7c48e289-8189-4d34-a0da-dadd29c8069c)
     
	    ![Image](https://github.com/user-attachments/assets/6cefba98-ef34-402c-a3b6-90d857b9f2b3)
     
	    ![Image](https://github.com/user-attachments/assets/af201137-fa48-414e-98f8-aee717b71ed3)            
           
#### Integration of Buttons, Custom Slicer Panel and Tooltip

Power point is used to design the background, logos and images for buttons. The colour scheme for the theme for power bi is also imported.

Buttons and slicer panel is integrated and utilised for the better user navigation.


Tooltip is used on the maps to give users a better understanding of the different geolocational aspects.

Snapshot of the tooltip

	    <img width="724" alt="Image" src="https://github.com/user-attachments/assets/983d82b6-3a5f-444b-8946-549fb76c06fb" />

#### Cover page

A cover page is created to give the user some details on what to expect in the report and, subsequently different tabs are created to let the user jump to different views.
