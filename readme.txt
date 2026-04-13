#practical 1 : write a program to perfrom tokenization over word & sentence

import nltk
from nltk.tokenize import word_tokenize
from nltk.tokenize import sent_tokenize
nltk.download('punkt_tab')
dataset = """Hello Mr. Watson, how are you doing today?
The weather is awesome.
The garden is green.
We should go out for a walk
The sky is pinkish-blue.
You shouldn't eat cardboard. """
#tokenization the sentences
print(sent_tokenize(dataset))
for i in sent_tokenize(dataset):
  print(i)
from nltk.tokenize import word_tokenize
print("word tokenize",  word_tokenize(dataset))


# practical 2: Write a Program to identify Stopwords in a given sentence in English.
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
dataset = """ English is a very important asset when seeking employment in Guatema"""
stop_words = set(stopwords.words('english'))
print(stop_words)
print("Total count of stopwords:", len(dataset))
words = word_tokenize(dataset)
print(words)
print("total words: ", len(words))
filtered_sentence=[]
for w in words:
if w not in stop_words:
filtered_sentence.append(w)
print(filtered_sentence)
print()
print("After removing stopwords", len(filtered_sentence))
filtered_sentence1=[]
for w in words:
if w in stop_words:
filtered_sentence1.append(w)
print(filtered_sentence1)
print()
print("Exsiting stopwords", len(filtered_sentence1))


# practical 3- Write a program to perform Stemming and Lemmatization for English Text

import nltk
nltk.download('all')
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize
ps = PorterStemmer()
words = ["program", "programs", "programer", "programming", "programmers"]
for w in words:
print(w, " : ", ps.stem(w))
sentence = "Programmers program with programming languages"
words = word_tokenize(sentence)
for w in words:
print(w, " : ", ps.stem(w))
from nltk.stem import PorterStemmer
e_words = ["wait", "waiting", "waited", "waits"]
ps = PorterStemmer()
for w in e_words:
rootWord = ps.stem(w)
print(rootWord)
from nltk.stem import PorterStemmer
from nltk.tokenize import sent_tokenize, word_tokenize
sentence = "He was waiting for the boat at the dock, watching as the waves gently lapped against the pier. The sun was beginning to set,
words = word_tokenize(sentence)
ps = PorterStemmer()
for w in words:
rootWord = ps.stem(w)
# create an object of class PorterStemmer
from nltk.stem import PorterStemmer
from nltk.stem import LancasterStemmer
porter = PorterStemmer()
lancaster=LancasterStemmer()
# provide a word to be stemmed
print("Porter Stemmer: - ")
print(porter.stem("cats"))
print(porter.stem("trouble"))
print(porter.stem("troubling"))
print(porter.stem("troubled"))
print()
print("Lancaster Stemmer: -")
print(lancaster.stem("cats"))
print(lancaster.stem("trouble"))
print(lancaster.stem("troubling"))

