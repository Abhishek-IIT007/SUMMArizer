# README #

goto config file:

Make sure all the dependencies mentioned in the config files are installed.


first set the folder_to_watch to the folder containing the articles.
set the summarization ratio(what should be the size of summary relative to the original text)
now set the folder_to_save to the output folder.
select the summarizer you want to use by changing the value of function (1 to 5)mentioned below
You have an option to merge all the summaries into one text file. For doing that set single_file =True
### What is this repository for? ###

This repository is for extractive based text summarization.
I tried 5 different Extractive based text summarization. They are:-
1.	Tf-Idf (Term frequency- Inverse document frequency) based text summarizer.
2.	Term frequency based text summarizer.
3.	Text rank summarizer (based on Page rank algorithm)
4.	Lex rank summarizer
5.	LSA(latent semantic analysis ) based text summarizer.
I will give a brief description about these summarizers.
Tf-Idf based summarizer:- 
I used scikit-learn's TfidfVectorizer class to construct a term-document matrix containing the TF-IDF score for each word in each document in the Wikipedia Articles (50 articles). In essence, the rows of this sparse matrix correspond to documents in the corpus, the columns represent each word in the vocabulary of the corpus, and each cell contains the TF-IDF value for a given word in a given document. The code starts by selecting an article, then it iterates through the article, calculating a score for each sentence by summing the TF-IDF values for each word appearing in the sentence. We normalize the sentence scores by dividing by the number of tokens in the sentence (to avoid bias in favour of longer sentences). Then we sort the sentences by their scores, and return the highest-scoring sentences as our summary. The number of sentences returned corresponds to roughly 20% of the overall length of the article.
Term Frequency based text summarizer:- Procedure  remains the same as tf-idf based extraction but instead of calculating idf scores  by going through each document , only term frequency score is calculated by considering only the current document.
Text Rank Summarizer:- this algorithm works on the basis of PageRank algorithm (https://en.wikipedia.org/wiki/PageRank) 
The steps are:-
Pre-process the text: remove stop words and stem the remaining words. Create a graph where vertices are sentences. Connect every sentence to every other sentence by an edge. The weight of the edge is how similar the two sentences are. Run the PageRank algorithm on the graph. Pick the vertices (sentences) with the highest PageRank score.
I used gensim’s Summarization model to summarize as it implements text rank algorithm.  We have an option to decide how long the summarization should be. I chose it to be around 30 percent of the original text.

LexRank Summarizer:-LexRank is an unsupervised graph based approach similar to TextRank. LexRank uses IDF-modified Cosine as the similarity measure between two sentences. This similarity is used as weight of the graph edge between two sentences. LexRank also incorporates an intelligent post-processing step which makes sure that top sentences chosen for the summary are not too similar to each other.
LSA Text Summarizer:- LSA works by projecting the data into a lower dimensional space without any significant loss of information. One way to interpret this spatial decomposition operation is that singular vectors can capture and represent word combination patterns which are recurring in the corpus. The magnitude of the singular value indicates the importance of the pattern in a document.
For more information on LSA based text summarizer please refer http://user.ceng.metu.edu.tr/~e1395383/papers/TextSummarizationUsingLSA(Journal).pdf


### How do I get set up? ###

'''

List of articles/documents should be present in folder_to_watch
The following summarization functions are present in this code
1:Tf-Idf
2:Term frequency
3:Text Rank
4:Lex Rank
5:LSA summarization

DEPENDENCIES:- sumy , nltk , sklearn ,gensim
'''

Put all the 3 files in same folder and do the necessary changes in the config.py file.

### Contribution guidelines ###

* Writing tests
* Code review
* Other guidelines

### Who do I talk to? ###

* Repo owner or admin
* Other community or team contact