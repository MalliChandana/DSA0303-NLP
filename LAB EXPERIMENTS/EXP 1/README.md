import re

# Input text
text = "My email is student@gmail.com and my number is 9876543210"

# Search for email
email = re.search(r'[\w.-]+@[\w.-]+\.\w+', text)

# Search for mobile number
number = re.search(r'\d{10}', text)

# Find all words
words = re.findall(r'\b[A-Za-z]+\b', text)

# Display results
print("Original Text:", text)

if email:
    print("Email Found:", email.group())

if number:
    print("Mobile Number:", number.group())

print("Words:", words)

# Replace email with hidden text
new_text = re.sub(r'[\w.-]+@[\w.-]+\.\w+', 'EMAIL HIDDEN', text)

print("Modified Text:", new_text)
