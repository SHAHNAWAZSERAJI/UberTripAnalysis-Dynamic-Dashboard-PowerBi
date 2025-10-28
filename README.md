# UberTripAnalysis-Dynamic-Dashboard-PowerBi
# 🚗 UberTripAnalysis-Dynamic-PowerBi-Dashboard: Demand, Revenue, and Efficiency Dashboard

The Uber Trip Analysis Dynamic Power Bi Dashboard is a dynamic, interactive data visualization tool designed to provide deep, actionable insights into Uber's ride-hailing operations.
It focuses on analyzing key performance indicators (KPIs) related to trip volume, revenue, distance, and duration, enabling operational teams to optimize pricing strategies, improve driver deployment, and understand user behavior across time and geography.

### Tech Stack
The dashboard was built using a robust Business Intelligence platform (like Power BI), Sql, Excel and relies heavily on Calculated Columns, Measures and  DAX (Data Analysis Expressions) for creating analytical measures. 

#### 1. 📊 Business Intelligence Platform:
Power BI Desktop– Main data visualization platform used for interactive report creation.
##### 2. 📂 Data Preparation:
Excel, SQL– Used for data extraction, cleaning, and preliminary transformation of the TRIP DETAILS and LOCATION TABLE.
####  3.📂 Power Query:-
Data transformation and cleaning layer for reshaping and preparing the data.
#### 4.📝 Data Modeling: 
Relationships established between the TRIP DETAILS (fact table) and the LOCATION TABLE (dimension table) via PULocationID and DOLocationID to enable seamless geographic analysis and enable cross-filtering and aggregation..
#### 🧠 5. DAX Operations (Calculated Measures & Columns):
Essential for transforming raw data into meaningful KPIs. Used for calculated measures, dynamic visuals, and conditional logic.
#### 📁 6. File Format –
.pbix for development and .png for dashboard previews.

## DAX Operations :- 
* DAX Element	Purpose & Logic	Base Table Columns Used
* Total Booking (Measure)	Counts the total number of unique trips in the dataset.	TRIP DETAILS[Trip ID]
* Total Booking Value (Measure)	Calculates the sum of all fare amounts across all trips.	TRIP DETAILS[Fare Amount]
* Total Trip Distance (Measure)	Sums the total distance covered by all trips.	TRIP DETAILS[Trip Distance]
* Avg Booking Value (Measure)	Calculates the average fare charged per trip. Logic: [Total Booking Value] / [Total Booking]	TRIP DETAILS[Fare Amount], TRIP DETAILS[Trip ID]
* Avg Trip Distance (Measure)	Calculates the average distance of a trip in miles. Logic: [Total Trip Distance] / [Total Booking]	TRIP DETAILS[Trip Distance], TRIP DETAILS[Trip ID]
* Trip Duration (min) (Calculated Column)	Calculates the difference between Drop Off Time and Pickup Time, converting the result to minutes.	TRIP DETAILS[Drop Off Time], TRIP DETAILS[Pickup Time]
* Avg Trip Time (Measure)	Calculates the average duration of all trips in minutes. Logic: AVERAGE('TRIP DETAILS'[Trip Duration (min)])	TRIP DETAILS[Drop Off Time], TRIP DETAILS[Pickup Time]
* Pickup Hour (Calculated Column)	Extracts the hour (0-23) from the Pickup Time column to enable hourly trend analysis.	TRIP DETAILS[Pickup Time]
* Trip Day/Night (Calculated Column)	Categorizes a trip as 'Day Trip' or 'Night Trip' based on the Pickup Hour (e.g., 6 AM - 6 PM is Day, otherwise Night).	TRIP DETAILS[Pickup Time]
## Data Source
#### Source: Uber trip records of one month from Kaggle.
                 * 1.Location Table .
                 * 2.Uber Trip Details.
#### Data Structure:
##### The dashboard leverages a star schema model based on two primary tables:
* 1.TRIP DETAILS (Fact Table): Contains granular data for each ride, including:
* 2.Temporal Data: Trip ID, Pickup Time, Drop Off Time.
* 3.Financial/Volume Data: Passenger Count, Payment Type, Fare Amount, Surge Fee.
* 4.Operational Data: Trip Distance, Vehicle.
* 5.LOCATION TABLE (Dimension Table): Provides the geographical context for the trips, mapping numeric IDs to readable   names.
* Geographic Data: LocationID, Location (Area Name), City.
               
### Features:-

##### Business Problem
A modern ride-hailing platform must continuously monitor and react to fluctuating demand to ensure service reliability, maximize revenue, and maintain driver satisfaction. Key challenges include: predicting peak hours, ensuring adequate vehicle supply in high-demand zones, and understanding which services (vehicle types) are the most profitable and popular.

#### Goal of the Dashboard
To deliver a comprehensive, multi-layered visual tool that:

