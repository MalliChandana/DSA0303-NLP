!pip install spacy

# Download English language model
!python -m spacy download en_core_web_sm

import spacy

# Load English model
nlp = spacy.load("en_core_web_sm")

# Input text
text = "Sundar Pichai is the CEO of Google. Google is located in California."

# Process text
doc = nlp(text)

# Display named entities
print("Named Entities:")

for ent in doc.ents:
    print(ent.text, "->", ent.label_)
