from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Documents
documents = [
    "Machine learning is a part of artificial intelligence",
    "Python is used for machine learning",
    "Natural language processing deals with text",
    "Artificial intelligence is changing technology",
    "Python is a popular programming language"
]

# Create TF-IDF vectorizer
vectorizer = TfidfVectorizer()

# Convert documents into TF-IDF vectors
tfidf_matrix = vectorizer.fit_transform(documents)

# User search query
query = "Python machine learning"

# Convert query into TF-IDF vector
query_vector = vectorizer.transform([query])

# Calculate cosine similarity
similarity = cosine_similarity(query_vector, tfidf_matrix)

# Rank documents
ranked_indices = similarity.flatten().argsort()[::-1]

# Display ranked results
print("Search Query:", query)
print("\nRanked Documents:")

for rank, index in enumerate(ranked_indices, start=1):
    print("\nRank:", rank)
    print("Document:", documents[index])
    print("Similarity Score:", round(similarity[0][index], 4))
