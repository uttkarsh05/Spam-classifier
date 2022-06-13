# Spam-classifier
Contents:
    1.1 Datasets , 
    1.2 Preprocessing the Data , 
    1.3 Features Extraction , 
    1.4 Classification Model , 
    1.5 Training and testing the model , 
    1.6 Performance Metrics , 
    1.7 Hyperparameter Tuning , 
    1.8 Predictions and Observations . 

**1.1 Datasets:**
    The Dataset used is from Kaggle and has 5572 emails from same user containing 13% mails as spam


**1.2 Preprocessing the Data:**
    In the first step, the model removes punctuation marks, hyperlinks, and numbers
    from the text emails as these are useful in classifying the data and can also
    hamper the model performance.
    In the second step, the model removes stop words like(the ,is ,a ,an..etc) and
    also removes the gibberish words if present in the emails


**1.3 Features Extraction :**
    The main part of spam classification is to understand and quantify the features
    which will be helpful in classifying the emails.
    Features used in the model are:

    – Bag of words: It contains every word present in an email after preprocessing.
    This feature helps in vectorizing the string datasets into a numerical datasets

    – Ratio of unique words: It is a ratio of the no of unique words in an email to the
    total no of words in that email

    – Ratio of stop words: It is a ratio of the no of stop words in an email to the total
    no of words in that email. This feature is used so that if any useful info was lost
    while removing stop words in preprocessing can be used.

    –Ratio of non-dictionary words: It is a ratio of the no of gibberish words in an
    email to the total no of words in that email. Its useful to classify mails as many
    spam emails tends to have various gibberish contents and this feature will be
    able to catch those indicators for the mail to be spam.

**1.4 Classification Model:**
    The Binary Classifier used is SVM with the linear kernel as most of the data
    matrix has zeros and ones the decision trees would not be a good classifier for
    this problem and by using naive Bayes the extra features like the ratio of
    unique_words can’t be used.
    So the model uses SVM with hyperparameter C, which represents the soft
    margin that we allow for the misclassification penalty.

**1.5 Training and testing the model**
    The datasets are split into 2 datasets, training and test datasets, to understand
    the performance of the model.
    After fitting the model the values of w are stored in the classifier variable and are
    used to classify the emails in test datasets.

**1.6 Performance Metrics :**
    There are various metrics that can be used to judge a model's performance:
    – Accuracy
    – Precision
    – Recall
    – F1 score
    *1.6.1 Accuracy:*
        It is a measure of how must percentage of predictions are actually correct.

    *1.6.2 Precision:*
        It represents what proportion of positive/negative classification was actually
        correct.

    *1.6.3 Recall:*
        It represents what proportion of actual positive/negative classification was
        identified correctly.

    *1.6.4 F1 score:*
        To fully evaluate the effectiveness of a model, we must examine both
        precision and recall. But precision and recall are often in tension. That is,
        improving precision typically reduces recall and vice versa. So we derive a
        metric which is the harmonic mean of precision and recall.

    So the best metric to judge the model is the weighted average of the F1 score for
    both spam classification and ham classification.

1.7 **Hyperparameter Tuning (c):**
    For finding the best hyperparameter C, we will use 5-fold cross-validation with
    the performance metric to be an F1 score with a weighted average for every C
    and compare them to get best C .

1.8 **Predictions and Observations:**
    Now using this C we use our classifier variable to predict emails in test datasets.
    
    **1.8.1 Classification report:**
    As it can be seen the f1 score for spam classification is lesser than that for ham
    classification. If a model predicts every mail as ham then that model can have
    87% accuracy from our datasets but the f1 score avg would be around 0.5 which
    is the defining factor now to judge a model performance

    **1.8.2 Confusion Matrix:**
    -This matrix shows the true label of a mail vs the predicted label of the mail
    from the classifier.
    -Here we can see most of the mails are classified correctly as evident by 96%
    accuracy
    -False positives are less than False negatives is an important aspect to look
    at. False positives mean that the mail which was ham has been classified as
    spam, which can lead to some tough situations and we generally want to reduce
    this no as much as possible.
    -Whereas False negatives which mean spam mail has been classified as ham,
    are an easier situation to handle if the false negatives are low in number as well.
