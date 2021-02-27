### About the Problem Statment
Sentiment analysis remains one of the key problems that has seen extensive application of natural language processing. This time around, given the tweets from customers about various 
tech firms who manufacture and sell mobiles, computers, laptops, etc, the task is to identify if the tweets have a negative sentiment towards such companies or products.
#### Dataset: https://datahack.analyticsvidhya.com/contest/linguipedia-codefest-natural-language-processing-1
#### About the Dataset :
	1> Number of entries: 7920 (train)
	2> Target variable distribution: 74.4% positive sentiment and 25.5% negative sentiment samples
	3> Dataset does not contain any null values

### Exploratory Data Analysis
	1> Character Counts
	2> Word Counts
	3> Hashtag Counts
	4> Stopword Counts
	5> Special symbol counts i.e. words which are not alphanumeric
	6> Vulgar word counts 
	7> Sentiment Score (Vader)
### Preprocessing
	1> Remove URL, mentions, hashtags
	2> Remove multiple spaces
	3> Convert tweet to lowercase
	4> Remove all non-alphanumeric terms
	5> Remove single character words
	6> Contraction to Expansion
	7> Extract words present in `#` 
	8> Convert to words to base form (lemmatization)
	9> Remove stopwords
### Create additional features
	By decomposing the text using Latent Dirichlet Allocation we extracted top 5 features
	
#### According to EDA, doing basic feature extraction as we did above gave quite a good results even for basic models.

## Models

#### Random Forest
	feature used: ['word_count', 'charcter_count', 'hashtag_count', 'vulgar_word_count', 'symbol_count', 'stop_word_count', 
	'sentiment_score', 'topic_1', 'topic_2', 'topic_3']
	* I used only the top 3 features extracted using LDA.
	* Hyperparameters: n_estimator = 50, max_depth = 6
	* 10-fold CV : 0.88
#### Adaboost
	feature used: ['word_count', 'charcter_count', 'hashtag_count', 'vulgar_word_count', 'symbol_count', 'stop_word_count', 
	'sentiment_score', 'topic_1', 'topic_2', 'topic_3']
	* Hyperparameters: Default
	* 10-fold CV : 0.89
#### Gradient Boost
	feature used: ['word_count', 'charcter_count', 'hashtag_count', 'vulgar_word_count', 'symbol_count', 'stop_word_count', 
	'sentiment_score', 'topic_1', 'topic_2', 'topic_3']
	* Hyperparameters: Default
	* 10-fold CV : 0.89
#### Convolutional Neural Net
	feature used: ['tweet']
	* Preprocessing done for text is same except this time we did not remove stop words
	* validation score : 88
#### LSTM
	feature used: ['tweet']
	* Preprocessing done for text is same except this time we did not remove stop words
	* validation score : 88
##### * The above neural network model does word are in some cases they get stuck in local minima

## For the Final Prediction : Mode of all the prediction are taken













