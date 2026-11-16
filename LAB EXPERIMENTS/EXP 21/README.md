
# Syntax-Driven Semantic Analysis
# Extract noun phrases and their meanings

import nltk
import spacy

# Download required NLTK resources
nltk.download('punkt')

# Load English NLP model
!python -m spacy download en_core_web_sm

nlp = spacy.load("en_core_web_sm")

# Input sentence
sentence = "The intelligent student developed a useful software application."

# Process the sentence
doc = nlp(sentence)

print("Original Sentence:")
print(sentence)

print("\nNoun Phrases and Their Meanings:")

# Extract noun phrases
for chunk in doc.noun_chunks:
    print("\nNoun Phrase:", chunk.text)

    # Extract meaning using root word and its grammatical role
    print("Main Noun:", chunk.root.text)
    print("Meaning:", chunk.root.lemma_)

    # Display grammatical structure
    print("Structure:", chunk.root.pos_)

