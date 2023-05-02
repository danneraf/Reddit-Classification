# <img src="https://www.nicepng.com/png/detail/206-2065604_facial-expression-black-and-white-nose-head-reddit.png" width="55" height="55"> READ ME: Am I The Asshole for posting in the wrong subreddit?
#### NTA
---
### Contents:
- [Introduction](#Introduction)
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Datasets](#Datasets)
- [Data Dictionary](#Data-Dictionary)
---
## Introduction
Reddit has thousands of subreddits for people to post in for many different topics: games, politics, stocks, and more importantly: advice.

Am I The Asshole and Relationship Advice are two subreddits meant for people to share posts about their situations and ask for people's opinions/advice. Though you can find similar sounding posts on both subreddits, the subreddits are meant for different reasons.

In a way they are similar because people share interpersonal conflicts, especially in relationships. 
Both subreddits have certain rules for what you can share there, meaning what AITA may allow, Relationship Advice may not. For example, Relationship Advice requires posts to be about a *current* issue, whereas someone could post on AITA about something that happened 10 years ago. 

The responses people give on the posts can contain advice, but the responses expected are different. AITA has a voting system to determine who is the asshole, and Relationship Advice responses are meant to help someone with their issue at the moment. 

Both subreddits have commenters analyzing the posted situations and providing their opinions, both include posts about current situations, and both include posts about relationships.

Posting the issue you'd like an opinion for in the wrong subreddit could result in unhelpful comments, or your post not being approved to begin with. 

## Problem Statement 
### Can a model predict which subreddit you should post to?  

## Executive Summary 
To answer this question, I created a model using logistic regression to help redditors post in the correct subreddit. I collected 3,000 posts from both *Am I the Asshole* and *Relationship Advice* subreddits, cleaned and transformed the data using the TfidfVectorizer, and used the post titles to predict the subreddit. 
 
The logistic regression model performed well, with train and test accuracies and f1-score all around 97%. False predictions were relatively low, and the model outperformed the baseline of 50%. In comparison, the decision tree model performed well, but not as well as the logistic regression, with a train and test accuracy and f1-score of around 94%.

To further assist redditors, I **recommend** a tool called *Reddy* that analyzes the post title and recommends a suitable subreddit. This not only helps redditors post in the appropriate subreddit, but also makes the process easier for moderators who need to filter posts. Additionally, it ensures that members or 'potential assholes' see more posts related to the subreddit they joined.

Overall, using logistic regression can predict which subreddit a post belongs to with high accuracy, and adding a tool like Reddy can make Reddit more user-friendly for everyone involved.

---

## Datasets
---
* [`ra2.csv`](./datasets/ra2.csv): Collected Relationship Advice Data  
* [`aita2.csv`](./datasets/aita2.csv): Collected AITA Data  
* [`ra_cleaned.csv`](./datasets/ra_cleaned.csv): Cleaned Relationship Advice Data
* [`aita_cleaned.csv`](./datasets/aita_cleaned.csv): Cleaned AITA Data
* [`ra_eda.csv`](./datasets/ra_eda.csv): Relationship Advice Data After EDA
* [`aita_eda.csv`](./datasets/aita_eda.csv): AITA Data After EDA  
* [`reddit_combined.csv`](./datasets/reddit_combined.csv): Relationship Advice Data and AITA Data Combined
* [`reddit_final.csv`](./datasets/reddit_final.csv): Final Combined Reddit Dataset Used for Modeling   

## Data Dictionary
---
|Feature|Type|Dataset|Description|
|---|---|---|---| 
|**title**|*object*|reddit_final|The titles of the subreddit posts cleaned and vectorized |
|**subreddit**|*int*|reddit_final|The subreddits encoded as Relationship Advice: 1 and AITA: 0 for predictions |
|**selftext**|*object*|reddit_final|The bodies of the subreddit posts cleaned and vectorized |




1. [*How does a real estate agent set my home asking price?*](https://themortgagereports.com/42630/how-does-a-real-estate-agent-set-my-home-asking-price) 

#### Methods
The original datasets were imported and cleaned using the Python Data Analysis Library (pandas) to ensure the findings would be accurate and to prevent any issues with analysis. The datasets were saved as new datasets following data cleaning, and these dataframes were transformed a final time before being used for modeling with Scikit-learn. Visualizations were created using Matplotlib and Seaborn libraries during exploratory data analysis and following modeling to show correlations. Visualizations utilized to display the data include heatmaps, histograms, scatterplots, and boxplots. Conclusion and recommendations were given based on the findings of the analyzed data.

## Conclusions and Recommendations

**In conclusion,** the Lasso regression model (compared to Linear and Ridge) was the most successful in predicting home sale prices, with a Root Mean Square Error of 26794.86 and an R2 of around 90%. This indicates that the predicted home prices are on average within $26,794.86 of the actual home price, with 90% of the variability of the sale price explained by the predictor variables (home qualities). The baseline Root Mean Square Error was 81999.94, and with the Root Mean Square Error of the Lasso model being less than a third of that, this shows that the model works better than the baseline. 

![Top 20 Qualities](./images/amescorr20.png)

Based on the correlations between home qualities and sale price, **recommendations** for realtors wanting to help their clients would be:

1. Focus on the overall quality of the home, making sure any obvious repairs are completed before listing.

2. Adding extra square footage in living or garage space can increase value.

3. Improving the quality of the kitchen can raise the sale price.

4. If the home has a basement that you can easily walk through (80+ inches), this should be showcased in the listing. 

![Top 20 Coefficients](./images/amescoef.png) 

Based on the coefficients (increase in Sale Price based on one unit change in home quality), realtors can **recommend** homeowners to focus on the following areas to increase the sale price of their home:

1. Gr Liv Area: Increasing the above ground living area in the home could lead to a significant increase in the sale price. ($27009 per increase)

2. Overall Qual: Improving the overall quality of the home, such as through renovations or upgrades, can also have a large impact on the sale price. ($11401 per increase in Overall Qual rating)

3. Neighborhood_NridgHt and Neighborhood_StoneBr: Being in a desirable neighborhood, such as Northridge Heights and Stone Brook, can also increase the sale price - if the home is located in one of these neighborhoods, this should be shown in the listing. ($6192 - 8462 increase based on neighborhood)

4. 1st Flr SF: Increasing the size of the first floor of the home can also have a positive impact on the sale price. ($7742 per increase)

5. Kitchen Qual: Improving the quality of the kitchen, through upgrades or renovations, can increase the sale price. ($6562 per increase in Kitchen Qual rating)

6. Bsmt Qual: If the home has a basement that you can easily walk through (80+ inches), this should be showcased in the listing. ($6343 increase)

7. Bsmt Exposure: Showcasing a basement that has an access to walk outside can increase the sale price. ($6343 increase) 

8. Garage Cars: Increasing the number of cars the garage can hold, through expanding or adding a garage, can also increase the sale price. ($5372 per car space increase) 

9. Exter Qual: Improving the quality of the exterior of the home, through renovations or upgrades, can also have a positive impact on the sale price. ($5343 per increase in Exter Qual rating) 

Realtors should consider these factors when guiding homeowners on where to invest their time and money in preparing their home to sell, as well as when choosing which home qualities to feature in a lisiting. 


These recommendations are consistent with articles regarding home renovations that increase home value:

1. [*Top 15 Home Updates That Pay Off*](https://www.hgtv.com/lifestyle/real-estate/top-home-updates-that-pay-off-pictures) 
2. [*10 Home Updates That Quickly Increase Value*](https://www.ahs.com/home-matters/real-estate/home-updates-increase-value/) 
3. [*These 7 Major Home Renovations Add Value*](https://www.bhg.com/home-improvement/advice/expert-advice/4-home-renovations-that-add-major-value-281474979622820/)  

**Bonus:** an *amazing* chart can be found [*here*](https://cdn.fixr.com/content/01-ROI-9a7b.jpg) from [*this article*](https://www.fixr.com/resources/cost-vs-value) 