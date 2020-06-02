*Note: This document is still on-going! Last update --2020/06/02*
## Classification of user utterance and sentiment in daily conversation

### Project description

Primary research tool in psychology and psychiatry researches are quantitative methods like questionnaires.
Still, qualitative research is essential when studying psychological or psychiatric features. 
Unfortunately, qualitative research requires great amount of time and resources in its process and analysis. 
Especially in counseling, although initial criteria is set according to first visit questionnaire, 
qualitative analysis based on counseling results holds the most critical portion.

As the advance of NLP technology, multi-sentiment analysis from daily dialog became possible. 
In addition, speaker's utterance classification is also available.
Considering such previous results, it would be possible to automatically detect speaker's intention and emotion
underlying the daily log and present the results to its stakeholders.

### Project goal

Classification of speech intent and sentiment of dialog

### Project process
```
Data collection - Data preprocessing - Model Building - Model testing (- Extend using semi-supervised learning)
```
Primary goal of the project is to finish up to  model testing.<br>
After that, semi-supervised learning methods will be applied to extend dataset.<br>

### Data Collection

#### Data source
- AI Hub(Open data platform) <http://www.aihub.or.kr/keti_data_board/language_intelligence> <br>
- Intonation-aided intention identification for Korean <https://github.com/warnikchow/3i4k> <br>

#### Data description

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

### Data Preprocessing

### Model Building

## Model Testing

When evaluating final model, critical criteria will be **Accuracy** and,**F1-score**.<br>

