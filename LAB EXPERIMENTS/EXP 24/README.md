
# Dialog Act Recognition using Python

import re

# Input conversation
dialog = [
    "Hello, how are you?",
    "I am fine, thank you.",
    "Can you help me with Python?",
    "Sure, I can help you.",
    "Thank you!",
    "Goodbye!"
]

# Function to recognize dialog acts
def recognize_dialog_act(sentence):
    text = sentence.lower()

    if re.search(r'\b(hello|hi|hey)\b', text):
        return "Greeting"

    elif re.search(r'\b(how are you|what|where|when|why|who|can you|could you)\b', text):
        return "Question / Request"

    elif re.search(r'\b(thank you|thanks)\b', text):
        return "Thanking"

    elif re.search(r'\b(goodbye|bye|see you)\b', text):
        return "Farewell"

    elif re.search(r'\b(sure|yes|okay|of course)\b', text):
        return "Agreement"

    else:
        return "Statement"

# Display results
print("Dialog Act Recognition\n")

for sentence in dialog:
    act = recognize_dialog_act(sentence)
    print("Sentence:", sentence)
    print("Dialog Act:", act)
    print()

