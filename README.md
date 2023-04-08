# PWC-Switzerland-PowerBI-virtual-case

## Task 2-Call Centre Trends


Visualizing customer and agent behavior
Create a dashboard in Power BI for Call Centre Manager that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset. 


###  *Table of Contents:

#### •		Problem Statement

#### •		Flow of work-:
```             
Step 1- Upload Data
             
Step 2-Cleaning data
            
Step 3-Transform data
             
Step 4-Load data 
```
#### •	Data Preparation
```
Data Modelling

Writing DAX 
```
#### •		Data Visualization

#### •		Data Analysis

#### •		Insights

#### •		Shareable link

#### •Problem Statement

The purpose of this analysis is to create a dashboard in PowerBI for call canter manager that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset. Get creative!

Possible KPIs include (but are not limited to):

•	Overall customer satisfaction

•	Overall calls answered/abandoned

•	Calls by time

•	Average speed of answer

•	Agents performance quadrant -> average handle time(talk duration) vs calls answered


#### •	Flow of work

##### Step 1- Upload Data

The Dataset used for this analysis was presented by PWC_Switzerland and available at their official website page - [Dataset_link]

##### Step 2-Cleaning data

Data transformation was done in Power Query and the dataset was loaded into Microsoft Power BI Desktop for modelling.The call canter dataset is given by a table named:

•	Call Center which has 10 columns and 5000 rows of observation

The tabulation below shows the Call center table with its column names and their description:

| Column Name	    | Description     | 
| ------------- | ------------- | 
| `Call Id`        |Represents every unique observation in the dataset         | `NewYork`   |
| `Agent	  `         | Describes the name of the agent           | `Toronto`   |
| `Date` |    	                  Describes the date of the call|
| `Time` |	                        Represents the time of the call|
|`Topic` |                       Describes the topic of the caller|
| `Answered`                     |(Y/N)	Describes if the call was Answered or not|
|  `Resolved`	                    |Describes if the problem was Resolved or not|
| `Speed of answer(in seconds)`	|Represents the speed of answer in seconds|
| `AvgTalkDuration`              |	Represents the average talk duration of call|
| `Satisfaction rating`	        |Represents the satisfaction rating of the agent during the call|

##### Step 3-Transform data
Data Cleaning and transformation for the dataset were done in power query as follows:
•	Unnecessary columns were removed
•	Each of the columns in the table was validated to have the correct data type
•	Unnecessary rows were removed

#### Data preparation: -

##### Data Modelling
After the dataset was cleaned and transformed, it was ready to be modelled.
•	The official dataset is marked as the `FACT` table in the dataset.

•	A separate Agent Table is created by using the DAX function-
Agent table = `DISTINCT` ('Fact Table'[Agent])

•	A separate Topics table is created by using the DAX function
        Topics = `DISTINCT` ('Fact Table'[Topic])
        
•	Along with this, a separate table- All Measuress is created to store all the measures which we have used in this model.

##### Data Visualization
Data visualization for the datasets was done in Microsoft Power BI Desktop:
•	The Call Center Manager Page: Shows KPIs including overall customer satisfaction, overall calls answered/abandoned, calls by time, average speed of answer, 
agents performance quadrant -> average handle time(talk duration) vs calls answered

#### Data Analysis
Measures used in visualization are:

•	`Answered_call` = CALCULATE(COUNT('Fact Table'[Call Id]),FILTER('Fact Table','Fact Table'[Answered (Y/N)]="Y"))

•	`Resolved count` = CALCULATE(COUNT('Fact Table'[Call Id]),'Fact Table'[Resolved]="Y")

•	`Avg_rating` = AVERAGE('Fact Table'[Satisfaction rating])

•	`Average speed of answer` = AVERAGE('Fact Table'[Speed of answer in seconds])

•	`Target Value Satisfaction` = 4.5

•	`%Call Answered` = DIVIDE('All Measuress'[Answered_call],[Total_calls],0)

•	`%call resolved` = DIVIDE([Resolved count],[Total_calls],0)

•	`%Call Unanswered` = DIVIDE([Not_answered],[Total_calls],0)

•	`%call unresolved` = DIVIDE('All Measuress'[Unreolved count],[Total_calls],0)

•	`Agent_slicer` = DISTINCTCOUNT('Fact Table'[Agent])

•	`Average speed of answer(IN MIN)` = DIVIDE('All Measuress'[Average speed of answer],60,0)

•	`Avg duration of talk` = AVERAGE('Fact Table'[AvgTalkDuration])

•	`Avg talk of duration (IN MIN)` = DIVIDE('All Measuress'[Avg duration of talk],60,0)

•	`No of agent` = CALCULATE(DISTINCTCOUNT('Fact Table'[Agent]))

•	`Not_answered` = CALCULATE(COUNT('Fact Table'[Call Id]),FILTER('Fact Table','Fact Table'[Answered (Y/N)]="N"))

•	`Total_calls` = COUNTROWS('Fact Table')

•	`Unreolved count` = CALCULATE(COUNT('Fact Table'[Resolved]),'Fact Table'[Resolved]="N")


#### Insights

As shown by Data Visualization, It can be deduced that:

•	The average satisfaction rating is 3.40

•	81.08% of total calls were answered and 18.92% of total calls were not answered

•	72.92% of total calls were resolved and 27.08% of total calls were not resolved

•	The average speed of answer is 67.52 seconds

•	Jim has answered total 536 call which is highest whereas Stewart answered lowest number of calls i.e. 477



#### Dashboard image


![image](https://user-images.githubusercontent.com/127341700/227794003-eabb02dd-3e8e-40c8-9611-79bedba25ce7.png)










