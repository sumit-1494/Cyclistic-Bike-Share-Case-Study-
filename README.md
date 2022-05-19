# Cyclistic-Bike-Share-Case-Study

## CYCLISTIC BIKESHARE ANALYSIS


## Author

- [**SUMIT KOKANE**](https://github.com/sumit-1494?tab=repositories)



![App Screenshot](https://images.squarespace-cdn.com/content/v1/5e8f31c8664e7b358a701917/1600853755630-29XAUBBXU45UGP1DWRHX/ch_Divvy-bikes+%281%29.jpg?format=1500w)


### About Cyclistic
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.


## Business Task
The goal of this case study is to convert casual riders into member riders. We need to present them how casual and member riders differ and why casual riders would buy a membership. 
Based on those insights marketing team will make decisions about how to present cyclistic program to casual members to buy a membership.


## The Stakeholders
 **Lily Moreno:** The director of marketing and cyclistic analytics team manager.Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program.

 **Cyclistic executive team:** The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.


## Data Exploration
Data is located on [cyclistic database](https://divvy-tripdata.s3.amazonaws.com/index.html).The Data was available yearly , Half-yearly , Quarterly and Monthly. The Data we used for analysis is from **Jan 2021 to Dec 2021**. 
We are adressing licensing by accepting and following terms and conditions under [License Agreement](https://ride.divvybikes.com/data-license-agreement). 

The data was unbiased and credible.The data is reliable, original, and current as it is internally collected and stored safely by Cyclistic. The data is comprehensive and it provided the necessary information to carryout statistical analysis.


## Data Issues
The Attributes Provided were sufficient but not complete. It could have contain information about gender and birth year which was provided in earlier datasets (2013-2019) which would provide some additional insights.

The data for station names & IDs contains many blank fields only for electric bike rides.
This issue is resolvable because longitude and latitude was provided without any null values.


## Data Cleaning
Data was divided into twelve monthly sheets. We used Microsoft Excel to perform data cleaning. SQL is used to merge all twelve sheets into single one because total number of rows after merging came out to be 5.5 millions which is out of the scope for excel.
For visualizaing most frequent stations on map we used tablue.

Steps taken for data cleaning:

1) Identified the source error which turnout to be negative time values that gave !value error while subtracting time. This Issue is resolved using MOD() function.

2) Formatted date and time correctly

3) Removed extra white space using TRIM() Funtion.

4) Checked for duplicates using DISTINCT() Function in SQL and Remove Duplicate funtion in Excel.

5) No mismatch data was found while cleaning

6) Data aligns perfectly with business logic

7) 739170 of station names out of 5.5M records are missing which constitutes 13.21% of the total. Surprizingly data about station names for electric bikes were missing. This issue is resolved using longitude and lattitude data. 

8) Around 4800 records of geographical latitudes and longitudes are missing, but since it constitutes less than 0.1% of the total records it can be filtered out. 


## Data Transformation
1) In each sheet Date & Time was merged into single column which is separated into date and time for finding start date and time & end date and time for each ride.
2)  In each sheet I Created a column named ride_length by subtracting Start_time from end_time under MOD() function.
3) Then, From start date we extracted day of the the date using function named WEEKDAY()  and created a column which specifies cosecutive number for that day. Then we used function TEXT() to convert that number into the day and created a column named start_day().
4) Renamed column name member_casual to rider_type which specifies riders with membership and without membership(Casual riders)

After performing the above mentioned steps I uploaded the 12 CSVs on the Microsoft SQL Server Management Studio and combined them using UNION ALL function in Transact-SQL. 

The free public version of Tableau could not be linked to SQl, so I exported the combined 12 months data into a CSV . Although the maximum number of records a CSV can process is 1048576, but it can store any number of records. The total turned out to be 
5.5M which I uploaded onto Tableau as a text file.



## Data analyzing
1) I created a pivot table for calculating average ride length for each rider type on weekly basis to provide weekly analysis of each month. The goal at this point was to find out which rider type has longer ride length in the particular period.
2) Another Pivot table is generated for ride counts of each rider type on weekly basis. The goal at this point was to find out whether casual riders had a preference for certain days or months compared with member riders.
3) Third pivot table is generated for analyzing which bike type was used more frequently by rider type.
4) From All these pivot tables separate table is prepared for monthly analysis of average ride length, Ride count and preferred ride type.
5)

## Insights & Visulizations


### Ride Count
<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Total%20Ride%20Count.png" align="center" height="480" width="480" ></a>

Ride Count for the year 2021 is 5.59M out of which 2.52M hiring of bikes is by casual riders and 3.06M by member riders. This indicates 45% hiring is by casual riders and 55% by member riders which shows number of casual riders are abundant and supports business strategy of converting casual riders into member riders instead of adding new membership riders. 

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Ride%20Count.png" align="center" height="640" width="896" ></a>

1) Number of bikes hired by casual riders Start increasing from March till July and then starts decreasing from August to February. July is the peak point of hiring bikes by casual riders and lowest is in the month of February which has a freezing weather conditions. Number of bikes leased by casual riders has excceded member rider count from June-August which is probably due to peak period of tourism in Chicago.
2) For member riders bike leasing starts increasing from March till september and then starts decrasing from October till February. Maximum hiring is in the months of August/september which is peak period for tourism and lowest hiring is in the month of February which I suspect to be freezing weather conditions of that month. 
3) After carefully observing monthly data, Overall on weekends of each month bike hiring by casual riders is more than member riders and on weekdays maximum hiring is by member riders. I reckon that maximum member riders are hiring bikes for commute purposes which can be school/college/working places on weekdays.

### Ride Length

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Total%20Ride%20Length.png" align="center" height="480" width="480" ></a>

