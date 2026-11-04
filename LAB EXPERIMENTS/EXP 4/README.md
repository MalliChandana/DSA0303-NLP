# Finite State Machine for plural formation

def plural(noun):

    if noun.endswith(('s', 'sh', 'ch', 'x', 'z')):
        return noun + "es"

    elif noun.endswith('y') and noun[-2] not in "aeiou":
        return noun[:-1] + "ies"

    else:
        return noun + "s"


# Input nouns
nouns = ["cat", "dog", "bus", "box", "baby", "dish"]

print("Singular\tPlural")

for noun in nouns:
    print(noun, "\t\t", plural(noun))
