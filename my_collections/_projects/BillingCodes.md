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
<!-- <a href="#6">Error and Analysis</a> -->
<a href="#7">Team</a>
</div>
<br>
<hr>



<br>
<h1><a name="1"></a>Introduction and Impact</h1>

A key medical inefficiency is the hospital revenue cycle - where hospitals bill for services provided. Due to fragmented workflows, care providers must accurately bill for procedures that could have happened hours or days in the past<sup>1</sup>. Errors in the process are common and often - some sources suggest that up to 80% of billing cases contain an error in some form<sup>2</sup>, and errors often lead to billing discrepancies in excess of $1300<sup>3</sup>. These errors also result in claims denials, which adversely affect the patient experience. CodeAssist is an intelligent system that leverages sophisticated machine learning techniques to generate surgical and anesthesia CPTs based on patient data, preoperative free text, and post-operative free text.

Working with industry professionals has led to a thorough understanding of the billing process, which is reflected in the product UX. Preoperative data informs an initial prediction, which is surfaced to the surgeon for confirmation or denial, along with a simple prompt for brief post-operative notes. The surgeon’s input is then passed to the facility billing staff along with a revised set of predictions and a risk rating of incorrect billing.

<img src="/assets/images/CA_workflow.PNG" alt="drawing" />

With a relatively small starting dataset, we predict anesthesia billing codes with 77.3% accuracy (human baseline of 72.9%). We predict incorrectly billed cases with 75% accuracy (baseline of 56%). Due to the large number of surgical CPT codes, human billing staff are still 11% more accurate in delineating exact sets of surgical CPT codes, which we aim to address with ongoing data collection efforts.

<br><br>
<!--more-->
<hr>
<h1><a name="2"></a>Pre-Model Processing</h1>
In order to ensure the most efficient model, CodeAssist employed two major data preprocessing steps: text cleaning and output class category merging or binning.

Text cleaning included null/NA data removal, tokenization, lowercasing, deduplication, stopword removal, stemming and lemmatization on the input, namely, the preoperative notes, used to train the model.

<br>
![textProcess]({{ "/assets/images/CA_textProcess.PNG"  }})
<br>

The motivation for binning was driven by the observation that the number of output classes was very large in comparison to the size of the dataset, and that there were many clusters of output codes referring to surgical procedures that differed only in details of dimensions, location or other attribute. Predicting the specific code based on preoperative notes alone would have led to inaccuracies, since in many cases the specific dimensions and locations of the procedure are only known after the procedure is complete.

From a performance metric perspective, by combining these codes into bins, training the models on the bins and predicting the bins, CodeAssist achieved a higher accuracy and recall, as more false positives were surfaced when the bin(s) are expanded and presented to the user. This issue is mitigated because the surgeon can select the correct individual codes from the expanded bin(s).

The decision to prioritize accuracy and recall over precision was validated with potential users of the system.


<br><br>
<hr>
<h1><a name="3"></a>CodeAssist Code Prediction</h1>

CodeAssist leverages a unique design to address the key challenges of predicting surgical CPT codes. The model architecture allows for the consumption of multi-label training data and yields multiple outputs using proprietary heuristic confidence thresholds.     

![model_NLP]({{ "/assets/images/NLP_modelProcess.PNG"  }})

The ML pipeline contains both a surgeon-specific model set as well as a general model set. The surgeon specific model set captures the tendencies of high-volume surgeons, while the general model prevents bias against new codes. Combining predictions from both model sets allows for robust, specific, and generalizable predictions.
<br>
![CA_logic]({{ "/assets/images/CAinference.PNG"  }})
<br>
This video explains our training paradigm and inference logic and how it impacts code predictions.     

{% include googleDrivePlayer.html id="1d3VAJbX4qsLIWfw7M_VwxLYmm8LrfkPi/preview" %}


<br><br>
<hr>

<br><br>
<h1><a name="4"></a>CodeAssist Risk Prediction</h1>
In addition to predicting CPT codes, CodeAssist also predicts the risk of a billing error by a facility. The predictor is built upon a CNN (Convolutional Neural Network) based text classifier: the model uses the Pre-Op and Post-Op notes as its input and predicts the accuracy of a facility billing coder by assessing the depth of information in the provided text.     
To capture the semantic meanings of words, we encode the input text using pre-trained GloVe word embeddings. These word embeddings are not rigidly implanted- they can be altered during the training of the model, enabling the learning of task-specific features. To alleviate overfitting, we also apply L2 regularization and dropout to the model, making each decision node more robust.

![CA_CNN]({{ "/assets/images/CA_CNN.PNG"  }})

Our EDA shows the hospital billing codes are correct 57% of the time. Improving over this baseline, our CNN model has achieved a risk prediction [accuracy of 70%]({{site.baseurl}}/assets/images/CA_CNNperform.PNG") [across patients]({{site.baseurl}}/assets/images/CA_CNNerror.PNG"). Experiments show the prediction accuracy improves with the size of training data, thus, we expect better model performance when more data becomes available.



{% include googleDrivePlayer.html id="1U64s25RWixvsZJugtcytwkjUDiTnhaH3/preview" %}
<br><br>
<hr>
<h1><a name="5"></a>Demo</h1>
##### CodeAssist Code Prediction
{% include googleDrivePlayer.html id="1TI_yhOaJ9EP76ezN-_-iotlWyCuHJHkD/preview" %}_
<br>
##### CodeAssist Risk Prediction
{% include googleDrivePlayer.html id="1Lt1soFW3cUKEBVQJ4PQumuxBo4GGv8cf/preview" %}
<br><br>
<hr>

<hr>
<h1><a name="7"></a>Team</h1>
![CA_team]({{ "/assets/images/CA_team.PNG"  }})
<div align="middle">
  <a style="padding: 0px 45px;" href="https://www.linkedin.com/in/nvelagapudi/">
    <i class="fa fa-linkedin"></i>   Nishant
  <a style="padding: 0px 45px;" href="https://www.linkedin.com/in/sohag-desai/">
    <i class="fa fa-linkedin"></i>   Sohag
  <a style="padding: 0px 45px;" href="https://www.linkedin.com/in/charlotte-swavola/">
    <i class="fa fa-linkedin"></i>   Charlotte
  <a style="padding: 0px 15px;" href="https://www.linkedin.com/in/zhaoning-yu/">
    <i class="fa fa-linkedin"></i>   Zhaoning</a>

<br><br><br><hr>
<div align="left">
<sup>1</sup> <a href="https://www.forbes.com/sites/brucelee/2016/09/07/doctors-wasting-over-two-thirds-of-their-time-doing-paperwork/#5e3d4ec75d7b">Doctors wasting over two thirds of their time doing paperwork (Forbes)</a>   <br>  
<sup>2</sup> <a href="http://www.healthcarebusinesstech.com/medical-billing/">Medical Billing (Healthcare business and Technology)</a>        <br>
<sup>3</sup> <a href="https://healthcareinamerica.us/medical-billing-errors-are-seriously-hurting-healthcare-67d134441adc">Medical Billing Errors Are Seriously Hurting Healthcare (Healthcare via Employee Benefits Advisor)</a>
