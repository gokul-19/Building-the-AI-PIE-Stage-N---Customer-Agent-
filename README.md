# 🧠 AI PIE – RAG-Based Feature Specification Generator

## 📌 Overview

AI PIE is a Retrieval-Augmented Generation (RAG) system designed to generate **grounded technical feature specifications** from user feature requests.

The system retrieves relevant context from:

* **Code Lane** (implementation details)
* **Decision Lane** (design reasoning)

It then generates a structured specification while ensuring **high faithfulness and precision**, evaluated using a **RAGAS-style evaluation pipeline**.

---

## 🚀 Key Features

* 🔍 Context-aware retrieval using vector search (Qdrant)
* 🧾 Structured specification generation using LLM (Gemini/OpenAI)
* 🎯 Grounded output (no hallucination)
* 📊 Automatic evaluation using RAGAS-style metrics:

  * Faithfulness
  * Precision
  * Recall
* ✅ Designed to pass strict evaluation thresholds

---

## 🏗️ System Architecture

```
Feature Request
      ↓
Embedding (query)
      ↓
Vector DB (Qdrant)
      ↓
Retrieve Top-K Context
      ↓
LLM Generation (Grounded Spec)
      ↓
Post-processing (Grounding Filter)
      ↓
Evaluation (RAGAS-style)
```

---

## ⚙️ Components

### 1. Embedding

* Converts text into vector representations
* Used for similarity search

### 2. Retrieval

* Uses Qdrant vector database
* Retrieves relevant chunks from:

  * Code Lane
  * Decision Lane

### 3. Generation

* Uses LLM to generate structured JSON output:

  * Edge Cases
  * Risk Reports
* Strictly grounded in retrieved context

### 4. Grounding Filter

* Removes hallucinated or weak claims
* Ensures high precision

### 5. Evaluation

* RAGAS-style scoring:

  * Faithfulness
  * Precision
  * Recall
  * Pass/Fail decision

---

## 📂 Project Structure

```
.
├──EVALUTION
|--INPUT 
│--OUTPUT
├── notebook.ipynb
├── README.md
```

---

## 🧪 How It Works

### Step 1: Index Data

* Chunk code and decision documents
* Store in Qdrant with embeddings

### Step 2: Retrieve Context

```python
code_hits, decision_hits = retrieve(query, top_k=6)
```

### Step 3: Generate Spec

```python
spec = generate_spec(query, code_hits, decision_hits)
```

### Step 4: Filter Grounded Claims

```python
spec = filter_grounded(spec, code_hits, decision_hits)
```

### Step 5: Evaluate

```python
evaluate(spec)
```

---

## 📊 Evaluation Metrics

| Metric       | Description                          |
| ------------ | ------------------------------------ |
| Faithfulness | Output aligns with retrieved context |
| Precision    | % of claims that are grounded        |
| Recall       | Coverage of relevant information     |
| FPR          | False positive rate                  |

✅ **Pass Criteria:**

* High precision & faithfulness
* Low false positive rate

---

## 🔒 Design Principles

* ❌ No hallucination
* ✅ Context-only generation
* ✅ Structured outputs
* ✅ Deterministic evaluation

---

## ⚠️ Challenges Faced

* API changes (Qdrant, Gemini)
* Handling hallucinated outputs
* Ensuring claim-level grounding
* Improving precision in RAG evaluation

---

## ✅ Final Outcome

* Successfully built a **robust RAG pipeline**
* Achieved **passing evaluation scores**
* Generated **reliable, grounded specifications**

---

## 📌 Future Improvements

* Switch to OpenAI unified pipeline
* Improve retrieval ranking
* Add semantic reranking
* Expand evaluation metrics

---

## 🙌 Acknowledgements

* Qdrant (Vector DB)
* Google Gemini 
* RAGAS (Evaluation inspiration)

---

## 📬 Contact

Gokul
📧 Email: [gorthigokul77@gmail.com](mailto:gorthigokul77@gmail.com)
