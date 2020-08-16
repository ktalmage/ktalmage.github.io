---
layout: post
title:      "React-Redux Project"
date:       2020-08-16 18:34:46 +0000
permalink:  react-redux_project
---


Following previous advice to keep things simple, for this project I wanted to create a React-Redux version of my previous project - leveraging pieces of the front and back end. While this helped me to get started by having a well defined concept, this was certainly still a completely new project to build.

During this project, the skills I've learned at Flatiron School have come full circle. In particular, one aspect I'm particuarly proud of was being able to fully realize debugging. After putting the shell of the project together, I came across a frustating situation: my data was appearing on the backend, but was not showing up on the frontend.

However, this time I was able to take the time to diagnose my own problems and solve it by stepping away and talking out the problem on paper and thinking about it logically. I was able to isolate what was really going on under the hood and test it out in the console.

The challenge was that I wasn't able to fetch data from the backend. Because I had placed console.log inside my cities loaded reducer, I could see in my console that I was skipping over my cities loaded action.

```
case "CITYS_LOADED":
            console.log(action)
            return {
                ...state,
                cities: action.payload.data,
                loading: false
```

I tested this in console by running a generic fetch request to my cities backend URL and I think this proves my learning from all of the time spent in JavaScript and learning fetch API. This key discovery allowed me to see that I had a spelling mistake in my cityReducer. I was able to isolate that and change it from "CITYS_LOADED" to "CITIES_LOADED," which was a key aspect of rendering the information on my page properly and allowing me to get through the rest of my project - overcoming a big bottleneck.

```
case "CITIES_LOADED":
            console.log(action)
            return {
                ...state,
                cities: action.payload.data,
                loading: false
```

After that, it was mostly a challenge of getting things to render and properly deleting front and back end. Overall, I wish I had a bit more time to refine my project, but I am happy with how it turned out given the constraints. 

My time at Flatiron School has been one of the most challenging and rewarding experiences I've had - I look forward to building more projects and seeing what's next.
