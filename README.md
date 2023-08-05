A case study from [Google Data Analytics](https://www.coursera.org/professional-certificates/google-data-analytics) offered by Coursera.

As a data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The Director of Marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, as a member of the marketing analyst team, I want to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members.

# **ABOUT CYCLISTIC**
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are tracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system at any time.

![Image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/c3a105aa-797f-4541-bab7-65488ed99930) 
<figure>
  <img src="image.png" alt="Photo Credit: Divvybikes">
  <figcaption>Caption text</figcaption>
</figure>

One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who buy annual memberships are Cyclistic members.

# **BUSINESS TASK?**

To help meet Cyclistic Business objectives, these questions will guide the future marketing program;

1. How do annual members and casual riders use Cyclistic bikes differently?

2. Why would casual riders buy Cyclistic annual memberships?

3. How can Cyclistic use digital media to influence casual riders to become members?

# **DATA PREPARATION**
Cyclistic previous [12 months' trip](https://divvy-tripdata.s3.amazonaws.com/index.html) data was downloaded. Structured and third-party data made available by Motivate International Inc under the license of [Divvybikes](https://divvybikes.com/)

I ensured the data is free from bias and credible to work on. Ensured each dataset is reliable, original, comprehensive, current, and cited.

I have taken a thorough and thoughtful approach to selecting and working with the data, with a focus on ensuring quality, accuracy, and integrity.

# **DATA PREPROCESSING AND CLEANING**

**Skill- Python. Libraries- Pandas, Numpy. Tool- Jupyter Notebook**

I will be working with 12 months of data to get actionable insights. After downloading 12 months of datasets from the cloud database in CSV file format. CSV stands for "Comma-Separated Values". It is a simple file format used for storing tabular data. I will use Python skills to process my datasets, merge the datasets to one full year, and clean my dataset for null values, duplicates, inconsistencies, and outliers before processing to analyzing stage.

Importing each CSV files into my Jupyter Notebook on my local machine. Jupyter Notebook is an open-source web application that allows me to create and share interactive documents containing live code, equations, visualizations, and explanatory text. It supports many programming languages, including Python which I will be using throughout my work. First import needed packages. Pandas is a Python package for data manipulation and analysis. It provides data structures for efficiently storing and working with tabular, labeled, and relational data. The second package, NumPy is a Python package for scientific computing and numerical analysis.

Importing each month datasets dec_2021, jan_2022, feb_2022… with ```pd.read_csv()``` method

```bash
#Importing "Pandas" and "Numpy" libraries 
import pandas as pd
import numpy as np

#Importing each CSV files for 12 months from DECEMBER 2021 - NOVEMBER 2022
dec_2021 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202112-divvy-tripdata.csv')
jan_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202201-divvy-tripdata.csv')
feb_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202202-divvy-tripdata.csv')
mar_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202203-divvy-tripdata.csv')
april_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202204-divvy-tripdata.csv')
may_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202205-divvy-tripdata.csv')
june_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202206-divvy-tripdata.csv')
july_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202207-divvy-tripdata.csv')
aug_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202208-divvy-tripdata.csv')
sep_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202209-divvy-tripdata.csv')
oct_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202210-divvy-tripdata.csv')
nov_2022 = pd.read_csv(r'C:\Users\USER\Desktop\Deloni Analytics\Projects\CASE STUDY\Case Study 1\CASE STUDY EXTRACTS\202211-divvy-tripdata.csv')

print('CSV files imported successfully')
```
The next stage is to merge the CSV files to a full year with ```pd.concat()``` method as shown in the code block below.
After a successful merge, I have a total of 5,733,451 rows × 13 columns using ```pd.DataFrame()``` method. Pandas data frame consists of rows and cells to display data in tabular format.
```bash
#Merging one full year datasets 

cyclistic = [dec_2021, jan_2022, feb_2022, mar_2022, april_2022, may_2022,
             june_2022, july_2022, aug_2022, sep_2022, oct_2022, nov_2022]

cyclistic = pd.concat(cyclistic)

print('One full year merged successfully')

#After merging to one full year, I have  [5733451 rows x 13 columns]

df = pd.DataFrame(cyclistic)

print(df)
```
The name of my dataset is now cyclistic after merging, with the ```cyclistic.info()``` method. This display all the columns names and data types I will be working with as shown below:
```bash
cyclistic.info()

<class 'pandas.core.frame.DataFrame'>
Int64Index: 5733451 entries, 0 to 337734
Data columns (total 13 columns):
 #   Column              Dtype  
---  ------              -----  
 0   ride_id             object 
 1   rideable_type       object 
 2   started_at          object 
 3   ended_at            object 
 4   start_station_name  object 
 5   start_station_id    object 
 6   end_station_name    object 
 7   end_station_id      object 
 8   start_lat           float64
 9   start_lng           float64
 10  end_lat             float64
 11  end_lng             float64
 12  member_casual       object 
dtypes: float64(4), object(9)
memory usage: 612.4+ MB
```
Checking for null values in my cyclistic dataset using ```cyclistic.isnull().sum()``` method to return a total number of null values in each column.
In the code block below, we have the start_station_name, start_station_id, end_station_name, end_station_id, end_lat, and end_lng columns.
```bash
#Checking for null values 
cyclistic.isnull().sum()

ride_id                    0
rideable_type              0
started_at                 0
ended_at                   0
start_station_name    854844
start_station_id      854844
end_station_name      915082
end_station_id        915082
start_lat                  0
start_lng                  0
end_lat                 5874
end_lng                 5874
member_casual              0
dtype: int64
```
To improve my data quality and better visualizations I will remove the null values rows using ```dropna()``` method. The result can be displayed as shown in code block below 
```bash
#Removing the null values

cyclistic = cyclistic.dropna(how='any', axis=0)

print("Null values removed successfully")

#Confirming the null values
cyclistic.isnull().sum()

ride_id               0
rideable_type         0
started_at            0
ended_at              0
start_station_name    0
start_station_id      0
end_station_name      0
end_station_id        0
start_lat             0
start_lng             0
end_lat               0
end_lng               0
member_casual         0
dtype: int64
```
With ```cyclistic.duplicated().any()``` method, I checked for duplicates in my cyclistic dataset, and the result returns “False" i.e. no duplicates in rows and columns.

Code block below shows “ride_length” a new column that I created by calculating the time difference between the "started_at" and "ended_at" columns. Essentially, it represents the length of time in minutes that a particular ride lasted from start to finish.

After a new column was created “ride_length” from the “started_at” and “ended_at” columns, I used the z-score method to remove outliers that can affect my analysis. The z-score method is a statistical technique used to identify and handle outliers in a dataset.
```bash
#Checking for duplicates 

cyclistic.duplicated().any()

False

#Converting "started_at" and "ended_at" columns to datetime format  

cyclistic['started_at'] = pd.to_datetime(cyclistic['started_at'])

cyclistic['ended_at'] = pd.to_datetime(cyclistic['ended_at'])

#Calculating the ride_length in minutes 

cyclistic['ride_length'] = (cyclistic['ended_at'] - cyclistic['started_at']).dt.total_seconds() / 60

#Removing outliers from "ride_length" column using z-score method

z_scores = np.abs((cyclistic['ride_length'] - cyclistic['ride_length'].mean()) / cyclistic['ride_length'].std())

cyclistic = cyclistic[z_scores < 3]

#Printing result after removing outliers
print (cyclistic)
```
To get insights into how Cyclistic riders use cyclistic bikes weekdays from weekends and to see if I can find a trend in weekday/weekend the week mostly use among riders. I used dts.weekday attributes to extract the day of the week from the “started_at” column. The weekday column is created, with ```dts.weekday``` attribute returns an integer value that represents the day of the week, where Monday is 0 and Sunday is 6.
```bash
#Generating weekday from "started_at" column. This method returns the day of the week as an integer, 
# where MONDAY is 0. TUESDAY is 1, WEDNESDAY is 2, THURSDAY is 3, FRIDAY is 4, SATURDAY is 5, and SUNDAY is 6

cyclistic['weekday'] = cyclistic['started_at'].dt.weekday

print(cyclistic)
```
The code block below shows the distance in km calculation from latitude and longitude coordinates columns using the Haversine formula. The Haversine formula is a mathematical equation used to calculate the distance between two points on the surface of a sphere, such as the Earth. “distance_km” column is created after defining the Haversine formula, and also the z-score method is used to remove all outliers that can influence my analysis.
```bash
#Calculating distance travelled in "km" using "start_lat","end_lat","start_lng","end_lng" columns with haversine formula 

#Defining the haversine formula

def haversine(lat1,lon1,lat2,lon2):
    r = 6371 #Earth radius in kilometers
    phi1 = np.radians(lat1)
    phi2 = np.radians(lat2)
    delta_phi = np.radians(lat2 - lat1)
    delta_lambda = np.radians(lon2 - lon1)
    a = np.sin(delta_phi/2)**2 + np.cos(phi1) * np.cos(phi2) * np.sin(delta_lambda/2)**2
    c = 2 * np.arctan2(np.sqrt(a), np.sqrt(1 - a))
    d = r * c
    return d

cyclistic['distance_km'] = haversine(cyclistic['start_lat'], cyclistic['start_lng'], cyclistic['end_lat'], cyclistic['end_lng'])

#Removing outliers from "distance_km" column using z-score method

z_scores = np.abs((cyclistic['distance_km'] - cyclistic['distance_km'].mean()) / cyclistic['distance_km'].std())

cyclistic = cyclistic[z_scores < 3]

#Printing result after removing outliers
print (cyclistic)
```
After cleansing, ```cyclistic.info()``` method gives updated results and returns changes made to the dataset. I have 4,398,064 rows and 16 columns to work with.
```bash
cyclistic.info()

<class 'pandas.core.frame.DataFrame'>
Int64Index: 4398064 entries, 0 to 337734
Data columns (total 16 columns):
 #   Column              Dtype         
---  ------              -----         
 0   ride_id             object        
 1   rideable_type       object        
 2   started_at          datetime64[ns]
 3   ended_at            datetime64[ns]
 4   start_station_name  object        
 5   start_station_id    object        
 6   end_station_name    object        
 7   end_station_id      object        
 8   start_lat           float64       
 9   start_lng           float64       
 10  end_lat             float64       
 11  end_lng             float64       
 12  member_casual       object        
 13  ride_length         float64       
 14  weekday             int64         
 15  distance_km         float64       
dtypes: datetime64[ns](2), float64(6), int64(1), object(7)
memory usage: 570.4+ MB
```
# **ANALYSIS STAGE**
**Skill: Python. Libraries- Pandas, Matplotlib Tool- Jupyter Notebook**

To the main business tasks. First, **How do annual members and casual riders use Cyclistic bikes differently?**

From the Data, I have to divide my data into two groups “annual_members” and “casual_riders” in order to get insights into how both groups differ.

That is what code block illustrates below
```bash
#Using the 'member_casual' column to split the data into two groups i.e creating dataframes for annual members and casual riders

annual_members = cyclistic[cyclistic['member_casual'] == 'member']

casual_riders = cyclistic[cyclistic['member_casual'] == 'casual']

#Importing visualization library "matplotlib" 

import matplotlib.pyplot as plt

#To compare the usage of Cyclistic bikes between annual members and casual riders

#Calculating the number of rides for annual members
num_rides_annual = annual_members['ride_id'].count()

#Calculating the number of rides for casual riders
num_rides_casual = casual_riders['ride_id'].count()

#Printing the results
print("Total number of rides for annual:\n", num_rides_annual)
print("Total number of rides for casual:\n", num_rides_casual)

Total number of rides for annual:
 2636578
Total number of rides for casual:
 1761486
```
Introduced Matplotlib to my work, Matplotlib is a data visualization library in Python. It provides a wide range of customizable visualizations such as line plots, scatter plots, bar plots, histograms, and many more.

I calculated the total number of rides for each group

Annual members 2.6M+

Casual riders 1.7M+

To better understand the insight, and rides distribution between annual members and casual riders, I used a pie chart to visualize my insight.

Python lines of code to create a pie chart for my ride distribution are shown in code block below.
```bash
#Creating a pie chart showing the percentage of rides for each group
labels = ['Annual Members', 'Casual Riders']
sizes = [num_rides_annual, num_rides_casual]

#Plotting the pie 
plt.pie(sizes, labels=labels, autopct='%1.1f%%')

#Titling the pie chart 
plt.title('Distribution of Rides by Rider Type')

#Displaying the pie chart 
plt.show()
```
I have my pie chart showing rides distribution

![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/c4325fd0-1c20-4a62-9582-2d2e712cd9d7)

From the pie chart, annual members 59.9% casual riders 40.1%

Now this is Cyclistic’s KPI, what are marketing strategies aimed at converting casual riders into annual members? Can it build an annual membership increase of 59.9% to 70–75%? To best solve the problem, lets me dive deeper.
```bash
#Calculating the average ride length and average distance per ride for each group

avg_ride_length = cyclistic.groupby('member_casual')['ride_length'].mean()

avg_distance = cyclistic.groupby('member_casual')['distance_km'].mean()

# Printing the results
print("Average ride length by rider type:\n", avg_ride_length)
print("\nAverage distance travelled per ride by rider type:\n", avg_distance)

Average ride length by rider type:
 member_casual
casual    21.707435
member    12.102288
Name: ride_length, dtype: float64

Average distance travelled per ride by rider type:
 member_casual
casual    2.151454
member    2.047847
Name: distance_km, dtype: float64
```
Average ride length in minutes between each group. To best understand the longer usage of bikes between each group

From the code block above, using the ride_length metric to calculate the Average ride length Casual riders averaged 21.7 minutes while Annual members averaged 12.10 minutes. Average distance in km, Casual riders 2.15km Annual members 2.04km For a better view of the insights, I used bar charts to convey my views.

To create a bar chart for the average ride length for both groups
```bash
#To create bar chart displaying average ride length for both groups, casual riders and member riders

#Assignining the 'casual' values from the 'avg_ride_length' dictionary to the 'group1' variable
group1 = avg_ride_length['casual']

#Assigning the 'member' values from the 'avg_ride_length' dictionary to the 'group2' variable
group2 = avg_ride_length['member']

#Setting the width of the bars to be plotted to 0.35
bar_width = 0.35

#Creating a new figure and axis object using matplotlib
fig, ax = plt.subplots()

#Creating a bar plot with the 'group1' data using a width of 'bar_width' and label it 'Casual'
bars1 = ax.bar(0, group1, bar_width, label='Casual')

#Creating a bar plot with the 'group2' data using a width of 'bar_width' and label it 'Member'
bars2 = ax.bar(1, group2, bar_width, label='Member')

#Setting the x-axis tick locations to [0, 1] and label them with the corresponding user types
ax.set_xticks([0, 1])
ax.set_xticklabels(['Casual', 'Member'])

#Adding a legend to the plot
ax.legend()

#Setting the x-axis label to 'User Type'
ax.set_xlabel('User Type')

#Setting the y-axis label to 'Average Ride Length(minutes)'
ax.set_ylabel('Average Ride Length(minutes)')

#Setting the plot title to 'Average Ride Length by User Type'
ax.set_title('Average Ride Length by User Type')

#Displaying the plot
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/ab6873df-1368-49de-8bb1-6580b645eba7)

Casual riders use Cyclistic’s bikes longer. This insight tells Casual riders to enjoy Cyclistic’s bikes, it does meet their daily needs to commute to work, around the street, ride for leisure, and others

To create a bar chart for the average distance
```bash
#Assigning the 'casual' values from the 'avg_distance' dictionary to the 'group1' variable 
group1 = avg_distance['casual']

#Assigning the 'member' values from the 'avg_distance' dictionary to the 'group2' variable
group2 = avg_distance['member']

#Setting the width of the bars to be plotted to 0.35
bar_width = 0.35

#Creating a new figure and axis object using matplotlib
fig, ax = plt.subplots()

#Creating a bar plot with the 'group1' data using a width of 'bar_width' and label it 'Casual'
bars1 = ax.bar(0, group1, bar_width, label='Casual')

#Creating a bar plot with the 'group2' data using a width of 'bar_width' and label it 'Member'
bars2 = ax.bar(1, group2, bar_width, label='Member')

#Setting the x-axis tick locations to [0, 1] and label them with the corresponding user types
ax.set_xticks([0, 1])
ax.set_xticklabels(['Casual', 'Member'])

#Adding a legend to the plot
ax.legend()

#Setting the x-axis label to 'User Type'
ax.set_xlabel('User Type')

#Setting the y-axis label to 'Average Distance(km)'
ax.set_ylabel('Average Distance(km)')

#Setting the plot title to 'Average Distance by User Type'
ax.set_title('Average Distance by User Type')

#Displaying the plot
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/2c27ce1c-57ef-4b17-960f-d2a83a57359c)

Casual riders averaged 2.15km distance while Annual members averaged 2.04km. A slight difference in average distance covered between these groups tells Casual riders are committed to Cyclistic bikes for their day-to-day activities, regarded it meets their daily needs.

How do annual members use Cyclistic’s bikes differently from casual riders? Another insight I got is to look at popular stations between annual members and casual riders.

```bash
#Identifying the most popular start stations for each group 
popular_start_annual = annual_members.groupby('start_station_name')['ride_id'].count().sort_values(ascending=False)
popular_start_casual = casual_riders.groupby('start_station_name')['ride_id'].count().sort_values(ascending=False)

#Identifying the most popular end stations for each group
popular_end_annual = annual_members.groupby('end_station_name')['ride_id'].count().sort_values(ascending=False)
popular_end_casual = casual_riders.groupby('end_station_name')['ride_id'].count().sort_values(ascending=False)

#Printing the results
print("Most popular start stations for annual members:\n", popular_start_annual.head())
print("Most popular start stations for casual riders:\n", popular_start_casual.head())
print("Most popular end stations for annual members:\n", popular_end_annual.head())
print("Most popular end stations for casual riders:\n", popular_end_casual.head())

Most popular start stations for annual members:
 start_station_name
Kingsbury St & Kinzie St        23961
Clark St & Elm St               20878
Wells St & Concord Ln           19992
Clinton St & Washington Blvd    18976
Loomis St & Lexington St        18533
Name: ride_id, dtype: int64
Most popular start stations for casual riders:
 start_station_name
Streeter Dr & Grand Ave               55147
DuSable Lake Shore Dr & Monroe St     30667
Millennium Park                       24060
Michigan Ave & Oak St                 23710
DuSable Lake Shore Dr & North Blvd    22131
Name: ride_id, dtype: int64
Most popular end stations for annual members:
 end_station_name
Kingsbury St & Kinzie St        23559
Clark St & Elm St               21220
Wells St & Concord Ln           20555
Clinton St & Washington Blvd    19645
Clinton St & Madison St         18824
Name: ride_id, dtype: int64
Most popular end stations for casual riders:
 end_station_name
Streeter Dr & Grand Ave               58004
DuSable Lake Shore Dr & Monroe St     28749
Millennium Park                       25928
Michigan Ave & Oak St                 25441
DuSable Lake Shore Dr & North Blvd    25267
Name: ride_id, dtype: int64
```
From code block above, I ran the Python lines of code to identify popular start stations and end stations for annual members and casual riders
For a better understanding of my insight, I introduced a horizontal bar chart to convey my results. Now after studying my popular station's insights, I then merged “start stations" and “end stations" for each group and visualized it

To create my horizontal bar chart for annual members
```bash
#Concatenating the two data frames containing the most popular start and end stations for annual members
popular_annual = pd.concat([popular_start_annual.head(), popular_end_annual.head()], axis=1)

#Assigning column names to the concatenated data frame
popular_annual.columns = ['Most popular start stations for annual members', 'Most popular end stations for annual members']

#Creating a horizontal bar chart for the joint data of the most popular start and end stations for annual members
plt.barh(popular_annual.index, popular_annual.values[:,0], label='Most popular start stations')
plt.barh(popular_annual.index, popular_annual.values[:,1], label='Most popular end stations')

#Inverting the y-axis so that the stations are plotted in descending order from top to bottom
plt.gca().invert_yaxis()

#Setting the title, x-label, y-label, and legend for the chart
plt.title("Most popular start and end stations for annual members")
plt.xlabel("Number of rides")
plt.ylabel("Station name")
plt.legend()

#Displaying the chart
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/d837db9c-1b68-4f74-bd97-ed92e940a83d)

The most popular start and end station for annual members is **“Kingsbury St & Kinzie St"**

What about casual riders?
```bash
#Concatenating the two data frames containing the most popular start and end stations for casual members 
popular_casual = pd.concat([popular_start_casual.head(), popular_end_casual.head()], axis=1)

#Assigning column names to the concatenated data frame
popular_casual.columns = ['Most popular start stations for casual riders', 'Most popular end stations for casual riders']

#Creating a horizontal bar chart for the joint data of the most popular start and end stations for casual riders
plt.barh(popular_casual.index, popular_casual.values[:,0], label='Most popular start stations')
plt.barh(popular_casual.index, popular_casual.values[:,1], label='Most popular end stations')

#Inverting the y-axis so that the stations are plotted in descending order from top to bottom
plt.gca().invert_yaxis()

#Setting the title, x-label, y-label, and legend for the chart
plt.title("Most popular start and end stations for casual riders")
plt.xlabel("Number of rides")
plt.ylabel("Station name")
plt.legend()

#Displaying the chart
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/05a4aa96-59e3-4274-8ea2-86c9c1a2faa5)

