import nltk
from nltk import CFG
from nltk.parse import ChartParser

# Define grammar
grammar = CFG.fromstring("""
S -> NP VP
NP -> Det N
VP -> V NP
Det -> 'a' | 'the'
N -> 'girl' | 'boy' | 'dog'
V -> 'saw' | 'liked'
""")

# Create parser
parser = ChartParser(grammar)

# Input sentence
sentence = "a girl saw the dog".split()

# Generate parse tree
print("Sentence:", " ".join(sentence))

for tree in parser.parse(sentence):
    print("\nParse Tree:")
    tree.pretty_print()
