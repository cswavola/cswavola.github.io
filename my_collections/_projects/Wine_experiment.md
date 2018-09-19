---
layout: page
title:  "Vous voulez du vin?"
description: Experimental analysis of wine-market features and purchase likelihood
date:   2018-08-20 17:49:38 +0100
category: Market Testing
language: R
links_as: buttons
permalink: /_projects/Wine_Exp
side-nav: on
excerpt_separator: <!--more-->
summary: {{excerpt}}
rank: 7
---

##### In collaboration with [Sharad Varadarajan][sharadsite] and [Rory Liu][rorysite].
###### [View full PDF]({{site.baseurl}}/assets/Wine_Writeup.pdf)  
<div id="nav" class="clearfix">
<a href="#design">Design</a>  
<a href="#methods">Methods</a>  
<a href="#results">Results</a>
</div>
<br>
<h1><a name="summary"></a>Summary</h1>
Design, launch, and statistical analysis of a multifactorial advertising experiment to evaluate the impact of foreign language marketing on perceived value of wine. Analysis used experimental techniques and multiple types of linear regression models.
<br>


<hr class="style-thin">

<br>
<h1><a name="design"></a>Design</h1>
This experiment was used to analyze multiple effects of marketing environment on the perception of product value. The multifactorial design includes three treatment variables: page language, flavor description length, and country of origin. While a product's country of origin is non-mutable for marketing purposes, this was an important feature to analyze any interaction with the page format. In addition to French and English, German was added as a language format to observe the effects of a foreign language that's not usually associated with the product. The description length was be used both as a feature and a metric of dosage for the language format.



<img src="/assets/images/Group_Design.png" alt="drawing" width="350" class="center"/>
<!--more-->
The experiment was conducted as a survey. Participants first answer demographic questions, then were prompted with the treatment. The multiple treatments were administered simultaneously in the form of an image of an online marketing page. Each variable appeared on the page
<br>

![Wine_sample]({{ "/assets/images/Sample_wine_page.png"  }})

The participants were then asked to guess the value of the wine advertised to them; this provided a continuous outcome variable. They were then asked if they would purchase the wine at three descending price points ($50, $35, $20), which would be used as binary variables to calculate purchase likelihood.    

<img src="/assets/images/survey_flow.png" alt="drawing" width="350" class="center"/>

The initial launch (after a pilot) showed a need for currency familiarity and/or engagement management. To achieve this while maintaining comparability, a baseline question was asked after the treatment and outcome steps- guess the cost of a gallon of milk. For the test group, responses that priced milk above $10 were filtered out. Filtering for duplicate IP addresses and geographical location were conducted to avoid inclusion of bots, clickfarms, and the risk of treatment spillover. This resulted in only 5% total attrition.  


<br>
<h1><a name="methods"></a>Analysis Methods</h1>
Initial analysis was conducted on the training set of data in order to establish hypotheses before launching the test set. While p-value penalties could have been used with a single launch, the baseline question for re-launch was critical, so a training/test set approach was used to prevent p-hacking. This allowed the use of multiple statistical methods across many hypotheses and interaction hypotheses to be tested. In addition to hypothesis testing, statistical methods were also used to examine heterogeneous treatment effects for specific demographic categories.  
<br>
The following statistical methods were tested with and without demographic covariates. The price guesses were processed as a continuous outcome variable, while the willingness to purchase responses were processed as binary variables, using logistic regression to evaluate probability of purchase as a percentage.  
<ul>
<li>Random inference with Sharp Null hypothesis (on bottom 95% of guesses) </li>
<li>Linear regression</li>  
<li>Robust linear regression (Huber method to control for outlier influence)</li>
<ul>
<li>Simple treatment</li>
<li>Paired treatment (2 variables)</li>
<li>Treatment track (3 variables)</li>
<li>Interaction models</li>
  <ul>
  <li>Same origin and page format</li>
  <li>Two-pronged interactions</li>
  <li>Three-pronged interactions</li>
  <li>Fully saturated model</li>
  </ul></ul>
  <li>Binary logistic regression (including above models and  interactions)</li>
</ul>

<br><br>
<h1><a name="results"></a>Findings</h1>
Treatment signals were undetectable using random inference (on the bottom 95% of price guesses) and the sharp-null and simple linear regression. Statistical significance was observed in binary logistic regressions with french layout * french origin at 5% statistical significance in the training set and 10% in the test set. It should be noted that further data acquisition could increase the intensity of this signal.

### Sample Images from Report
<br>
![Winecosts]({{ "/assets/images/Guess_costs_origin_description.PNG"  }})
<br>
![WineOLS]({{ "/assets/images/wine_OLS_table.PNG"  }})
<br>

[Project Git][Wine_git]  

<!-- <a href="#linktotop">Back To Top</a> -->

[sharadsite]: [https://github.com/sharadv99]
[rorysite]: [https://github.com/roryliu112]
[Hurricane_site]: http://people.ischool.berkeley.edu/~cswavola/Economics%20of%20a%20Hurricaine/d3/index.html
[Wine_git]: https://github.com/cswavola/241_Wine_Final
