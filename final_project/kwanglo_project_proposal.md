*Note: This document is still on-going! Last update --2020/04/08 22:30*

# Project Objective

Classifying the underlying intent and sentiment of daily dialog.

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

Main goal: Classification of speech intent and sentiment of dialog
Sub goal: Extend data labels using semi-supervised learning

## Project Process
```
Data collection - Data preprocessing - Model Building - Model testing (- Extend using semi-supervised learning)
```
Primary goal of the project is to finish up to  model testing.<br>
After that, semi-supervised learning methods will be applied to extend dataset.<br>

## Data Collection

### Data source
- AI Hub(Open data platform) <http://www.aihub.or.kr/keti_data_board/language_intelligence> <br>
- Intonation-aided intention identification for Korean <https://github.com/warnikchow/3i4k> <br>

### Data description

Datasets are classified into 3 categories.
1) Dataset for training/testing intent classification model
2) Dataset for training/testing sentiment classification model
3) Dataset for possible extention of dataset

##### 1) 3i4K - Intonation-aided intention identification for Korean
```
Korean title: 한국어 의도파악 데이터셋
Description: 61,255 words & sentences with intent labels
```
Data consist of 2 columns.
- Intent label
- Word/Sentence

Intent labels are consist of 7 different labels: <br>
Fragments(FR) - 6009 / Statements(S) - 18300 / Questions(Q) - 17869 / Commands(C) - 12968 /<br> 
Rhetorical questions(RQ) - 1745 / Rhetorical commands(RC) - 1087 / Intonation-dependent utterances(IU) - 3277<br>
<br>
Numbers after "-" are number of sentences labeled as each class. <br>
Since there are imbalance between each classes, some classes might show low accuracy at the results. <br>
Dropping such classes or finding alternative ways to boost the dataset will be used to enhance overall performance.

##### 2) Korean emotion-labeled singular dialog dataset
```
Korean title: 한국어감정정보 단발성 대화셋 
Description: Consist of dialog sentence and emotion label of the sentence - 38,594 dialog
```
Data consist of 2 columns.
- Sentence
- Emotion Label

Emotion label consist 7 different classes: 중립(4830), 공포(5468), 놀람(5665), 분노(5665), 슬픔(5267), 행복(6037), 혐오(5429)<br>
Number in "()" are number of sentences labeled as each class. Data seems to be balanced.

##### 3-1) Twitter based daily divalog
```
Korean title: 트위터 기반 일상대화/대화형 한글 에이전트
Description: Twitter based daily dialog - 2,000 continuous dialog(Tweets)
```
Data consist of multiple columns which each columns represent a single tweet and each row represents one multi-sentence dialog.<br>

##### 3-2) Wellness dialog script dataset
```
Korean title: 웰니스 대화 스크립트 데이터셋
Description: Labeled dialog about psychiatric topics
5,232 User dialog with 1,023 chatbot response about 359 different mental health counseling topics
```
Data consist of 3 columns.
- Mental Disorder Classification Label
- User Input
- Chatbot Response

## Data Preprocessing
Both datasets for initial model building(data1, 2) only have 2 columns with text and labels.<br>
Thus, basic preprocessing procedure before using embedding models will be:
- Null-value check/handling
- Regularizing / Tokenizing&Stemming / Removing stop-words(Using existing libraries like KoNLPy, SoyNLP, etc)
<br>
Since initial goal of the project is to classify intent and sentiment of given sentence, we do not need multi-sentence classification and response label. As for data 3-1, seperating each column into indiviudal row is required since we are not interested in multi-sentence dialoge issue. As for data 3-2, dropping chatbot response and classification label are required for future use.

## Model Building

Initial datasets used in model building are '3i4k intent set' and 'Korean emotion-labeled singular dialog'.<br>
Each dataset will be used in building different(intend/sentiment) models.<br>
<br>
Various embedding models will be tested in advance to enhance the performance of the models.<br>
Both word embedding and sentence embedding methods will be tested. Considered embedding methods for the projects are:<br>
Word Embedding: Word2Vec, FastText, Glove, Swivel<br>
Sentence Embedding: ELMo, KorBERT(Korean-ver BERT provided by ETRI)<br>
<br>
Possible machine learning techniques for basic comparisons are: **Naive Bayes**, **Logistic regression**, **SVM**<br>
This three models are widely adapted in various classification and also used in simple NLP classifications like Ham/Spam filters.<br>
In addition, classification methods like **Decision Tree** and, **Random Forest** can be also implemented.<br>
<br>
Initial deep learning algorithms that will be tested are **CNN**, **RNN(Bi-LSTM)**.<br>
Since there are many pre-trained models using RNN, varous models using concepts like **Seq2Seq**, **Attention**, **Transformer** will be implemented.<br>
<br>
In semi-supervised learning part, various methods from previous researches like **self-training**, **multi-view learning**, **self-ensembling** will be adapted.

## Model Testing

When evaluating final model, critical criteria will be **Accuracy** and,**F1-score**.<br>
<br>
For primary goal(classification of sentiment and intent), accuracy and F1-score will be measure for each class.<br>
Since we are building two seperated model for classification and intent, initial evaluation will be conducted seperately.<br>
After validating two models, cross-classification of each dataset(1,2) will be done using the other classification model.<br>
<br>
In extension phase, semi-supervised learning methods will be applied to label dataset 3-1 and 3-2.<br>
In this phase, 3 different confusion matrix(only intent, only sentiment and both) will be compared to test accuracy and F1-score.
<br>
In addition, learning steps and time will be also measured regarding maximum daily running limit of Google colab.<br>
Any model that requires more then 12hrs in learning will be depreciated.<br>

