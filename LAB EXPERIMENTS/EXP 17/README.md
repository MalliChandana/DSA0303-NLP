import nltk

# Download WordNet resources
nltk.download('wordnet')
nltk.download('omw-1.4')

from nltk.corpus import wordnet

# Input word
word = "bank"

# Retrieve synsets
synsets = wordnet.synsets(word)

print("Word:", word)
print("\nSynsets and Meanings:")

for syn in synsets:
    print("\nSynset:", syn.name())
    print("Meaning:", syn.definition())
    print("Examples:", syn.examples())

    # Display synonyms
    synonyms = []
    for lemma in syn.lemmas():
        synonyms.append(lemma.name())

    print("Synonyms:", synonyms)
