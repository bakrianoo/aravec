## AraVec
AraVec is a pre-trained distributed word representation (word embedding) open source project which comes to enhance the Arabic NLP research
community with free to use and powerful word embeddings models built with one of the most popular word embedding techniques, Word2Vec.
AraVec comes in its first version with six different word embeddings models built on top of three different Arabic content domains;
1. Twitter tweets
2. World Wide Web pages
3. Wikipedia Arabic articles

By total tokens of more than 3,300,000,000.


## Citation
`CITATION GOES HERE`

## Download
Model        	  | Docs No.             | Tokens No.    | Dimension	| Technique 	| Download |
-----        	  | --------             | ----------    | ---------	| --------- 	| -------- |
Twittert-CBOW          | 66,900,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/ce9phmmawoe1ure/Twt-CBOW.zip?dl=0) |
Twittert-SG          | 66,900,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/26mfjdspmz22dqp/Twt-SG.zip?dl=0) |
Web-CBOW         | 132,750,000           | 2,225,317,169 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/3zfjii6ap79hwng/WWW-CBOW.zip?dl=0) |
Web-SG          | 132,750,000           | 2,225,317,169 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/jt42ry9q4vqn4js/WWW-SG.zip?dl=0) |
Wikipedia-CBOW          | 1,800,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/yk1vx8givzk6yvo/Wiki-CBOW.zip?dl=0) |\
Wikipedia-SG          | 1,800,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/xnz5d4oxqsm4wdm/Wiki-SG.zip?dl=0) |


## How to use
These models were built using [gensim](https://radimrehurek.com/gensim/models/word2vec.html) Python library. Here's a simple code for loading and using
one of the models by following these steps:
1. Install `gensim` using either `pip` or `conda`

>> pip install gensim

>> conda install gensim

2. extract the compressed model files to a directory [ e.g. `Twittert-CBOW` ]
3. run this python code to load and use the model

```
import gensim

# load the model
model = gensim.models.Word2Vec.load('Twittert-CBOW/Twt-CBOW')


# python 3.X
word = u'مصر'
# python 2.7
# word = 'مصر'.decode('utf8', errors='ignore')

# find and print the most similar terms to a word
most_similar = model.wv.most_similar( word )
for term, score in most_similar:
	print(term, score)
	
# get a word vector
word_vector = model.wv[ word ]

```

## Citation
`CITATION GOES HERE`