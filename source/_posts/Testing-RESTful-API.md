---
title: Testing RESTful API
date: 2016-04-05 06:12:44
categories:
- tools
tags:
- REST
- SoapUI
---
Nowadays in Internet there are a lot of public APIs and most of them are REST APIs. In this post I am going to use SoapUI to test weather service API published by [openweathermap.org](https://home.openweathermap.org/). <!-- more --> A detailed documentation can be obtained from [how to start guide](http://openweathermap.org/appid).

### Obtain API Key
In order to access the service you will need an API key, you can register with your email at https://home.openweathermap.org/ to receive and activate the key.

### Test manually the functionality
The website provides GUI to access and validate the functionaly. You can play around with that to get the information on the parameters that are needed for the API to work. So the URL will be something like `api.openweathermap.org/data/2.5/weather?q=chantilly,us&appid=xxxxxx`.

### SoapUI project
In SoapUI, you must create a REST project and add the following URL
`http://api.openweathermap.org/data/2.5/weather?q=Chantilly,us&appid=xxxxxx`

#### Create a TestSuite and TestCase
You can right click on the GET request, and add it to a new TestSuite. The screenshot below shows the request and corresponding JSON response received.
![](../downloads/weather/3.png)

#### Add assertions
I will add the following assertion to validate the content of the response.
 - Specify JSONpath expression to check the Longitude and Latitude are valid or not.
 - JSON path match valid or not
 - Specify JSONpath existance match valid or not

The screenshot below shows the assertions that were added to the testcase.
![](../downloads/weather/4.png)
        
That is all you need to do to test this RESTful endpoint. A working project is available in [soapui_weatherapp repository](https://github.com/manjupaul/soapui_weatherapp).
        

 

