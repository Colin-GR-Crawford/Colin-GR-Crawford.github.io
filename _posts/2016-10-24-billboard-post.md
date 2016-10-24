---
layout: post
title: "A brief look at the Billboard 100 in the year 2000"
date: 2016-10-24
excerpt: "A forumla for the perfect chart hit."
tags: [Billboard, Linear regression, Descriptive Statistics]
comments: true
---
![Billboard Logo](https://colin-gr-crawford.github.io/assets/img/Billboard/Billboard.png)

## In my blog post today I am going to take a quick look at some of the steps you can take to improve the chance of success in the Billboard 100 Chart (albeit for the year 2000).

In case you are not familiar with the Billboard 100, here is a short excerpt from the [wikipedia](https://en.wikipedia.org/wiki/Billboard_Hot_100) article:
> The Billboard Hot 100 is the music industry standard record chart in the United States for singles, published weekly by Billboard magazine. Chart rankings are based on radio play, online streaming, and sales (physical and digital).\n",

I am using a small data set that contains a list of 317 tracks that peaked in the calendar year 2000. The database includes the following details:
* The Artist and Genre.
* The length of the song.
* The date the track entered the chart, and the date that it peaked.
* The chart position the track was in for every week it was in the chart.

Scrolling through the tracks is actually pretty nostalgic, it really was a year for music with Eminem and Jay-Z producing hit after hit along with Britney and Christina select few, and anthems like Bon Jovis \"It's my life\" still a dancefloor filler, what more could you want? (My personal Favorite from the list is Learn to Fly by the Foos)

On closer inspection of the data it seem some of the genre tags are a bit dubious, Destiny’s Child's Independent Woman a Rock song? I am not sure many people would agree with that. However I think it would be a bit too much of an exercise to change each and everyone so I will have a go with what I have. I imagine there is a script I could write to search for each artist on Wikipedia and return the string following the genre tag, but I will save that for a rainy day.

So what makes the perfect chart entry? Being incredibly good looking? The [magic 4 chords](https://www.youtube.com/watch?v=5pidokakU4I)? ...... Most Definitely! But for today I will look at some perhaps less interesting questions but much more quantifiable given the data available and timescale. The questions I have come up with and will look at are."

1. What Genre should I choose?
2. How long should the track be?
3. What time of year should I release the track?
4. Will I be more successful if I have already released a track in this calendar year?
5. How long do I need to be in the charts for me to have a higher chance of getting a higher rank?

#### 1. What genre should I choose?
There are 10 genre tags used in this data set, comprising of the following:

Country, Electronica, Gospel, Jazz, Latin, Pop, R&B, Rap, Reggae and Rock. The number of tracks in each Genre is displayed below.

![Chart 1](https://colin-gr-crawford.github.io/assets/img/Billboard/NofTbyGen.png)

Unfortunately, as you will see above, there is only 1 track each from Gospel, Reggae and Jazz, 4 Electronica tracks and 9 tracks from Latin and Pop meaning that these samples are on the low side and any information taken from them should be treated with a pinch of salt. Rock tracks are clearly the most popular with over 40% of the total proportion of tracks released in the year, this is perhaps unsurprising given the loose definition of the rock genre tag as mentioned above.

Below are another three bar charts, these charts display the following information; The average number of weeks a track by each genre remains in the charts, The average number of days it took a track by each genre to reach its peak and the average highest rank for each genre.

![Chart 2](https://colin-gr-crawford.github.io/assets/img/Billboard/Genre_Subplots.png)

Although Jazz tracks seem to perform extremely well, as there is only one of them (as mentioned above) we will ignore them for now along with the other low frequency genres. This leaves us with Rock, Rap R&B and Country. Between these categories rock is the clear winner with a much longer time in the charts and a much lower average rank. It does seem that the genre takes a while to pick up momentum. Also from the above graphs it looks like there might be a relationship between number of weeks a track spends in the charts at a point in which they peak. I will look into this a bit more lower down.

#### 2. How long should the track be?

Ok, so we have got the genre nailed (well slightly). The next question is track length, the first thing I did was to check to see if there was any sort of relationship between track length and the highest rank a track achieves - there does not seem to be or the how quickly it peaks or the number of weeks it stays in the chart for that matter... I haven't presented any of these as I do not want to overload the blog with too many charts, I am sure there will be enough. So there doesn’t seem to be a significant link with how successful a track does with its length, how about what is the most common track times? Below is a distribution chart of all the tracks in the dataset.

![Chart 3](https://colin-gr-crawford.github.io/assets/img/Billboard/TrackLengthHit.png)

The track lengths form a fairly normal distribution albeit a skewed positively, this is unsurprising as track lengths can increase indefinitely especially within the progressive rock sub-genre (I am looking at you Pink Floyd) and a lot of electronic music, however I don’t think I can remember any big hits that have been less than a minute. The mean for the data is 242 seconds so we will go with that.

#### 3. What time of year should I release the track?

For this question am going to work with the assumption that a probability of a track reaching the top spot based on the time of year is subject entirely to amount of competition. This is because, for any given day there is always 1 track on the top spot and so other variables aside, the chances of your track being that one are based on how many you have to complete against, if there are no other tracks then you **will** be number 1. Therefore, I have plotted below a Datetime plot of all the tracks in the database and the month in which they entered the chart.

![Chart 4](https://colin-gr-crawford.github.io/assets/img/Billboard/NTrkPerM.png)

As you can see the data set is not quite complete as it only contains tracks that peaked in the chart in the year 2000, with many tracks probably peaking in 2001 and only entering in 2000, the data is therefore probably not ideal for this analysis. However, there is a clear slump in tracks being released/entering the chart between April and July, meaning that this is prime time, and this is unsurprising as the musical sales year tends to revolve around the Christmas period.

#### 4. Will I be more successful if I have already released a track this year?

So does the chart favor new comers? - So that people can say \"Oh yea I likes this band, you have probably never heard of them\". Or do people latch on to artists they have heard before? Below are two plots one showing the following; the average time taken to reach the peak in weeks and the average highest rank. Each plot shows these values as averages for the first, second third fourth and fifth track released by all respective artists for each genre.

![Chart 5](https://colin-gr-crawford.github.io/assets/img/Billboard/AppChrt.png)

What is interesting as that there is from the data provided there is a clear improvement for artists up until their third track, after which presumably the public get a bit tired of their music. So if you are going to place a bet on which track is going to be the most successful it is the third of a given year, by any artist. Obviously a year is a quite arbitrary unit but within a similar time period should be sufficient.

#### 5. How long do I need to be in the charts for me to have a higher chance of getting a higher rank?

Ok so we have worked out the winning formula - Rock song, about 242 seconds long, released in April, and the third song you release in the year. You are on track for a winner! But when will i know if I have been a success? When am I likely to peak in my chart lifespan?

The charts below is split into two charts, the top shows the average rankings of all genres throughout their lifetime in the chart, the chart below it is broken down into the split by the 4 main genres.

![Chart 6](https://colin-gr-crawford.github.io/assets/img/Billboard/Rank_By_Week.png)

There is a general pattern that the longer you stay in the chart the higher you will climb it, no surprise there really. The graph shows us that on average you will peak between week 35-45. What is very surprising the large drop off between week 20 and week 21, essentially telling us that if you can keep climbing to week 20, you work is about to pay off! This average is mirrored by all 4 of the major genres, although pop does climb up again. However as less and less tracks make it past week 30, the results may be a bit distorted and a larger database would be needed to verify them.

#### Extra: The relationship between how long a track stays in the chart and when it peaks.

As the title above says this is a very brief examination of the relationship of the above. I was interested in this relationship after noticing almost identical bar charts when looking at question 1. I plotted the two values against each other along with the linear regression below.

![Chart 7](https://colin-gr-crawford.github.io/assets/img/Billboard/TtoPkvsWkCht.png)

This is essentially saying that if you spend twenty weeks in the charts you will likely peak at " (20*3.806)-12.229 days or 63 days. Or another example it is day 120, you have just peaked, how long do you have left? The answer is roughly ((120-12.229)/3.806)-(120/7) == 11 weeks."
