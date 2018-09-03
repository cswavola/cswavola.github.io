---
layout: post
title:  "The Risks of an Open Dataset: Crime Edition"
date:   2018-03-14 12:22:57 +0100
description: A public dataset gets an in depth look from a privacy perspective.
category: Ethics
language: SQL
excerpt_separator: <!--more-->
links_as: buttons
image: assets/images/bigquery_crimemap.PNG
---

<div id="nav" class="clearfix">
<a href="#b1">Dataset</a>  
<a href="#b2">Identified Risks</a>  
<a href="#b3">Mitigation Methods</a>
</div>
<br>
<h1>Summary</h1>  
The Chicago Crime Data, accessible through Google BigQuery, provides a plethora of information regarding reported crime incidents in the city. Though it could be used to create metrics for community health, policing fairness, and incident-type frequency, the exposure and lack of recourse for unintentional participants could be at best inconvenient and possibly traumatic. After querying the dataset through the BigQuery client, I analyzed ethical risks in the publicly available dataset, and propose mitigation practices. Includes references to Solove, Nissenbaum, and Mulligan et al..

<br>
<hr class="style-thin">
<br>

<h1><a name="b1"></a>The Dataset</h1>

Among the extensive publicly available datasets on Google’s BigQuery is an in depth account of reported crimes (excluding murder) in Chicago. This dataset is updated as recently as the previous week, and contains data extracted from the Chicago Police Department’s Citizen Law Enforcement Analysis and Reporting (CLEAR) system. The dataset, containing data from as far back as 2001, had about 6.6 million records as of March 9th, 2018, with each record providing a location and block address for the reported incident and a description from the police report. While records of new incidents added to the database are presumably still accurate, it is unclear if there are any standard practices in place to update older records in the database to reflect follow-up actions including arrests or dismissal.    
<!--more-->
Each record contains a unique identifier, date of the incident, date of most recent update, incident details including a short description, if it’s domestic, if an arrest was made, administrative details, and location in multiple formats including coordinates, latitude/longitude, and block. The Incidents reported span many documented categories, including violent crimes, drug possession, parole violation, and crimes involving children. Locations are also described by property type, differentiating as far as kinds of businesses, or areas of a residence (“Residence- garage”). The data has been masked to protect the privacy of individual properties by removing house addresses beyond the block-level.  Upon further investigation into the table schema descriptions, the field contains the explanation that the location is shifted due to redaction, however this is not immediately clear from the BigQuery overview.    

![Data_sample]({{ "/assets/images/BigQuery_snip1.png"  }})

There may be a collection bias dependent on civilian-police relations or inherent policing biases. These potential biases can’t be identified in the dataset, as the data does not distinguish between police-identified incidents and incidents in which the police were called by civilians. At face value, fewer reports means fewer incidents, yet the relationship between the police and the community may impact their willingness to call the authorities, or lead to more incidents reported in specific communities or populations.
Still, the data reported here reflects an agreement of context to responsible policing, as population details like race, age, gender, and income, are not recorded. Even the inclusion of unverified reports has a role in determining overall activity and impact of current police presence. Additionally, when an individual reports a potential crime incident to the police, they generally expect that the police will respond and collect data/information on the incident for later use. However, when this dataset was initially made publicly available, the context of the usage changed from protection to potential exposure among peers and community members, without an opportunity for recourse

<br>
<h1><a name="b2"></a>Identified Risks</h1>
#### _Unverified Reports_
At a general level, without any data interaction, the dataset has fraught implications. First, the acquisition of records is generated from individual unverified reports, including incidents in which nobody was charged or arrested. While the surveillance of activity in an area may be a useful tool to the Chicago Police Department, it’s important to remember that the information collected correlates to surveillance of citizens who may have committed no wrong, possibly without their knowledge. In addition to the risk to personal privacy, the unverified reports, some of which correlate to verified incidents, distorts the dataset as an indicator of crime on the whole. This distortion and surveillance, specifically for the reports that should have been dismissed or excluded from the “crime data,” pose a privacy risk to the subjects of the reports (Solove, 2005).
<br><br>
#### _Identification Risks_

After interacting with the data, the lack of standardized entry practices show opportunities for risk and exploitation. The level of detail of the location type and block creates a risk of exposure for individuals in their own neighborhoods and communities. As the blocks are potentially very small and may only contain one property of a certain type (for example, it would be difficult to imagine that more than one or two department stores could be on the same block), identification within the community or through public business listings is a potential risk. While the latitude and longitude locations for residences are “shifted”, multiple locations coordinates often occur on the same block-level address, giving the perception of accuracy. Using these location coordinates, some of which only have a few associated incidents reported back through 2001, it’s possible to aggregate reports that appear to correspond to an individual or family - whether or not the actual incidents occurred at the same location described within data. The description of the incidents, some implicating multiple members of a household, are an invasion into people’s homes, a space considered especially private.  

For those without community familiarity of the blocks listed in the dataset, the latitude and longitude coordinates are provided to nine decimal places; at five decimal places, accuracy is less than 10ft. There are potential risks for those whose homes are implicated by the perceived accuracy of the coordinate systems, with no recourse to correct the dataset. The distortion of the dataset, detailed description of the reports, and insecurity in the updating and dismissal protocol without recourse for the subject pose a significant risk of harm to the social status of an individual incorrectly (or correctly) identified, and could even affect employment. In unregulated industries reliant on character references, like nannying, even perceived accuracy of these reports could harm employment chances of an individual.  

