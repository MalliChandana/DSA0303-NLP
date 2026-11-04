# Input sentence
words = ["I", "am", "playing", "football"]

# Initial POS tags
tags = ["PRP", "NN", "NN", "NN"]

print("Initial Tags:")
print(list(zip(words, tags)))

# Apply transformation rules
for i in range(len(words)):

    # Rule 1: Words ending with 'ing' are verbs
    if words[i].endswith("ing"):
        tags[i] = "VBG"

    # Rule 2: Helping verbs
    elif words[i].lower() in ["am", "is", "are"]:
        tags[i] = "VBP"

    # Rule 3: Football is a noun
    elif words[i].lower() == "football":
        tags[i] = "NN"

# Display final tags
print("\nAfter Transformation:")

for word, tag in zip(words, tags):
    print(word, "\t", tag)
