# The Data Incubator
## Problem Statement:
With the lack of vaccine/effective treatment + the limited medical resources, it is critical that the spread of coronavirus be contained by social distancing. However, social distancing has been implemented with mixed effectiveness in different areas. This project aims to predict the degree to which social distancing is effectively practiced on the US city level. The usefulness of this is apparent in understanding what stops the effective practice of social distancing, where this is occuring, and how we can better support social distancing as well as identify future clusters to better prepare.

The inputs to a predictive model for the level of social distancing on a US county level will grow over time, but the current ideas involve Twitter data on a county level as well as socio-economic data on a US county level.

## 1st Asset: Inputs to the model: Twitter and socio-economic data
We crawl for county level data using the GetOldTweets3 library. We install the library, import it, and can set criteria such as what query we want, the date, the location, and the maximum number of tweets we are looking for.
```python
import GetOldTweets3 as got
tweetCriteria = got.manager.TweetCriteria().setQuerySearch('coronavirus')\
                                           .setSince("2020-04-11")\
                                           .setUntil("2020-04-12")\
                                           .setNear('Montgomery, Alabama')\
                                           .setMaxTweets(20)
tweets = got.manager.TweetManager.getTweets(tweetCriteria)
for tweet in tweets:
    print(tweet.text)
    print('\n')
```
Output:
```
'TELL IT LIKE IT IS' Talk Show: Trump’s Faulty Malaria-Coronavirus Connection https://talktoalabama.tellitlikeitistalkshow.com/2020/04/trumps-faulty-malaria-coronavirus.html?spref=tw

Partying... in the time of Coronavirus? If someone has a birthday coming up, then you can celebrate virtually! There are lots of ways to maintain physical distance while staying socially connected. #mgmready #montgomeryready

Babyface Reveals Coronavirus Diagnosis https://goo.gl/fb/JAAiB2

Avoid Coronavirus Scams -- Tip #3: Fact-check information. Before you pass information on, check trusted sources like federal, state and local government websites. 

He got the coronavirus 

Fascinating read! #2A #SecondAmendment #coronavirus #COVID

@SenFeinstein wants to give $5B US tax dollars to Iran to “help fight coronavirus.” Will the Democrats ever learn? Who truly believes Iran? #crickets

Hey Bill I Would Love To Help My Mom Out She’s In The Process Of Moving & She’s Not Working Due To The Coronavirus Anything Would Help Thank You 

Corporate structures are shells. The owner injects into them, what agenda they want to promote. Kind of like the Corona virus. A shell, with an active agent injected into it to achieve a given purpose. Don't focus on the tool. Focus on the owners.

Só pra lembrar esse povo que insiste em ficar aglomerado: EUA já registrou 18.860 mortes pelo novo Coronavirus. Maior número de mortos no mundo. É logo ali, galera. Se liga!

Alabama News Network has a list of which local restaurants and businesses are still open. Check it out! http://bit.ly/2Us1Trl #coronavirus #whatsopen #Montgomery #MyMGM #Prattville

Just a reminder when you see that scary headline about the US having more deaths from coronavirus than Italy: 

50 Pushups #challenge #donaldtrump #money #coronavirus #usa #rawlife #fiebeezy https://www.instagram.com/p/B-2bmF9lFSl/?igshid=1fyp494dj5mqf

Structural changes are needed to address coronavirus http://dlvr.it/RTbrN1

I love Twitter! I love that I can search #hashtags and get answers to anything I need or want. #Twitter #Worldwide #SocialSaturday #Covid19 #coronavirus

Please protect the November election from the coronavirus by passing a bill to guarantee every voter can cast a ballot by mail! https://act.demandprogress.org/sign/vote-by-mail-november/?source=tt @SenShelby

Business as normal as we are deemed an essential service. We will monitor the corona virus situation closely. We will not put anyone’s safety and health in jeopardy and will take precautions. Call (334) 265‑9990. #extermitech #prattville #wetumpka #montgomery #millbrook

We are working hard to mobilize the #vote amid the #coronavirus pandemic. Watch our social media pages for more information coming soon! #electionsmatter #Alabama

Scott Gottlieb: Coronavirus Would Have Been ‘Far More Deadly than Spanish Flu’ If It Appeared in 1918 https://www.nationalreview.com/news/scott-gottlieb-coronavirus-would-have-been-far-more-deadly-than-spanish-flu-if-it-appeared-in-1918/. What a stupid article. in 1918 people were much younger and healthy. How would he draw such a dumb conclusion?

Fact check false. Trump never called Corona virus a hoax.
```
