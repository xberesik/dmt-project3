# PROJECT ON DATA VISUALISATION FOR THE FISHING COMPANY USE CASE  

In the project, we imported preprocessed data into PostgreSQL to facilitate efficient data management and analysis. Additionally, to enhance data integrity and enforce data consistency, we modified the structure of the proposed tables from Project 1 by adding constraints. These constraints, such as primary keys, foreign keys, and not-null constraints, were implemented to ensure the validity and reliability of the stored data. All queries that we used in pgadmin are included in the file querys.txt.

## Route visualisations

- a. Create a new layer in ArcGIS with all the trips of one vessel (e.g., Rodney) 

For this task, we created a view that contains the name of the trip and geometry (LINESTRING) that represents the trajectory of each trip. We selected just trips for boats with the name Rodney. We faced some problems with selecting the proper coordinate system and also with the fact that function ST_MakeLine takes as input only GEOMETRY type so we had to use the CAST function on our geometry.

- b. Visualize and compare the same trajectory using the fishing and AIS datasets.

For this task, we selected trajectory as the connection of each trip for the Rodney boat. Then we compared the trajectory obtained from the AIS dataset and the fishing dataset. The trajectories from the AIS dataset looked quite checkered since we normalized them in the previous assignment. We also played a bit with a different setting like text position and size or colour and style of trajectories to make visualization look better. 

- c. Create a chart to show each route’s total length (distance) of one vessel (e.g., Rodney) 

For this task, we used a query to create a view that contains the calculated distance of each trip of Rodney boat. To calculate the actual distance in km we used ST_Length function that returns the distance in meters. It was important to use a propper geometry system to get correct results same as the CAST function two times as ST_MakeLine and ST_Length work with different types.

## Plotting fishing data

- a. Create a chart to show the total quantity of fish per different vessels

Firstly we created a view by a query that used the aggregation function SUM with GROUPBY to calculate the total quantity of fish per different vessel. Then we also used ArcGIS to make aggregation for us. It was really interesting that it's easy to make this kind of data operation without querying. After this, we plotted a bar plot and enhance its style and description.

- b. Create a chart to show the trend of average fish caught in different trips of one vessel in one year (e.g., Rodney in 2020) 

With this task we followed the same steps as in the previous one, firstly making a view with aggregation query and then making aggregation by ArcGIS . We used the new function EXTRACT to extract the year from the Date column. 


## Plotting temperature and chlorophyll

- a. Create chart to show the correlation between the fish caught and temperature for one vessel (e.g., Rodney).

Merged data containing fishing and temperature information is used to plot correlation between caught fish and temperature for boat Rodney. Scater plot was chosen as adequate visualisation to plot correlation but in the end it showes that there is no significant correlation. 

- b. Visualize the chlorophyll as a Raster

For the visualization, a suitable color scheme was applied, with green representing high levels of chlorophyll, indicating favorable fishing spots, and red representing low levels, indicating unfavorable fishing spots. The maximum value of chlorophyll concentration was manually defined to ensure that the colors accurately represent the concentration levels.
This approach allows for clear identification of areas with different chlorophyll concentrations, aiding in the prediction of good and bad spots for fishing based on chlorophyll levels.

- c. Plot the distribution of the temperature for the raster created

For the color scheme, red shades were chosen, with bright red indicating high temperatures and light red representing low temperatures. This color scheme allows for easy identification of temperature levels across the map.
Interestingly, when analyzing the fishing data, it was observed that all the fishing spots were located in areas with lower temperature levels.