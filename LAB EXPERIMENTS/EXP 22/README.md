
# Reference Resolution using spaCy

import spacy

# Load English NLP model
!python -m spacy download en_core_web_sm

nlp = spacy.load("en_core_web_sm")

# Input text
text = "Ravi bought a laptop. He uses it every day."

# Process the text
doc = nlp(text)

print("Original Text:")
print(text)

print("\nReference Resolution:")

# Identify pronouns and their possible references
for token in doc:
    if token.pos_ == "PRON":
        reference = "Unknown"

        if token.text.lower() == "he":
            reference = "Ravi"
        elif token.text.lower() == "it":
            reference = "laptop"

        print(token.text, "->", reference)
