---
layout: post
title: Daily Workout Challenge, An Alexa Skill
feature-img: "img/workout-challenge-alexa-post-cover.jpg"
---


## The Problem
There has been a lot written about the power of getting up a little bit earlier than most and doing productive things for yourself, before your 'real day' gets going.  This way you can do things for yourself, that you like, are good for you and energize or re-energize you, before other people and things take away your time.  I am personally a fan of [The Miracle Morning](link), though I need to get back on the train and stick with it.  Even so, I still wake up most mornings and meditate and work out or work on a professional development area.  Most of the time it is either learn to code or work on my startup, [9104 Studios](link).  

I've found though that despite best intentions, sometimes its really hard to get that workout in because usually my workouts require about 60 - 75 minutes, from the moment I walk out of the door to when I walk back in.  One day skipped turns into two and next thing, you only worked out twice in a week.  

## The Solution
A little bit of working out, multiplied by many times can add up over time and even a little bit of working out each day, is much better than none at all.  What if Alexa could guy you through a 10-15 minute workout, that changes each time and uses nothing but your body?  No transit time to go to the gym, no equipment to buy or wait to become free and no research to do on techniques.  Just the basics.

>A little bit of working out each day, is much better than none at all.

### Introducing Daily Workout Challenge, an Alexa Skill. 
Workout Challenge is simple.  I will pre-load it with a ton of different exercises that only require some room and your body.  You wake up (or at any time of the day), put on some clothes and say _Alexa, let's burn some calories!_  

Alexa will then guide you through a quick warmup, a combination of simple but effective exercises that hit your whole body, change regularly (for muscle confusion!) and cool down.  All you have to do is follow the directions.

