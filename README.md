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

            Jan :
            Ride Count: Member: Friday
                        Casual: Saturday

            Avg. Ride Length: Member: Tuesday
                              Casual: Monday   

            Ride Type: Member: classic & electric friday,
                       Casual:  Classic,electric & docked Saturday,                      




            Feb :
            Ride Count: Member: Wednesday
                        Casual: Saturday

            Avg. Ride Length: Member: Sunday
                              Casual: Saturday   

            Ride Type: Member: Classic Wed, Electric Fri
                       Casual: Classic,electric & docked Saturday     




             Mar :
            Ride Count: Member: Tuesday
                        Casual: Saturday

            Avg. Ride Length: Member: Sunday
                              Casual: sunday   

            Ride Type: Member: Classic,electric sat
                       Casual: Classic,electric & docked Saturday       
     less diiference of Ride count between casual and memeber on sat and sunday        


             Apr :
            Ride Count: Member: Friday
                        Casual: Saturday

            Avg. Ride Length: Member: Sunday
                              Casual: Sunday   

            Ride Type: Member: Classic,electric friday
                       Casual:  Classic,docked sat,electric fri   
casual ride count exceeded on sat & sun

             May:
            Ride Count: Member: Saturday
                        Casual: Saturday

            Avg. Ride Length: Member:Sunday
                              Casual: Sunday    

            Ride Type: Member: Classic,electric sat
                       Casual: Classic,electric sat, docked sunday                                               
casual ride count exceeded on sat & sun



            Jun :
            Ride Count: Member: Wednesday
                        Casual: Saturday

            Avg. Ride Length: Member: sunday
                              Casual: sunday   

            Ride Type: Member: Classic,electric wed
                       Casual: Classic,electric & docked Saturday                       

casual ride count exceeded on fri, sat & sun




             Jul :
            Ride Count: Member: Thursday
                        Casual: saturday

            Avg. Ride Length: Member: Sunday
                              Casual: Sunday   

            Ride Type: Member: classic thurs, electric fri
                       Casual: Classic,electric & docked Saturday                 

casual ride count exceeded on fri, sat & sun,mon



             Aug :
            Ride Count: Member: Tuesday
                        Casual: Sunday

            Avg. Ride Length: Member: Sunday
                              Casual: Sunday   

            Ride Type: Member: Classic,electric tuesday
                       Casual: Classic sat,electric & docked sunday    
casual ride count exceeded on fri, sat & sun



             Sep :
            Ride Count: Member: Thursday
                        Casual: saturday

            Avg. Ride Length: Member: Sunday
                              Casual: Sunday   

            Ride Type: Member: Classic,electric thursday
                       Casual: Classic,electric & docked Saturday       
casual ride count exceeded on sat & sun
           
           
           
             Oct:
            Ride Count: Member: Saturday
                        Casual: Saturday

            Avg. Ride Length: Member:sunday
                              Casual: sunday    

            Ride Type: Member: classic saturday,electric friday,
                       Casual: Classic,electric & docked Saturday                                        
casual ride count exceeded on sat & sun


             Nov :
            Ride Count: Member: Tuesday
                        Casual: Saturday

            Avg. Ride Length: Member: Sunday
                              Casual:  Sunday  

            Ride Type: Member: Classic,electric tuesday
                       Casual: Classic,electric & docked Saturday       



             Dec :
            Ride Count: Member: Thrusday
                        Casual: Friday

            Avg. Ride Length: Member: Sunday
                              Casual: Sunday   

            Ride Type: Member: Classic,electric thursday
                       Casual: classic,electric friday and docked saturday


April - Oct Ride count exceeded june-aug on fridays,sat and sunday & sat , sunday in apr, may ,sep ,oct
march-dec Avg ride length max on sundays
 Ride Preferred   
 (oct-dec) electric max preferred, exceeded claasic by casual & (nov-dec) by member , exceeded casual
 Jan difference between electric and classic during weekdays is almost negligible
 usage of docked bike is  very less in casual and no usage in members
 Claasic bike is more prefeered (feb-sep) by casual in 


jun-sep warm season -> tourism max
oct-cool, nov-cold,dec-feb very cold,mar-cold,apr-cool
rain: feb-may increasing, may-aug max 
sep-jan - decreasing rain 

## Insights & Visulizations
1) Average Ride length for casual riders is always greater than member riders.
2) Average Ride length for casual members is almost similar from February to May and then decreases from month June to January.
3) Ride Count for Casual Riders Start increasing from March till July and then Starts decreasing from September to February.
4) Casual Riders has excceded Member Rider Counts from June-August in which tourism is also maximum.
5) Overall classical bike is more preferred over electric bike.
6) Electric bike is more preffered than classic bike from October to December by Casual riders and in November & December by Member riders.
7) In January both Electric and Classical bike is Equally Prefeered in weekdays by Casual Riders.
8) Docked bikes are very less preferred by Casual Riders & No usage of docked bikes by members.
9) 
