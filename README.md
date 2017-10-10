## AraVec
Advancements in neural networks have led to developments in fields like computer vision, speech recognition and natural
language processing (NLP). One of the most influential recent developments in NLP is the use of word embeddings, where
words are represented as vectors in a continuous space, capturing many syntactic and semantic relations among them.

AraVec is a pre-trained distributed word representation (word embedding) open source project which aims to provide the Arabic NLP
research community with free to use and powerful word embedding models. The first version of AraVec provides six different
word embedding models built on top of three different Arabic content domains; Tweets, World Wide Web pages and Wikipedia
Arabic articles. The total number of tokens used to build the models amounts to more than 3,300,000,000. This paper describes
the resources used for building the models, the employed data cleaning techniques, the carried out preprocessing step, as well as
the details of the employed word embedding creation techniques.

AraVec comes in its first version with six different word embeddings models built on top of three different Arabic content domains;
1. Twitter tweets
2. World Wide Web pages
3. Wikipedia Arabic articles

By total tokens of more than 3,300,000,000 tokens.


## Citation
`Abu Bakr Soliman, Kareem Eisa, and Samhaa R. El-Beltagy, “AraVec: A set of Arabic Word Embedding Models for use in Arabic NLP”, in proceedings of the 3rd International Conference on Arabic Computational Linguistics (ACLing 2017), Dubai, UAE, 2017.`

## Download
Model        	  | Docs No.             | Tokens No.    | Dimension	| Technique 	| Download |	Mirror-1 |
-----        	  | --------             | ----------    | ---------	| --------- 	| -------- |	-------- |
Twittert-CBOW          | 66,900,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/ce9phmmawoe1ure/Twt-CBOW.zip?dl=0) |	[Download](https://archive.org/download/AraVec/Twt-CBOW.zip) |
Twittert-SG          | 66,900,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/26mfjdspmz22dqp/Twt-SG.zip?dl=0) |	[Download](https://archive.org/download/AraVec/Twt-SG.zip) |
Web-CBOW         | 132,750,000           | 2,225,317,169 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/3zfjii6ap79hwng/WWW-CBOW.zip?dl=0) |	[Download](https://archive.org/download/AraVec/WWW-CBOW.zip) |
Web-SG          | 132,750,000           | 2,225,317,169 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/jt42ry9q4vqn4js/WWW-SG.zip?dl=0) |	[Download](https://archive.org/download/AraVec/WWW-SG.zip) |
Wikipedia-CBOW          | 1,800,000           | 1,090,082,092 | 300	        | CBOW 	        | [Download](https://www.dropbox.com/s/yk1vx8givzk6yvo/Wiki-CBOW.zip?dl=0) |	[Download](https://archive.org/download/AraVec/Wiki-CBOW.zip) |
Wikipedia-SG          | 1,800,000           | 1,090,082,092 | 300	        | Skip-Gram 	        | [Download](https://www.dropbox.com/s/xnz5d4oxqsm4wdm/Wiki-SG.zip?dl=0) |	[Download](https://archive.org/download/AraVec/Wiki-SG.zip) |


## How to use
These models were built using [gensim](https://radimrehurek.com/gensim/models/word2vec.html) Python library. Here's a simple code for loading and using
one of the models by following these steps:
1. Install `gensim` using either `pip` or `conda`

>> pip install gensim

>> conda install gensim

2. extract the compressed model files to a directory [ e.g. `Twittert-CBOW` ]
3. run this python code to load and use the model

```
# -*- coding: utf8 -*-
import gensim
import re

# load the model
model = gensim.models.Word2Vec.load('Twt-CBOW')

# Clean/Normalize Arabic Text
def clean_str(text):
    search = ["أ","إ","آ","ة","_","-","/",".","،"," و "," يا ",'"',"ـ","'","ى","\\",'\n', '\t','&quot;','?','؟','!']
    replace = ["ا","ا","ا","ه"," "," ","","",""," و"," يا","","","","ي","",' ', ' ',' ',' ? ',' ؟ ',' ! ']
    
    #remove tashkeel
    p_tashkeel = re.compile(r'[\u0617-\u061A\u064B-\u0652]')
    text = re.sub(p_tashkeel,"", text)
    
    #remove longation
    p_longation = re.compile(r'(.)\1+')
    subst = r"\1\1"
    text = re.sub(p_longation, subst, text)
    
    text = text.replace('وو', 'و')
    text = text.replace('يي', 'ي')
    text = text.replace('اا', 'ا')
    
    for i in range(0, len(search)):
        text = text.replace(search[i], replace[i])
    
    #trim    
    text = text.strip()

    return text

# python 3.X
word = clean_str(u'القاهرة')
# python 2.7
# word = clean_str('القاهرة'.decode('utf8', errors='ignore'))

# find and print the most similar terms to a word
most_similar = model.wv.most_similar( word )
for term, score in most_similar:
	print(term, score)
	
# get a word vector
word_vector = model.wv[ word ]

```

## Citation
`Abu Bakr Soliman, Kareem Eisa, and Samhaa R. El-Beltagy, “AraVec: A set of Arabic Word Embedding Models for use in Arabic NLP”, in proceedings of the 3rd International Conference on Arabic Computational Linguistics (ACLing 2017), Dubai, UAE, 2017.`

## [Read the Full-Text Paper](https://www.researchgate.net/publication/319880027_AraVec_A_set_of_Arabic_Word_Embedding_Models_for_use_in_Arabic_NLP)