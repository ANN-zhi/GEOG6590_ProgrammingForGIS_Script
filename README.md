# GEOG6590_ProgrammingForGIS_Script
Fall, 2021 

## 1.0 Tweet Scraper
Two methods are used to scrape and dump Tweets using [Twitter API for Academic research](https://developer.twitter.com/en/products/twitter-api/academic-research), they could produce exactly the same results. The API grants free access to full-archive search and other v2 endpoints, with a volume cap of 10,000,000 tweets per month.   
Method 1 was written by me, while Method 2 calls the [twarc package](https://github.com/DocNow/twarc). Method 2 is recommended because it's more convenient and understandable: all the raw codes are encapsulated, and it's possible to finish all the work with only one line. 
### 1.1 Method 1
The tweetScraper.ipynb is the main program, all the other py files are functions used in the tweetScraper program.  
- The **auth()** in auth_function.py saves the “Bearer Token” you use to assess Twitter API in an an “environment variable”. Since this Bearer Token is sensitive information, you should not be sharing it with anyone at all.
- The **create_url()** in create_url_function.py build the request for the endpoint we are going to use and the parameters we want to pass. You could adjust your params here based on the [API reference](https://developer.twitter.com/en/docs/twitter-api/tweets/search/api-reference/get-tweets-search-all):
```
query_params = {'query': keyword,
                'start_time': start_date,
                'end_time': end_date,
                'max_results': max_results,
                'expansions': 'author_id,geo.place_id',
                'tweet.fields': 'id,text,author_id,in_reply_to_user_id,geo,conversation_id,created_at,lang,public_metrics,referenced_tweets,reply_settings,source',
                'user.fields': 'id,name,username,created_at,description,public_metrics,verified',
                'place.fields': 'full_name,id,country,country_code,geo,name,place_type',
                'next_token': {}}
```

  
### 1.2 Method 2
The [twarc package](https://github.com/DocNow/twarc)
    

## 2.0 Data Cleaning

  
    
    
## 3.0 Data Analysis
### 3.1 AnalyzeLocalTime
Please refer to another repository of mine-[iso1861-UTC-timestamp-transfer-to-local-time](https://github.com/ANN-zhi/iso1861-UTC-timestamp-transfer-to-local-time) for detailed information.
  
    
    
### 3.3 Topic Moldeling  
Topic Modeling nbviewr [interactive interface](https://nbviewer.org/github/ANN-zhi/GEOG6590_ProgrammingForGIS_Script/blob/main/3.0%20Data%20Analysis/pyLDAvis_5.html)
