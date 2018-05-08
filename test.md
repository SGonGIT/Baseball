## Tableau Story for Basketball Dataset

### Summary

##### dataset details
"baseball_data" dataset containing 6 variables/features, in which data types of "Name","Handedness"  are string, so in Tableau they are under DIMENSIONS category and 
data types of "Avg","Height","Weight","HR" are numeric so they are under MEASURES category of the Tableau.
"Handedness" feature could be used as a categorical variable,since its containing only 3 type of string values,such as : R , L & B (Here R : Right , L : Left, B: Both).

There are total 1157 observations/rows/players

In the dataset "Avg" column representing batting average and "HR" column representing home run.

In the dataset there are 6 players with same name(Bobby Mitchell,Dave Roberts,Dave Stapleton,Jim Wright,Mel Stottlemyre & Mike Brown), but their other attributes such as
height or weight or handedness or avg or HR are different ,so they are not duplicate values.

##### data visualization
Out of 1157 players there are 316 Left handed , 737 Right handed & 104 Both handed players.

In a Packed Bubbles ,I showed how home runs are distributed ;interesting point is 62 Left handed,203 Right handed & 21 Both handed players never scored a home run. Same goes with 
batting average,out of 1157 players many of them have batting average of 0.0
And these records would take a  vital role in Statistical measurements.

In form of Boxplot & Barchart ,I have shown median values of batting average & home runs for each handedness.
Median batting average for Left handed, Right handed & Both handed players are 0.248,0.233,0.2405 respectively.
Median home run for Left handed, Right handed & Both handed players are 23.5,14,13 respectively.

In Linechart , I have shown how players mean batting average and mean home run are decreasing as players height increasing.
But if we consider only non-zero HR(home runs) data points(by just the changing HR value from 0 to 1) , we would see an opposite trend in the Line chart for home runs.
That would not effect the trend of batting average though.
If we deep into further and see Line chart for each handedness(differentiate by color), we would notice for "Both handed" players as per height increases, mean home run trend increases too.
Another point,If we consider only non-zero HR data points, for "Both handed" players, mean batting average trend is almost constant in respect of player heights.

Anyway, since the trend direction of batting average & home run are similar, so there must be a correlation exist between these two variables.
And that's why I created a Scatterplot to investigate a relationship between batting & home run.
From the scatterplot , we can see a positive linear relationship exist between these two variables. 
We can see,as batting avg increases ,homeruns increases too.Relationship is not very strong though.
To investigate further, Handedness(differentiate by color) introduced in the scatterplot too and we can see a similar correlation exists between avg & HR irrespective of Handedness.
Trend line model shows R-Squared : 0.181386 , Standard error : 67.0593 & p-value (significance) : < 0.0001


### Design

##### Initial design 
At first sheet, I created a Bar chart which would display median values of avg(batting average) and HR(homerun) for each handedness. 
To crate a barchart we need just one MEASURES variable.
On a single sheet I have created 2 rows barchart. 
To build this visualization,I dragged and dropped MEASURES variables : HR , avg from Tableau Data field to rows field. That would create two bars in two rows. Now I changed the measure 
from SUM to MEDIAN. Now to break the bar in 3 category of Handedness , I dragged and dropped DIMENSIONS variable : Handedness from Data field to Tableau columns field.
After that I dragged and dropped MEASURES variable : Number of Records(by default calculated field) to the Marks > detail field. That would help me to display number of data points 
exist on each bar of the barchart (when hovering).
I also decided to make a filter of these variables : HR,avg,Name,Height,Weight. So dragged and dropped all these 5 variables to Filter field. And then I enabled "Show Filter" option for all 
these 5 filters. This would help later readers/viewers to play around with data visualization by just changing these filter values. 

On next sheet, I have created a boxplot to show median,minimum,quantile values of HR(homerun) for each handedness on a single visualization.
To crate a boxplot we need at least one DIMENSIONS variable.
To build this visualization, I clicked on MEASURES variable : HR ,then clicked on "Show me" and by hovering on box-and-whisker plots, I noticed, its asking a DIMENSIONS variable.
So I selected HR and name variables together ,and then Tableau allowed me to make a boxplot. Finally dragged and dropped Handedness on columns field,since I want to create separate
boxplot for each Handedness.
From rows field ,I can change HR from MEASURES to DIMENSIONS,it would effect anything.
I decided not to show names on hovering data points(since they are overlapping each other).To do that ,I have disabled name "include in Tooltip" option from Marks field.
I also decided to make a filter of these variables : HR,avg,Name,Height,Weight. And I achieved that by repeating same steps as like I did on previous sheet.

