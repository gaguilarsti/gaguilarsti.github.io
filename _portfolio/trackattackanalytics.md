---
layout: post
title: Track Attack Analytics
feature-img: "img/sample_feature_img_2.png"
thumbnail-path: "img/data_acquisition_thumbnail.jpg"
short-description: Making squiggly lines make sense... with video.

---
## The problem
For those not familiar with motorsports, both the competitive and *for fun* versions of the sport, it is just like any other sport.  There is a quantitive measure of how you finished or at least, how you performed.  In motorsports (and the lap-based version specifically), it's all abou the **lap time**.  

Go back a couple decades ago and most people had stop watches, in the car or with someone outside, manually logging lap and split times (e.g. times for sections of the track).  As GPS systems started taking off, we started seeing GPS based lap timers, primarily in Formula One and eventually trickling down to things that individuals could buy.  Sort of.  

These solutions, GPS-based lap timer and data acquisition systems, exist and do some awesome things.  The issue is that they are expensive.  Ranging from sort of expensive, like the [AiM Solo](https://www.pegasusautoracing.com/productdetails.asp?RecId=8780&utm_source=google&utm_medium=cpc&utm_campaign=MC-570&gclid=Cj0KEQjw6uO-BRDbzujwtuzAzfkBEiQAAnhJ0Es6GfE23wPeVE16zCwd40C2hWl5MCcNhYLg9M8tfc8aAj5S8P8HAQ) at $399.99USD to the [AiM MXL 2 Digital Dash](https://www.pegasusautoracing.com/productdetails.asp?RecID=10846) coupled with the [AiM HD SmartyCam](https://www.pegasusautoracing.com/productdetails.asp?RecID=12286), at close to $4,000.00USD, for just the parts, let alone the installation, configuration and training to use.  All in, these solutions cost upwards of $10,000USD before they are ready to be used.

And, we're still talking about the low-end of the market.  

So let's assume you have decided to make this investment and have this solution up and running.  You have lap times and data to start analyzing your performance.  You get out of your car, hookup your laptop to your datalogger, download the data and open the file.  This is what you'll be staring at...

![alt text](http://www.epicscore.com/online/AIM-Data-Analysis.jpg "Squiggley lines - what do the mean?")

What are these squiggely lines?  Why are there different ones in different graphs?  Once you figure out what they are, where on the track is this happening?  What lap was this?  What happend in that a lap?  What did I do as a driver to cause the squiggely line to be different than another one?

¯\_(ツ)_/¯

### Some background

I have a confession. I am biased, very biased in my opinion here about.  By training and background, I am a market and user researcher.  [My job for the past decade](https://www.linkedin.com/in/gaguilar1) has been to understand what is going on in the marketplace and within specific products, by generating, combing through and analyzing digital stacks and stacks and stacks of quantitative data.

In just about every situation where we were trying to make a decision or at least, inform a decision and we had this data, I or at least one other person would ask *why is x thing happening?.  Why is this advertising campaign, or copy or spot doing better than the others or relative to competition?  Why is this feature not being used?*  **_Why???_**

And to answer that question well, we'd have watch our customers or target customers in the wild, through various forms of qualitative research.  Actually watch them use the products or look at an advertisement.  Seeing things happen real time would help us understand the data and why the data was a certain way.

### This isn't just motorsports problem, it's an insights problem

As that story hopefully illustrates, the issue of understanding data, why it is what it is and how to do something differently next time, is not a motorsports problem, it's a data problem.  

And if we peel the onion one more layer, ultimately what we're all trying to do with the data is make decisions on it to do something different.  So we don't really care about the data itself, in its raw form.  We care about the insights we can gleam from the data, to inform our decisions and actions.  While drivers are struggling with many challenges with the available solutions today, ultimately - they are struggling with insights.  What should they be learning to do differently?

## Coming up with a solution

To come up with a solution, we immersed ourselves in data acquisition solutions, analysis software and seminars/webinars/coaching sessions to understand what it looks like when there is success. 

This also meant spending a lot of time with drivers at the track, watching them debrief about their last session.  Thinking through what they wanted to improve on or do differently.  Seeing what tools they were using to try to achieve this.

We ultimately decided to create an extension to our existing product, [Track Attack](http://www.trackattackapp.com) - an analytics experience where when drivers used our lower cost data acquisition solution or even brough their own data from other systems, they would immediately be able to understand the data and be able to get to insights. 

### The right views of the data are important

We worked with one of the leading driver coaches and former Indy Car driver, [Ross Bentley of Speed Secrets](https://speedsecrets.com/).  We identified the following key scenarios:
1. Is a driver driving at the traction limit?
2. Is a driver driving consistently?
3. How can a driver improve their fastest lap with just their own data?
4. How can a driver improve their fastest lap with other people's data?

### But video is the key

The last requirement is that the driver should be able to extract insights without the help of a coach or instructor.  And for that, based on our research - having the video was critical.  Every analytic view of the data should have video as a promiment aspect.  No views without video!

### Do a few things, really well

We wholly embraced this design principle (choice) and by necessity.  With limited resources and even more limited design talent, we created the most critical views:

#### Basic home screen centered on what the user could do

![alt text](/img/Home Screen - Pin Favorites.png)

#### Analyzing a single session to determine if driver is driving at the traction limit

![alt text](/img/track_attack_analytics_single_session_view.png)

#### Analyzing a session across segments and determining consistency, fastest current pace and fastest theoretical pace

![alt text](/img/Segment Analysis.png)

#### Stitching together a video of that fastest theoretical pace so the driver can see, themselves going faster than they could have ever imagined

![alt text](/img/Virtual Best Lap.png)

#### Comparing two individual laps

![alt text](/img/Comparing two laps.png)

#### Easily sharing of video 

![alt text](/img/Comparing two laps.png)

#### Make video a first class citizen

True to our promise, every single view of data, has a prominent place for video.  We went so far as to allow the users to manually bring in video, from any camera source if they have it for the session data, regardless of what data acquisition system they use - Track Attack, AiM, RaceLogic and coming soon, MoTec, Bosch and TraqMate.

## Next steps

It is early days on the this project, with a lot of fit and finish to be implemented but we've already received feedback from drivers, coaches and even professional drivers that the approach we've taken, makes data analysis much less intimidating to get started and hope to actually be able to do something with it.

Over the next several months we plan on:
⋅⋅⋅Enable importing of MoTec, Bosch and TraqMate data⋅⋅⋅
⋅⋅⋅Automate specific insights to help drivers more easily understand how they're doing agains the key scenarios⋅⋅⋅
⋅⋅⋅Enable drivers to easily share and compare data amongst themselves⋅⋅⋅

This is an example of a post which includes a feature image specified in the front matter of the post. The feature image spans the full-width of the page, and is shown with the title on permalink pages.

## Credit

Credit goes, where credit is deserved.  I lead the development of this product but the actual software development was lead by [Marco Del Frari](https://it.linkedin.com/in/marcodelfrari) and contributions across our team, including [Manu Yareshimi](https://www.linkedin.com/in/manuyareshimi), [Roberto Codarini](https://it.linkedin.com/in/robertocodarini) [Alex Ignatov](https://ua.linkedin.com/in/alexignatov/en), [Ian James](https://www.linkedin.com/in/ian-james-22462317) and [Ross Bentley](https://www.linkedin.com/in/rossbentley).