<img src="/assets/images/BigQuery_snip_lat_long.png" width="50" class="center_small">

The description of the incidents can implicate multiple members of a household or community, disseminating personal information about relationships within families, partnerships, employers, or even with the law. Through aggregation, individuals of a specific residence could have their parole status exposed, as well as their history with law enforcement. This level of detail is especially critical with domestic incidents or reports involving children. Some descriptions include phrases like “attack on unborn child,” or “sexual assault on child by family member.” This dissemination defeats the purpose of protecting these victims, and instead the assumed victims of the reported incident have potentially had their trauma shared without their consent. While data companies are required to erase or anonymize the data of minors, communities and individuals hold no such obligation and interact with the exposed subject more regularly than cookies would.
<br><br>

#### _Potential Harm from Privacy Violations_
An examination of the data along the Privacy Analytic Framework also raises concerns of potential violations of privacy.  Publicizing location and type of reported crime allows users of the data to potentially identify individual victims and perpetrators, contesting a main object of privacy - protecting victims’ right to keep their dignity and control over personal information (Mulligan, et.al, 2016).  Additionally, psychological and physical harm could result from having this data publicly available.  Not only is it possible that specific victims of crime could be identified through the dataset’s location and block fields, it is also possible that perpetrators of crime could be wrongly identified by a dataset user based on the “shifted” locations.  Not only would this result in emotional distress, but also physical and financial harm if wrongly identified perpetrators are denied employment or other benefits.  As a society, we expect our law enforcement officers to protect us from harm, however because this data is gathered from police activity, the Chicago Police Department may actually be inadvertently causing harm.  This is especially problematic when you consider that most people also require more privacy in their own homes than when out in public - based on contextual expectations, but many of the records in the data set are records of reported crimes in people’s homes.  
<br>
<h1><a name="b3"></a>Mitigation Methods</h1>
Multiple parties could provide some mitigation for the privacy risks in this publicly available data. The Chicago PD’s CLEAR program could institute technical solutions during the preprocessing stage of compiling the data. In an effort to reduce perceived accuracy or property identification, locations could be aggregated by wards or beats, both included in the dataset already. The inclusion of the precise coordinates enables easier processing to create map overlays and crime density infographics, like that of the Chicago Data Portal (below); however, using a predetermined location value for each block would eliminate the discrepancies that contribute to this perception of location exactness. Still, latitude and longitude values could be rounded upon entry, for even quicker processing.  

<img src="/assets/images/BigQuery_crimemap.png" width="50" class="center">

In order to reduce the risk of exposure for sensitive information, reports made about residences could receive separate preprocessing to remove victim information. To reduce distortion, the inclusion of a datafield indicating the status of the report as verified or unverified would offer significantly more clarity than the “arrest” field. Finally, enhancements to both transparency and choice could help mitigate privacy violations (Nissenbaum, 2011).  The process in which records are updated could be explained at the introduction of the dataset, to give insight as to the accuracy of each incident record.  Additionally, for citizens who find that their homes are within the crosshairs of an incident location coordinate - there should be a process for which the location coordinate can be disputed and changed.  

As this data was collected and released by a government institution, the government itself could institute standards for data processing and dissemination. The government also has a responsibility to guarantee that the assumptions made from the dataset cannot be used for institutional decision making.  There is a disclaimer on the City of Chicago website, however there are no notification, consent, or correction protocols in place.  Additionally, Google BigQuery could better educate users about the exact precision (or lack thereof) of each field before they offer the user a console to begin their research. While legally this data cannot be easily identified to an individual, the lasting effects of community perception and interpersonal risks are much more easily prevented than corrected.

<br>

----

<br>
The article above was originally posted on the Berkley blog for Ethical Legal Data Science on February 6, 2018. Check out the [original post][Berkeley-post] and more articles about data ethics on [Berkeley's Blog][Berkeley-home].

----

#### References

Solove, D. J. (2005). A Taxonomy of Privacy. University of Pennsylvania Law Review, 154.

Mulligan DK, Koopman C, Doty N. (2016) Privacy is an essentially contested concept: a multi-dimensional analytic for mapping privacy. Phil. Trans. R. Soc. A 374: 20160118.

Nissenbaum, H. (2011) A Contextual Approach to Privacy Online.  Daedalus: the Journal of the American Academy of Arts & Sciences, 32

[Berkeley-post]:https://blogs.ischool.berkeley.edu/w231/2018/02/06/candy-cigarettes-now-available-in-blue-speech-bubble-flavor/
[Berkeley-home]:https://blogs.ischool.berkeley.edu/w231/
[mkids-home]:https://messengerkids.com/
[mkids-brand]:https://newsroom.fb.com/news/2017/12/introducing-messenger-kids-a-new-app-for-families-to-connect/
[USlaw]:https://www.ftc.gov/enforcement/rules/rulemaking-regulatory-reform-proceedings/childrens-online-privacy-protection-rule
[CCFC-letter]:http://www.commercialfreechildhood.org/sites/default/files/devel-generate/gaw/FBMessengerKids.pdf
[fb-pub]:https://newsroom.fb.com/news/2017/12/hard-questions-kids-online/