Similarly I created boxplot to show median,minimum,quantile values of avg(batting average) on a new sheet.

Then I created a dashboard to include all above 3 sheets. I also applied all the filters from all these 3 sheets to the selected worksheets of the dashboard. 
   
On Next step, I have created a new sheet for a linechart, it would display height v/s mean avg and mean HR.
To create a linechart , We need at least one DIMENSIONS variable, but neither height nor avg or HR are DIMENSIONS variable. So we need to convert one of them to DIMENSIONS when required.
To build this visualization,I dragged and dropped MEASURES variables : HR ,avg from Data field to rows field.That would create two 2 bars in two rows.Now I changed the measure from SUM to 
AVG. Then I dragged and dropped MEASURES variable : height to the columns field. And finally change it to DIMENSIONS from MEASURES.
I dragged and dropped number of records and weight from data field to Marks > detail field to show those informations of player on hovering over the chart.
I also decided to make a filter of these variables : HR,Name,Weight.  

I created another sheet for line chart with same information as above , only addition was to categorize Handedness by color.I achieved that just by dragged and dropped  Handedness from 
data field to Marks > details field.
Point to see, a Legend field had been attached with the sheet, there were 3 colors, each assigned to each Handedness handed value(L,R,B) 
I also decided to make an extra filter for this chart. Filter was for variable : Handedness

Then I created a dashboard to include last 2 sheets.I also applied all the filters except one(Handedness) from all these 2 sheets to the selected worksheets of the dashboard. 

On final sheet I created a scatter plot.
To create a scatter plot , We need DIMENSIONS variables on both Axis. So after dragged and dropped avg to the columns field and HR to the rows field, we need to convert both of them 
from MEASURES to DIMENSIONS. And this would create a details scatter plot for every data point of the dataset.
I have added a trend(linear model) line  for the plot too.
I also decided to make a filter of these variables : HR,Name,Weight,Height,Handedness.

Last step , I added last 2 dashboards & last sheet into a story. So my story containing 3 slides in total. 

In all over the designing process,I attached Annotate (as an Area or a Point) on sheets and dashboard whenever a special note need to be displayed additionally for viewers.


##### changes to the visualization after collecting feedback  
On feedback No. 1, that overlapping problem could be easily fixed on data science by just applying colour transparency technique(alpha).But it looks like on my Tableau that cant not be 
done for this kind of scatter plot. 
Because when I draw a scatter plot on Tableau with multiple colours(by adding a dimension variable to the color Marks), only color opacity option was present there! 
But just changing opacity value would not help me in this case, it would bring down whole color brightness(or fade up), instead we need to change color transparency, which would help me 
to display a darker color, whenever multiple data points exist on the same spot of the scatter plot, but no such transparency option is available there.
I searched on  the internet and found a blog post about it. (LINK : https://www.thedataschool.co.uk/emily-dowling/tableau-tip-tuesday-using-transparency-scatterplots/ )
But unfortunately on my Tableau Public version 2018.1 ,no such transparency option exist! 

On feedback No. 2, That problem could fixed by simply adding a annotate(Text Area) in sheets or by adding a text Object in Dashboards, which would display full meaning of  Handedness 
abbreviation : L,R,B ,such as Left Handed , Right Handed & Both Handed respectively.

On behalf of feedback No. 3,I introduced "Packed Bubbles" for showing distribution of home runs.In this process I had to convert HR variable from MEASURES to DIMENSIONS.
I have made this "Packed Bubbles" on a new sheet and then attached the new sheet to the 1st dashboard(where 3 sheets were already there).
So basically this would be the part of the 1st slide of my story. 

### Feedback

No. 1>
On final slide of the story ,there is a scatter plot and data points are overlapping with each other,so that causing a viewing issue.

No. 2>
Audience did not get the meaning of Handedness abbreviation : L,R,B (Specially B).

No. 3> How avg & HR distributed? and if consider non-zero values only,then does trends remains same?
 
### Resources

https://en.wikipedia.org/wiki/Category:Handedness_in_baseball

https://www.azsnakepit.com/2010/2/17/1303361/on-the-other-hand-handedness-in

https://data-flair.training/blogs/tableau-branding/
