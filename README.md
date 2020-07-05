# llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT
Smart Agriculture system based on IoT.

### IBM Cloud

The whole project is based on IBM Cloud service. First I had to create an account in [IBM Cloud](https://cloud.ibm.com/login). Then create the Internet of Things Platform Service from the catalog.

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/IBM%20Cloud.png)

Launch the service after creating it. 

### IBM IoT Platform

After launching the service from the IBM CLoud. It will redirect you to [IBM Watson IoT Platform](https://internetofthings.ibmcloud.com/). Here we have to create couple of devices, one device will be for transmitting the data from sensor to the mobile application while other will be for receiving any command from the aplication.

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/IBM%20Devices.png)

Next we have to create an API Key. An API key or ***application programming interface key*** is a code that gets passed in by computer applications. The program or application then calls the API or application programming interface to identify its user, developer or calling program to a website.

*NOTE: You should also copy the API Key and auth-token along with the device identity.*

### Installing the Node-Red

#### 1. Install Node.js

Download the latest 10.x LTS version of Node.js from the official [Node.js home page](https://nodejs.org/en/). It will offer you the best version for your system.

Run the downloaded MSI file. Installing Node.js requires local administrator rights; if you are not a local administrator, you will be prompted for an administrator password on install. Accept the defaults when installing. After installation completes, close any open command prompts and re-open to ensure new environment variables are picked up.

Once installed, open a command prompt and run the following command to ensure Node.js and npm are installed correctly.

Using cmd: node --version && npm --version

You should receive back output that looks similar to:

v10.16.3

6.11.3

#### 2. Install Node-RED

Installing Node-RED as a global module adds the command node-red to your system path. Execute the following at the command prompt:

**npm install -g --unsafe-perm node-red**

#### 3. Run Node-RED

Once installed, you are ready to run Node-RED.

Use the command **node-red** in Node.js

### Installing Python IDLE 3

The Python 3.8 series is the newest major release of the Python programming language, and it contains many new features and optimizations. It is available at [Python's Official site](https://www.python.org/downloads/release/python-382/).

This is required to run the code for recieving the command from the mobile application. 

### Connecting the IoT Simulator to the Watson IoT platform.

One of the device created in the IBM Watson IoT Platform will have to recieve the data from a sensor. I used the IBM's [Bluemix IoT Sensor](http://watson-iot-sensor-simulator.mybluemix.net/) simulator and then I connected it to the device created in Watson IoT Platform.

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/IBM%20Sensor.png)

### Creating a Node-red UI to view data in graphical form

To install IBM nodes in Node-red flow editor click on manage palette in the menu option which is on the top-right of the screen. 

In install section search for ibmiot and install the ibm nodes to flow editor. 

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/Node%20Palette.png)

Further we need to install the dashboard nodes if they aren't installed already.

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/Node%20Dashboard.png)

### Building the Web Application

This flow pulls weather data from OpenWeatherMap (OWM) then presents it in a dashboard showing current weather conditions along with forecasts for the next 6 hours and 6 days. The mix of text and icons creates a compact and attractive display.

![image](https://user-images.githubusercontent.com/5475317/84967619-a3bdcd80-b0d1-11ea-89bb-452d0387316c.png)

Moreover there are also different tabs that shows the data pulled from the bluemix sensor. These are the temperature, humidity and the mositure level of the soil.

1. No Custom Nodes
The OpenWeatherMap custom node is good but it doesn't use the new One Call API. So I used standard nodes which was fairly easy. The HTTP call is simple and JSON data is returned which is perfect for Node-Red.

2. Weather Icons
I used the "lite" set of weather icons which are now included in Node-Red. No need to install an icon set.

3. Setup and Configuration of Open Weather Map

Go to [OpenWeatherMap](https://openweathermap.org/) and sign up for a free account to get an API key.

Open the node labeled "Set location, appid, units" and change these parameters:
* Change `msg.payload.lat` to your latitude.
* Change `msg.payload.lon` to your longitude.
* Change `msg.payload.appid` to your API key.
* Change `msg.payload.units` to imperial or metric.

NOTE: You can get your latitude and longitude by looking up your town in OpenWeatherMap.

#### One Call
I used the new [One Call API](https://openweathermap.org/api/one-call-api) from OpenWeatherMap that returns all this data:
* Minute forecast for 1 hour
* Hourly forecast for 48 hours
* Daily forecast for 7 days
* Historical data for 5 previous days

![image](https://user-images.githubusercontent.com/5475317/84967765-01eab080-b0d2-11ea-81c5-4f5d48b53d14.png)

#### Setup and Configuration of IBM IoT

Open the node labeled "IBM IoT" and change these parameters:
* Change `msg.applicationId` to your API Key from the Watson IoT Platform:
* Change `msg.deviceType` to your Device Type.
* Change `msg.deviceId` to your Device ID.

![image](https://github.com/SmartPracticeschool/llSPS-INT-2735-Smart-Agriculture-system-based-on-IoT/blob/master/Node-Red%20Dashboard.png)

flow link.


### Configure Your Device To Receive The Data From The Web Application And Control Your Motors

Copy the given folder link.
