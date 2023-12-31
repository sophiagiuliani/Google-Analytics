# Google-Analytics

This is an ongoing project for a company that has a online store. Most of purchases are made directly with clients on Instagram, but the owner wants to increase the sales made directly on the website. In order to do so, I will use Google Analytics to create custom events, implement URL's, connect Google Analytics with Google Ads and create dashboards. After this first step I will present a report with marketing campaigns results, audience profile, and most used traffic sources. 

 ## Attribution report

Metrics and dimensions of the attribution report were edited to show relevant data for the business.

 ![attribution report ](https://github.com/sophiagiuliani/Google-Analytics/assets/126698969/1c1e5f30-c338-430a-8946-2d12642f47ad)

 I created a dashboard on Looker Studio because it is possible to connect the data in Google Analytics directly with Looker. The purpose of this dashboard is to show the session attribution through time; compare the number of sessions that are attributed to each origin and campaign; and compare the bounce rate, engagement rate and revenue attributed to each campaign and origin. I also included the possibility of choosing the data range and the city of the session. The idea is to show, in general, where the users are coming from before arriving at the website, so the store can have a better idea of the performance of each campaign and social media. This is the dashboard: 

![Captura de Tela (133)](https://github.com/sophiagiuliani/gif/assets/126698969/b772ea53-69f5-49a0-996d-5a4626a41e4b)

 ### Challenges:
 
1. One of the problems of the attribution report is the data when analysing number sessions by session origin. The store uses a tool that allows users to create a landing page with links to their social media profiles. The URL of this tool is what appears as "session's origin", instead of the social media itself. Not knowing exactly from which platform the user arrived from can affect the real numbers.

To solve this problem, I will propose the store to use UTM parameters (tags added at the end of a URL) to track the performance of this tool links across different social media platforms. Once the tags are added, it is possible to see the results in the campaigns section of the google analytics reports.

2. In a similar sense, some traffic sources such as instagram are not unified, which means that "l.instagram" and "instagram" are shown as different traffic sources. The problem is that not unifying them can lead to wrong conclusions, since "instagram" can be in the second place in number of sessions, but would be the first if the sessions from "l.instagram" were combined.

In Universal Analytics it was possible to unify the traffic sources by creating a filter in the admin section. However, it is not possible to do that in Google Analytics 4 and I could not find anything online that explains how to unify them. To solve this issue I decided to export the data to BigQuery and will use SQL to unify the sources and then connect it to Looker Studio for the visualization. Update: The data from GA4 takes up to a day to be uploaded at BigQuery. While I waited for it, I explored other options and realized that it was possible to use the Looker Studio calculated fields to group all instagram sources into one. In order to do that I simply used the function REGEXP_REPLACE. Here is how it looks like:

```
REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE(
Session Origin,'l.instagram.com','instagram.com'),'lm.facebook.com','facebook.com'
),'m.facebook.com','facebook.com'),'l.facebook.com','facebook.com')
```

3. Considering tha Google Analytics provides several attribution models, it is important to choose the one that fits better the business. Last click, first click or linear could be used, depending on the focus. If the focus is on channels that are driving the most immediate conversions, last click would be the option; if the focus is on the channels that are driving initial awareness and interest, then first click would be best option; and if the focus is in all touchpoints of the user journey, then linear would fits better the goal. I personally believe that linear would be the best option because it can help to understand which channels are driving initial awareness and interest, which channels are driving consideration and evaluation, and which channels are driving conversion and loyalty. This model can be changed as the marketing campaigns expand in reach. 

## Engagement report

Metrics and Dimensions of the events and conversions reports were edited to fit better the business characteristics and needs. Because the target audience was not configured yet, the conversions by the target audience graph will not who relevant data. 
 

   This project will be updated weekly. 
