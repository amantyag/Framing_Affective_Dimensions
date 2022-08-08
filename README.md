# Framing_Affective_Dimensions

## Appendix 1

Definition of framing dimensions from Boydstun, A.E., Card, D., Gross, J., Resnick, P., A. Smith, N.,
Tracking the development of media frames within and across policy issues (Jun 2018):

Economic: costs, benefits, or other financial implications
Capacity and resources: availability of physical, human
or financial resources, and capacity of current systems
Morality: religious or ethical implications
Fairness and equality: balance or distribution of rights,
responsibilities, and resources
Legality, constitutionality and jurisprudence: rights,
freedoms, and authority of individuals, corporations, and
government
Policy prescription and evaluation: discussion of specific
policies aimed at addressing problems
Crime and punishment: effectiveness and implications of
laws and their enforcement
Security and defense: threats to welfare of the individual,
community, or nation
Health and safety: health care, sanitation, public safety
Quality of life: threats and opportunities for the individual’s wealth, happiness, and well-being
Cultural identity: traditions, customs, or values of a social
group in relation to a policy issue
Public opinion: attitudes and opinions of the general public, including polling and demographics
Political: considerations related to politics and politicians,
including lobbying, elections, and attempts to sway voters
External regulation and reputation: international reputation or foreign policy of the U.S.
Other: any coherent group of frames not covered by the
above categories



Total number of common words in each frame lexicon f and EPA lexicon l. 
| Frame                                      | Total                                                        |
|--------------------------------------------|--------------------------------------------------------------|
| Capacity and Resources                     | 1210                                                         |
| Crime and Punishment                       | 1756                                                         |
| Cultural Identity                          | 1756                                                         |
| Economic                                   | 1690                                                         |
| External Regulation and Reputation         | 1312                                                         |
| Fairness and Equality                      | 1590                                                         |
| Health and Safety                          | 1712                                                         |
| Legality, Constitutionality,~ Jurisdiction | 1779                                                         |
| Morality                                   | 1631                                                         |
| Policy Prescription and Evaluation         | 1747                                                         |
| Political                                  | 1768                                                         |
| Public Sentiment                           | 1685                                                         |
| Quality of Life                            | 1720                                                         |
| Security and Defense                       | 1519                                                         |



