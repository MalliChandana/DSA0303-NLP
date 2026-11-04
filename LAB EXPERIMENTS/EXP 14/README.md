import nltk
from nltk import CFG
from nltk.parse import ChartParser

# Define grammar with agreement rules
grammar = CFG.fromstring("""
S -> NP_SG VP_SG
S -> NP_PL VP_PL

NP_SG -> Det_SG N_SG
NP_PL -> Det_PL N_PL

VP_SG -> V_SG
VP_PL -> V_PL

Det_SG -> 'the'
Det_PL -> 'the'

N_SG -> 'boy' | 'girl' | 'student'
N_PL -> 'boys' | 'girls' | 'students'

V_SG -> 'runs' | 'plays' | 'studies'
V_PL -> 'run' | 'play' | 'study'
""")

parser = ChartParser(grammar)

# Test sentences
sentences = [
    "the boy runs",
    "the boys run",
    "the boy run",
    "the girls plays"
]

for sentence in sentences:
    words = sentence.split()
    parses = list(parser.parse(words))

    if parses:
        print(sentence, "-> Correct Agreement")
    else:
        print(sentence, "-> Incorrect Agreement")