word_list = ["friend", "friendship", "friends", "friendships", "companionship", "ally", "allies", "companions", "acquaintances", "bond",
print("{0:20}{1:20}{2:20}".format("Word","Porter Stemmer", "Lancaster Stemmer"))
for word in word_list:
print("{0:20}{1:20}{2:20}".format(word, porter.stem(word), lancaster.stem(word)))

sentence = "Pythoners are very intelligent and work very pythonly and now they are pythoning their way to success."
porter.stem(sentence)

# stemming
import nltk
from nltk.stem.porter import PorterStemmer
porter_stemmer = PorterStemmer()
text = "studies studying cries cry"
tokenization = nltk.word_tokenize(text)
for w in tokenization:
print("Stemming for {} is {}".format(w, porter_stemmer.stem(w)))

# Lemmitization
import nltk
from nltk.stem import WordNetLemmatizer
wordnet_lemmatizer = WordNetLemmatizer()
text = "studies studying cries cry"
tokenization = nltk.word_tokenize(text)
for w in tokenization:
print("Lemma for {} is {}".format(w, wordnet_lemmatizer.lemmatize(w)))

practical 4: Write a program to segregate Part Of Speech (POS Tagging) for english Text.

import nltk
nltk.download('all')
import nltk
from nltk.tokenize import wordpunct_tokenize
from nltk.tag import pos_tag

dataset = """The Taj Mahal, located in Agra, India, is one of the most iconic and beautiful monuments in the word """
new_data = wordpunct_tokenize(dataset)
print(new_data)
pos_tag(new_data)
nltk.help.upenn_tagset()


practical 5: NER AND CHUNKING
import nltk
nltk.download('all')
dataset_tag=pos_tag(word_tokenize(dataset))
print(dataset_tag)
data_ner=ne_chunk(dataset_tag)
print(data_ner)
import nltk
from nltk.tokenize import word_tokenize
from nltk.tag import pos_tag
from nltk.chunk import RegexpParser

dataset = """Taj Mahal is one of the world's most celebrated structures in the world. It is a stunning white marble mausoleum located in
# Tokenize the data
new_data = word_tokenize(dataset)
print(new_data)

postagging = pos_tag(new_data)
print(postagging)

practical 6 - Write a program to perform WordNet & also check Word Similarity on English Text
import nltk
nltk.download('all')

nltk.down
load('wordnet')
from nltk.corpus import wordnet
syns = wordnet.synsets("program")
print(syns)
print(syns[0])
print(syns[0].lemmas())
print(syns[0].lemmas()[0].name())

# to find the defination
print(syns[0].definition())

# to get an example
print(syns[0].examples())

from nltk.corpus import wordnet
antonyms = []
# defining the function to find Antonyms
def TofindAntonyms(x):
for syn in wordnet.synsets(x):
for lm in syn.lemmas():
if lm.antonyms():
antonyms.append(lm.antonyms()[0].name()) #adding into antonyms
return antonyms
print(set(TofindAntonyms("bright")))

print(set(TofindAntonyms("inactive")))
print(set(TofindAntonyms("good")))

synonyms=[]
antonyms=[]
for syn in wordnet.synsets("good"):
for l in syn.lemmas():
synonyms.append(l.name())
if l.antonyms():
antonyms.append(l.antonyms()[0].name())
print("Synonyms: ",set(synonyms))
print("Antonyms: ",set(antonyms))

# WordSimilarity
car = wordnet.synset('car.n.01')
automobile = wordnet.synset('automobile.n.01')
print("Similarity between car and automobile", car.path_similarity(automobile))


# Wu-Palmer Similarity
from nltk.corpus import wordnet as wn
w1 = wordnet.synset('run.v.01') # v here denotes the tag verb
w2 = wordnet.synset('sprint.v.01')
print("Wu-Palmer Similarity between run and sprint", w1.wup_similarity(w2))


jump = wn.synset('jump.v.01')
leap = wn.synset('leap.v.01')
ship = wn.synset('ship.n.01')
print("Wu-Palmer Similarity between jump and leap", jump.wup_similarity(leap))

#practical  7: word cloud in english text

from wordcloud import wordcloud
import matplotlib.pyplot as plt
import matplotlib.pyplot as pPlt
from wordcloud import WordCloud, STOPWORDS
import numpy as npy
from PIL import Image
dataset = open("/content/Indian Motorcycle.txt", "r").read()

dataset = dataset.upper()
maskArray = npy.array(Image.open("/content/video-300x300.jpg"))
cloud = WordCloud(background_color = "#000012", min_font_size=5, colormap='Oranges',
max_font_size=70, font_path='/content/LEMONMILK-Medium.otf', max_words= 2000, width=1400, height=800,
collocations=True, mask = maskArray, stopwords = set(STOPWORDS)).generate(dataset)
# plot the WordCloud image
plt.figure(figsize = (6, 10), facecolor = None)
plt.imshow(cloud)
plt.axis("off")


practical 8: Write a program to process Text Summarization.

import nltk
nltk.download('all')
import nltk
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('maxent_ne_chunker')
nltk.download('words')

from nltk.tokenize import sent_tokenize, word_tokenize
dataset = open("/content/Indian Motorcycle.txt", encoding='cp1252').read()
dataset

def summarization(dataset):
result = []
for number, sentence in enumerate(sent_tokenize(dataset)):
number_tokens = len(word_tokenize(sentence))
tagged = nltk.pos_tag(word_tokenize(sentence))
number_nouns = len([word for word, pos in tagged if pos in ['NN', 'NNP']])
ners = nltk.ne_chunk(nltk.pos_tag(word_tokenize(sentence)), binary=False)
number_ners = len([chunk for chunk in ners if hasattr(chunk, 'label')])
score = (number_ners + number_nouns)/float(number_tokens)
result.append((number, score, sentence))
return result
summ = summarization(dataset)
summ

for i in sorted(summ, key=lambda x: x[1], reverse=True):
print(i[2])

























