# DARA

**Automated data retrevial system**  
Natural language queries into automaed finings. With the goal to start conversations with data across many tables in an intelligent way. 

Example: How many students are in Markeing at WP Carey


**Reason for development**  
We want to create conversations with our data. This can help ease the work that business intelligence developers have when examining lage amounts of data. A conversational system also allows for rapid brainstorming and question asking. Moving more focus on the value the data has and not the efforts to mine said data.
 
**Notable available products**  
Power BI Q@A is a Microsoft product that helps translate nautral language to automated reporting within Power BI models.

Kueri allows users to navigate, explore, and present their Salesforce data with using a Google style as-you-type auto-complete suggestions. [http://kueri.me/](http://kueri.me/])

## Phases 


1. Natural Langugae 
2. Reduced to fixed intents or parts of speech
3. Reduced to query intents (SELECT, GROUP, FROM)
4. Build intelligble queries

#### Semantic Parksing ( Parse natrual text )

The first technical challeneg that nees to be solved is the process of converting natural language into annotated text. We want to take any arbitrary sentence and derive meaning from these words. Once the intent is derived and other imporant information is extracted we will use a finate set of extropations to build the further logic on. 

Top choice: `Google API`

#### Information retrevial

The system will need to know where to look. The second challenege and ongoing concern is indexing the available data effecticly and effeicently. A database or managed collection of meta data is needed for lookups. This sections applies to the range of databases the query will consider when building a query to answer the intented question

Top choice: `DNE`  
Next up:	`DENODO` maybe**


#### Building query/ies

Building fucntioning queries from a fixed amount 

Here we will aid our efforts with the hardworkd that Microsoft has done in building Power BI's Q&A system. In this [page](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-q-and-a-tips/) they map out what capabilies their program has and how it matches text into queries. We will use this as a framework to build SQL queries. 

Top choice: `QUEPY`

#### Execute query

This is not a complex function of the system. However additional logic must be added here to return satisfactory results. For example - a query that may never be written by a human because of obvious runtime issues need to be hardcoded into the system. We can focus on fixed timeout, then semi-intelligent timouts. Lastly the system must be able to run in a secure enviroment that has connection access to the needed datasources. 


## Conquering each problem

1. Semantic Parksing
2. Information retrevial
3. Building query/ies
4. Execute query


### Semantic Parksing Approaches


**Text tagging**  

Large syntax labeled text files exists and models are trained on the labels and text. 

**Vector representation**  

This is the most efficent and cutting edge method for extracting meaning out of text. By abstracting each word to a vector in a extremly high dimentional space, a naive understanding of the relationship between words and thier individual meaning can be extracted. Googls Word2Vec impementation is an amazing example of this extact phenom. After deriving the meaning of words (as a set of complex vectors) these computer generated features (vectors) can be fed into an online classifcation model. This classifcaiton model would reduce the meanings of words into consise intent that is based off of the meaning of the words. This is the leading way seach engines derive your actual meaning from 


**Google Cloud Natural Language API**  

Google as usual offers this as a service. A great one too. This service I assume uses the same technologies as mentioned above, vector representation and the intent classifcation. However this is trained over a massive corpus and backed with the reliabilty of Googles APIs. 

[Example usage](https://cloud.google.com/blog/big-data/2016/07/using-the-cloud-natural-language-api-to-analyze-harry-potter-and-the-new-york-times)

### Information retrevial Approaches

This section just refers to seraching through metadata. 

### Building query approaches

#### [ Quepy ](http://quepy.readthedocs.io/en/latest/tutorial.html) 
text to query framework


`python dbpedia/main.py "Who is Tom Cruise?"`
