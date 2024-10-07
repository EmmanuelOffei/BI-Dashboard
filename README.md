# Faith Community-Dashboard


### Dashboard Link : https://app.powerbi.com/groups/me/reports/b8490e5c-9bda-408a-8701-fd7aebcbce71/ReportSection?experience=power-bi
## Problem Statement

This dashboard provides a comprehensive overview of the membership statistics for the Faith Community. It enables community leaders to effectively track and monitor the status of their members.

### Key Insights:

####  Active and Inactive Members:
 The dashboard identifies active and inactive members, allowing leaders to focus on engagement and retention strategies.
#### Demographics:
 It provides valuable insights into the demographic profile of the membership, helping leaders tailor initiatives to specific groups.
Geographical Representation: The map visualization offers a visual representation of member locations, facilitating targeted outreach and engagement efforts.
Benefits:
#### Member Wellbeing:
 By tracking member activity and demographics, leaders can assess overall wellbeing and ensure that all active members are connected to relevant departments.
#### Retention: 
This dashboard supports efforts to retain members by identifying areas for improvement and tailoring initiatives to meet their needs.
### Overall Goal:

The ultimate goal is to foster a thriving and supportive community by ensuring the well-being and engagement of all Faith Community members.



### Steps followed 

- Step 1 : Lunch the Microsoft Powe BI App on the Desktop.
- Step 2 : Load data into Power BI Desktop, dataset is a csv file.
- Step 3: Open the Power Query Editor and analyze the data:

Column Distribution: The distribution of values within each column was checked to identify any outliers or inconsistencies.
Column Quality: Data quality, including completeness, accuracy, and consistency was checked.
Column Profile: Data types, null values, and other characteristics of each column was checked.
- Step 4 : For the purposes of this project, Columns with null values were replaced with the key word 'empty'for easy reporting.
- Step 5 : Step 5: Add geographical coordinates:
longitude and latitude coordinates were in the correct format (e.g., decimal degrees).
Geocoding tools was used to automatically convert addresses or postal codes to coordinates.
- Step 6 : In the report view, under the view tab, the default theme was used.
- Step 7 :Two card visuals were added to the canvas, one showing the total number of members and the other showing active number of members 
- Step 8 :  Visual filters (Slicers) were added for two fields named "filter members" & "Circle Leader". 

- Step 9 : Three bar charts were also added to the report design area to visualize the Department, Agegroup and the Location by gender 

- Step 10 : A Gender breakdown was visualized using a pie chart,

- Step 11 : Calculated column was created in which, members were grouped into various age groups.

for creating new column following DAX expression was written;

    = Table.AddColumn
    (#"Changed Type1", "Age Group", each if [Age] < 20 the "Teenager" 
    else if [Age] < 30 then "young Adult"
    else if [Age] < 50 then "Adult" 
    else if [Age] = 124 then "Not Specified"
    else null)
       
       
        
Snap of new calculated column ,

![Agegroup](https://github.com/user-attachments/assets/282f5ddf-f2e2-4501-b8e6-7a9e000fdf98)

        
-For Map ploting the following DAX expression was written,


        Table.AddColumn(#"Added Conditional Column", "Custom", each 
        if [Location] = "Saki" then "5.734640596673972,-0.0137255959703581" 
        else if [Location] = "Dawhenya" then "5.756582929956301,0.05107990535312465"
        else if [Location] = "Afienya" then "5.796105772496278,0.002859672802545078" 
        else if [Location] = "Central University" then "5.774106710445348,0.08324584358054171" 
        else if [Location] = "Affordables" then "5.72403032442272,0.043599389451238174"
        else if [Location] = "Outside Accra" then "6.075247912730172,-0.25765813170473384" 
        else if [Location] = "Kpone" then "5.6937595758639725,0.05266301270515875" 
        else if [Location] = "Ashaiman" then "5.69375668207861,-0.03166869001837211" 
        else if [Location] = "Community 25" then "5.726989190221458,0.01561335554842037" 
        else if [Location] = "Accra" then "5.55936011068018,-0.19868403744630966"
        else if [Location] = "Prampram" then "5.724982082596127, 0.11918528632884724" 
        else if [Location] = "Tema Main" then "5.688015974070328, -0.014460909446022614"
          else "Not Specified")

In other to plot the map on the the Cordinates were slipted into the longitude and latitude columns with using th below DAX expression

    = Table.SplitColumn(#"Added Conditional Column1", "Custom", Splitter.SplitTextByDelimiter(",", QuoteStyle.None), {"Custom.1", "Custom.2"})
        
Snap of splited columns.

![Map dashboard](https://github.com/user-attachments/assets/16638b18-04c3-4e9e-b8c8-5beb1202af56)

        
 - Step 12 : A new tab showing individual details was created.

 Snap of the individual details

 ![individual Dash  board](https://github.com/user-attachments/assets/3d5c15a7-f5ea-451e-b919-b1e2f9fd41de)

 
 

 - Step 13 : The report was then published to Power BI Service.
 
 


## Snapshot of Dashboard
![Dasboard](https://github.com/user-attachments/assets/4019b0ba-f063-4fe9-bed2-39134fed1782)



# Insights

A two  page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of members = 61

   Number of Active members  = 25 (41 %)

   Number of Active Female members = 15 (24.59 %)

   Number of Active Male members = 10 (16.39 %)

   Majority of members are from Central University & Community 25 with a count of 9 members from each location followed by people outside of Accra with a Count of 8 members.


Most members are not comfortable providing their birth year hence age calculation for such members were unspeficied
           
 
 ### Age Group
 
 2.1)  24.59 % members belong to young age group.
 
 2.2)  22.95 % members belong to 'Adult' age group.
 
 2.3)  8.20 % members belong to 'Teenage' age group.
 
 2.4)  44.26 % members belong to the Not specified age group.
 