For casual riders, **“Streeter Dr & Grand Ave"** is the popular start and end station.

Insights from popular stations, start stations, and end stations. average distance traveled, average ride length and rides distribution tell how annual member differs from casual riders with Cyclistic bikes.

**Why would casual riders buy Cyclistic annual memberships?**

Now, my team understands how annual members use Cyclistic bikes differently from casual riders.

Casual riders use bikes longer and cover most distances with these bikes. Basically, they enjoy the Cyclistic bike share program. What type of bikes do casual prefer?

To filter out this information from my data.

I ran these Python lines of code as shown in code block below 
```bash
#Filtering the data to include only casual riders 
casual_rideable = cyclistic[cyclistic['member_casual'] == 'casual']

#Grouping the data by rideable type and count the number of occurrences for each type
casual_rideable_counts = casual_rideable.groupby('rideable_type').size()

#Calculating the percentage of rides for each rideable type among casual riders
casual_rideable_percentages = casual_rideable_counts / len(casual_rideable) * 100

#Creating a pie chart showing the percentage of rides for casual riders by rideable type
casual_rideable_percentages.plot(kind='pie', autopct='%1.1f%%', startangle=90)

#Setting the title of the chart
plt.title('Percentage of Rides by Rideable Type for Casual Riders')

#Setting the axis to be equal to make the chart circular
plt.axis('equal')

#Adding a legend to the chart
plt.legend()

#Displaying the chart
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/68e2ee55-e598-4830-93c7-a08571c63969)

Casual riders use classic bikes and electric bikes more. We can offer discounts on annual membership for these rideable type “classic bikes" and “electric bikes"

We can offer benefits of annual membership to casual riders such as cost savings and convenience since Cyclistic is flexible with its pricing plan. Likewise, Cyclistic bikes are accessible to casual riders to commute to work, market, exercise, and for leisure.

**How can Cyclistic use digital media to influence casual riders to become members?**
From the popular casual start and end stations insight, these are casual riders preferred stations. These are stations Cyclistic needs to target with a marketing campaign aimed at casual riders. We can run targeted social media campaigns for these stations' areas and communities.

**What’s the best time to reach out to casual riders?**

Here are Python lines of code to show the frequency of rides by start hour for casual riders in code block below 
```bash
#Creating 'start_hour' column from  'started_at' column 
cyclistic['start_hour'] = cyclistic['started_at'].dt.hour

