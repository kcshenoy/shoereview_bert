# shoereview_bert
Unsupervised Sentiment Analysis using bert-base-multilingual-uncased-sentiment, to help me decide which basketball shoe I should buy next out of the specified options.

## Process:
### Data Collection:
I decided to turn to Reddit to collect post text and comments, as these tend to be very raw and unfiltered. There is a popular subreddit called BBallShoes which I thought would be perfect to scrape. I found many "report card/performance review" posts, many from one user with the same format which helped with consistency. I tried my best to use posts that seemed neutral or gave a review and opened more discussion, in order to open the possibility for an equal number of positive and negative sentiment reviews.

I had to add a time sleep while scraping to adhere to Reddit's scraping policy :/, that was annoying.

For the initial scraped data, I thought that the upvotes and downvotes were not good sources of data as there are many reasons to do either. The volatility of those reasons is why I left those out, and only included the shoe name, the post text if it had any, and the link/source.

### Models:
bert-base-multilingual-uncased-sentiment, which uses the BERT (pre-trained) uncased model to assign 1-5 star values to text.
I also used the pipeline feature from the transformers library to apply the model to the data, simply by inputting the model and the tokenizer.

### Final Data:
At the end, I had the original 3 columns (text, link, shoe) along with the predicted star rating of each text chunk. Some had to be truncated as BERT base only allows 512 tokens. Truncating is the easy method, but splitting into chunks and reorganizing, averaging out the ratings based on the length of each text could have proven to be more accurate. There are many other methods but truncating was the easiest and quickest.

### Outcomes:
Feel free to check the notebook for details, but I wanted to see which shoes had the best ratio between positive (4-5 stars) and negative (1-2 stars) ratings. That was my main concern. After this, I wanted to analyze the highest-rated comments to sift out comments that I thought wouldn't suit my purpose. Overall, there are a lot more ways I could have analyzed the data, but I came into this project with some internal bias. Again, I comment through all my code in the ipynb, so feel free to read through it and see my thoughts at the bottom!

