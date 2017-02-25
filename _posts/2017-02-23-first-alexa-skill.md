---
layout: post
title: Building My First Alexa Skill
feature-img: "img/amazon_echo.jpg"
---

As I'm nearing the end of the [full-stack web developer program on Bloc](https://www.bloc.io/web-developer-career-track), I've reached the capstone stage and as part of it, I am learning to build [Alexa Skills](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/getting-started-guide) for [Amazon Echo](https://www.amazon.com/gp/product/B01E6AO69U?tag=googhydr-20&hvadid=178760267665&hvpos=1t1&hvexid=&hvnetw=g&hvrand=11045156873175209291&hvpone=&hvptwo=&hvqmt=e&hvdev=c&ref=pd_sl_4azkexk7h5_e) devices. 

While this is not a 'traditional' web application, with a web-based user interface in the form of a web page, I wanted to do this project because I believe intelligent assistant experiences such as Alexa, [Siri](http://www.apple.com/ios/siri/), [Cortana](https://www.microsoft.com/en-us/mobile/experiences/cortana/), [Google](https://assistant.google.com/) and others, are a potentially explosive growth area.  So I wanted to know more.  

My wife and I have an Amazon Echo in our house. My wife got one for me and her parents this past Christmas and aside from randomly/accidentally triggering it to start listening, we've really enjoyed having it.  Our typical use cases include:
- Checking the weather forecast
- Listening to background music
- Seeing when certain stores open and close
- Checking random facts we're curious about
- Adding things to our grocery list (we use Amazon Fresh)

However, I know even today and especially in the future, it can be used to do so much more.  Such as turn on or off lights in specific rooms.  Maybe even start playing the next episode of [Mr. Robot](http://www.imdb.com/title/tt4158110/) on our TV that has an [Amazon Fire TV Stick](https://www.amazon.com/All-New-Fire-TV-Stick-With-Alexa-Voice-Remote-Streaming-Media-Player/dp/B00ZV9RDKK) connected to it. I know, I'm setting a really high bar here. 

### Reindeer Trivia for Alexa

To get started on building an Alexa skill, we used a really great tutorial and sample application that was mostly already created by [Amazon](https://github.com/alexa/skill-sample-nodejs-trivia) and provided in their tutorials.  The documentation and instructions were really straight forward and by the end of it, you have a functioning Reindeer Trivia game where it is triggered by saying something like "Alexa, start Reindeer Trivia."  Alexa responds by initiating the game, providing a bit of instruction on how the game will work and then starts asking the question.  

All of the questions are multiple choice and the user can respond by saying the number or title of the choice they want to submit as the answer. It's pretty straight forward but magical what can be created in a few hours (or less if you're more experienced).

### Starting to drink the Amazon koolaid early

It's a common experience that the tools and concepts someone picks up as they are learning  something new, i.e. as a student, there is a higher probability that they will want to continue to use those tools and concepts when they start applying those learnings in the real world.  We see this today, especially with millenials, they pick up using Mac's (I'm on one right now), Google (Gmail, Docs, Sheets, Slides, Drive) and the such and want to use them at work.  They slowly push their organizations to adopt and next thing you know, the landscape of IT in business looks much different than it did in 2007.  It's not bad thing either.   

From the documentation and syllabus, it appears that Amazon realized this is a thing and wanted to make sure that newly minted web developers, especially through Bloc, knew how to use Amazon Web Services and build stuff for Alexa, from day one.  I even heard that in the early days, Amazon was even giving each developer an Echo device upon succesful creation, submission and approval of their own Alexa Skill.  

Those efforts and success in general, must have been good and possibly too good because there were several resources, webinars, videos, weekly newsletters, forums and specific people focused on developer evangelism in this space that were wiped from the internet or not updated/active in the past 12 months.  All of the documentation that came in useful (like the one I linked to above), were new (which is great) but available only through Amazon, not through Bloc or really any other 'official' education partner.  **Greed is a hella of drug.**

Through the documention, you sign up for a developer account with Amazon, a free Amazon Web Services account (with a credit card on file but not charged, to make it super easy to start paying for stuff), prepared your environment for developing an Alexa Skill, created an AWS Lambda (of which I am still not 100% sure I know what it is really) and submitted an Alexa skill for publishing in the Alexa Skills store.  

I'm just through step 1 of learning to build Alexa skills and I already feel much more confident in using AWS for my developer cloud solutions, over competitive solutions such as Microsoft Azure.  Sneaky Amazon, really sneaky.

![](https://media0.giphy.com/media/IteKtmQg9gP4I/giphy.gif)

### Half of the hard stuff is taken cared of

Going into this project, I was scared but excited about having to do write code to handle voice input and API calls to some Amazon service.  This stuff isn't impossible or possibly  too hard but I just haven't done it much.  However, the way they've created the SDK and templates, most of this heavy lifting is taken cared of.  For example:

#### Figuring out a user's intent

It's really hard in real life to figure out what someone else really wants.  Just ask my wife.  :(  Let alone through a software program.  As part of the interaction model, Amazon has an **Intent Schema** which at least let's you create all the possible things a user could intend to do when interacting with your Alexa Skill.  And for this particular skill, they gave us a template, of which after studying it for a bit, is fairly straight-forward and it's in JSON format!  Here's an example snipit of the code:

```
{"intents": [
    {"intent": "AnswerIntent", "slots": [{"name": "Answer", "type": "AMAZON.NUMBER"}]},
    {"intent": "DontKnowIntent"},
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

Well, that was easy.

#### Deciphering natural language variance

There are several ways to do something and in any given language, there are several ways to communicate the same thing.  So to go along with each intent, you provide and create several ways for people to communicate they want to do one of your prescribe (or thought of) intents.  Now, you might not catch everything but that's a different problem.

```
AnswerIntent the answer is {Answer}
AnswerIntent my answer is {Answer}
AnswerIntent is it {Answer}
AnswerIntent {Answer} is my answer
AnswerIntent {Answer}

AMAZON.StartOverIntent start game
AMAZON.StartOverIntent new game
AMAZON.StartOverIntent start
AMAZON.StartOverIntent start new game
```

![](https://media1.giphy.com/media/zcCGBRQshGdt6/giphy.gif)

#### The real heavy lifting - application logic

Alright, the real heavy stuff here is designing the real logic that powers the game.  This is the JavaScript that powers the game itself and tells the application to do x when y happens and so on.  

This JavaScript leverages the various Amazon SDK's to interact with cloud services.  Technically, this is the type of stuff I've learned to write from scratch for web applications.  Therefore, in some way, shape or form, I am supposed to be able to do this from scratch.

Right...

Here is a little snipit of the code.  Note how much more there is.  :)  It makes sense to read the code and I can generally see the flow but holy crap I am glad they did this.  

![Alexa Skill Reindeer Triva JS code example](/img/Reindeer_game_code_screenshot.png)

I won't even go into what is in this `node_modules` folder, because I don't really know. PS, pretty sure this sentence will cost me a job at some point. 

![Crazy SDK code](/img/Reindeer-game-crazy-code.png)

### The other hard stuff - content

Someone's product (code) might be great but if the actual value of the product, what it does and it's content, isn't great - it doesn't matter.  The kit and template did a great job of guiding me through the basic setup, handling the hard stuff (noted above) and let you focus on editing and adding content.

In this project, it was the questions themselves.  Adding and editing questions was pretty straight forward as a `questions.js` already exists, pre-populated with questions, in `JSON` format, so you just add or change questions.

Each set of questions is broken up into language specific objects.  During the application setup in the Amazon Web Services dashboard, you specify the languages you will support and create the corresponding interaction model for each language.  There are only three choices right now: English (UK), English (US) and German.  Not sure if you can create more language support but I didn't explore that.

Here is one of my favorite questions that I added about Reindeer:

```
       {
            "Male reindeer can end up mating with how many females during a mating period?":
            [
                "Fifteen to Twenty",
                "Two to Four",
                "One",
                "Zero",
                "Five to Nine",
                "Ten to Fourteen"
            ]
        }
```

![](https://media1.giphy.com/media/1000fHsBSKSL6w/giphy.gif)


#### Wrapping up

In the end, we learned to go through the submission process (though I didn't want to actually publish it), mainly to experience the process.  Ultimately and thankfully, Amazon rejected the submission because it was too similar to something that already existed.  Great!  

I'm impressed by how easy Amazon has made it for people to just build and get started. The experience has instilled confidence that it's possible to not be a full on computer scientist but be able to build things, little by little, which eventually can turn into something really valuable and/or complex. 

I have some ambitous ideas about what could be done with Alexa in the long term and what I would want to do but for the 'build your own' stage that is coming up in the next couple of weeks, I'm going to focus on simple code and great content.