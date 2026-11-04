# Finite State Automaton

def fsa(string):
    state = 0

    for ch in string:
        if ch == 'a':
            if state == 0 or state == 1:
                state = 1
            else:
                state = 1

        elif ch == 'b':
            if state == 1:
                state = 2
            else:
                state = 0

        else:
            return False

    return state == 2


# Test strings
strings = ["ab", "aab", "bab", "abab", "aba", "abb", "abc"]

for s in strings:
    if fsa(s):
        print(s, "-> Accepted")
    else:
        print(s, "-> Rejected")
