import nltk

from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer

# Download WordNet
nltk.download('wordnet')
nltk.download('omw-1.4')

# Create objects
stemmer = PorterStemmer()
lemmatizer = WordNetLemmatizer()

# Input words
words = ["playing", "studies", "running",
         "happiness", "cars", "better"]

print("Word\t\tStem\t\tLemma")

for word in words:
    stem = stemmer.stem(word)
    lemma = lemmatizer.lemmatize(word)
    print(word, "\t\t", stem, "\t\t", lemma)
