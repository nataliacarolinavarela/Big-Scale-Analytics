# Big-Scale-Analytics: Team Samsung

# Project Description: 

You have decided to build a
model for English speakers that predicts the difficulty of a French written text. This can be then
used, e.g., in a recommendation system, to recommend texts (for example, recent news articles)
that are appropriate for someone’s language level. If someone is at A1 French level, it is
inappropriate to present a text at B2 level, as she won’t be able to understand it. Ideally, a text
should have many known words and may have a few words that are unknown so that the person
can improve.

# Milestone 1: (15/03): 

## 1. Which paper did you read on the topic ? 

We focused our research on two different aspects. The first one is how can we find some similarities between the English and the French language, this would enable us to classify the different sentences more accurately (we believe). The second one focuses on the different measures to classify the difficulty of words / sentences in a given text. 

## 2.1. Similarities between English and French: 

We read different research papers in order to find solutions to resolve the problem, in the different sections, we explain the solutions and how we could use it. 

#### 2.1.1: Cognates: 
We first took a look at cognates, they seemed interesting as they are similar words between two languages. In fact, “[…] French and English share many roots, leading to tons of cognates”. [1] They are very present in the French vocabulary: “30% of the French vocabulary consists of cognates. “[2]. However, we have to be careful with false / partial cognates, that are similar words which have a common meaning only in some contexts. For example, the word police in French can translate to police, pol- icy or font, depending on the context. 

We are planning to use them as this would enable an English speaker to find words that he might know in a sentence, making it easier for him/her to understand the sentence. In fact, cognates are also useful for estimating the readability of a text for non-native readers. To do so, our initial idea will be to make an exhaustive list of cognates and partial cognates and when a cognate is identified, to add a ponderation to the sentence in terms of readability. 

#### 2.1.2: Prefixes and suffixes similar in French and English: 
French and English prefixes are historically linked, this will be an interesting path to analyse in order to find similarities between English and French words and evaluate the difficulty of given words in a sentence.  For example, “anti-“ in French and English means against” or “opposed to.” We can see that through this example: anti- + bactérien (bacterial) → antibactérien (antibacterial) [3]. In addition, the same methodology could be used for suffixes [4]

#### 2.1.3: Research on the etymology of words: 
We could also take a look at etymological similarities between the two languages. In fact, “45% of all English words have a French origin [...] Although French is derived mainly from Latin (which accounts for about 60% of English vocabulary ), it also includes words from Gaulish and Germanic languages (especially Old Frankish). ” [5] 

We could use this to find similarities between texts in order to evaluate the level of a given French text and the way it could be understood by a native English speaker by making, for example, a list of words with similar etymology [6]

## 2.2. Readability / Difficulty / lisibility of texts: 

#### 2.2.1: Lisibility of text: 
We have found a Python library [7] that returns the Flesch-Kincaid Grade of a given text in French. In fact, the Flesch-Kincaid Grade is based on a calculation based on the length of the word and the length of the sentence and gives a weight on this Sentence (or text in input). [8]. 

This would be interesting to find the level attributed to the different sentences in order to classify them correctly based on their difficulty. 

#### 2.2.2: Difficulty of text: 
More in this field, we have found that the  “the number of syllables and the lengths of sentences increase the difficulty to understanding a text (new learners)” [9]. 
In this study they use “ features extracted by the system consists in: (i) part-of-speech (POS) tags, chunks, words and sentences features; (ii) verb features and different metrics involving averages and frequencies; (iii) several metrics involving syllables” [10] to find the difficulty of a text given. They concluded interesting elements, such as that: 
The length of a text is related with its readability, i.e. typically, longer texts, specially with long sentences, have much more detail or content, which can make them more difficult to understand
The average number of verb phrases per sentence and the average length of sentences derive from Pitler and Nenkova (Pitler and Nenkova, 2008): the more verbs a sentence contains and the longer a sentence is, the more complicated it becomes to understand it. 
We will also explore the different conjugation tenses of sentences (past, present, future, etc) as an indicator level.

This will be interesting for us to understand and evaluate the difficulty of a given text based on the length of sentences and the number of the words in sentences. 


## 3: How do you intend to solve the problem ? 

We will begin by cleaning the data: We will use notions that we have learned in the past course of DMML in order to clean the data: NLTK: Tokenization, Stopword, text classification [11].

To create the model: we will browse through every sentence and extract the different words and compare them to our lists in order to find words with similar etymological, suffixes, prefixes, cognates. We could also calculate the different number of words and the lengths of sentences in order to evaluate its difficulty. We are planning to use classification in order to weight every sentence according to its difficulty using the language evaluation of French, A1,A2, B1,B2, C1, C2. We are planning to put a weight to every sentence and classify in one of those levels and suggest them to the user. As we are still in an exploratory phase, we will begin by using a classification and see the results, however, we also plan to try a regression and compare both results.  



Sources: 

- [1] 60+ French Cognates You Can Count On (Plus Fake Ones You Can’t)
 https://www.fluentu.com/blog/french/french-cognates/ 
- [2] Cognate Identification using Machine Translation https://www.aclweb.org/anthology/U15-1018.pdf 
- [3] https://www.fluentu.com/blog/french/french-prefixes/  
- [4] https://www.fluentu.com/blog/french/french-suffixes/  
- [5] https://en.wikipedia.org/wiki/
- [6]List_of_English_words_of_French_origin#:~:text=According%20to%20different%20sources%2C%2045,words%20have%20a%20French%20origin.&text=Although%20French%20is%20derived%20mainly,languages%20(especially%20Old%20Frankish).   
- [7] https://pypi.org/project/textstat/ 
- [8] https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests  
- [9] http://thormay.net/lxesl/tech4.html 
- [10] https://www.inesc-id.pt/publications/11043/pdf  
- [11] https://www.datacamp.com/community/tutorials/text-analytics-beginners-nltk 


## 4. How many annotated sentence you contributed:  

We have collected sentences from different sources, most of our sentences were collected from “la fondation Esprit Francophonie” [4] where we fetched sentences from exams of “comprehension écrite” according to the different levels (A1…C2). We then copied them in an algorithm that we built in PyCharm that enabled us to clean the sentences and import them one by one in the Google Sheet [5]. Then we annotated the 1178 sentences with their level difficulty by hand. We created a Jupiter Notebook in order to see the distribution of the levels in our dataset. The Jupiter Notebook is available on our Github Page. 

Dataset:
- A1
- A2
- B1
- B2
- C1
- C2

Total sentences: 1178

Links to the different websites where we extracted our sentences to fill our database. 
- [1] https://lire-et-ecrire.be/?lang=fr 
- [2] https://www.lepointdufle.net 
- [3] https://lepetitscribe.com/category/niveaux/a1/ 
- [4] https://www.delfdalf.ch/niveaux/exemples-dexamens
- [5]https://docs.google.com/spreadsheets/d/1oQGKQZLj6JRbgY-ZQLfClUsq-AHA8LIegtSZvxw6s6A/edit#gid=1508059658 


# Milestone 2:

# Milestone 3: 

# Participants: 
- Alexis Erne
- Maxime Raisin
- Natalia Varela
 
