import nltk
from nltk.tag import RegexpTagger

# Download tokenizer
nltk.download('punkt_tab')

# Define tagging rules
patterns = [
    (r'.*ing$', 'VBG'),
    (r'.*ed$', 'VBD'),
    (r'.*ly$', 'RB'),
    (r'.*ous$', 'JJ'),
    (r'.*ness$', 'NN'),
    (r'I|You|He|She', 'PRP'),
    (r'.*', 'NN')
]

# Create tagger
tagger = RegexpTagger(patterns)

# Input sentence
text = "I am learning quickly"

# Tokenization
words = nltk.word_tokenize(text)

# Apply tagging
tags = tagger.tag(words)

# Display results
print("Word\tPOS Tag")

for word, tag in tags:
    print(word, "\t", tag)
