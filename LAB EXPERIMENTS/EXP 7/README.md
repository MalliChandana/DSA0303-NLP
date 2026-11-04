import nltk

# Download required resources
nltk.download('punkt_tab')
nltk.download('averaged_perceptron_tagger_eng')

# Input sentence
text = "The smart student is learning Python quickly."

# Tokenization
words = nltk.word_tokenize(text)

# POS tagging
tags = nltk.pos_tag(words)

# Display result
print("Word\tPOS Tag")

for word, tag in tags:
    print(word, "\t", tag)
