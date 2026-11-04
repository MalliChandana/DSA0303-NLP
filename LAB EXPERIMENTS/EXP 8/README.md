# Training data
training_data = [
    ("I", "PRP"),
    ("love", "VBP"),
    ("Python", "NNP"),
    ("students", "NNS"),
    ("learn", "VBP"),
    ("quickly", "RB"),
    ("good", "JJ"),
    ("coding", "NN")
]

# Calculate word-tag probabilities
word_tag = {}

for word, tag in training_data:
    word_tag[word.lower()] = tag

# Input sentence
sentence = "I love Python quickly"

words = sentence.split()

# Assign POS tags
print("Word\tPOS Tag")

for word in words:
    tag = word_tag.get(word.lower(), "NN")
    print(word, "\t", tag)
