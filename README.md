# Fake-news-detection-project-
import numpy as np
import pandas as pd
import re
from nltk.corpus import stopwords
from nltk.stem.porter import PorterStemmer
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

import nltk
nltk.download('stopwords')

# printing the stopwords in English
print(stopwords.words('english'))


# loading the dataset to a pandas DataFrame
news_dataset = pd.read_csv('/content/train.csv.zip')

news_dataset.shape


# print the first 5 rows of the dataframe
news_dataset.head()


# counting the number of missing values in the dataset
news_dataset.isnull().sum()



# replacing the null values with empty string
news_dataset = news_dataset.fillna('')



# merging the author name and news title
news_dataset['content'] = news_dataset['author']+' '+news_dataset['title']


print(news_dataset['content'])


# separating the data & label
X = news_dataset.drop(columns='label', axis=1)
Y = news_dataset['label']

print(X)
print(Y)


port_stem = PorterStemmer()


news_dataset['content'] = news_dataset['content'].apply(stemming)

print(news_dataset['content'])


#separating the data and label
X = news_dataset['content'].values
Y = news_dataset['label'].values




