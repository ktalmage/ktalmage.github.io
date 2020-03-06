---
layout: post
title:      "**My CLI Project**"
date:       2020-03-06 21:22:03 +0000
permalink:  my_cli_project
---


For my CLI project I decided to create a weather program. I had many ideas in the beginning for how I should accomplish something like this and at first found I was spending a lot of time choosing either using the learn IDE or choosing a local environment. Just figuring out that part of this project was a challenge itself especially for someone who had barely coded prior to February 10th. 

The next part of this challenge involved making sure I had the right gems included in my local environment as well as github access. Without the browser IDE, at first I didn't realize you need to install pry and Nokogiri and other important tools. After a day or so I finally began coding  and realized that I needed a solid method to obtain data. Because of the nature of this program, it was a little tough to find truly free or easily accessible weather information without an API key. I found myself searching many free API sites. I first tried Nokogiri on some major weather websites and found that I was either scraping a lot of data as strings  or pulling data from very dynamic sites that would return a blank arrays. I was experimenting with parsing strings but the data was very limited - there seemed to be  a better method to me. I found a pretty good free API for weather that required sign up but seemed to have a lot of data to access. My original idea involved just being able to input a zip code and have weather from anywhere in the country. After setting up my code and the time horizon of this project, I opted to use a different technique to bring data from multiple sources in one shot instead of pinging the API each time a new request was called by the user. The bulk data source didn't seem current as just pinging the API based on cycle method.  I used the city collect method and took the lattitude and longitude of my location - New York City. From there I set the parameter to 20 nearby cities so I could have a large of dataset to choose from. This can be changed to a larger area but for this project I decided this was enough to showcase this program. 

The last part of this project was tying everything together using objected oriented programming concepts and using the CLI itself. I found this to be a little challenging but I decided to create a class based on location that would instantiate with a name and then call class methods related to weather. Basically each location should be an object with a different attribute of weather associated to it. For this project,  for CLI purposes I think it made  sense to present all the weather data in a snapshot-like view. Most users wouldn't just need wind speed or minimum temperature they would like to see all of that at once. 

I really liked working on this project. It was definitely one of more challenging things I've done and its amazing to think how far I've come from when I started this a month ago. 




