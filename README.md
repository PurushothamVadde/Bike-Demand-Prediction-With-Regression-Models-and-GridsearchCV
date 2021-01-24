# Bike Demand Prediction With Regression Models and GridsearchCV

![BikeShare](https://github.com/PurushothamVadde/Bike_Demand_Prediction/blob/main/Images/image1.jpg)

## Business Understanding
#### Project Goal:
The goal of the project is to work on the Bike share Dataset and predict the demand of Bikes sharing on daily basis by building the Regression Models and GridsearchCV.
#### Practical use:
* The project will help the Bike Sharing Companies to solve the realtime problems such as:
    * By knowing the demand the companies can plan in better way to meet the demand.
    * Better planning on seasons when there is high demand.
    * Better planning on the days/hours have high demand.
    * Increase the profit by managing the bikes based on demand.
  
 Data Source: Https://cycling.data.tfl.gov.uk/
## Data Understanding
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/Dataframe.png)

**timestamp** :timestamp field for grouping the data\
**cnt** :the count of a new bike shares\
**t1** :real temperature in C\
**t2** :temperature in C "feels like"\
**hum** :humidity in percentage\
**windspeed** :wind speed in km/h\
**weathercode** :category of the weather\
**isholiday** :boolean field - 1 holiday / 0 non holiday\
**isweekend** :boolean field - 1 if the day is weekend\
**season** :category field meteorological seasons:
   > 0-spring\
   > 1-summer\
   > 2-fall\
   > 3-winter.
   
**weathe_code** :category description:
   > 1 = Clear mostly clear but have some values with haze or fog or patches of fog or fog in vicinity.\
   > 2 = scattered clouds or few clouds.\
   > 3 = Broken clouds.\
   > 4 = Cloudy.\
   > 7 = Rain or light Rain shower or Light rain.\
   > 10 = rain with thunderstorm.\
   > 26 = snowfall.\
   > 94 = Freezing Fog.\
    
* In the above table we can see the few rows of Bikesharing dataframe:
   * The dataframe has 17414 entries, from 0 to 17413.
   * All the features in the dataframe are numerical.
   * There are **0** Null values inthe complete dataframe.
   * The timestamp feature is splitted into Day, Month, Year and Hours features.

## Exploratory Data Analysis
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/Correlation_Matrix.png)
* from the above correlation matrix we can see that there is a positive linear relation ship

## Feature Engineering

## Modeling and Performance Tuning

## Model Evaluation and Conclusion
