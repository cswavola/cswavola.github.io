---
layout: page
title:  "Whether to Cycle"
description: Predict bike share usage with machine learning algorithms
date:   2017-12-10 17:49:38 +0100
category: Machine Learning
language: Python
links_as: buttons
permalink: /_projects/bikeshare
image: false

---
<div id="nav" class="clearfix">
<a href="#1">Introduction</a>  
<a href="#2">EDA and Pipeline</a>  
<!-- <a href="#3">Models</a> -->
<!-- <a href="#4">Performance</a> -->
</div>
<br>
<h1>Summary</h1>
Application of machine learning to predict bike share usage in Washington D.C.. Design and implementation of data pipeline, tested across multiple regression and decision models with performance output. Submitted to a Kaggle competition.
<br>


<hr class="style-thin">

<br>
<h1><a name="1"></a>Introduction</h1>
This project uses machine learning techniques to predict hourly bike rental demand in the Capital Bikeshare program in Washington, D.C.. The learning algorithms combine historical usage patterns with weather data such as temperature, humidity, windspeed and weather conditions.

Using bike sharing systems, people rent a bike from a one location and return it to a different place on an as-needed basis. The process of obtaining membership, rental, and bike return is automated and tracked via a network of kiosks around the city. The duration of travel, departure location, arrival location, and time elapsed is recorded. The data consists of hourly rental data spanning two years. The training set is comprised of the first 19 days of each month, while the test set is the 20th to the end of the month.

<img src="/assets/images/EDA_count.PNG" alt="drawing" />
<br><br>


<h1><a name="2"></a>EDA and Pipeline</h1>
The data consists of hourly rental data spanning two years. The training set is comprised of the first 19 days of each month, while the test set is the 20th to the end of the month.
The features include:
- a datetime stamp for bike sharing event
- numeric values to categorize holidays, work days, seasons (1-4) and weather conditions (1-4)
- numeric values to quantify the temperature, actual temperature, humidity and windspeed. These quantity values are fairly normally distributed with different means.
The predictors include a total hourly count of bike sharing events, also split into two separate counts for registered and casual users.
<br>
![EDA_features]({{ "/assets/images/EDA_features.PNG"  }})
<br>

For processing purposes, the features were transformed as such:
- Datetime feature creation - transformed the timestamp into individual variables for hour, day, month and year
- Categorical datatype - the data set included 4 integer variables which were converted into categorical data type: Season, holiday, workingday, weather
- Numeric scaling - the measurement values for temperature, humidity and windspeed were scaled to normalized z-scores

Additionally, the training set was split to include a dev set. Models were tested using casual and registered output variables as well as the total count in the training and dev sets.





<!-- <h1><a name="3"></a>Models</h1> -->
<!-- <h1><a name="4"></a>Performance</h1> -->
