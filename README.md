## AraVec 3.0
Advancements in neural networks have led to developments in fields like computer vision, speech recognition and natural
language processing (NLP). One of the most influential recent developments in NLP is the use of word embeddings, where
words are represented as vectors in a continuous space, capturing many syntactic and semantic relations among them.

AraVec is a pre-trained distributed word representation (word embedding) open source project which aims to provide the Arabic NLP
research community with free to use and powerful word embedding models. The first version of AraVec provides six different
word embedding models built on top of three different Arabic content domains; Tweets and Wikipedia
This paper describes
the resources used for building the models, the employed data cleaning techniques, the carried out preprocessing step, as well as
the details of the employed word embedding creation techniques.

The third version of AraVec provides 16 different word embedding models built on top of two different Arabic content domains; Tweets and Wikipedia Arabic articles. The major difference between this version and the previous ones, is that the we produced two different types of models, unigrams and n-grams models. We utilized set of statistical techniques to genrate the most common used n-grams of each data domain.

1. Twitter tweets
2. Wikipedia Arabic articles

By total tokens of more than 1,169,075,128 tokens.


## Citation
`Abu Bakr Soliman, Kareem Eisa, and Samhaa R. El-Beltagy, “AraVec: A set of Arabic Word Embedding Models for use in Arabic NLP”, in proceedings of the 3rd International Conference on Arabic Computational Linguistics (ACLing 2017), Dubai, UAE, 2017.`

## [Read the Full-Text Paper](https://www.researchgate.net/publication/319880027_AraVec_A_set_of_Arabic_Word_Embedding_Models_for_use_in_Arabic_NLP)

***
***

## Rapid Example

1. Install gensim >= 3.4 and nltk >= 3.2 using either pip or conda
2. extract the compressed model files [ e.g. Twittert-CBOW ] to a directory called `models`

```python
import gensim

# Unigrams models
t_model = gensim.models.Word2Vec.load('models/full_uni_cbow_100_twitter.mdl')
word_vector = t_model.wv[ 'تونس' ]

# Ngrams models [when you have a multiple words token]
t_model = gensim.models.Word2Vec.load('models/full_grams_cbow_100_twitter.mdl')
word_vector = t_model.wv[ 'السلام عليكم'.replace(' ','_') ] # you need to replace spaces with _ character

# find most similar tokens
token = clean_str(u'ابو تريكه').replace(" ", "_")

if token in t_model.wv:
    most_similar = t_model.wv.most_similar( token, topn=10 )
    for term, score in most_similar:
        term = clean_str(term).replace(" ", "_")
        if term != token:
            print(term, score)
# OUTPUTs
# تريكه 0.752911388874054
# حسام_غالي 0.7516342401504517

```

