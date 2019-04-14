---
layout: page
title:  "CodeAssist"
description: Predict hospital billing codes using NLP on hospital notes
date:   2019-04-10
category: NLP
language: #python
links_as: #buttons
permalink: /_projects/codeassist
excerpt_separator: <!--more-->
image: false
rank: 8

---
<div id="nav" class="clearfix">
<a href="#1">Introduction and Impact</a>  
<a href="#2">Pre-model Processing</a>  
<a href="#3">Code Prediction</a>
<a href="#4">Risk Prediction</a>
<a href="#5">Demo</a>
<a href="#6">Team</a>
</div>
<br>
<hr>



<br>
<h1><a name="1"></a>Introduction and Impact</h1>

A key medical inefficiency is the hospital revenue cycle - where hospitals bill for services provided. Due to fragmented workflows, care providers must accurately bill for procedures that could have happened hours or days in the past. Errors in the process are common and often - some sources suggest that up to 80% of billing cases contain an error in some form, and errors often lead to billing discrepancies in excess of $1300<sup>1</sup>. These errors also result in claims denials, which adversely affect the patient experience. CodeAssist is an intelligent system that leverages sophisticated machine learning techniques to generate surgical and anesthesia CPTs based off patient data, preoperative free text, and post-operative free text.

Working with industry professionals has led to a thorough understanding of the billing process, which is reflected in the product UX. Preoperative data informs an initial prediction, which is surfaced to the surgeon for confirmation or denial, along with a simple prompt for brief post-operative notes. The surgeon’s input is then passed to the facility billing staff along with a revised set of predictions and a risk rating of incorrect billing.

<img src="/assets/images/CA_workflow.PNG" alt="drawing" />

With a relatively small starting dataset, we predict anesthesia billing codes with 77.3% accuracy (human baseline of 72.9%). We predict incorrectly billed cases with 75% accuracy (baseline of 56%). Due to the large number of surgical CPT codes, human billing staff are still 11% more accurate in delineating exact sets of surgical CPT codes, which we aim to address with ongoing data collection efforts.

<br><br>
<!--more-->
<hr>
<h1><a name="2"></a>Pre-Model Processing</h1>

<br>
<!-- ![EDA_features]({{ "/assets/images/EDA_features.PNG"  }}) -->
<br>

<br><br>
<hr>
<h1><a name="3"></a>CodeAssist Code Prediction</h1>

##### NLP Model Structure

![model_NLP]({{ "/assets/images/NLP_modelProcess.PNG"  }})
<br><br>
##### Inference Logic

![CA_logic]({{ "/assets/images/CAinference.PNG"  }})
<br><br>
<hr>

<br><br>
<h1><a name="4"></a>CodeAssist Risk Prediction</h1>
![CA_CNN]({{ "/assets/images/CA_CNN.PNG"  }})
<hr>
<h1><a name="5"></a>Demo</h1>
##### CodeAssist Code Prediction
{% include googleDrivePlayer.html id="1TI_yhOaJ9EP76ezN-_-iotlWyCuHJHkD/preview" %}
<br>
##### CodeAssist Risk Prediction
{% include googleDrivePlayer.html id="1Lt1soFW3cUKEBVQJ4PQumuxBo4GGv8cf/preview" %}
<br><br>
<hr>
<h1><a name="6"></a>Team</h1>
![CA_team]({{ "/assets/images/CA_team.PNG"  }})
<div align="middle">
  <a style="padding: 45px;" href="https://www.linkedin.com/in/nvelagapudi/">
    <i class="fa fa-linkedin"></i>   Nishant
  <a style="padding: 45px;" href="https://www.linkedin.com/in/sohag-desai/">
    <i class="fa fa-linkedin"></i>   Sohag
  <a style="padding: 45px;" href="https://www.linkedin.com/in/charlotte-swavola/">
    <i class="fa fa-linkedin"></i>   Charlotte
  <a style="padding: 45px;" href="https://www.linkedin.com/in/zhaoning-yu/">
    <i class="fa fa-linkedin"></i>   Zhaoning

<br><br><br><hr>
1: <a href="https://healthcareinamerica.us/medical-billing-errors-are-seriously-hurting-healthcare-67d134441adc">Medical Billing Errors Are Seriously Hurting Healthcare (Healthcare via Employee Benefis Advisor)</a>
