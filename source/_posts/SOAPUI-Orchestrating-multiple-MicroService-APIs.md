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

Service 1 : ZipCodeApi.com 
 