For more detailed answer included the used clean function which required to preprocess the query tokens. Please go to the detiled answer [Here](https://github.com/bakrianoo/aravec#Code-Samples).


## Download

### N-Grams Models

Let's take a look on what we can retieve from the n-grams models using some most similar queries. 

![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-1.jpg)
***
![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-2.jpg)
***
![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-3.jpg)
***
![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-4.jpg)
***
![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-5.jpg)
***
![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/query-6.jpg)
***

***
### N-Grams Models

Model        	  | Docs No.             | Vocabularies No.    | Vec-Size		| Download      |
-----        	  | --------             | ----------          | ---------	    | --------- 	|
Twitter-CBOW          | 66,900,000           | 1,476,715 | **300**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_grams_cbow_300_twitter.zip) |
Twitter-CBOW          | 66,900,000           | 1,476,715 | **100**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_grams_cbow_100_twitter.zip) |
Twitter-SkipGram          | 66,900,000           | 1,476,715 | **300**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_grams_sg_300_twitter.zip) |
Twitter-SkipGram          | 66,900,000           | 1,476,715 | **100**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_grams_sg_100_twitter.zip) |
Wikipedia-CBOW          | 1,800,000           | 662,109 | **300**	        | [Download](https://archive.org/download/aravec_3_wiki/full_grams_cbow_300_wiki.zip) |
Wikipedia-CBOW          | 1,800,000           | 662,109 | **100**	        | [Download](https://archive.org/download/aravec_3_wiki/full_grams_cbow_100_wiki.zip) |
Wikipedia-SkipGram          | 1,800,000           | 662,109 | **300**	        | [Download](https://archive.org/download/aravec_3_wiki/full_grams_sg_300_wiki.zip) |
Wikipedia-SkipGram          | 1,800,000           | 662,109 | **100**	        | [Download](https://archive.org/download/aravec_3_wiki/full_grams_sg_100_wiki.zip) |

***
***


### Unigrams Models

Model        	  | Docs No.             | Vocabularies No.    | Vec-Size		| Download      |
-----        	  | --------             | ----------          | ---------	    | --------- 	|
Twitter-CBOW          | 66,900,000           | 1,259,756 | **300**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_uni_cbow_300_twitter.zip) |
Twitter-CBOW          | 66,900,000           | 1,259,756 | **100**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_uni_cbow_100_twitter.zip) |
Twitter-SkipGram          | 66,900,000           | 1,259,756 | **300**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_uni_sg_300_twitter.zip) |
Twitter-SkipGram          | 66,900,000           | 1,259,756 | **100**	        | [Download](https://archive.org/download/full_grams_cbow_300_twitter/full_uni_sg_100_twitter.zip) |
Wikipedia-CBOW          | 1,800,000           | 320,636 | **300**	        | [Download](https://archive.org/download/aravec_3_wiki/full_uni_cbow_300_wiki.zip) |
Wikipedia-CBOW          | 1,800,000           | 320,636 | **100**	        | [Download](https://archive.org/download/aravec_3_wiki/full_uni_cbow_100_wiki.zip) |
Wikipedia-SkipGram          | 1,800,000           | 320,636 | **300**	        | [Download](https://archive.org/download/aravec_3_wiki/full_uni_sg_300_wiki.zip) |
Wikipedia-SkipGram          | 1,800,000           | 320,636 | **100**	        | [Download](https://archive.org/download/aravec_3_wiki/full_uni_sg_100_wiki.zip) |

***
***


## How to use
These models were built using [gensim](https://radimrehurek.com/gensim/models/word2vec.html) Python library. Here's a simple code for loading and using
one of the models by following these steps:
1. Install `gensim` >= **3.4** and nltk >= **3.2** using either `pip` or `conda`

>> pip install gensim nltk

>> conda install gensim nltk

2. extract the compressed model files to a directory [ e.g. `Twittert-CBOW` ]
3. keep the **.npy** files. You are gonna to load the file with no extension, like what you'll see in the following code.
4. run this python code to load and use the model

![alt text](https://raw.githubusercontent.com/bakrianoo/aravec/master/assets/how.jpg)

## Code Samples

```python

# -*- coding: utf8 -*-
import gensim
import re
import numpy as np
from nltk import ngrams

# =========================
# ==== Helper Methods =====

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

def get_vec(n_model,dim, token):
    vec = np.zeros(dim)
    is_vec = False
    if token not in n_model.wv:
        _count = 0
        is_vec = True
        for w in token.split("_"):
            if w in n_model.wv:
                _count += 1
                vec += n_model.wv[w]
        if _count > 0:
            vec = vec / _count
    else:
        vec = n_model.wv[token]
    return vec

def calc_vec(pos_tokens, neg_tokens, n_model, dim):
    vec = np.zeros(dim)
    for p in pos_tokens:
        vec += get_vec(n_model,dim,p)
    for n in neg_tokens:
        vec -= get_vec(n_model,dim,n)
    
    return vec   

## -- Retrieve all ngrams for a text in between a specific range
def get_all_ngrams(text, nrange=3):
    text = re.sub(r'[\,\.\;\(\)\[\]\_\+\#\@\!\?\؟\^]', ' ', text)
    tokens = [token for token in text.split(" ") if token.strip() != ""]
    ngs = []
    for n in range(2,nrange+1):
        ngs += [ng for ng in ngrams(tokens, n)]
    return ["_".join(ng) for ng in ngs if len(ng)>0 ]

## -- Retrieve all ngrams for a text in a specific n
def get_ngrams(text, n=2):
    text = re.sub(r'[\,\.\;\(\)\[\]\_\+\#\@\!\?\؟\^]', ' ', text)
    tokens = [token for token in text.split(" ") if token.strip() != ""]
    ngs = [ng for ng in ngrams(tokens, n)]
    return ["_".join(ng) for ng in ngs if len(ng)>0 ]

## -- filter the existed tokens in a specific model
def get_existed_tokens(tokens, n_model):
    return [tok for tok in tokens if tok in n_model.wv ]





# ============================   
# ====== N-Grams Models ======

t_model = gensim.models.Word2Vec.load('models/full_grams_cbow_100_twitter.mdl')

# python 3.X
token = clean_str(u'ابو تريكه').replace(" ", "_")
# python 2.7
# token = clean_str(u'ابو تريكه'.decode('utf8', errors='ignore')).replace(" ", "_")

if token in t_model.wv:
    most_similar = t_model.wv.most_similar( token, topn=10 )
    for term, score in most_similar:
        term = clean_str(term).replace(" ", "_")
        if term != token:
            print(term, score)

# تريكه 0.752911388874054
# حسام_غالي 0.7516342401504517
# وائل_جمعه 0.7244222164154053
# وليد_سليمان 0.7177559733390808
# ...

# =========================================
# == Get the most similar tokens to a compound query
# most similar to 
# عمرو دياب + الخليج - مصر

pos_tokens=[ clean_str(t.strip()).replace(" ", "_") for t in ['عمرو دياب', 'الخليج'] if t.strip() != ""]
neg_tokens=[ clean_str(t.strip()).replace(" ", "_") for t in ['مصر'] if t.strip() != ""]

vec = calc_vec(pos_tokens=pos_tokens, neg_tokens=neg_tokens, n_model=t_model, dim=t_model.vector_size)

most_sims = t_model.wv.similar_by_vector(vec, topn=10)
for term, score in most_sims:
    if term not in pos_tokens+neg_tokens:
        print(term, score)

# راشد_الماجد 0.7094649076461792
# ماجد_المهندس 0.6979793906211853
# عبدالله_رويشد 0.6942606568336487
# ...

# ====================
# ====================




# ============================== 
# ====== Uni-Grams Models ======

t_model = gensim.models.Word2Vec.load('models/full_uni_cbow_100_twitter.mdl')

# python 3.X
token = clean_str(u'تونس')
# python 2.7
# token = clean_str('تونس'.decode('utf8', errors='ignore'))

most_similar = t_model.wv.most_similar( token, topn=10 )
for term, score in most_similar:
    print(term, score)

# ليبيا 0.8864325284957886
# الجزائر 0.8783721327781677
# السودان 0.8573237061500549
# مصر 0.8277812600135803
# ...



# get a word vector
word_vector = t_model.wv[ token ]

```

## Citation
`Abu Bakr Soliman, Kareem Eisa, and Samhaa R. El-Beltagy, “AraVec: A set of Arabic Word Embedding Models for use in Arabic NLP”, in proceedings of the 3rd International Conference on Arabic Computational Linguistics (ACLing 2017), Dubai, UAE, 2017.`

## [Read the Full-Text Paper](https://www.researchgate.net/publication/319880027_AraVec_A_set_of_Arabic_Word_Embedding_Models_for_use_in_Arabic_NLP)