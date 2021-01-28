# Twitter-Project

## Features:
We have incorporated the following in our project:
1. Streaming and collecting real-time tweets based on hashtags, locations and username.
2. Developing Machine Learning Classifiers to predict the political orientation of the tweet.
3. Performing Sentiment Analysis on the collected data.
4. Visualizing and analyzing the data with the help of bar graphs, pie charts, word-clouds and maps. 
5. Indentifying Bots amongst most tweeted users. 

## Dataset Creation:

### Data Collection:

* Used Tweepy Streaming API to stream through real-time tweets.
* Used "Filter_by_hashtags.py" to stream through real-time tweets.
* Stored the collected tweets locally using Sqlite Database as well as in the Cloud using Firebase.
* Tweets collected by "Filter_by_hashtags.py" has the following attributes:
 'tweetText','hashtags','user','date','location','latitude','longitude','state'.
* We further extracted the details of the user using "Getting_details.py". Thus the final attributes include 'tweetText','hashtags','user','date','state','latitude','longitude','followers','verified','mentioned_location'. 
* The reason we have extracted only a few details of the tweets and the detail of the users using "Filter_by_hashtags.py" and collected further details using "Getting_details.py" was to avoid data limit breach. 
* The attributes are explained below to better understand them:
   1. tweetText: The tweet which is of 1 to 280 characters in length. 
   2. hashtags: The hashtags mentioned in the tweet.
   3. user: The username of person tweeted.
   4. date: The date the tweet was posted.
   5. state: The state from which the tweet was posted (Null: 'XXXX').
   6. latitude: The latitude from which the tweet posted (Null: '99999.99'). 
   7. longitude: The longitude from which the tweet posted (Null: '99999.99').  
   8. followers: The number of followers of the user ('-1' if unable to extract the details).
   9. verified: Whether the username is a verifed by Twitter ('-1' if unable to extract the details).
   10. mentioned_location: The location mentioned in the user profile by the user.
 * We ran "Getting_details.py" exactly a week after collecting the tweets through "Filter_by_hashtags.py". We found that certain accounts had been deactivated/banned/removed. Thus we couldn't exctract the 'followers', 'verifed', 'mentioned_location' of those particular accounts and  appended '-1' instead.
 * The date of collection of the tweets are as follows:
    1. Democ1.csv, Repub1.csv: Aug 19th
    2. Democ2.csv, Repub2.csv: Aug 20th
    3. Democ3.csv, Repub3.csv: Aug 22nd
    4. Democ4.csv, Repub4.csv: Aug 23rd 
    5. Democ5.csv, Repub5.csv: Aug 25th
 * We ran two 'Filter_by_hashtags.py' simultaneously. One contains pro-democratic tweets in 'track' while the other contains pro-republic tweets in 'track'.
 * Based on this method, we were able to seperated pro-democratic tweets and pro-republic tweets , thereby elliminating the need for manual annotations, and stored them seperately in a database. This reduced the need for manual labour(by large margins) and saved us a lot of time(in hours) but came at a cost of reduced accuracy.
 * The hashtags used for this purpose were:
    1. Pro- Democratic:
    '#voteblue',' #BlueWave2020', '#UniteBlue','#Biden2020', ''#VoteBlue2020','#Biden2020ToSaveAmerica',  '#BidenHarrisLandslide2020','#Biden2020Landslide' , '#BidenHarris2020', '#BlueTsunami', '#VoteBlueToEndThisNightmare', '#BlueDot','#Resistance','#TheResistance','#FBR','#FBRParty','#DumpTrump2020' .
    2. Pro- Republican:
   #Trump2020Landslide','#FourMoreYears', '#KAGA2020',  '#MAGA2020','#Trump2020NowMoreThanEver', '#Trump2020Victory','#KAG2020', '#RedWave2020','#VoteRedToSaveAmerica','#VoteRedToSaveAmerica2020','#keepamericagreat','#donaldtrump2020','#magacountry','#magamovement','#ThatsMyPresident','#donaldtrump2020','#americafirst',''#KeepAmericaGreat','#MakeAmericaGreatAgain','#TrumpRocks','#protrump','#prorepublican',#Trump2020','#TRUMP2020','#DemocratsAreADisgrace','#DemocratsAreDestroyingAmerica','#DemocratsHateAmerica','#DemocratsHaveLostTheirDamnMinds','#DoNothingDemocrats','#Demexit' ,'#Joementia'
* We considered anti-Trump as pro-Democratic and anti-Biden as pro-Republican.
* We have also collected tweets to perform Sentiment Analysis based on the election results. The Sentiment Analysis focuses to capture how the twitter users feel about the US Elections 2020 results. All the methods of data collection were similar to the methods mentioned earlier.      
 * The date of collection of the tweets are as follows:
    1. sentiday1.csv: Nov 8th 
    2. sentiday2.csv: Nov 9th 
    3. sentiday3.csv: Nov 11th
    4. sentiday4.csv: Nov 13th
 * The hashtags used for this purpose were:
 '#USElection2020',' #USElections2020', '#USAelection2020', '#USElectionResults2020','#uselection2020', '#RaceForTheWhiteHouse', '#POTUS46', '#USPresidentialElections2020', '#USElectionResults' , '#USPresidentialElections','#Elections2020', '#Elections2020results', '#Election2020'.

### Creating Datasets:
* The collected tweets stored in the Database was converted into .csv files so as to facilitate easier data manipulation and processing through python pandas library.