#Separating casual rides
casual_rides = cyclistic[cyclistic['member_casual'] == 'casual']

#Grouping rides by start hour and count number of rides
casual_rides_by_hour = casual_rides.groupby('start_hour')['ride_id'].count()


#Plotting frequency of rides by hour for casual riders
casual_rides_by_hour.plot(kind='line')
plt.xlabel('Hour')
plt.ylabel('Number of rides')
plt.title('Frequency of rides by hour for casual riders')
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/4e5b1a00-d9b9-4b93-916c-37b0daf99551)

From the chart above Casual riders' frequency of rides by hour, from the chart 16 hours (4:00 pm) Eastern time is the most frequent hour. Chicago which is one hour behind Eastern time will be 3:00 pm

**How about weekdays vs weekends, what is the most frequent day of the week for casual riders?**
```bash
#Grouping rides by weekday and count number of rides for casual riders
casual_rides_by_weekday = casual_rides.groupby('weekday')['ride_id'].count()


#Plotting frequency of rides by weekday for casual riders
casual_rides_by_weekday.plot(kind='line')
plt.xlabel('Weekday')
plt.ylabel('Number of rides')
plt.title('Frequency of rides by weekday for casual riders')
plt.show()
```
![image](https://github.com/eniayejudaniel/Riding-the-Wave-of-Success-Strategies-for-Cyclistic-Bike-Share/assets/124352785/caf7ab6d-c440-4812-b818-b591e4d8cedd)

The most frequent day is 5 which represents Saturday back from the weekday column I created 

For Cyclistic to maximize the results and effective usage of digital media to influence casual riders to become members. We need to use these insights as part of the marketing strategies we are imploring.

# SUMMARY
Cyclistic Bike Share data reveals that annual members make up 59.9% of its ridership, while casual riders make up 40.1%. Casual riders tend to take longer rides and travel greater distances than annual members. Casual riders use classic bikes and electric bikes as most preferred bikes. Popular stations for annual members include Kingsbury St & Kinzie St, while casual riders favor Streeters Dr & Grand Ave. To increase annual membership, Cyclistic could offer targeted promotions to casual riders at high-demand and popular stations. To promote popular stations, we could use digital media to increase awareness and usage of these locations, while also optimizing station locations to better serve riders. Overall, Cyclistic has a wealth of data at our disposal, and by leveraging it effectively, we can better meet the needs of our riders and continue to grow our business.

# RECOMMENDATIONS
1. Increase Annual Membership: Given that casual riders tend to take longer rides and travel longer distances, Cyclistic could offer targeted promotions to attract more annual members. For instance, we could offer discounts or free ride credits to new annual members who commit to an annual membership. We could also offer special rates for weekday rides or develop packages that incentivize more frequent use. By targeting casual riders who are already inclined to Cyclistic’s service, Cyclistic could increase annual membership from 59.9% to 70%.

2. Promote Popular Stations through Digital Media: Cyclistic could use digital media to increase awareness and usage of popular stations such as Kingsbury St & Kinzie St and Streeters Dr & Grand Ave. We could target ads to users who live or work near these stations, highlighting the convenience and benefits of riding from these locations. We could also partner with local businesses to offer promotions to new annual members with riders who start or end their ride at these stations, further incentivizing annual membership by promoting popular stations through targeted digital media campaigns, we could increase overall usage of these locations.

3. Finally, by understanding the rideable type preferences of casual riders, Cyclistic could consider offering targeted promotions or discounts on electric bikes, which have the potential to be more expensive, to encourage casual riders to switch to an annual membership.
