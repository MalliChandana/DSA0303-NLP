import nltk

from nltk import CFG
from nltk.parse import RecursiveDescentParser

# Define grammar
grammar = CFG.fromstring("""
S -> NP VP
NP -> Det N
VP -> V NP
Det -> 'the' | 'a'
N -> 'boy' | 'dog' | 'cat'
V -> 'saw' | 'liked'
""")

# Create parser
parser = RecursiveDescentParser(grammar)

# Input sentence
sentence = "the boy saw a dog".split()

# Parse sentence
print("Input Sentence:", " ".join(sentence))

for tree in parser.parse(sentence):
    print("Parse Tree:")
    tree.pretty_print()
