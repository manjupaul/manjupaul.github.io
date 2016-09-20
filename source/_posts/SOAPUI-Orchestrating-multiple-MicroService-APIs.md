---
title: SOAPUI - Orchestrating multiple MicroService APIs
draft: true
date: 2016-09-16 10:10:54
categories:
- tools
tags:
- REST
- SoapUI
---

Internet of MicroServices is the backbone on which IOT stands. Amazon Echo playing music from your album or Camera uploading the photos you take directly to Google Photos etc. When you make an order in Amazon, the ordering system will ask the Inventory system to hold the items, and when payment is made it will ask shipping system to process the shipment. Well, testing this fictitious Amazon servies is not in scope. In this post I will show how SoapUI can be used to orchestrate two dispirate RESTful webservice. 

###  The plot
Find the Congressman in your city. 
For this, here I used two public REST API services.
Service 1 : [ZipcodeAPI](https://www.zipcodeapi.com) - Has web service endpoints that can return the zip codes within a city.
Service 2 : [Sunlight Lbs](https://sunlightlabs.github.io/congress/index.html) Has web service endpoints that can locate the legislator based upon zip code.

 Next I am going to show how to write a TestCase that accesses public REST Webservice endpoints.The idea is to first identify the zip code using the city/state name and then use these zipcode to figure out the current senator.
 Let's first test it manually and see how it is functioning.  
    
  First you have to [Register for API key](http://www.zipcodeapi.com/API#zipToLoc). Use this API, to pass the parameter city name thenit shows the zipcode.  The JSON and XML responses will allow contain alternative acceptable city names for a location. 
  
  Example :http://www.zipcodeapi.com/rest/PfcLH5o2y033eqSQpuvVRsfJGTwS2ruSHHDpN2rl3vohVg8lLEhC7wlNqSFtk9l2/info.xml/20152/degrees
  
  Add picture  ![](../downloads/weather/3.png)
  
  Here we passed the parameter zipcode is 20190 and result is Reston
  
 Next I am going to use [sunlightlabs] (https://sunlightlabs.github.io/congress/index.html).Here it provides the details on how to access the web service.In order to access the service, we need to obtain an [API key](http://sunlightfoundation.com/api/accounts/register/).  
 Let's see how to test this manually using the web interface.
    
  Addpic 2
  
 Testing using RESTAPI service
 Step1 :Create a new REST project in SoapUI and add the zipcodeapi webservice endpoint.ie https://www.zipcodeapi.com//rest/apikey/city-zips.xml/Reston/va.
 
Step 2 : Add  Sunlight congress API /legislators/locate?zip=xxxx. Add this request to SoapUI Rest project.
End point :https://sunlightlabs.github.io/congress/index.html/legislators/locate/?zip=xxxx&apikey=xxxxx

Step 3 :Create a test suite under this rest project and add these two requests into one test suite

Step 4 : Add property transfer between these two test cases.Property Transfer enables us to transfer the values of zipcode from Zipcode RestfulAPI Response to Sunlight congress API Request.When we create a property transfer it will ask Source,property and target,property.

add picture 3----property transfer

Step 5 : Run the TestSuite  and check the result

add picture 4 

step 6: Add some assertions and execute this.



  
  
  
  
  
 