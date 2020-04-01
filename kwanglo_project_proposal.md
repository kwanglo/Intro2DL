*Note: This document is still on-going! Last update --2020/04/01 13:30*

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

Data set is from AI Hub(Open data platform) <http://www.aihub.or.kr/keti_data_board/language_intelligence>.<br>
To be specific, data from "recognition-language intelligence" section is considered as promising candidate for the project.<br>
<br>
Among various datasets, below dataset were seemed to fit the project objective.<br>
```
"웰니스 대화 스크립트 데이터셋", "한국어 대화 데이터셋", "트위터 기반 일상 대화 데이터셋", "대화형 한글 에이전트 데이터셋", "한국어 감정정보 연속/단발 대화 데이터셋", "VRM 화행 ","인공지능 윤리 연구를 위한 비정형 텍스트 데이터셋"
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
##### VRM(Verbal Response Mode) Dialog dataset
```
Korean title: VRM 화행 데이터
Description: Classified into 8 different intent of dialog.
100,000 singular dialog with VRM labels. 
```
##### Korean emotion-labeled continuous/singular dialog dataset
```
Korean title: 한국어감정정보 연속/단발성 대화셋 
Description: Consist of dialog sentence and emotion label of the sentence
Continuous dialog set - 10,000 dialog(55,627 singular dialog)
Singular dialog set - 38,594 dialog
```
Specific classification criteria of intent is as in below table.
|경험의 원천	|경험에 대한 추정|인용프레임 (타인)|인용프레임 (화자)|
|------|---|---|---|
|타인|타인|Reflection(R)|Interpretation(I)|
|타인|화자|Acknowledgment(K)|Question(Q)|
|화자|타인|Confirmation(C)|Advisement(A)|
|화자|화자|Education(E)|Disclosure(D)|

## Data Preprocessing

Initial dataset for model training has similar data size(VRM: about 100,000 / Korean dialog: about 95,000).<br>


Data will go through ordinal NLP preprocessing procedures such as regular expression handling, tokenization, stopwords removal, stemming and etc. Specific preprocessing procedure will be updated afterwards.

## Model Building

Possible machine learning techniques for basic comparisons are: **Naive Bayes**, **Logistic regression**, **SVM**<br>
This three models are widely adapted in various classification and also used in simple NLP classifications like Ham/Spam filters.<br>

Initial datasets used in model building are 'VRM dialog' and 'Korean emotion-labeled continuous/singular dialog'.<br>
Each dataset will be used in building different(intend/sentiment) models.<br>

## Model Testing

