# Bike Sharing Demand Prediction With Regression Models and GridsearchCV

![BikeShare](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/image1.jpg)

This project has below modules:
- [Business Understanding](#business-understanding)
- [Data Understanding](#data-Understanding)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Feature Engineering](#feature-engineering)
- [Modeling and Performance Tuning](#modeling-and-performance-tuning)
- [Model Evaluation](#model-evaluation)
- [Conclusion](#conclusion)
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
The Dataframe has below features :
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
   > 94 = Freezing Fog.
    
* from the above, we can see the few rows of Bikesharing dataframe:
   * The dataframe has 17414 entries, from 0 to 17413.
   * All the features in the dataframe are numerical.
   * We have categorical features such as Weathercode, isholiday, isweekend, season.
   * There are **0** Null values inthe complete dataframe.
   * The timestamp feature is splitted into Day, Month, Year and Hours features.

## Exploratory Data Analysis
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/Correlation_Matrix.png)
* from the above correlation matrix we can see that there is a positive linear relationship between the features t1, t2, hour, windspeed and cnt.
* we can also see that there is negative linear relationship between hum and cnt.
* there is no linear relationship with cnt and other features.

![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/countVSlinearvariables.png)

#### Temparature VS count in different seasons:
* From the above plots we can see that the bike sharing is high in season1,2(**Summer,Fall**) and low in season4(**Winter**) and Moderate in season0(**Spring**) 
#### Temparature Feelslike VS count in different seasons:
* From the above plots we can see that the bike sharing is high in season1,2(**Summer,Fall**) and low in season4(**Winter**) and Moderate in season0(**Spring**) 

![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/countvscategoricalvariables.png)
#### weekend VS count:
* from the above boxplot we can say that the median of bike sharing is higher in weekdays which is **0** and low during weekend which is **1**.
#### Month VS count:
* from the above boxplot we can say that the median of bike sharing is higher in Months like 7,6,8,5,9 and moderate in 4,10 and low in remaning months.
#### hour VS count:
* from the above boxplot we can say that the median of bike sharing is higher during the hours 7,8,9,17,18,19.
#### Holiday VS count:
* from the above boxplot we can say that the median of bike sharing is higher in Non Holidays which is **0** low during holidays which is **1**.
#### Season VS count:
* from the above boxplot we can say that the median of bike sharing is higher in season **1** summer.
#### Weather VS count:
* from the above boxplot we can say that the median of bike sharing is higher in weather_code **1,2,3**.

## Feature Engineering
#### Normalization with MinMaxScalar:
 MinMaxScalar scales each input variable separately to the range 0-1, in the above data frame the features 't1','t2','hum','wind_speed' are in high scale compare to the other features to normalize the data we applied the MinMaxScalar on the above features.

#### Onehotencoding with pandas:
A one hot encoding is a representation of categorical variables as binary vectors, A one hot encoding allows the representation of categorical data to be more expressive.
we applied the onehot encoding on the categorical features 'Weather_code','season','weekend','holiday'.

After applying the Minmaxscalar and onehot encoding on the features we got the dataframe with 24 features as below.
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/Dataframe%20(2).png)

## Modeling and Performance Tuning
#### Regression Models

* By predicting the Bike sharing demand on daily basis using the Linear regression models and error evaluation metric as Root Mean Square Error i got errors for each model as     below.
* Without tuning the performance metrics we got the best results with Linear Regression model with Test_RMSE as 905.633076  where as the Train RMSE is 885.999083.
		
|     Model          | Train RMSE         | Tuning Parameters  |      Test RMSE     |
| :------------------| :------------------| :------------------| :------------------|
| Linear_Regression  | 885.999083         | none               | 905.633076         |
| Lasso              | 886.790976         | none               | 906.141956         |
| Ridge              | 886.086497         | none               | 905.764295         |
| Elastic            | 886.944678         | none               | 906.506568         |

#### Regression Models With GridSearchCV

* **Lasso With GridsearchCV**
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/alphavsRMSElasso.png)

	* By using the GridsearchCV with CV as 10 and different alpha values we got the RMSE error as above plot.
	* We can see that the RMSE value increases as the alpha value increases from 0.0
	* The Optimal alpha value where the RMSE value is low is 'alpha': 0.0010000000000000024.

* **Ridge With GridsearchCV**
![DataFrame](https://github.com/PurushothamVadde/Bike-Demand-Prediction-With-Regression-Models-and-GridsearchCV/blob/main/Images/alphavsRmseridge.png)

	* By using the GridsearchCV with CV as 10 and different alpha values we got the RMSE error as above plot.
	* We can see that the RMSE value increases as the alpha value increases from 0.0
	* The Optimal alpha value where the RMSE value is low is 'alpha': 0.03162277660168379.
	
* **Elastic With GridsearchCV**
	* By using the GridsearchCV with CV as 10 and different alpha values and l1 norm  we got the RMSE  error as 886.851187.
	* We got the optimal solution at 'alpha': 1.5848931924611134e-05, 'l1_ratio': 0.8.
	
|     Model                            | Train RMSE         | Tuning Parameters                                  |      Test RMSE     |
| :----------------------------------- | :------------------| :------------------------------------------------- | :------------------|
| Linear_Regression                    | 885.999083         | none                                               | 905.633076         |
| Lasso_with_GridsearchCV              | 886.790976         | {'alpha': 0.0010000000000000024}                   | 886.851327         |
| Ridge_with_GridsearchCV              | 886.086497         | {'alpha': 0.03162277660168379}                     | 886.851185         |
| Elastic_with_GridsearchCV            | 886.944678         | {'alpha': 1.5848931924611134e-05, 'l1_ratio': 0.8} | 886.851187         |

## Model Evaluation
From the below table we can see that we got the best results by parameter tuning and we got the least RMSE value for Ridge_with_GridsearchCV and Elastic_with_GridsearchCV models.

|     Model                            | Train RMSE         | Tuning Parameters                                  |      Test RMSE         |
| :----------------------------------- | :------------------| :------------------------------------------------- | :----------------------|
| Linear_Regression                    | 885.999083         | none                                               | 905.633076             |
| Lasso              		       | 886.790976         | none                                               | 906.141956             |
| Ridge                                | 886.086497         | none                                               | 905.764295             |
| Elastic                              | 886.944678         | none                                               | 906.506568         	  |
| Lasso_with_GridsearchCV              | 886.790976         | {'alpha': 0.0010000000000000024}                   | **886.851327**         |
| Ridge_with_GridsearchCV              | 886.086497         | {'alpha': 0.03162277660168379}                     | **886.851185**         |
| Elastic_with_GridsearchCV            | 886.944678         | {'alpha': 1.5848931924611134e-05, 'l1_ratio': 0.8} | **886.851187**         |


## Conclusion

By this project we are able to predict the Bike sharing demand on daily basis with more accuracy. the Bike sharing companies can use this project for predicting the demand of bike sharing which helps them in managing the bikes in correct manner which helps in increase of profits.
