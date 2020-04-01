*This document is depreciated. New proposal is being prepared.*<br>
*Note: This document is still on-going! Last update --2020/03/30 18:30*

# Project Objective

Detecting/Classifying psychiatric features in daily dialog settings

## Project Description

Primary research tool in psychology and psychiatry researches are quantitative methods like questionnaires.
Still, qualitative research is essential when studying psychological or psychiatric features. Unfortunately, qualitative research requires great amount of time and resources in its process and analysis. Especially in counseling, although initial criteria is set according to first visit questionnaire, qualitative analysis based on counseling results holds the most critical portion.

As the advance of NLP technology, multi-sentiment analysis from daily dialog became possible. If so, what if we can derive psychiatric features from user's dialog to detect changes without researcher's hands-on labeling? 

## Project Goals

Main goal: Build psychiatric feature classification model

Sub goal: Expand dataset using external sources and validate with current model

## Project Process
```
Data collection - Data preprocessing - Model Building - Model testing (- Expand dataset - Validate dataset)
```
Primary goal of the project is to finish up to  model testing. 

## Data Collecting

Data set is from AI Hub(Open data platform) <http://www.aihub.or.kr/keti_data_board/language_intelligence>.<br>
To be specific, data from "recognition-language intelligence" section is considered as promising candidate for the project.<br>
<br>
Among various datasets, below dataset were seemed to fit the project objective.<br>
```
"웰니스 대화 스크립트 데이터셋", "한국어 대화 데이터셋", "트위터 기반 일상 대화 데이터셋", "대화형 한글 에이전트 데이터셋", "한국어 감정정보 연속/단발 대화 데이터셋", "인공지능 윤리 연구를 위한 비정형 텍스트 데이터셋"
```
Specific descriptions and potential use in current project is as following.

##### Wellness dialog script dataset
```
Korean title: 웰니스 대화 스크립트 데이터셋
Description: Labeled dialog about psychiatric topics
5,232 User dialog with 1,023 chatbot response about 359 different mental health counseling topics
```
##### Korean dialog / Twitter based daily dialog / Conversational Korean agent dataset
```
Korean title: 한국어대화/트위터 기반 일상대화/대화형 한글 에이전트
Description: 3 different datasets about daily dataset 
3 datasets are composed of daily dialogs.
1) Korean dialog - 748 continuous dialog(4,975 singular dialog)
2) Twitter based daily dialog - 2,000 continuous dialog(Tweets)
3) Conversational Korean agent dataset - 8,000 continuous dialog // From drama&scenario scripts
```
##### Korean emotion-labeled continuous/singular dialog dataset
```
Korean title: 한국어감정정보 연속/단발성 대화셋 
Description: Consist of dialog sentence and emotion label of the sentence
Continuous dialog set - 10,000 dialog(55,627 singular dialog)
Singular dialog set - 38,594 dialog
```
##### Unstructured text dataset for AI ethics study
```
Korean title: 인공지능 윤리연구를위한 비정형 텍스트 데이터셋
Description: Corpus about ethical/unethical contents collected via online 
1) Online News 70 million comments / Twitter 30 million tweets
2) Online community 45 million comments(Labeled unethical)
3) Online community 20 million comments(Labeled unethical)
```

## Data Preprocessing

The target/labeled data for the project contains 5,232 sentences with 359 topics.<br>
Still, ordinary dialog set contains 109,196 dialog even without the last 165 million comments dataset.<br>
Thus, target data is about 4.8% of ordinary dialog set, meaning great imbalance in data. <br>
<br>
To solve this problem, related reference was selected for citation.<br>
Title : "Dealing with “rare” events in Machine Learning" by Deepa Mahidhara, May 2, 2019<br>
<a> https://medium.com/@dmahidhara/dealing-with-rare-events-in-machine-learning-14c2c167e222 <br>
In above, reference, ROC AUC score was used instead of accuracy to minimize FP. In addition, boosting(Gradient boosting) and oversampling(SMOTE, Synthetic Minority Over-Sampling Technique) were used to fix imbalance issue. Similar techniques will be considered in future progress after more detailed research.
<br>

## Model Building

Possible machine learning techniques for basic comparisons are: **Naive Bayes**, **Logistic regression**, **SVM**<br>
This three models are widely adapted in various classification and also used in simple NLP classifications like Ham/Spam filters.<br>

## Model testing

Test metrics for the project are **F-measure** and **ROC AUC score** from the classification results according to the reference.
