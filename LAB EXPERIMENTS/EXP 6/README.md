import random
from collections import defaultdict

# Training text
text = "I love machine learning. I love Python. Python is easy. I love coding."

# Convert text into words
words = text.lower().replace(".", "").split()

# Create bigram model
bigram = defaultdict(list)

for i in range(len(words) - 1):
    bigram[words[i]].append(words[i + 1])

# Generate text
current_word = "i"
generated = [current_word]

for i in range(10):

    next_words = bigram.get(current_word)

    if not next_words:
        break

    current_word = random.choice(next_words)
    generated.append(current_word)

print("Generated Text:")
print(" ".join(generated))
