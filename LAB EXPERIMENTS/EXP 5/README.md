import nltk
from nltk.stem import PorterStemmer

# Create Porter Stemmer
ps = PorterStemmer()

# Input words
words = ["playing", "played", "plays",
         "running", "studies", "happiness"]

print("Original Word\tStemmed Word")

for word in words:
    print(word, "\t\t", ps.stem(word))
