---
title: Testing RESTful API
date: 2016-09-16 07:12:44
draft: true
categories:
- tools
tags:
- REST
- SoapUI
---
Step1:

I am going to test a current weather data using RESTAPI service
Step 1: Singn on https://home.openweathermap.org/ and get the API key.I created account on openweathermap.org  after that I can access the API key.

Step 2: Goto http://openweathermap.org/current.

 Here I am going to call current weather data for one location by city and country code.
         API call : api.openweathermap.org/data/2.5/weather?q={city name},{country code}
         Parameter q : q city name and country code divided by comma, use ISO 3166 country codes.
         
Example of API calls:http://api.openweathermap.org/data/2.5/weather?q=London,uk&appid=xxxxxx

Step 3: Create a new REST project  and type  URL = http://api.openweathermap.org/data/2.5/weather?q=Chantilly,us&appid=xxxxxx

https://raw.githubusercontent.com/manjupaul/manjupaul.github.io/sources/ref/weather/2.png 

Step 4: When we run the GET request, we will get the all data based on parameter we passed.

https://raw.githubusercontent.com/manjupaul/manjupaul.github.io/sources/ref/weather/3.png 

Now you can see a nicely formatted JSON response in the JSON view .

Step 5: Time to add an actual assertion to validate the content of the response.


