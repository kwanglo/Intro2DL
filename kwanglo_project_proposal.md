*Note: This document is still on-going! Last update --2020/04/08 18:30*

# Project Objective

Classifying the underlying intent and sentiment of daily dialog(and provide appropriate response).

##### Short Summary of previous proposal

Previously, "Detecting/Classifying psychiatric features in daily dialog settings" was set as the project goal.
However, when reviewing the data contents, the labeled(taget) data was consist of too many classes with small data volume. 
As a result, the project goal shifted a little with similar topic related with automation in counselling.

## Project Description

Primary research tool in psychology and psychiatry researches are quantitative methods like questionnaires.
Still, qualitative research is essential when studying psychological or psychiatric features. 
Unfortunately, qualitative research requires great amount of time and resources in its process and analysis. 
Especially in counseling, although initial criteria is set according to first visit questionnaire, 
qualitative analysis based on counseling results holds the most critical portion.

As the advance of NLP technology, multi-sentiment analysis from daily dialog became possible. 
In addition, speaker's intention classification is also available.
Considering such previous results, it would be possible to automatically detect speaker's intention and emotion
underlying the daily log and present the results to its stakeholders.

## Project Goals

Main goal: Classification of speech intent and sentiment of dialog(input)

Sub goal: Generation of following response dialog(output) / Extend to psychiatric context dialogs

## Project Process
```
Data collection - Data preprocessing - Model Building - Model testing (- Build response model - Extend model)
```
Primary goal of the project is to finish up to  model testing. 

## Data Collection

### Data source
- AI Hub(Open data platform) <http://www.aihub.or.kr/keti_data_board/language_intelligence> <br>
- Intonation-aided intention identification for Korean <https://github.com/warnikchow/3i4k> <br>

### Data description

Datasets are classified into 3 categories.
1) Dataset for training/testing intent classification model
2) Dataset for training/testing sentiment classification model
3) Dataset for possible extention of dataset

##### 1) 3i5K - Intonation-aided intention identification for Korean
```
Korean title: 한국어 의도파악 데이터셋
Description: 61,255 words & sentences with intent labels
```
##### 2) Korean emotion-labeled singular dialog dataset
```
Korean title: 한국어감정정보 단발성 대화셋 
Description: Consist of dialog sentence and emotion label of the sentence - 38,594 dialog
```
This dataset will be used for building 

##### 3-1) Twitter based daily divalog
```
Korean title: 트위터 기반 일상대화/대화형 한글 에이전트
Description: Twitter based daily dialog - 2,000 continuous dialog(Tweets)
```

##### 3-2) Wellness dialog script dataset
```
Korean title: 웰니스 대화 스크립트 데이터셋
Description: Labeled dialog about psychiatric topics
5,232 User dialog with 1,023 chatbot response about 359 different mental health counseling topics
```
This data 

## Data Preprocessing

Initial dataset for model training has similar data size(VRM: about 100,000 / Korean dialog: about 95,000).<br>


Data will go through ordinal NLP preprocessing procedures such as regular expression handling, tokenization, stopwords removal, stemming and etc. Specific preprocessing procedure will be updated afterwards.

## Model Building

Possible machine learning techniques for basic comparisons are: **Naive Bayes**, **Logistic regression**, **SVM**<br>
This three models are widely adapted in various classification and also used in simple NLP classifications like Ham/Spam filters.<br>
In addition, classification methods like **Decision Tree** and, **Random Forest** can be also implemented.<br>
<br>
Initial datasets used in model building are 'VRM dialog' and 'Korean emotion-labeled singular dialog'.<br>
Each dataset will be used in building different(intend/sentiment) models.<br>

## Model Testing

When evaluating final model, critical criteria will be **Accuracy** and,**F1-score**.<br>
Since the goal of current classification model is multi-labeled, it is important to choose a balanced metric.<br>
There may be changes in chosen metrics according to unknown details of each speech intents.<br>
<br>
In addition, learning steps and time will be also measured regarding maximum daily running limit of Google colab.<br>
Any model that requires more then 12hrs in learning will be depreciated.<br>

