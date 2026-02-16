---
layout: project
title: Airbnb - London
date: 2024-06-15 16:49
author: "Charles De Barros"
category: ['Projects', 'Portfolio']
tags: ['Projects', 'Portfolio']
image: "assets/images/post/airbnb_banner.jpg"
---

> Note: All the project's Jupyter Notebook files, including images and my notes, can be seen [here](https://drive.google.com/drive/folders/1Svg11idFDG7Rt2dI3GweODNkhkrn_Wg4?usp=sharing).

## Sources 
* [InsideAirBnb](http://insideairbnb.com/get-the-data.html)  
* [London data](http://insideairbnb.com/london/)  

## About the source

___Inside Airbnb___ is an independent, non-commercial set of tools and data that allows you to explore how Airbnb is really being used in cities around the world.  
The data behind the Inside Airbnb site is sourced from publicly available information from the Airbnb site and published under a Creative Commons CC0 1.0 Universal (CC0 1.0) "Public Domain Dedication" license.

<br>

## Airbnb info

Airbnb, Inc. is an American company operating an online marketplace for short- and long-term homestays and experiences. The company acts as a broker and charges a commission from each booking.

The company was founded in 2008 by Brian Chesky, Nathan Blecharczyk, and Joe Gebbia. Airbnb is a shortened version of its original name, AirBedandBreakfast.com. Airbnb is the most well-known company for short-term housing rentals.

The Airbnb headquarters is in San Francisco, CA, USA.

> Airbnb is listed as a Public Company.

| Airbnb Numbers | |
|---|---|
|  Revenue | US$5.99 billion (2023)  |
| Operating income | US$429 million (2023)  |
| Net Income | US$−352 million (2023)  |
| Total Assets  | US$20.6 billion (2023)  |
| Total equity  | US$8.17 billion (2023) 
| Owners | Brian Chesky (10%) |
|        | Nathan Blecharczyk (10%) |
|        | Joe Gebbia (7%) |
| Number of employees | 6,907 (2023) |

<br>

## Airbnb Corporate Affairs

| Year | Revenue  (US$ bn) | Net income  (US$ m) | Total assets (US$ bn)  [[108](https://en.wikipedia.org/wiki/Airbnb#cite_note-108)] | Employees  [[109](https://en.wikipedia.org/wiki/Airbnb#cite_note-109)] |
|:---|:---:|:---:|:---:|:---:|
| 2014 | 0.4 |||		
| 2015 | 0.9 |||	
| 2016 | 1.7 |||		
| 2017 | 2.6 | −70.5 | 6.0 ||	
| 2018 | 3.6 |	−16.8 |	6.6 ||
| 2019 | 4.8 |	−674 | 8.3 | 5,465 |
| 2020 | 3.3 |	−4,584 | 10.4 | 5,597 |
| 2021 | 5.9 |	−352 | 13.7 | 6,132 |
| 2022 | 8.3 |	1,893 |	16.0 |	6,811 |
| 2023 | 9.9 |	4,800 |	20.6 |	6,907 |

<br>

## Airbnb in London

![London Boroughs map](https://res.cloudinary.com/charlesdebarros/image/upload/v1751470860/airbnb_data_analytics_project/London_boroughs_map_eo9asn.png)

<br>

### Initial considerations
The data used for the analysis comes from a dataset from 2019, pre-COVID-19 pandemic consequences. The first COVID-19 case was only detected on the 12th of February 2020.  
There are 83850 rows of data ranging from property name/description to price and availability.
Airbnb is present in all 33 London Boroughs.  

<br>

### On Neighbourhoods

Out of the 33 London Boroughs, the most expensive borough to rent an Airbnb property, with rental prices of almost £15k, was Westmister, followed by Haringey, Hackney, Wandsworth and Merton.

The most affordable neighbourhood was Richmond-upon-Thames. Followed by Barking and Dagenham, Kingston-upon-Thames, Enfield, and the City of London.

An intereting fact is that the most expensive neighbourhood, Westminster, and one of the most affordable, the City of London, are close to each other. Both at the heart of London.

![Top 5 most expensive and most affordable Airbnb neighbourhoods in London](https://res.cloudinary.com/charlesdebarros/image/upload/v1751472978/airbnb_data_analytics_project/airbnb_top_5_most_expensive_affordable_london_2019__w1w8kb.png)


### On room types

The most commonly available rental option in London is the _entire home/flat_, with almost 5000 locations available. _Private rooms_ are the second most available, a little short of 5000 locations. _Shared room_ rentals are the least available option. 

![Airbnb - room types availability](https://res.cloudinary.com/charlesdebarros/image/upload/v1751473493/airbnb_data_analytics_project/airbnb_london_room_type_availability_pvvrb8.png)

### Some statistical numbers  

As of December 2019:  

* There were 1952 properties available 365 days a year.  
* The average minimum number of nights requested by renters was 4.  
* The average number of properties available at any time was 169.  
* The borough with the greatest number of properties was Westminster.  
* Westminster was also the most expensive borough to rent properties.  
* There had been 62826 reviews.  
* The average number of reviews per property was 22.  
* The average number of reviews per property per month was 1.21.  
