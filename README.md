# GEOG6590_ProgrammingForGIS_Script
Fall, 2021 

## 1.0 Tweet Scraper
Two methods are used to scrape and dump Tweets using [Twitter API for Academic research](https://developer.twitter.com/en/products/twitter-api/academic-research), they could produce exactly the same results. The API grants free access to full-archive search and other v2 endpoints, with a volume cap of 10,000,000 tweets per month.   
Method 1 was written by me, while Method 2 calls the [twarc package](https://github.com/DocNow/twarc). Method 2 is recommended because it's more convenient and understandable: all the raw codes are encapsulated, and it's possible to finish all the work with only one line. 
### 1.1 Method 1
The tweetScraper.ipynb is the main program, all the other py files are functions used in the tweetScraper program.  
- The **auth()** in auth_function.py saves the “Bearer Token” you use to assess Twitter API in an an “environment variable”. Since this Bearer Token is sensitive information, you should not be sharing it with anyone at all.
- The **create_url()** in create_url_function.py builds the request for the endpoint we are going to use and the parameters we want to pass. You could adjust your params here based on the [API reference](https://developer.twitter.com/en/docs/twitter-api/tweets/search/api-reference/get-tweets-search-all):
```
query_params = {'query': keyword,
                'start_time': start_date,
                'end_time': end_date,
                'max_results': max_results,
                'expansions': 'author_id,geo.place_id',
                'tweet.fields': 'id,text,author_id,geo,created_at,lang,public_metrics,referenced_tweets,
                'user.fields': 'id,name,username,created_at,description,public_metrics,verified',
                'place.fields': 'full_name,id,country,country_code,geo,name,place_type',
                'next_token': {}}
```
- The **connect_to_endpoint()** function puts all of the URL, headers, and parameters together to connect to the endpoint.
The function below will send the “GET” request and if everything is correct (response code 200), it will return the response in “JSON” format.
  
### 1.2 Method 2
The twarc is a command line tool and Python library for collecting and archiving Twitter JSON data via the Twitter API, please refer to their page for more information [twarc package](https://github.com/DocNow/twarc).
In this project, the command line looks like this:
~~~
!twarc2 search --archive --limit 500000 --start-time "2019-03-01" --end-time "2019-04-01" \
--expansions "author_id,geo.place_id,in_reply_to_user_id,referenced_tweets.id,referenced_tweets.id.author_id,entities.mentions.username" \
--tweet-fields "id,text,author_id,context_annotations,public_metrics,conversation_id,created_at,geo" \
--user-fields "created_at,id,location,name,public_metrics" \
--place-fields "contained_within,country,country_code,full_name,geo,id,name,place_type" \
"(obesity OR (gain weight) OR bmi OR diet)"
~~~
    

## 2.0 Data Cleaning
- The part one in Data Cleaning section is used for deleting the unqualified rows or columns, join the tables, etc.
- The part two in Data Cleaning section is used for understanding the distribution and numeric counts of the dataset. More importantly, four thresholds based on state, county, zip-code, and census tract are set to filter the bounding box to get the tweets with more precise geoinformation.
  
    
    
## 3.0 Data Analysis
### 3.1 AnalyzeLocalTime
Please refer to another repository of mine-[iso1861-UTC-timestamp-transfer-to-local-time](https://github.com/ANN-zhi/iso1861-UTC-timestamp-transfer-to-local-time) for detailed information.
### 3.2 WordCloud


    
### 3.3 Topic Moldeling  
Topic Modeling nbviewr [interactive interface](https://nbviewer.org/github/ANN-zhi/GEOG6590_ProgrammingForGIS_Script/blob/main/3.0%20Data%20Analysis/pyLDAvis_5.html)

### 3.4 CorrelationAnalysis

### 3.5 SentimentAnalysis
