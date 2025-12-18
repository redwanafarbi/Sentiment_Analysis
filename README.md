# Sentiment_Analysis

1. Overview:
    This project implements a Twitter sentiment analysis system using the Kaggle Twitter Entity Sentiment Analysis dataset.
    The goal is to classify tweets into Negative, Neutral, or Positive sentiment while incorporating entity-aware context (e.g., brand or topic mentioned in the tweet).

    Two approaches are compared:
        a. Baseline machine learning model using TF-IDF + Logistic Regression
        b. Deep learning model using fine-tuned BERT (TensorFlow)

2. Dataset
    Source: Kaggle – Twitter Entity Sentiment Analysis
    Files used:
        i. twitter_training.csv
        ii. twitter_validation.csv
    
    Each data sample contains:
        i. Tweet_ID
        ii. Entity (topic/brand/person)
        iii. Sentiment (Positive, Negative, Neutral, Irrelevant)
        iv. Tweet (raw tweet text)

3. Baseline Model: TF-IDF + Logistic Regression
    The baseline model converts text into numerical features using TF-IDF, emphasizing informative and rare words while down-weighting common ones.

    First, the tweet text is converted into numerical features using TF-IDF (Term Frequency–Inverse Document Frequency).
    
    TF-IDF gives higher importance to words that are frequent in a specific tweet but rare across the entire dataset, while reducing the weight of very common words such as “the”, “is”, “and”. Bi-grams are used so that short phrases (for example, “very bad” or “not good”) can also be captured.
    
    These TF-IDF features are then fed into a Logistic Regression classifier, which learns to separate tweets into Negative, Neutral, or Positive sentiment based on the learned word patterns.

4. Deep Learning Model: BERT
    To capture contextual meaning, I fine-tuned BERT (bert-base-uncased) using TensorFlow.
    Key features:
        i. Entity-aware input format:  [ENTITY] Apple [TWEET] This phone is amazing
        ii. Captures semantic relationships and context
        iii. Handles mixed and subtle sentiment more effectively

5. Project Workflow
    i. Load dataset from Google Drive (Colab environment)
    ii. Clean tweet text (URLs, mentions, hashtags, extra spaces)
    iii. Encode sentiment labels
    iv. Create entity-aware input text
    v. Train baseline TF-IDF + Logistic Regression model
    vi. Fine-tune BERT for multi-class sentiment classification
    vii. Evaluate models using:
            a. Accuracy
            b. Precision, Recall, F1-score (macro)
            c. Confusion Matrix
    
    viii. Save trained models to Google Drive
    ix. Perform inference on unseen tweets