![Muscle Confusion](http://tannerbaze.com/wp-content/uploads/2014/12/muscle-confusion.jpg). 

### Why the 'challenge'?
This isn't about challenging you to compete against other people, it's about challenging yourself to put a small amount of hard work, each day to reach your health goals.  Other people will rarely be around to stop you from hitting snooze or looking at the clock and seeing only 20 minutes to work out and you say "ah, screw it."  It's only you, so now you have no excuse.  Let's do this!

## Nerd Time - Designing Workout Challenge
Now that I have you sold on Workout Challenge, let's use our brain muscles and talk about how I'll build the solution.  Luckily, this won't be too taxing, so feel free to pass on on pre-workout supplement for this section. 

![pre-workout](https://media.giphy.com/media/KCfzEx1zJL3dm/giphy.gif)

### The interaction model
Fairly straight forward in that the user will initiate the application by saying something like _Alexa, launch workout challenge_ or _Alexa, time to sweat_.  Alexa will come on, briefly describe the instructions and then start guiding the user through the exercises.  For example:

_I will go through a series of exercises that you will either do for thirty seconds or do a certain number of repititions. For example, I will say, do squats for thirty seconds or do fifteen pushups. Your job is to keep up. Let's begin._
Warm up:
 - _Run in place for 15 seconds. Go!_
 - _5 hip openers on your right leg. Go!_
 - _5 hip openers on your left leg. Go!_
 Workout:
 - _Squats, 30 repititions. Go!_
 - _Push-ups, do as many as possible in 30 seconds. Go!_
 - _Mountain climbers, 30 seconds. Go!_
 
Here is graphical overview of the interaction model, with the only back and forth interaction between Alexa and the user, is after the skill is initiated, the user can request a break or quit the workout session before it is completed.  

![Daily workout challenge interaction flow](/img/fitness-challenge-flow-overview.png)

### Intent Schema
Per above, the interaction model is pretty straight forward between the user and Alexa. Aside from starting a workout session, here are the general things the user can do:
- Skip the warmup and/or the cooldown
- Move to the next, previous or repeat the current exercise
- Pause, resume and stop/cancel the workout

**For the future:** Respond to questions with Yes or No.  I don't have something yet where the user will get a Yes or No answer but I was thinking at some point, Alexa can ask if the user is ready, confirm they completed the number of repititions in a workout, etc.

Here is the actual code for the intent schema:
```
{"intents": [
    {"intent": "DontKnowIntent"},
    {"intent": "SkipWarmUpIntent"},
    {"intent": "SkipCoolDownIntent"},
    {"intent": "AMAZON.NextIntent"},
    {"intent": "AMAZON.PreviousIntent"},
    {"intent": "AMAZON.PauseIntent"},
    {"intent": "AMAZON.ResumeIntent"},
    {"intent": "AMAZON.StartOverIntent"},
    {"intent": "AMAZON.RepeatIntent"},
    {"intent": "AMAZON.HelpIntent"},
    {"intent": "AMAZON.YesIntent"},
    {"intent": "AMAZON.NoIntent"},
    {"intent": "AMAZON.StopIntent"},
    {"intent": "AMAZON.CancelIntent"}
  ]
}
```
I am primarily using the built-in intents, leveraging the built in utterances for each intent but I am adding some additional utterance support and expecting to have to change these based off of actual user feedback:

```
AMAZON.NextIntent next
AMAZON.NextIntent next exercise
AMAZON.NextIntent done
AMAZON.NextIntent what's next

AMAZON.PreviousIntent previous
AMAZON.PreviousIntent previous exercise
AMAZON.PreviousIntent rewind

AMAZON.PauseIntent pause
AMAZON.PauseIntent I need a break
AMAZON.PauseIntent I need to rest
AMAZON.PauseIntent Just a second
AMAZON.PauseIntent water break
AMAZON.PauseIntent I need a water break
AMAZON.PauseIntent take five

AMAZON.StartOverIntent do over
AMAZON.StartOverIntent let's try that again
AMAZON.StartOverIntent again


DontKnowIntent i don't know
DontKnowIntent don't know
DontKnowIntent skip
DontKnowIntent i don't know that
DontKnowIntent who knows
DontKnowIntent i don't know this question
DontKnowIntent i don't know that one
DontKnowIntent dunno
```
## Campanion Cards
This is a really cool functionality with Alexa.  When a user invokes something with Alexa, Alexa responds AND the developer has an option to create a card that shows up on the corresponding user's phone that at minimum has a record of the command, with the response and potentially, additional information, via what they call _Companion Cards_.  

### If you ask for the weather in [city]:
![Alexa Seattle Weather Companion Card](/img/alexa-weather-companion-card.jpg)

Note the music card below the weather card.  It shows a picture of the artist/album that was playing and if the user clicks on the picture, it takes them to the Amazon Music app to start playing that album.  Right now Amazon allows you to include text and/or image on your companion card, not something more interactive or even a click-through link (I think).  So either Amazon has their own, private and more awesome abilities for companion cards (very likely) or they are dynamically generating images for these more sophisticated requests.  

E.g. that weather forecast image is a flat image that was dynamically generated and is hosted just like any other image.  Both are very likely but I hope for technological advancement's sake that it is the former.

### Companion card for Daily Workout Challenge
Ideally, I want to have a card for each exercise in a workout that includes a giphy (demonstrating the exercise) or one long card that has the entire workout, with still images or giphys of each exercices.  That way, users can have a visual tutorial of the exercise, in case they've never done one before.  

For now, I am going to create one companion card for each workout session, which has the entire workout outlined, hopefully like below.  Note - I'm not sure if I'll be able to do bullets in the card.

![Daily workout challenge](/img/Alexa-workout-challenge-example-card.png)

## The hard part
Most of what I've covered now is relatively straight forward.  The hard part is the core business logic of the application.  There are a couple layers:

1. I need to figure out how to have Alexa randomly select exercises for the warmup, core exercises and cool down.  To do this, I am going to create a new file called `exercises.js`.  In this file, I will have three `JSON` objects.  Each JSON object will have an array of exercises that will be used as the source for randomly selecting five warmup exercises, ten core exercises and five cool down stretches.  I _believe_ this is the right approach and should be easy enough.
2. Alexa cannot simply read out the selected exercises, like if she was reading a sentence or options to a multiple choice question.  She has to read each and then give the user time to complete the exercise and then move to the next exercise.  For this, I will need to create timing logic so that the user has the following experience when getting to an exercise:

_Run in place for 30 seconds. Go!_ **(25 seconds pass)** _five... four... three... two... one... Great!  Next exercise._

I have some ideas on how to approach this but I believe this will be the hardest part.

## The future
Ideally, I'd love to have the history of workouts completed saved for each user so we can keep track of the combinations of exercises someone has done and they can get a continuous mix of things to do.  It would be great to have this workout history fed into an activity tracking service/app but first things, first.  

On to build!