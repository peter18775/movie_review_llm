🎬 Movie Recommendation System

    A hybrid movie recommendation engine that supports semantic search, factual search, and intelligent natural-language question answering using movie summaries and pandas-driven analysis.

    This project integrates:

    Semantic Retrieval → Find movies relevant to a natural-language query.

    Factual Query Engine → Convert user questions into executable pandas code.

    Natural-Language Answering → Provide human-friendly answers and suggested movie titles.

🚀 Features

🔍 1. Semantic Query Answering

    Ask any open-ended question such as:

    "Movies where the hero sacrifices himself"
    "Films similar to Interstellar"

    The system:

    Retrieves the top-k most relevant summaries.

    Generates a high-quality natural-language answer.

    Returns a list of related movie titles.

📊 2. Factual Query Answering

    Ask data-driven questions such as:

    "What is the average rating of all movies?"
    "How many movies were released after 2010?"

    The system:

    Translates the question into pandas code

    Safely executes the code

    Returns a clean natural-language answer

🧠 3. Query Classification

    Determines whether a user question is:

    Semantic (meaning-based)

    Factual (data-based)

🧩 How the System Works

1️⃣ Semantic Retrieval

Uses embeddings to locate the top-k most semantically similar movie summaries.

docs = retrieve_semantic(question, k=5)
context = "\n".join(docs['Summary'].tolist())

2️⃣ LLM-Generated Answer

Injects the retrieved summaries into the LLM prompt:

prompt = f"""
Use the movie summaries below to answer the question.
Do NOT mention the context or how you got the answer.

Summaries:
{context}

Question: {question}
Answer:
"""

3️⃣ Factual Code Generation

The model converts questions into pandas code:

code = generate_pandas_code(question)
result = safe_execute(code)


Examples:

"df['Rating'].mean()"

"df[df['Year'] > 2010].shape[0]"

4️⃣ Unified Answer Flow
def answer(query):
    qtype = classify_query(query)
    if qtype == "semantic":
        return answer_semantic_query(query)
    if qtype == "factual":
        return answer_factual_query(query)

▶️ How to Run
1. Install Requirements
pip install -r requirements.txt