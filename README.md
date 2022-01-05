<h1><center>How was last year? Exploring New York Times world news over 1 year time span</center></h1>

<h2> Project Background </h2>

In a fast paced society being able to share information as fast as possible is key for growth. Data science comes in aid trying to process these informations and return them back in a usable and readeable way. To me, one of the most interesting applications for Data Science is the one that involves text analysis and Natural Language Processing (NLP). There are numerous books and publications about this subject and it's not hard to understand why: being able to make a computer process and understand human language is fascinating and nevertheless challenging. 

Having the possibility to evaluate in a blink of an eye what a time period has been characterized of by analyzing news is the point of focus of this study - condensing them in few graphs or charts giving simple answers to more complex data. With this project I wanted to apply text analysis techniques ad more in general exploratory data analysis to understand how did the past 12 months go judging from the world standpoint. In my opinion it is interesting to let a machine elaborate some refined data to have insights and outcomes on a certain period based on news and articles. Thus, I will measure and explore varius indicators that can give us an idea of the main topics, subjects and words that characterized the world last year. Also I wanted to discover some hidden patterns that could not be seen at first without a deeper analysis. For example, will Covid be the first topic amongst all or there will be some other topic on top of the list? I will try to answer these questions by exploring the data.

Altough the data available is fairly huge, the main limitation of this study could be not having acces to the full articles but only to the titles, abstracts and few others text sections. This could imply that our text analysis will be less precise or that simply extracting information from only the few lines of text could not be enough to have useful insights. I will try to address it extracting as much text information as possible from the retrived data.

Also, even if not expected, at the end of the study there might be some findings that could lead to "harmful assumptions". For example some topics that we judge as positive are instead judged negatively by the sentiment analysis or some topics being more often utilized than others could lead to some degree of discrimination depending on our line of thinking. I will try to address this being as objective as possible.

Throughout the study we will look for:

* Feature insights (eg. most used keywords, top subsection, etc.)
* Vocabulary diversity
* Most used words
* WordCloud visualization
* Sentiment analysis

<h2>Data</h2>

![Data provided by The New York Times](https://developer.nytimes.com/files/poweredby_nytimes_200a.png?v=1583354208344)

I decided to collect news information using  <a href="https://developer.nytimes.com/apis">New York Times public APIs</a> and specifically the Archive API that returns an array of NYT articles for a given month, going back to 1851. All data is provided by The New York Times - this source has been specifically choosen because it is widely recognized as a respectable and important source.

While using their APIs we need to make sure to not break their <a href="https://help.nytimes.com/hc/en-us/articles/115014893">Terms of service</a> and to comply with their API call limit:
* 4000 requests per day
* 10 requests per minute
  * Sleep our script 6 seconds to avoid hitting the per minute rate limit

Data is returned as JSON and will be structured as follows after being processed:

| Headline | Print Headline | Lead Paragraph | Abstract | Document Type | Keywords | News_desk | Section Name | Subsection Name | Word count | Date |
|----------|----------------|----------------|----------|---------------|----------|-----------|--------------|-----------------|------------|------|
| OBJ      | OBJ            | OBJ            | OBJ      | OBJ           | OBJ      | OBJ       | OBJ          | OBJ             | INT        | OBJ  |

<h2>Data Processing</h2>

The study will be structured as follows:

1. Pull data from the NYT APIs and process it
2. Reduce the dataset to the sole "World" section articles
   1. This will imply some data cleaning techniques
3. Save the new reduced dataframe as .csv - this will also comply with the assignment constrain of having a 10MB< dataset
4. Data cleaning and feature engineering
5. Proceed with Exploratory Data Analysis (EDA)
6. Conclusions and considerations
