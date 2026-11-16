
# Text Coherence Evaluation using Python

import nltk
from nltk.tokenize import sent_tokenize, word_tokenize
from nltk.corpus import stopwords

# Download required resources
nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('stopwords')

# Input text
text = """
Ravi is a college student.
He studies computer science.
He learns Python programming.
Python is useful for developing applications.
"""

# Split text into sentences
sentences = sent_tokenize(text)

# Load stopwords
stop_words = set(stopwords.words('english'))

# Extract important words from each sentence
sentence_words = []

for sentence in sentences:
    words = word_tokenize(sentence.lower())
    words = {word for word in words
             if word.isalpha() and word not in stop_words}
    sentence_words.append(words)

# Calculate similarity between consecutive sentences
similarities = []

for i in range(len(sentence_words) - 1):
    common = sentence_words[i].intersection(sentence_words[i + 1])
    total = sentence_words[i].union(sentence_words[i + 1])

    if len(total) == 0:
        score = 0
    else:
        score = len(common) / len(total)

    similarities.append(score)

# Calculate coherence score
if similarities:
    coherence = sum(similarities) / len(similarities)
else:
    coherence = 0

print("Number of Sentences:", len(sentences))
print("\nCoherence Score:", round(coherence, 2))

if coherence >= 0.2:
    print("Text Coherence: Good")
else:
    print("Text Coherence: Low")

