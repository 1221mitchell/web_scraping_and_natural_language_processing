EXECUTIVE SUMMARY

PROBLEM STATEMENT:

Can we use natural language processing to determine if a post on reddit came from the ask science subreddit or the personal finance subreddit? What is the most accurate model for classifying a post?

WHY IS THIS PROJECT IMPORTANT?:

This project demonstrates the ability for natural language processing and machine learning models to identify the subject and content of a post on social media. 

This process can be helpful for companies that would like to monitor social media to identify which topics are trending for a given focus group. 

This project helps show which machine learning tools may be most accurate when classifying a text based post. 


DATA COLLECTION:
    
I wrote a function used for scraping data from reddit. The function uses the reddit pushift API and I used it to gather data from the ask science subreddit and the personal finance subreddit. I saved the outputs of my function to a csv file so I could access the data I had scraped without redoing my query.

EDA AND CLEANING:

My datasets have 29677 entries, with almost exactly a 50/50 split between posts coming from the ask science and personal finance subreddit. I dropped the very few null values form my dataset. Next I checked for most common values in my title and self text columns. This was to see if there were any troublsome entries that repeated and could get in the way of proper natural languae processing and prediction modeling. I found that "removed" and "deleted" was repeated in the data sets in self text.

Next, I check how often "removed" is an input in the data sets for self text and for title. I find "removed" is the imput for the majority of the entries for self text in the ask science data frame.  I believe this is because in ask science the posts are phrased as a question which can be fully articulated in the title of the reddit post. I will not be using the selftext feature in my analysis due to the findings here and will instead focus on classifying my entries based on the title text of the posts. 

Next I wrote a function to add a column in each dataframe which classifies where each post came from. This calssifier will be used to train and test my data for modeling. I calssified the ask science subreddit as 0 and  the personal finance reddit as 1.

Next I stacked the two data frames on top of each other and created on large master data frame. I also dropped the column "Unnamed: 0".

PREPROCESSING AND MODELING:
    
I set my X and y variables. My X variable is the title text. My y variable is the subreddit that the text came from.

Next I ran my train test split and count vectorizer for nartural language processing. Then I fit and transformed training data with my count vectorizer. 

Then I printed out the most common words in each dataset and also in the combined datasets to give me an initial understanding of the common words used in each subreddit. 

Next I check the null model values to get my baseline accuracy score.

Finally I jump into modeling. I set up a pipeline and/or grid search to find optimized values for my models. I fit my model and then score my models based on the accuracy score specifically. I also print out other supporting statistics to contextualize my model's predictive capabilities. 

I used the following models: two types of Niave Bayes models, an Ada Boost Classifier, a Gradient Boost Classifier, and finally an SVC Model.

CONCLUSIONS AND RECOMENDATIONS:

In this project I found that we can use natural language processing to determine if a post on reddit came from the ask science subreddit or the personal finance subreddit with 97.1% accuracy on unseen data. 

I found the most accurate model for classifying a posts source to be a Naive Bayes model.

For companies trying monitor social media to identify which topics are trending for a given focus group, I recommend using a Naive Bayes model for classification
If a Naive Bayes model is not getting an ideal accuracy score, I recommend also trying the runner up model, SVC.  
