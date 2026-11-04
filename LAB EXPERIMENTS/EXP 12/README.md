import nltk

from nltk import CFG
from nltk.parse import EarleyChartParser

# Define grammar
grammar = CFG.fromstring("""
S -> NP VP
NP -> Det N
VP -> V NP
Det -> 'the' | 'a'
N -> 'boy' | 'dog' | 'cat'
V -> 'saw' | 'liked'
""")

# Create Earley parser
parser = EarleyChartParser(grammar)

# Input sentence
sentence = "the boy saw a dog".split()

# Parse sentence
print("Input Sentence:", " ".join(sentence))

parses = list(parser.parse(sentence))

if parses:
    print("Sentence is grammatically valid")
    for tree in parses:
        print(tree)
else:
    print("Sentence is not grammatically valid")
