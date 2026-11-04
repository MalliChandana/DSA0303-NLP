import nltk
from nltk import PCFG
from nltk.parse import ViterbiParser

# Define PCFG
grammar = PCFG.fromstring("""
S -> NP VP [1.0]
NP -> Det N [0.7] | N [0.3]
VP -> V NP [0.6] | V [0.4]
Det -> 'the' [0.6] | 'a' [0.4]
N -> 'boy' [0.3] | 'dog' [0.4] | 'cat' [0.3]
V -> 'saw' [0.6] | 'liked' [0.4]
""")

# Create Viterbi parser
parser = ViterbiParser(grammar)

# Input sentence
sentence = "the boy saw a dog".split()

# Parse sentence
print("Sentence:", " ".join(sentence))

for tree in parser.parse(sentence):
    print("\nMost Probable Parse Tree:")
    tree.pretty_print()
    print("Probability:", tree.prob())
