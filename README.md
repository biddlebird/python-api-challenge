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

### Data Visualization
With the collected weather data, I created a series of scatter plots to explore the relationships between latitude and various weather parameters. Specifically, I visualized:

Latitude vs. Temperature
Latitude vs. Humidity
Latitude vs. Cloudiness
Latitude vs. Wind Speed
These scatter plots allowed me to observe patterns and trends in how each weather variable changes with proximity to the equator. Each plot was carefully labeled and color-coded to highlight any notable correlations.

### Linear Regression Analysis
To further analyze the relationship between latitude and weather variables, I performed linear regression analysis on each pair of data points. The goal was to determine if there was a statistically significant trend between latitude and each weather parameter. I computed the linear regression line, the regression equation, and the R-value for each plot. Additionally, I split the data into two groups based on hemispheres—Northern Hemisphere (latitude ≥ 0) and Southern Hemisphere (latitude < 0)—to identify any differences in trends between the two regions. This approach provided a clearer understanding of how latitude influences weather patterns across the globe.

### Key Findings
Through the analysis conducted in WeatherPy, several key findings emerged:

- Latitude vs. Temperature: As expected, temperature showed a clear trend with latitude. Temperatures were highest near the Equator (0º latitude) and gradually decreased as one moved toward the poles. This confirms the well-known phenomenon that regions closer to the Equator tend to be warmer, while those near the poles are colder.
- Latitude vs. Humidity: There was no strong correlation between latitude and humidity, as indicated by the low R-value. However, some patterns suggested that humidity levels might be slightly higher near the Equator and lower at higher latitudes. The data showed considerable variation, suggesting that other factors may influence humidity more strongly than latitude alone.
- Latitude vs. Cloudiness: Cloudiness also did not exhibit a strong correlation with latitude. However, a pattern emerged where cloudiness was often clustered around 0% or 100%, with fewer instances of moderate cloudiness. This suggests that certain latitudes may experience extreme cloud conditions—either very clear or very cloudy—rather than a balanced mix.
- Latitude vs. Wind Speed: Wind speeds were generally lower near the Equator and higher at the poles, with the highest wind speeds observed at latitudes furthest from the Equator. This finding aligns with the understanding that wind speeds are often influenced by the Earth's rotation and the distribution of atmospheric pressure systems, which vary by latitude.

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

### Hotel Data Integration
To enhance the value of the map visualizations, I integrated hotel data using the Geoapify API. For each city that met the weather criteria, I queried the API to find the nearest hotel within a 10,000-meter radius. The hotel names and countries were then added to the map as hover information, enriching the interactive experience. This integration allowed users not only to identify ideal vacation destinations based on weather but also to find convenient accommodation options in those areas. By incorporating hotel data into the map visualizations, I provided a more comprehensive tool for planning vacations, combining both weather and lodging considerations into a single, easy-to-use interface.

## Acknowledgements

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)
- [Thay Chansy](https://github.com/thaychansy)
- [Nate Sheibley](https://github.com/Nate-Sheibley)
- [Brian Perry](https://github.com/bperry555)
