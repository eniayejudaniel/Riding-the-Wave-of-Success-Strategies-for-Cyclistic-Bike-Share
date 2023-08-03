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