* 1.Tracks core operational and financial KPIs in real-time.
* 2.Identifies temporal patterns (peak hours, days of the week) for surge pricing and driver incentive optimization.
* 3.Pinpoints high-value geographic zones for strategic driver placement.
* 4.Analyzes the performance and profitability of different vehicle types.
        
#### Walkthrough of Key Visuals: Outcomes & Insights

The analysis views provide the following critical operational and business insights:

##### *KPIs Establish a Performance Baseline:

The platform handled 103.7K bookings, generating $1.6M in revenue over the period, with an average trip being short (3 miles) and fast (16 minutes).
##### *Demand is Highly Concentrated at Night and on Weekends:
       *1. Night-time trips account for a preference of 65.28% of bookings, signaling higher activity after standard business hours.

       *2. The hourly/daily analysis confirms a clear surge in demand on Friday and Saturday evenings (Hours 16-23), which is the prime window for applying surge pricing to meet volume.
       
##### *Cash is the Dominant Transaction Method:
       *.Cash represents the overwhelmingly dominant Payment Type, making robust cash handling and reconciliation processes critical for financial security.

##### (UberX Drives Volume, While Premium Services Offer Higher Value:
      *.UberX is the highest volume and revenue generator, confirming its role as the mass-market standard.
      *.The dashboard allows for checking the Average Booking Value of premium services like Uber Black or Uber Comfort to assess their profitability and strategic value in the luxury segment.
      
##### *Urban Hubs Drive Core Demand:
       *.The most frequent pickup and drop-off points are concentrated in key urban centers like Penn Station/Madison Sq West and the  Upper East Side North, identifying high-traffic zones for targeted driver deployment and marketing efforts.
       
##### *Granular Data Supports Auditing and Validation:
       *.The Details view allows users to pull up individual trip records for auditing purposes, essential for validating the aggregate trends and investigating any suspicious or outlier data (like the Surge Fee column).

#### Overview KPIs (Baseline Performance)
##### Total Booking: 
103.7K trips handled during the period.
##### Total Booking Value: 
$1.6M in gross revenue generated.
##### Avg Trip Distance: 
3 miles (Short-haul focus).
##### Avg Trip Time: 
16 minutes (High operational efficiency).
###### Primary Service: 
UberX is the highest volume and revenue driver.
##### Key Geographies: 
Demand is heavily concentrated in urban centers like Penn Station/Madison Sq West (Most Frequent Pickup).
#### Temporal Insights (Demand & Pricing)
##### Peak Surge Windows: 
* Demand surges significantly on Friday and Saturday evenings (Hours 16-23), confirming the optimal time for peak surge pricing and driver incentives.
##### Weekly Trend: 
* A marked dip in activity occurs mid-week (Wednesday/Thursday), requiring targeted incentives to boost utilization.
#####Time Preference:
* A preference for Night-time trips is observed, accounting for 65.28% of total bookings.
#### Financial and Compliance Insights
##### Payment Type Risk: 
* Cash is the overwhelmingly dominant payment type, necessitating strict controls and reconciliation processes to manage associated financial risks.
##### Data Audit: 
* The Details tab provides granular access for auditing high-fare trips, applying the Surge Fee, and validating data integrity.

### Business Impact & Outcomes
The analysis provided by this dashboard translates directly into the following actionable business outcomes and insights:
Focus Area	Outcome / Insight Generated
##### Demand Forecasting & Pricing
* The Time Analysis clearly identifies peak demand periods (Saturday/Sunday and 3 PM - 9 PM daily).
* This is the key input for the Surge Fee mechanism, allowing the company to dynamically adjust pricing to maximize revenue and balance supply during these windows.
##### Operational Efficiency
* The average trip metrics (3 miles / 16 minutes) serve as an efficiency benchmark.
* Location analysis allows for proactive driver deployment; focusing on areas like Penn Station and the Upper East Side during peak times ensures less waiting time for customers and higher utilization for drivers.
##### Vehicle Strategy
UberX is confirmed as the mass-market volume leader, driving the majority of bookings and revenue. However, services like Uber Black and Uber Comfort should be analyzed for their high Average Booking Value to understand premium segment profitability.
##### Financial/Auditing
* The dashboard reveals that Cash is the predominant payment type (over 87% of bookings in the overview). 
* This insight mandates robust internal processes for cash handling, reconciliation, and minimizing fraud associated with cash payments.
##### Route Optimization
* Identification of the Farthest Trip (144.1 Miles) highlights outliers.
* This data can be used to analyze long-haul trips for specific pricing models or dedicated services that optimize long-distance travel efficiency.
  
![DASHBOARD PREVIEW].(https://github.com/SHAHNAWAZSERAJI/UberTripAnalysis-Dynamic-Dashboard-PowerBi/blob/main/overview%20analysis.PNG).
