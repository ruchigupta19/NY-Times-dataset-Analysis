# Performed analysis on NYT times data

I fetched the data from Article search API and Archive API with the help of requests library using the following code and stored them at a proper location:

```
apikey_parameter={'api-key':os.environ['auth_key'],'page':i}
time.sleep(4)                                         
response_articlesearch=requests.get('https://api.nytimes.com/svc/search/v2/articlesearch.json',params=apikey_parameter)
```

## Analysis - 1

While analyzing Article search data I first collected all the **unique section names** from all the articles and plotted a graph for the same:

![alt tag](https://github.com/ruchigupta19/Gupta_Ruchi_Spring2017/blob/master/midterm/Question2/output/5-famous-sections.PNG)

It can be seen that the **maximum number of articles are on world's news**.So the world's news articles can be analyzed closely to get further information and deep dived into all the subsections this section have, plotted a graph for the same:

```
U.S.
[None, 'Politics']
World
['Middle East', 'Asia Pacific', 'Europe', 'Africa', 'Americas', None, 'Canada']
Sports
['College Basketball', None, 'Golf', 'Cricket', 'Soccer', 'Pro Basketball', 'Baseball', 'Olympics', 'Hockey', 'Pro Football', 'Tennis', 'Rugby', 'Cycling', 'Skiing', 'College Football']
Business Day
[None, 'DealBook', 'Retirement', 'Energy & Environment ', 'Economy', 'Media']
Arts
['Television', None, 'Music', 'Dance', 'Art & Design']
```

![alt tag](https://github.com/ruchigupta19/Gupta_Ruchi_Spring2017/blob/master/midterm/Question2/output/pie-chart.PNG)

It can be seen that under world section category, **Europe subsection has the maximum number of articles**. We can deep dive into the main headlines of Europe subcategory to know more about its articles.So I fetched all the headlines for Section world and subsection Europe.

```
('eu', 17)
('say', 16)
('french', 11)
('talk', 10)
('leader', 8)
('fillon', 8)
('ireland', 7)
('turkey', 7)
('chief', 7)
('candidate', 7)
```

![alt tag](https://github.com/ruchigupta19/Gupta_Ruchi_Spring2017/blob/master/midterm/Question2/output/word-freq.PNG)

Hence we can see that the most talked words in the articles for Erope includes **"say,French,Talk,turkey,ireland,syria,german"**

## Analysis - 2 (Sentiment Analysis)

I performed sentiment analysis on the headlines for Europe using NaiveBayesAnalyzer and the output is recieved for each headline as follows:

```
Finland's Eurosceptic Leader Soini Says Will Step Down From Party Helm
Sentiment(classification='pos', p_pos=0.6110553027748823, p_neg=0.38894469722511693)
*****************************************************************************************
Expert Says Islamic State Has Badly Damaged Major Palmyra Monument
Sentiment(classification='neg', p_pos=0.10317982549780323, p_neg=0.8968201745021953)
*****************************************************************************************
EU, US to Recognize Each Other's Medical Site Inspections
Sentiment(classification='pos', p_pos=0.8989002428508415, p_neg=0.10109975714915861)
*****************************************************************************************
Hungarian Leader's Ally Acquires Stake in Major Media Firm
Sentiment(classification='pos', p_pos=0.7213725267227658, p_neg=0.2786274732772348)
*****************************************************************************************
Experts Find Mass Grave at Ex-Catholic Orphanage in Ireland
Sentiment(classification='pos', p_pos=0.8241633206234236, p_neg=0.17583667937657416)
*****************************************************************************************
```

Total postive counts:
97
Total negative counts:
27

- Percentage of negative sentiments : 21.774193548387096
- Percentage of positive sentiments : 78.2258064516129

### From all the articles on Europe total positive count is 97 and total negative coint of articles is 27

## Analysis -3 

The data recieved from Archive API have many different years and months.Hence I gathered all the data for the **last 6 months and analyzed** the same.

```
['2016-09', '2016-10', '2016-11', '2016-12', '2017-01', '2017-02']
```
I fetched unique section names for all years and their count which looks like this:

```
2016_09
[('World', 12180), ('U.S.', 11860), ('Opinion', 11460), ('Fashion & Style', 10920), ('Arts', 9700)]
2016_10
{'U.S.': 13040, 'Fashion & Style': 7320, 'T Magazine': 2600, 'World': 11280, 'Sports': 9540, 'Times Insider': 880, 'Style': 600, 'Arts': 10160, 'NYT Now': 160, 'Health': 560, 'Opinion': 13140, 'Corrections': 620, 'Crosswords & Games': 940, 'N.Y. / Region': 6160, 'Today’s Paper': 620, 'Business Day': 8660, 'The Upshot': 1100, 'Theater': 2180, 'Technology': 2440, 'Science': 1800, 'Books': 3640, 'Movies': 2780, 'Food': 2340, 'Travel': 1680, 'Briefing': 1480, 'Real Estate': 2140, 'Sunday Review': 40, 'Job Market': 280, 'Magazine': 1480, 'Multimedia/Photos': 460, 'The Learning Network': 1980, 'Blogs': 600, 'Well': 1680, 'Podcasts': 240, 'Your Money': 560, 'Public Editor': 100, 'Automobiles': 220, 'Universal': 100, 'Obituaries': 80, 'Admin': 20, 'Education': 60, 'Watching': 120, 'Giving': 40}
2016_11
{'World': 10320, 'N.Y. / Region': 6120, 'Arts': 8920, 'Business Day': 7880, 'Well': 1260, 'Theater': 1780, 'Sports': 7380, 'Fashion & Style': 5280, 'U.S.': 12480, 'Technology': 2180, 'Briefing': 1760, 'Blogs': 580, 'The Upshot': 1960, 'Movies': 2780, 'Watching': 560, 'Books': 3680, 'Opinion': 12320, 'Food': 2200, 'Science': 1520, 'Education': 280, 'T Magazine': 2200, 'Real Estate': 2180, 'Style': 700, 'Times Insider': 800, 'The Learning Network': 1920, 'Podcasts': 320, 'Travel': 1300, 'NYT Now': 80, 'Magazine': 1700, 'Multimedia/Photos': 720, 'Universal': 120, 'Health': 700, 'Corrections': 580, 'Crosswords & Games': 780, 'Today’s Paper': 560, 'Your Money': 940, 'Giving': 180, 'Automobiles': 160, 'Public Editor': 200, 'Job Market': 160, 'Sunday Review': 80, 'Admin': 20, 'Obituaries': 20}
```

I fetched top 5 sections for 2016_09 and analyzed their trend over 6 months

```
2016_09
[('Arts', 9700), ('Fashion & Style', 10920), ('Opinion', 11460), ('U.S.', 11860), ('World', 12180)]
2016_10
[('Arts', 10160), ('Fashion & Style', 7320), ('Opinion', 13140), ('U.S.', 13040), ('World', 11280)]
2016_11
[('Arts', 8920), ('Fashion & Style', 5280), ('Opinion', 12320), ('U.S.', 12480), ('World', 10320)]
2016_12
[('Arts', 8620), ('Fashion & Style', 4180), ('Opinion', 11760), ('U.S.', 9100), ('World', 11840)]
2017_01
[('Arts', 8799), ('Fashion & Style', 6216), ('Opinion', 11718), ('U.S.', 15624), ('World', 10920)]
2017_02
[('Arts', 8960), ('Fashion & Style', 7220), ('Opinion', 9960), ('U.S.', 10700), ('World', 9580)]
```

and the graphical visualization for the same is:

![alt tag](https://github.com/ruchigupta19/Gupta_Ruchi_Spring2017/blob/master/midterm/Question2/output/grouped-bar.PNG)











