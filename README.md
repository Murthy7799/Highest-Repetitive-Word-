# Highest-Repetitive-Word-
#It will check the highest repetitive words from a given file.
import collections
mail=open("F:\\Murthy\\mail.txt","r").read()
#print(mail)
words=mail.split()
len_Mail=len(mail)
#print(len_Mail)
#print(words)
num_lines=mail.count('\n')
#print(num_words)

d = {}
for w in words:
    if w in d:
        d[w] += 1
    else:
        d[w] = 1

num_words = sum(d[w] for w in d)
lst = [(d[w],w) for w in d]
lst.sort()
lst.reverse()

import nltk
from nltk.corpus import stopwords #here we have imported an natural language processor tool kit package for stop words
from nltk.tokenize import wordpunct_tokenize
#nltk.download()

stop_words=set(stopwords.words('english')) #here we used set to make the search faster
print([word for word in lst if word not in stop_words])

print("Number of characters in mail = "+str(len_Mail))
print("Number of lines in mail = "+str(num_lines))
print("Number of words in mail = "+str(num_words))

print("\n The 10 most frequent words are \n")

i = 1

for count,word in lst[:10]:
    print('%2s.%4s %s' %(i,count,word))
    i+=1
