import nltk

# Download required resources
nltk.download('wordnet')
nltk.download('omw-1.4')
nltk.download('punkt_tab')

from nltk.wsd import lesk
from nltk.tokenize import word_tokenize

# Input sentence
sentence = "I deposited money in the bank"

# Ambiguous word
target_word = "bank"

# Tokenize sentence
words = word_tokenize(sentence)

# Apply Lesk algorithm
sense = lesk(words, target_word)

# Display result
print("Sentence:", sentence)
print("Target Word:", target_word)

if sense:
    print("Predicted Meaning:", sense.definition())
    print("Synset:", sense.name())
else:
    print("No meaning found")
