---
title: RESTful API - Basics
date: 2016-03-22 03:13:08
categories:
- tools
tags:
- REST
- API
---
A _very minimal_ overview of REST. REST stands for Representational State Transfer. It is an architectural style originally described by Roy Fielding, one of the authors of HTTP 1.0 and 1.1, in a doctoral dissertation at UC Irvine in 2000. 

#### Why is REST so famous ? 
Towards the beginning of this decade, a lot of companies started making their applications and services available on Internet. Also, they are moving service APIs which otherwise was protected behind the firewall,to the wilderness of Internet. HTTP being the defacto communication protocol used in Internet, REST that blends well with HTTP has made it a good choice. 

#### Concepts
- URL - Stands for Uniform Resource Locator, for example `http://hilton.com/chantilly/rooms/25`
- Resource - The information or entity that is identified by a URL, example Room number 25 
- Representation - How it is represented. JSON, XML or HTML etc, by default RESTful APIs use JSON. 

REST vocabulary consists of mainly 4 HTTP actions/verbs, the `GET`, `PUT`, `POST` and `DELETE`. Let us see how they are getting used:
 
#### GET
 A `GET` request to a URL signify that you need to retrieve the resource. Example `GET http://hilton.com/chantilly/rooms/25` is supposed to respond with a JSON consisting the details of Room 25. 
```json
{
    room:"25",
    cost: "500.50",
    beds: "2",
    floor: "2",
    ..........,
    ..........
    
}
```
Alternately a `GET` on `rooms` example `GET http://hilton.com/chantilly/rooms/` will return an Array that has details of all the rooms available in the hotel. 

### DELETE
 A `DELETE` request to a URL will remove the entity represented by the URL. Example `DELETE http://hilton.com/chantilly/rooms/25` will delete Room 25 from the hotel.
 
### PUT
 A `PUT` request to a URL will create an entity in the system. The representation of the entity you want to create must be provided in HTTP Request Body. The example below adds Room 25 to the list of available rooms in the hotel. 
 ```json
 POST http://hilton.com/chantilly/rooms/
 {
     room:"25",
     cost: "500.50",
     beds: "2",
     floor: "2",
     ..........,
     ..........
     
 }
 ```
 
### POST
 A `POST` request to a URL will update an entity in the system. The representation of the entity must be provided in HTTP Request Body. The example below updates the number of beds from 2 to 3 in  Room 25 of the hotel.  
 ```json
 POST http://hilton.com/chantilly/rooms/25/
 {
     room:"25",
     cost: "500.50",
     beds: "3",
     floor: "2",
     ..........,
     .........., 
 }
 ```
 
It is quite easy to work and test REST API. To play around you can use public APIs you can find a lot at [Programmable Web](http://www.programmableweb.com/apis). I will shortly post on how SOAPUI can be used to test API published by Weather.com. 