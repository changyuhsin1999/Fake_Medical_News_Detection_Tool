# Fake Medical News Detection Tool
![Screenshot](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/image/Vitamin-D-in-moderation-protects-against-respiratory-infections-Meta-analysis.jpeg)

As we live in this era with exploding information content, it is always difficult to distinguish whether the information is real or fake. It can be a lot difficult when it comes to medical contents which often include lots of professional terms and acronyms. In this project, I combined two different existing dataset with a mix of real and fake medical journal and news, pass it through TFIDF word vectorizer and feed into trained model for binary classification.

The purpose of this module is to let people copy and paste the medical news that they found and do a quick fact check to see whether it is reliable to trust the sources.

## Data processing
1. [Kaggle - COVID Real News](https://www.kaggle.com/datasets/arashnic/covid19-fake-news?select=NewsRealCOVID-19_7.csv) for real news
2. [A comprehensive data repository for fake health news - dataset/content/HealthRelease](https://github.com/EnyanDai/FakeHealth/tree/master/dataset/content/HealthRelease) for fake news


I combined both datasets and shuffle them, get rid of null values and unneccesary columns to get raw_df.csv in the data folder

## Model and Vectorizer
I decided to use TFIDF as my vectorizer and compare them using non-neural network model as baseline model and use Long Short Term Memory(LSTM) for deep learning model
| Model         | Accuracy      |
| ------------- |:-------------:|
| Passive Aggressive Classifier      | 99.5 %        |
| Logistic Regression         | 99.5 %        |
| LSTM       | 98.6 %        |



## Metric Evaluation
The final model that I chose is the passive aggresive classifier with TFIDF as vectorizer. The training time was a lot faster and the performance was more robust. The overall metric performance for the final model is shown as below:

![Screenshot](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/image/Screen%20Shot%202023-07-16%20at%2012.23.04%20PM.png)

## Visual Interface
I decided to use Flask/html to display the passage prediction. Users can copy the news that they've found on internet and paste it in the empty text box or press the "generate" button to generate text from my dataset.

![Screenshot](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/image/Screen%20Shot%202023-07-20%20at%202.25.39%20PM.png)

## How to get started
### Prepare your environment

```
conda create --name envir python=3.7.15
conda activate envir
```
### Install requirement.txt

```
pip install -r requirements.txt
```
### Train the model
Run the [PA_Train.py](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/scripts/PA_Train.py) and [LSTM_Train.py](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/scripts/LSTM_Train.py) python script to train and evaluate your model

### Run the website
Run [web.py](https://github.com/changyuhsin1999/Fake_Medical_News_Detection_Tool/blob/main/web.py) python script to see the demo

## Reference
[Flask tutorial](https://towardsdatascience.com/how-to-build-a-fake-news-detection-web-app-using-flask-c0cfd1d9c2d4)

[Dropout method in Tensorflow](https://saturncloud.io/blog/how-to-implement-dropout-in-lstm-neural-networks-with-tensorflow/)

[Comparison between BERT and LSTM](https://arxiv.org/abs/2009.05451)

[HTML templates](https://colorlib.com/wp/templates/)

[Passive Aggressive Classifier for text classification](https://www.geeksforgeeks.org/passive-aggressive-classifiers/)
