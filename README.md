# Python API Challenge

For this module assignment, I started by creating a new GitHub repository called `python-api-challenge` and organized my project files within it. In Part 1, **WeatherPy**, I used Python libraries and APIs to gather weather data from over 500 cities around the world. I focused on visualizing the relationship between latitude and various weather variables like temperature, humidity, cloudiness, and wind speed. To delve deeper into these relationships, I computed linear regressions and separated the data by the Northern and Southern Hemispheres to identify any notable trends.

In Part 2, **VacationPy**, I took the weather data analysis a step further by planning potential vacations based on ideal weather conditions. I utilized the Geoapify API and the geoViews Python library to create interactive maps that display the weather data visually. I also filtered the data to pinpoint locations with specific weather criteria, such as mild temperatures and low wind speeds, and mapped the nearest hotels for each city. Throughout the project, I ensured my API keys were securely managed by using a `.gitignore` file, and I committed my work to GitHub as I progressed. This hands-on experience allowed me to apply my Python skills to solve real-world problems using data.

## Dependencies 

For VacationPy
```
import hvplot.pandas
import pandas as pd
import numpy as np
import requests
from api_keys import geoapify_key
import datetime
```
For WeatherPy
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import time
from scipy.stats import linregress
from api_keys import weather_api_key
from citipy import citipy
```
## Part 1: WeatherPy

### Data Collection
To collect weather data, I utilized the OpenWeatherMap API, which provides access to real-time weather data for cities around the world. I began by generating a list of random geographic coordinates using Python, and then used the citipy library to find the nearest cities to these coordinates. This approach ensured a diverse and global selection of cities. Once the city list was compiled, I made API requests to OpenWeatherMap to retrieve weather data, including temperature, humidity, cloudiness, and wind speed, for over 500 cities.

#### Data Visualization
With the collected weather data, I created a series of scatter plots to explore the relationships between latitude and various weather parameters. Specifically, I visualized:

##### Linear Regression Analysis
To further analyze the relationship between latitude and weather variables, I performed linear regression analysis on each pair of data points. The goal was to determine if there was a statistically significant trend between latitude and each weather parameter. I computed the linear regression line, the regression equation, and the R-value for each plot. Additionally, I split the data into two groups based on hemispheres—Northern Hemisphere (latitude ≥ 0) and Southern Hemisphere (latitude < 0)—to identify any differences in trends between the two regions. This approach provided a clearer understanding of how latitude influences weather patterns across the globe.

##### Latitude vs. Temperature
As latitude approaches 0º (the Equator), temperatures rise to a peak of 41.07ºC. Moving away from the Equator, temperatures steadily decrease, reaching a low of -10.24ºC. The coldest temperatures are found near the poles, while the Equator experiences the highest temperatures.

![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/1.Lat.Temp.North.png)
![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/2.Lat.Temp.South.png)

##### Latitude vs. Humidity

There is a weak correlation between humidity and latitude, as indicated by an R-value close to 0. This suggests that the linear regression line does not fit the data well, and no consistent trend is apparent. While there may be a slight indication of lower humidity levels near the Equator, further analysis is needed to confirm any significant patterns. 

![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/3.Lat.Hum.North.png)
![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/4.Lat.Hum.South.png)

##### Latitude vs. Cloudiness

The line of best fit is not an ideal method for evaluating this data set, as the R-value is close to 0, indicating a poor fit. However, a noticeable pattern emerges, with 'cloudiness' often clustering near 0% or 100%, leaving a gap in the middle of the graph. A more effective approach might be to calculate the average cloudiness at each latitude over several years to better understand the correlation. Additionally, breaking the data down by seasons and comparing the Northern and Southern Hemispheres could provide further insights into how cloudiness varies with latitude.

![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/5.Lay.Cloud.North.png)
![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/6.Lay.Cloud.South.png)

##### Latitude vs. Wind Speed

While the line of best fit doesn't clearly define the trend, it's evident that the average wind speed hovers around 6 m/s. By removing extreme outliers and calculating the average, we could gain valuable insights into global wind patterns. It's important to note that the highest wind speeds in both the Northern and Southern Hemispheres are found farthest from the Equator, while the lowest wind speeds occur much closer to the Equator.

![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/7.Lat.Wind.North.png)
![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/WeatherTrends/8.Lat.Wind.South.png)

These scatter plots allowed me to observe patterns and trends in how each weather variable changes with proximity to the equator. Each plot was carefully labeled and color-coded to highlight any notable correlations.

Overall, the analysis confirmed some expected trends, such as the temperature-latitude relationship, while also revealing more nuanced patterns in humidity, cloudiness, and wind speed. These findings offer valuable insights into how weather variables interact with latitude, though further analysis could explore additional factors and seasonal variations.

## Part 2: VacationPy

### Weather Conditions Filtering
In this part of the project, I filtered the cities based on specific weather criteria to identify ideal vacation spots. The criteria included:
- A maximum temperature between 21ºC and 27ºC, which is generally considered comfortable for outdoor activities.
- Wind speeds less than 4.5 m/s to ensure pleasant conditions for travelers.
- Zero cloudiness to maximize the likelihood of sunny weather.

I applied these filters to the weather data collected in WeatherPy, narrowing down the list of cities to those that met all the conditions. This filtered dataset was then prepared for further analysis and visualization, focusing on locations that offer the most favorable weather for vacations.

### Map Visualization
Using the `geoViews` Python library, I created interactive maps to visualize the filtered weather data. The maps displayed a point for each city, with the size of the point representing the humidity level. This allowed for a clear and interactive way to identify regions with ideal weather conditions at a glance. By hovering over each point, users could see additional information about the city, such as its name and specific weather details. This visualization provided a powerful tool for quickly assessing the best vacation spots based on real-time weather data.

![alt text](https://github.com/biddlebird/python-api-challenge/blob/main/map.png) 

### Hotel Data Integration
To enhance the value of the map visualizations, I integrated hotel data using the Geoapify API. For each city that met the weather criteria, I queried the API to find the nearest hotel within a 10,000-meter radius. The hotel names and countries were then added to the map as hover information, enriching the interactive experience. This integration allowed users not only to identify ideal vacation destinations based on weather but also to find convenient accommodation options in those areas. By incorporating hotel data into the map visualizations, I provided a more comprehensive tool for planning vacations, combining both weather and lodging considerations into a single, easy-to-use interface.

## Acknowledgements

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)
- [Thay Chansy](https://github.com/thaychansy)
- [Nate Sheibley](https://github.com/Nate-Sheibley)
- [Brian Perry](https://github.com/bperry555)
