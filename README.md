# Sentiment-Analysis
# install textblob
pip install pandas textblob

import pandas as pd
from textblob import TextBlob

# Sample data (replace this with your own dataset of tweets or reviews)
data = {
    "text": [
        "I love this product! It's amazing.",
        "Worst experience ever. Totally disappointed.",
        "It's okay, not great but not bad either.",
        "I am so happy with the service!",
        "Terrible customer support, never coming back."
    ]
}

# Create DataFrame
df = pd.DataFrame(data)

# Function to compute sentiment polarity and label
def analyze_sentiment(text):
    analysis = TextBlob(text)
    polarity = analysis.sentiment.polarity

    if polarity > 0:
        sentiment = "Positive"
    elif polarity < 0:
        sentiment = "Negative"
    else:
        sentiment = "Neutral"

    return pd.Series([polarity, sentiment])

# Apply sentiment analysis
df[['Polarity', 'Sentiment']] = df['text'].apply(analyze_sentiment)

# Display results
print(df)

# Output
                                               text  Polarity Sentiment
0     I love this product! It's amazing.           0.612     Positive
1  Worst experience ever. Totally disappointed.    -1.000     Negative
2  It's okay, not great but not bad either.        0.05      Positive
3        I am so happy with the service!           0.8       Positive
4  Terrible customer support, never coming back.   -1.000     Negative


