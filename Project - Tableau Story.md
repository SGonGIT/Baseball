## Tableau Story for Basketball Dataset

### Links

Initial Tableau Link : https://public.tableau.com/profile/sgontableau#!/vizhome/Udacity-DAND-Project_initialBaseball/Sotry?publish=yes
Final Tableau Link : https://public.tableau.com/profile/sgontableau#!/vizhome/Udacity-DAND-Project_finalBaseball/Sotry?publish=yes

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

Highest(maximum frequency) number of players Height between 72 & 72 .There are 232 players within that range of height.
Highest(maximum frequency) number of players Weight : between 180 & 190 .There are 299 players within that range of weight. 
Highest(maximum frequency) number of players batting average : between 0.00 & 0.01 .There are 266 players within that range of avg.. 
Highest(maximum frequency) number of players homerun score : between 0 & 20 .There are 624 players within that range of HR.

In a Packed Bubbles ,I showed how home runs are distributed ;interesting point is 62 Left handed,203 Right handed & 21 Both handed players never scored a home run. Same goes with 
batting average,out of 1157 players many of them have batting average of 0.0
And these records would take a vital role in Statistical measurements.

In form of Boxplot & Barchart ,I have shown median values of batting average & home runs for each handedness.
Median batting average for Left handed, Right handed & Both handed players are 0.248,0.233,0.2405 respectively.
Median home run for Left handed, Right handed & Both handed players are 23.5,14,13 respectively.
So Left-handed players have better edge over other handed players.

In Linechart , I have shown how players mean batting average and mean homerun are decreasing as players height increasing.
Line chart for each handedness(differentiate by color), we would notice that other than "Both handed" players as per height increases, mean homerun increases.
But if we consider only non-zero HR(home runs) data points(by just the changing HR value from 0 to 1) , we would see an opposite trend in the Line chart for home runs.
That would not effect the trend of batting average though.
If we dig into further and see Line chart for each handedness(differentiate by color), we would notice for "Right handed" and "Both handed" players as per height increases, 
mean home run trend is increasing too.
Another point,If we consider only non-zero HR data points, for "Both handed" players, mean batting average trend is almost constant in respect of player heights.

Whether weight and height together could make an effect on player performance?
I find out for a certain range of height & weight there are few players with highest performance. For example ,if we filter out batting average < 0.25 and homerun < 300 ,we would found
players with Height in between 70 & 76 and Weight in between 175 & 230 have better performance than any other players.

Anyway, since the trend direction of batting average & home run are similar, so there must be a correlation exist between these two variables.
And that's why I created a Scatterplot to investigate a relationship between batting & home run.
From the scatterplot , we can see a positive linear relationship exist between these two variables. 
We can see,as batting avg increases ,homeruns increases too.Relationship is not very strong though.
To investigate further, Handedness(differentiate by color) introduced in the scatterplot too and we can see a similar correlation exists between avg & HR irrespective of Handedness.
Trend line model shows R-Squared : 0.181386 , Standard error : 67.0593 & p-value (significance) : < 0.0001


### Design

##### Initial design 
At first I created a Histogram from height & weight to investigate the distribution of them. I used height bin size = 1 and weight bin size = 10.
Then I have created a bar chart with broken into 3 column of Handedness value(R,L,B) for Number of Records(by default calculated field) 
Then I created a text table with names in rows and  Number of Records in Marks > Text filed. And filter the data with CNT(Number of Records) : 2. So that would display players names 
those are not unique.

Then I attached all above individual sheets into a Dashboard.

Next on a new sheet, I created a Bar chart which would display median values of avg(batting average) and HR(homerun) for each handedness. 
To crate a barchart we need just one MEASURES variable.
On a single sheet I have created 2 rows barchart. 
To build this visualization,I dragged and dropped MEASURES variables : HR , avg from Tableau Data field to rows field. That would create two bars in two rows. Now I changed the measure 
from SUM to MEDIAN. Now to break the bar in 3 category of Handedness , I dragged and dropped DIMENSIONS variable : Handedness from Data field to Tableau columns field.
After that I dragged and dropped MEASURES variable : Number of Records to the Marks > detail field. That would help me to display number of data points 
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
Last, I changed the Y-Axis to log scale.
I also decided to make a filter of these variables : HR,avg,Name,Height,Weight. And I achieved that by repeating same steps as like I did on previous sheet.

