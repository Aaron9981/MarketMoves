Stock Portfolio Optimzation:
 - Main Implementation:
	 - Sentiment Analysis of News/Social Media
	 - Translation of foreign articles
	 - Make Financial Docs more accessible by summary without technical terms
	 - Using Sentiment Analysis as Input to overall Optimization RL Agent:
	 	 - Suggest a trading action to user
 - Front End development
	 - 
 
 https://docs.google.com/document/d/1iom2wuuppJt0wGYCAUpOEFlKTYcLIH9XP6RkGmMEvlA/edit?usp=sharing
 

 Sentiment Analysis Implementation:
	 - Use News API to import content
	 - Text Processing:
		 - Use the following Python Libraries:
		 	 - NLTK, spaCy, or TextBlob for:
			 	 - Tokenization: separate text into words called "tokens"
				 - Stemming/Lematization: Reduce words to their base form
				 - lowercasing for all words
	 - Sentiment Scoring:
	 	 - Can be done simply with TextBlob
		 	 - text analysis and polarity detection
		 - OR AFINN lexicon library


Implementation Pseudocode:

# NOTE: 
# Psuedocode for collecting data
function get_twitter_data(api_credentials, search_term):
    # Authenticate to the Twitter API
    authenticate(api_credentials)
    # Search for tweets related to the search_term
    tweets = api_search(search_term)
    return tweets

function get_news_data(api_credentials, search_term):
    # Use Google News API to fetch news articles
    authenticate(api_credentials)
    # Search for news articles
    articles = news_search(search_term)
    return articles

# Pseudocode for text processing
function clean_text(text):
    # Step 1: Convert all text to lowercase
    text = lowercase(text)
    
    # Step 2: Tokenize text into words (tokens)
    tokens = tokenize(text)  # Separate text into individual words
    
    # Step 3: Remove stopwords (common words like "the", "and")
    filtered_tokens = remove_stopwords(tokens)
    
    # Step 4: Stemming or Lemmatization (reduce words to their base form)
    base_form_tokens = stem_or_lemmatize(filtered_tokens)
    
    return base_form_tokens


# Pseudocode for sentiment scoring
function get_sentiment_score(text):
    # Use TextBlob for sentiment scoring
    sentiment_object = TextBlob(text)
    
    # Get the sentiment score (polarity ranges from -1 to 1)
    polarity_score = sentiment_object.sentiment.polarity
    
    return polarity_score


# Pseudocode for main function that combines all the processes.
function main():
    # Step 1: Get data from Twitter and Google News
    twitter_data = get_twitter_data(api_credentials, "stock market")
    news_data = get_news_data(api_credentials, "stock market")
    
    # Step 2: Clean and process the text data
    processed_twitter_data = []
    for tweet in twitter_data:
        cleaned_tweet = clean_text(tweet)
        processed_twitter_data.append(cleaned_tweet)
        
    processed_news_data = []
    for article in news_data:
        cleaned_article = clean_text(article)
        processed_news_data.append(cleaned_article)
    
    # Step 3: Get sentiment score for each piece of processed text
    sentiment_scores = []
    for text in processed_twitter_data:
        score = get_sentiment_score(text)
        sentiment_scores.append(score)
        
    # (Repeat for news_data)
    
    # Step 4: Use sentiment scores in your RL agent or other applications
    
    return sentiment_scores


Next for Implementation:
Use the following of the REST API connected to Yahoo finance data to add to the algorithm:
Simple Moving Average
Eponential Moving Average
Relative Strength Index