## Am I the Asshole? 
## a data scraping and NLP project by Jena Brentano

### Problem Statement

Create the underlying predictive model for an app that takes user input stories and outputs an alert that tells the user whether they played the role of asshole in their story. 

### Methods:
-	Gather training data from Subreddit r/AmItheAssole
-	Give submissions a vote of asshole or not asshole (our target) based on if they had more comments mentioning YTA or NTA (‘you’re the asshole’ and ‘not the asshole’, respectively, this subreddit’s convention for voting whether the submitter is the asshole.
-	Transform the submission text and title text by lemmatizing and stemming, removing stopwords, and running through CountVectorizer of TfidfVectorizor to build a bag of words model with Logistic Regression and Random Forest.

### Data Description
1,714 rows of data, each representing a submission on the reddit. 

For this project, the used columns for submissions are:
-	title (post title)
-	selftext (body of post, i.e. the submitted story)
-	id (post id)
For the comments, the relevant columns are:
-	parentid (used to associate the comment to the post it’s commenting on)
-	selftext (body text of the comment)

Unfortunately the PushShift API did not allow scraping of the scores of the comments (upvotes) which would have counted as extra votes. This can be manually scraped in the future to create a better training data by adding a for strength of the vote.

### Primary Findings/Conclusions
The models created were not better than the baseline.  The conclusion is that a bag of words model for this type of problem is insufficient. More sophisticated techniques and analysis are necessary for drawing accurate meaning from these stories. It seemed clear that intention, reflection, responsibility and blame were key components in determining whether the submitter was the asshole (words  like ‘feel’, ‘hurt’, ‘why’, ‘deserve’ could be especially important). It would be important to distinguish who did what in the story, and the directionality of statements (was it the submitter who said that, are they quoting the other party in the story, etc.) I can imagine one could get closer to a predictive model with sentiment analysis, or a more considered bag of words with ngrams and special phrases, done on individual sentences in the story with markers for ‘I’, ‘they’, etc.