Similarly I created boxplot to show median,minimum,quantile values of avg(batting average) on a new sheet.

Then I created a dashboard to include all above 3 sheets. I also applied all the filters from all these 3 sheets to the selected worksheets of the dashboard. 
   
On Next step, I have created a new sheet for a linechart, it would display height v/s mean avg and mean HR.
To create a linechart , We need at least one DIMENSIONS variable, but neither height nor avg or HR are DIMENSIONS variable. So we need to convert one of them to DIMENSIONS when required.
To build this visualization,I dragged and dropped MEASURES variables : HR and avg from Data field to rows field.That would create two 2 bars in two rows.Now I changed the measure from
SUM to AVG. Then I dragged and dropped MEASURES variable : height to the columns field. And finally change it to DIMENSIONS from MEASURES. And that created a mice line chart with all 
the data points. 
I dragged and dropped number of records and weight from data field to Marks > detail field,so these informations would be visible by just hovering over the chart.
I also decided to make a filter of these variables : HR,Name,Weight.  

I created another sheet for line chart with the same information as above , only addition was to categorize Handedness by color.I achieved that just by dragged and dropped  Handedness 
from data field to Marks > details field.
Point to see, a Legend field had been attached with the worksheet, there were 3 colors, each assigned to each handed value(L,R,B) 
I also decided to make an extra filter for this chart. Filter was for variable : Handedness

Then I created a dashboard to include last 2 sheets.I also applied all the filters except one(Handedness) from all these 2 sheets to the selected worksheets of the dashboard. 

Next, To investigate,whether hight & weight can make an effect on player performance, I created a scatter plot for hight v/s weight on a new sheet.
So I put weight in columns filed and height in rows field and then applied 2 filters avg,HR and enabled option to visible these filters. Then I set HR low : 300, HR high to the maximum
; avg low : 0.25 and avg high to the maximum.
I also dragged and dropped avg,HR,Number of Records from Data field to the Marks > detail filed. And convert avg,HR from MEASURES to DIMENSIONS & name from DIMENSIONS to ATTRIBUTE.
Created a new Dashboard and linked my last worksheet onto it. 

On next new sheet I created a scatter plot.
To create a scatter plot(with every data point of the dataset) , We need DIMENSIONS variables on both Axis. So after dragged and dropped avg to the columns field and HR to the rows field, we need to convert both of them 
from MEASURES to DIMENSIONS. And this would create a details scatter plot for every data point of the dataset.
I dragged and dropped name from data field to Marks > detail field. So if a user hover over a point of the plot,it would display player name too.
Since in this scatter plot there are 1157 points(each for a single player).And that causing a huge overlapping.So for better understanding of the plot,I used double encoding technique 
to differ Handedness. To achieve this ,I have dragged and dropped Handedness to the Marks > color field as well as Marks > shape field.
I have added a trend(linear model) line  for the plot too.This part done from Analytics field.
I also decided to make a filter of these variables : HR,Name,Weight,Height,Handedness.

On a new dashboard , I organized my all findings.

Last step , I added my all 5 dashboards & last sheet into a story. So my story containing 6 slides in total. 

In all over the designing process,I attached Annotate(as an Area or a Point) on sheets and dashboard whenever a special note need to be displayed additionally for viewers.

To avoid colour blindness issue, I used colors belongs to Palette : Color Blind

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

On behalf of feedback No. 3,I introduced  one "Packed Bubbles" and two Histograms to show distribution of home runs.
To make a  "Packed Bubbles" ,I had to convert HR variable from MEASURES to DIMENSIONS.
I have made this "Packed Bubbles" on a new sheet and then attached the new sheet to the 1st dashboard(where 4 sheets were already there).I also added newly created Histograms to the same Dashboard.
So basically this would be in the part of the 1st slide of my story. 

### Feedback

No. 1>
On final slide of the story ,there is a scatter plot and data points are overlapping with each other,so that causing a viewing issue.

No. 2>
Audience did not get the meaning of Handedness abbreviation : L,R,B (Specially B).

No. 3> How avg & HR distributed? and if we consider only non-zero values,then does trend remains same?
 
### Resources

https://en.wikipedia.org/wiki/Category:Handedness_in_baseball

https://www.azsnakepit.com/2010/2/17/1303361/on-the-other-hand-handedness-in

https://data-flair.training/blogs/tableau-branding/