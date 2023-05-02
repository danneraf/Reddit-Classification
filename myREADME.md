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
 
![Top 10 Titles](./images/aitatop10.png)
As shown in the bar chart above, there a highly common words in the titles of each subreddit that overlap, such as girlfriend, boyfriend, and ex. 

![Top 50 Words Venn Diagram](./images/aitavenn.png)
The venn diagram illustrates how many of the top 50 words in the titles of each subreddit overlap. With more than half of the words overlapping, you can see how it could be difficult to know which subreddit is the correct one to share in. 

The logistic regression model performed well, with train and test accuracies and f1-score all around 97%. False predictions were relatively low, and the model outperformed the baseline of 50%. In comparison, the decision tree model performed well, but not as well as the logistic regression, with a train and test accuracy and f1-score of around 94%.

To further assist redditors, I **recommend** a tool called *Reddy* that analyzes the post title and recommends a suitable subreddit. This not only helps redditors post in the appropriate subreddit, but also makes the process easier for moderators who need to filter posts. Additionally, it ensures that members or 'potential assholes' see more posts related to the subreddit they joined.

Overall, using logistic regression can predict which subreddit a post belongs to with high accuracy, and adding a tool like Reddy can make Reddit more user-friendly for everyone involved.

![Reddy](./images/snoo-small.png)

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
|**subreddit**|*int64*|reddit_final|The subreddits encoded as Relationship Advice: 1 and AITA: 0 for predictions |
|**selftext**|*object*|reddit_final|The bodies of the subreddit posts cleaned and vectorized |
|**gilded**|*int64*|reddit_final|The number of times the post has been gilded |
|**title**|*object*|reddit_final|The titles of the subreddit posts cleaned and vectorized |
|**subreddit_name_prefixed**|*float64*|reddit_final|The name of the subreddit |
|**hide_score**|*float64*|reddit_final|Whether the post score is hidden |
|**upvote_ratio**|*float64*|reddit_final|The ratio of upvotes to total votes on the post |
|**total_awards_received**|*int64*|reddit_final|The total number of awards the post has received |
|**is_reddit_media_domain**|*int64*|reddit_final|Whether the post is hosted on a Reddit media domain |
|**score**|*int64*|reddit_final|The score of the post |
|**author_premium**|*float64*|reddit_final|Whether the author has a Reddit premium account |
|**edited**|*int64*|reddit_final|Whether the post has been edited |
|**author_flair_richtext**|*int64*|reddit_final|The text of the author's flair |
|**is_self**|*int64*|reddit_final|Whether the post is a self-post |
|**author_flair_type**|*int64*|reddit_final|The type of the author's flair |
|**domain**|*int64*|reddit_final|The domain of the URL linked in the post |
|**allow_live_comments**|*float64*|reddit_final|Whether live comments are allowed on the post |
|**archived**|*int64*|reddit_final|Whether the post has been archived |
|**no_follow**|*int64*|reddit_final|Whether the post has the "no follow" attribute |
|**is_crosspostable**|*int64*|reddit_final|Whether the post is crosspostable |
|**over_18**|*int64*|reddit_final|Whether the post is marked NSFW |
|**awarders**|*int64*|reddit_final|The number of users who have given the post an award |
|**can_gild**|*int64*|reddit_final|Whether the post can be gilded |
|**locked**|*int64*|reddit_final|Whether the post is locked |
|**treatment_tags**|*int64*|reddit_final|Treatment tags applied to the post |
|**is_robot_indexable**|*int64*|reddit_final|Whether the post is indexable by search engines |
|**num_comments**|*int64*|reddit_final|The number of comments on the post |
|**send_replies**|*int64*|reddit_final|Whether replies are enabled for the post |
|**author_patreon_flair**|*int64*|reddit_final|Whether the author has a Patreon flair |
|**subreddit_subscribers**|*int64*|reddit_final|The number of subscribers to the subreddit |
|**created_utc**|*int64*|reddit_final|The time the post was created in UTC |
|**num_crossposts**|*int64*|reddit_final|Number of times the post has been cross-posted |
|**retrieved_utc**|*int64*|reddit_final|UTC time when the post was retrieved by the API |
|**updated_utc**|*int64*|reddit_final|UTC time when the post was last updated by the author |
|**author_cakeday**|*int64*|reddit_final|Boolean indicating if the author's Reddit account is celebrating a cake day |
|**subreddit_id_t5_2r0cn**|*float64*|reddit_final|Encoded subreddit id |
|**removed_by_automod_filtered**|*float64*|reddit_final|Indicates whether the post was removed by automoderator |
|**removed_by_deleted**|*int64*|reddit_final|Indicates whether the post was removed by the author |
|**removed_by_reddit**|*float64*|reddit_final|Indicates whether the post was removed by Reddit |
|**removed_by_nan**|*int64*|reddit_final|Indicates whether the removal status of the post is unknown |
|**thumbnail_nsfw**|*int64*|reddit_final|Indicates whether the thumbnail image for the post is NSFW |
|**thumbnail_self**|*int64*|reddit_final|Indicates whether the post has a self-post thumbnail |
|**gildings_{}**|*int64*|reddit_final|Number of times the post has been gilded |
|**title_word_count**|*int64*|reddit_final|Number of words in the post's title |
|**selftext_word_count**|*int64*|reddit_final|Number of words in the post's selftext |
|**subreddit_id_t5_2txi0n**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_id_t5_37roo**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_id_t5_5iegdf**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_id_t5_62obsy**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_id_t5_6anqhn**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_id_t5_6r00uj**|*float64*|reddit_final|Encoded subreddit id |
|**subreddit_type_restricted**|*float64*|reddit_final|Indicates whether the subreddit allows only certain users to post|
|**subreddit_type_user**|*float64*|reddit_final|Indicates whether the subreddit was created by a user |
|**thumbnail_other**|*float64*|reddit_final|Indicates whether the post has a non-default thumbnail |
|**gildings_'gid_2': 0**|*float64*|reddit_final|Number of times the post has been gilded with gid_2 |
|**gildings_'gid_3': 0}**|*float64*|reddit_final|Number of times the post has been gilded with gid_3 |
|**gildings_{'gid_1': 0**}|*float64*|reddit_final|The number of awards with the id {'gid_1': 0} received for the post|
|**gildings_{'gid_1': 1}**|*float64*|reddit_final|The number of awards with the id {'gid_1': 1} received for the post|
|**gildings_{'gid_1': 4}**|*float64*|reddit_final|The number of awards with the id {'gid_1': 4} received for the post|

