import re

# Tokenize logical expression
def tokenize(expression):
    pattern = r'forall|exists|AND|OR|NOT|[A-Za-z_]\w*|[(),.]'
    return re.findall(pattern, expression)

# Simple FOPC parser
def parse(tokens):
    position = 0

    def expression():
        nonlocal position

        if position >= len(tokens):
            raise ValueError("Incomplete expression")

        token = tokens[position]

        # Negation
        if token == "NOT":
            position += 1
            return ("NOT", expression())

        # Quantifiers
        if token in ["forall", "exists"]:
            quantifier = token
            position += 1
            variable = tokens[position]
            position += 1

            if position < len(tokens) and tokens[position] == ".":
                position += 1

            return (quantifier, variable, expression())

        # Parentheses
        if token == "(":
            position += 1
            result = expression()

            if position >= len(tokens) or tokens[position] != ")":
                raise ValueError("Missing closing parenthesis")

            position += 1
            return result

        # Predicate
        name = token
        position += 1

        if position >= len(tokens) or tokens[position] != "(":
            raise ValueError("Expected '(' after predicate")

        position += 1
        arguments = []

        while position < len(tokens) and tokens[position] != ")":
            if tokens[position] != ",":
                arguments.append(tokens[position])
            position += 1

        if position >= len(tokens):
            raise ValueError("Missing closing parenthesis")

        position += 1
        return (name, arguments)

    result = expression()

    if position != len(tokens):
        raise ValueError("Unexpected extra tokens")

    return result

# Input expression
text = "forall x. Human(x)"

# Parse expression
tokens = tokenize(text)

print("Input Expression:", text)
print("Tokens:", tokens)

try:
    result = parse(tokens)
    print("Parsed Expression:", result)
except ValueError as e:
    print("Invalid Expression:", e)
