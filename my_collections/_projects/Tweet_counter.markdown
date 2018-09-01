---
layout: page
title:  "Amazon AWS based Tweet counter"
description: A pipeline for streaming applications, real-time processing, and aggregation and analysis; using Amazon AWS
date:   2017-7-15 17:49:38 +0100
category: AWS / Postgres
language: Python
language2: SQL
permalink: /_projects/tweet_count
links_as: buttons
excerpt_separator: <!--more-->

---
<div id="nav" class="clearfix">
<!-- <a href="#design">Design</a>  
<a href="#methods">Methods</a>  
<a href="#results">Results</a> -->
</div>

<h1>Summary</h1>

This pipeline tool is launched through an Amazon EC2 instance to gather and perform live analysis on tweet content. It uses Apache Storm, Amazon EC2, Python, Twitter API, Streamparse, Postgres, PsycoPG, and Tweepy.


![topology]({{ "/assets/images/AWS_tweet_counter.png"  }})
<!--more-->


The pipeline has the following components, which are built from the files in the first table:

1. A spout connected to the Twitter streaming API, that pulls tweets and emits them to the parse bolt.
2. A parse-tweet-bolt, that parses the tweets emitted by the spout, and extracts individual words out of the received tweet text.
3. A Postgres database called **tcount**, with a table called **tweetwordcount**.
3. A count-bolt, that counts the number of words emitted by the tweet-parse bolt, and updates the total counts for each word in the Postgres table
<br><br>

| Name of the program | Location | Description |  
|---------------------|----------|-------------|  
| tweets.py | /tweetwordcount/src/spouts/ | tweet-spout |  
| parse.py | /tweetwordcount/src/bolts/ | parse-tweet-bolt |  
| wordcount.py | /tweetwordcount/src/bolts | count-bolt |  
| Twittercredentials.py | [top level] | Twitter API Keys (**excluded**) |  
| tweetwordcount.clj | /tweetwordcount/topologies/ | Topology for the application |  


When credentials are entered, the program finalresults.py can be run from the command line to return the number of occurrences of one word if added as an argument, or of all words in the stream (for 1 minute).

The histogram program- also run from the command line, takes two arguments, a min and max, and returns all words and their counts with total occurrences in the provided limits.

[View on Github](https://github.com/cswavola/tweet_counter)
