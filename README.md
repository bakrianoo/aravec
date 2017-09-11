## AraVec
AraVec is a pre-trained distributed word representation (word embedding) open source project which comes to enhance the Arabic NLP research
community with free to use and powerful word embeddings models built with one of the most popular word embedding techniques, Word2Vec.
AraVec comes in its first version with six different word embeddings models built on top of three different Arabic content domains;
1. Twitter tweets
2. World Wide Web pages
3. Wikipedia Arabic articles

by total tokens of more than 3,300,000,000.
Word embeddings models became one of the most powerful tools required by many researchers especially the Arabic NLP interesting researchers who are facing
a high difficulty to reach the sufficient open resources and that what pushes us to work on this project to fill like these gaps. 

## Citation
`CITATION GOES HERE`

## Download
Model        	  | Docs No.             | Tokens No.    | Dimension	| Technique 	| Download |
-----        	  | --------             | ----------    | ---------	| --------- 	| -------- |
Twittert-CBOW          | 66,900,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/preview/AraVec/Twt-CBOW.zip?role=personal) |
Twittert-SG          | 66,900,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/preview/AraVec/Twt-SG.zip?role=personal) |
Web-CBOW         | 132,750,000           | 2,225,317,169 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/preview/AraVec/WWW-CBOW.zip?role=personal) |
Web-SG          | 132,750,000           | 2,225,317,169 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/preview/AraVec/WWW-SG.zip?role=personal) |
WikiPedia-CBOW          | 1,800,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/preview/AraVec/Wiki-CBOW.zip?role=personal) |\
WikiPedia-SG          | 1,800,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/preview/AraVec/Wiki-SG.zip?role=personal) |


## How to use
These model were built using [gensim](https://radimrehurek.com/gensim/models/word2vec.html) Python library. Here's a simple code for loading and using
one of the models by following these steps:
1. Install `gensim` using either `pip` or `conda`

>> pip install gensim

>> conda install gensim

2. extract the compresse model files to a directory e.g. `Twittert-CBOW`
3. run this python code to load the model

```
import gensim

# load the model
model = gensim.models.Word2Vec.load('Twittert-CBOW/Twittert-CBOW')


# python 3.X
word = 'مصر'
# python 2.7
# word = 'مصر'.decode('utf8', errors='ignore')

# find and print the most similar words to a word
most_similar = model.most_similar( word )
for word, score in most_similar:
	print(word, score)
	
# get a word vector
word_vector = model.wv[ word ]

```