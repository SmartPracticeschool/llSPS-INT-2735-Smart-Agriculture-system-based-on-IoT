# llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT
Smart Agriculture system based on IoT.

This flow pulls weather data from OpenWeatherMap (OWM) then presents it in a dashboard showing current weather conditions along with forecasts for the next 6 hours and 6 days. The mix of text and icons creates a compact and attractive display.

This version is formatted in a portrait orientation.

![image](https://user-images.githubusercontent.com/5475317/84967619-a3bdcd80-b0d1-11ea-89bb-452d0387316c.png)

### One Call
I used the new [One Call API](https://openweathermap.org/api/one-call-api) from OpenWeatherMap that returns all this data:
* Minute forecast for 1 hour
* Hourly forecast for 48 hours
* Daily forecast for 7 days
* Historical data for 5 previous days

### No Custom Nodes
The OpenWeatherMap custom node is good but it doesn't use the new One Call API. So I used standard nodes which was fairly easy. The HTTP call is simple and JSON data is returned which is perfect for Node-Red.

### Weather Icons
I used the "lite" set of weather icons which are now included in Node-Red. No need to install an icon set.

## Setup and Configuration

Go to [OpenWeatherMap](https://openweathermap.org/) and sign up for a free account to get an API key.

Open the node labeled "Set location, appid, units" and change these parameters:
* Change `msg.payload.lat` to your latitude.
* Change `msg.payload.lon` to your longitude.
* Change `msg.payload.appid` to your API key.
* Change `msg.payload.units` to imperial or metric.

*NOTE: You can get your latitude and longitude by looking up your town in OpenWeatherMap.*

![image](https://user-images.githubusercontent.com/5475317/84967765-01eab080-b0d2-11ea-81c5-4f5d48b53d14.png)