### Data Collection Details
We collected Tweets using Twitter's standard API (https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/overview) using keywords "Climate Change", "\#ActOnClimate", "\#ClimateChange". The below table reports statistics of the dataset. We then classify each user into a news agency account and a non-news agency account using the method described in the paper. For each Tweet from a news agency account, we scrape the news article using the URL shared in that Tweet. To scrape the news articles, we built our software system, which uses python requests library to scrape the articles from the websites. We subscribed to news agencies mentioned in Pew Research's top online news media websites report (https://www.pewresearch.org/wp-content/uploads/sites/8/legacy/NIELSEN-STUDY-Copy.pdf) as these websites generally required login credentials. Extensive testing was done to ensure that we could collect as many articles as possible and circumvent possible obstacles such as AJAX calls and advertisements. Using the URLs we were able to collect 900k articles. However, some of these articles were non-text files or contained short error messages. We removed these files from our dataset. After this step, we were left with 810k news articles. In the table below we report statistics of news articles used in our dataset. We further cleaned each article for any HTML tags, other non-header, or non-body text for our analysis.

### Bert Model Details
For predicting frames at the sentence level, we use the pretrained Bert-Large-Uncased model. The model was trained on BookCorpus (https://yknzhu.wixsite.com/mbweb) and English Wikipedia after removing headers, tables, and lists. In this work, we predict frames for news articles, assuming that the formal language used in books and Wikipedia generally reflects the language used in news articles. To get embedding of a sentence we concatenate the last 4 layers of the BERT model. This embedding was then passed to a MLP/1D-CNN classifier as described in the paper.

Statistics of the Tweets and news articles collected.

|              | Tweets                              | Articles                               |
|--------------|-------------------------------------|----------------------------------------|
| Total Number | 38M                                 |  ~810k                                 |
| Mean per day | 48,860.5                            | 1,157.5                                |
| Min per day  | 2                                   | 0                                      |
| Max per day  | 243,574                             | 6,513                                  |


## Appendix 2



In this section, first, we will give some examples from our news articles dataset. Second, we use these examples to explain the frames and their projection in EPA space. Lastly, we discuss the methodology and results of our manual evaluation of 100 randomly selected news articles.

Snippets of news articles in our dataset:

Snippet (a):
"STUDY REVEALS HOW CLIMATE CHANGE COULD CAUSE GLOBAL BEER SHORTAGES
Severe climate events could cause shortages in the global beer supply, according to new research involving the University of East Anglia (UEA).
The study warns that increasingly widespread and severe drought and heat may cause substantial decreases in barley yields worldwide, affecting the supply used to make beer, and ultimately resulting in dramatic falls in beer consumption and rises in beer prices."

Snippet (b):
"Baltimore Is Suing Big Oil Over Climate Change
The Supreme Court heard arguments this week in a case brought by the city of Baltimore against more than a dozen major oil and gas companies including BP, ExxonMobil and Shell. The city government argued that the fossil fuel giants must pay for the costs of climate change because they knew that their products cause potentially catastrophic global warming".

Snippet (c):
Small islands use big platform to warn of climate change
"On the map, their homes are tiny specks in a vast sea of blue, rarely in the headlines and far removed from the centers of power. But for a few days each year, the leaders of small island nations share a podium with presidents and prime ministers from the world’s most powerful nations, and their message is clear: Global warming is already changing our lives, and it will change yours too. Speaking shortly after U.S. President Donald Trump — whose fiery speech made no mention of climate change — Danny Faure told the U.N. General Assembly this week that for his country, the Seychelles, it’s already a daily reality".

The snippets from the dataset show different frames used in climate change news articles. The topic discussed in these snippets is different; moreover, these snippets are addressed towards geographically different audiences. Snippet (a) addresses the change in a decrease in yield for barley due to climate change referencing a research study. This whole news article predominantly uses Cultural Identity frame. Similarly, the article in snippet (b) uses more economic and Legality, constitutionality and jurisprudence frame. The article from which Snippet (c) was taken is predominantly using Quality of life, Capacity and Resources and Morality frames. Our algorithm, discussed in the paper, predicts that the article of snippet (c) is high in emotional value or affect followed by the article of snippet (b) and then by the article of snippet (a). This order can also be followed by looking at the predominant frames of these articles.


In order to find out the general stories reported in news articles, we manually verify stories of a sample of 100 news articles from our dataset. Moreover, we also find that if the news article is from a popular news agency or not. We mark the source as popular if its name is mentioned in Pew Research's top online news media websites report. 

Two annotators independently annotated each news article to be related to: protests, natural disasters, social practices (such as drinking, eating, festivals, sports etc.), economic, policy or legal, flora and fauna, political, historical facts/data, satire on climate change action/lack of action, new scientific finding and, any other. We recognize these topics do not constitute all possible topics in the context of climate change. Using these groups, we were able to generalize the dominant stories in the climate change discussion to explain the dominant frames.

We find that social practices (15/13), protests (10/12) and, natural disaster-related (9/10) stories are most prominent. The any other  (11/8) category was also prominent. The least prominent stories were in satire (1/4) and historical facts (2/2) group. The values in the bracket represent the number of stories as marked by each annotator. The % agreement between annotators is relatively high at 77%. A thorough topical analysis of a large sample of news articles would give a more robust insight into the dynamics of frames in climate change news articles. Future work could further the NLP frames research by connecting generic and topical frames/topics in large datasets. We also find that only 2 news articles are from popular news agencies as listed by Pew Research.

