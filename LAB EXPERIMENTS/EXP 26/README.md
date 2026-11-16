!pip install transformers sentencepiece -q

from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

# Load English to French translation model and tokenizer directly
model_name = "Helsinki-NLP/opus-mt-en-fr"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSeq2SeqLM.from_pretrained(model_name)

# Input English text
text = "Hello, how are you? I am learning Python."

# Tokenize and translate into French
tokenized_text = tokenizer(text, return_tensors="pt")
translation_ids = model.generate(**tokenized_text)
result = tokenizer.batch_decode(translation_ids, skip_special_tokens=True)[0]

# Display output
print("English Text:", text)
print("French Translation:", result)