On an average casual riders are spending twice as much time in riding than member riders, even though bike hiring by casual riders is 10% less than member riders. 

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Avg.%20Ride%20Length.png" align="center" height="640" width="896" ></a>
 
 Average Ride length for casual members is almost similar from February to May and then decreases further until January. Average Ride length for member members is almost similar from April to August and then decreases further until January. Throughout the year casual riders have higher ride length than member riders. 
In each month ride time is higher on sunday for casual/member riders.


### Ride Preference
<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Overall%20Ride%20Preference.png" align="center" height="640" width="896" ></a>

Overall Classic bike is more preferred over electric and docked bike. Usage of classic bike is more in member riders and for electric bikes usage is comparable.
Docked bikes are very less preferred by casual riders and not preferred by member riders.

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Casual%20Bike%20Preference.png" align="center" height="640" width="896" ></a>

 Usage of Classical bike for casual riders start increasing from February till july and starts decreasing onwards. Electric bike is more preferred  over classic bike by casual riders for the period October - December, I suspect the reason to be start of winter season. Usage of Electric bike starts increasing from march and remains almost similar from June till October and then start decreasing onwards.
 
Maximum usage of all bike types is in the month of july. Lowest Usage is in the months of January & February for all bike types, the reason I suspect is freezing weather condition. In January Electric bike and Classic bike almost equal usage. Largest rise in the usage of classical bike is in between May and June. Largest drop for classical bike is between September and October. For Electric and Docked bike largest rise in usage is in between April and May & Largest drop is in between October and November.

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Member%20Bike%20Preference.png" align="center" height="640" width="896" ></a>

Usage of Classic bike for member riders start increasing from March till August and decreases onwards till February. Maximum usage for classic bike is in the month of August. Lowest usage is in the month of february. Highest rise in the usage of claasic bike is between February and March & Highest drop in the usage is in between October and November. Classic Bike Hiring by member riders is almost comparable in months July - September. 

For Electric Bike usage increases from March till October and then decreases onwards. Maximum usage is in the month of October and lowest use is in the month of February. Largest rise in the usage is in between september and october & largest drop is in between November and December. Electric bike hiring by members is similar in period from June - Sepetember.

For members, electric bike usage exceeds classical bike usage in the months November and December which is probably due to start of winter season. Docked Bikes never used by member riders.

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Bike%20Preference.png" align="center" height="640" width="896" ></a>

From graph we Can see Classic bike hiring of member rider is always excceding classic bike hiring of casual riders. Docked Bikes are used only by casual members but have least preference. No usage of docked bikes by member riders. Electric bike hiring for Casual riders exceeds electric bike usage of member riders after may till September. 

Usage of classic bike and electric bike is evenly ditributed from Tuesday to Saturday for member riders and lowest use is on Monday and Sunday. For Casual riders maximum use of all bike types is on Saturday. Among three types classical is more preferred over electric and docked, which are almost equally preferred on saturday. 

## Top 20 Busy Stations
<a href="url"><img src="https://github.com/sumitkokane/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Top%2020%20Busy%20Stations%20(2).png" align="center" height="600" width="750" ></a>
Majority of docking stations are near the coastal area. Streeter Dr and Grand Ave' is the most famous docking station with highest number of riders due to excursion places in its vicinity. Difference between number of rides at the top 1st (Streeter Dr & Grand Ave) and top 2nd (Michigan Ave & Oak St) docking stations is significantly large.

## Peak Hour 
<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Weekday%20Peak%20Hours_%20Member%20Riders%20.png" align="center" height="500" width="1000" ></a>

As seen From the Graph On Weekdays bike hiring by member riders is maximum in morning between 7.00 AM - 8.00 AM & in evening from 4.00 PM to 6.00 PM. I suspect most of the member riders are using bikes for commute. Also, member riders seem to be using the bikes to travel towards train station since most of the peak cyclistic docking stations are near train stations. 

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Weekdays%20Peak%20Hours_%20Casual%20Riders.png" align="center" height="500" width="1000" ></a>

Bike Hiring by Casuals on weekdays is maximum in evening from 4.00 PM to 6.00 PM. I suspect that Casual riders are using bikes for commute & leisure activities. May be Casual riders are using bikes more for leisure activities because in morning time member riders are hiring more bikes than Casual riders and above mentioned morning time is commute time.  

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Weekend%20Peak%20Hours%20_%20Member%20Riders%20.png" align="center" height="500" width="1000" ></a>

On Weekend bike hiring by member riders starts increasing from 9.00 AM till 5.00 PM. Maximum Hiring is between 12.00 PM to 4.00 PM. Bike Hiring is also increased at night between 11.00 PM - 12.00 AM. Maximum rise in hiring is from 8.00 AM to 10.00 AM.

<a href="url"><img src="https://github.com/sumit-1494/Cyclistic-Bike-Share-Case-Study-/blob/main/Graphs/Weekend%20Peak%20Hours%20_%20Casual%20Riders.png" align="center" height="500" width="1000" ></a>
 
 On Weekend bike hiring by Casual riders starts increasing from 9.00 AM till 5.00 PM. Maximum Hiring is between 12.00 PM to 4.00 PM. Bike Hiring is also increased at night between 11.00 PM - 12.00 AM. Maximum rise in hiring is from 8.00 AM to 11.00 AM.  
 The Trend on weekends is normal distribution curve for both types of riders where as trend on weekdays is a spike during commute hours.

## Recommendations
1) Slash membership rates from may to September.
2) Design Half-Yearly and Quarter-Yearly membership plans.
3) Design flash sales of membership plans on top 20 busiest stations on weekends during peak hours.




