# LexRAG
### Enterprise Legal Assistant using Hierarchical Parent-Child Retrieval-Augmented Generation(RAG)

An enterprise-grade Legal AI Assistant designed for university student affairs regulations.

The system transforms complex legal and administrative documents into a structured knowledge base and provides accurate, grounded, and explainable answers through an advanced Hierarchical Parent-Child Retrieval-Augmented Generation (RAG) architecture.

Developed as a graduation project at Tafila Technical University (TTU), this solution addresses one of the major limitations of traditional RAG systems: **context fragmentation in hierarchical legal documents**.

---

# 🚀 Project Overview

University regulations are typically distributed across lengthy PDF documents and administrative manuals.

Traditional keyword search systems struggle to understand:

* Legal terminology
* Hierarchical article structures
* Context dependencies
* Semantic relationships

To solve this challenge, Legal_TTU introduces a complete legal intelligence pipeline that:

1. Extracts metadata from legal documents using LLMs.
2. Converts unstructured regulations into structured JSON trees.
3. Preserves legal hierarchy through Parent-Child Retrieval.
4. Retrieves complete legal articles instead of fragmented chunks.
5. Generates grounded legal answers with source attribution.

---

# 🏗️ System Architecture

```text
Raw Legal Documents
        │
        ▼
Metadata Extraction (LLM)
        │
        ▼
YAML Frontmatter Injection
        │
        ▼
Legal Structure Parser
        │
        ▼
JSON Tree Generation
        │
        ▼
Parent Documents
        │
        ├─────────────► Local Document Store
        │
        ▼
Child Chunk Generation
        │
        ▼
Multilingual E5 Embeddings
        │
        ▼
Chroma Vector Database
        │
        ▼
ParentDocumentRetriever
        │
        ▼
Groq LLM
        │
        ▼
Grounded Legal Response
```

---

# 🧠 Key Innovation

## Hierarchical Parent-Child Retrieval

Most traditional RAG systems split documents into fixed-size chunks.

This causes critical problems in legal documents:

* Loss of article hierarchy
* Context fragmentation
* Semantic dilution
* Incomplete legal reasoning

Legal_TTU solves this using LangChain's ParentDocumentRetriever.

### Retrieval Process

**Child Documents**

* Small semantic chunks
* Embedded using multilingual E5
* Indexed in ChromaDB

**Parent Documents**

* Complete legal articles
* Stored separately in Document Store

When a relevant child chunk is retrieved:

```text
Child Chunk Match
        │
        ▼
Parent Article Lookup
        │
        ▼
Full Legal Context Returned
```

This ensures that the LLM receives the entire legal article rather than a partial fragment.

---

# 🔍 Data Engineering Pipeline

## Metadata Extraction

Each legal document is processed through:

* Groq API
* Llama 3.3 70B Versatile

Extracted metadata includes:

```yaml
document_type:
document_title:
issuing_authority:
document_year:
effective_date:
```

The metadata is automatically injected into the document using YAML Frontmatter.

---

## Legal Structure Parsing

A custom Python parser was developed to:

* Detect legal hierarchy
* Normalize numbering
* Extract articles
* Preserve legal relationships

Output:

```json
{
  "chapter": {},
  "section": {},
  "article": {}
}
```

This transforms unstructured regulations into machine-readable legal trees.

---

# 🤖 Retrieval-Augmented Generation (RAG)

### Embedding Model

```python
intfloat/multilingual-e5-large
```

Features:

* Arabic semantic understanding
* Multilingual support
* High retrieval accuracy
* Optimized for legal content

---

### Vector Database

```python
ChromaDB
```

Used for:

* Semantic search
* Similarity retrieval
* Persistent vector storage

---

### Document Store

```python
LocalFileStore
```

Stores complete parent articles used during context reconstruction.

---

# 🛡️ Hallucination Prevention

The assistant operates under strict legal guardrails.

Rules include:

* Answer only from retrieved regulations.
* Never invent legal articles.
* Explicitly state when information is unavailable.
* Reference the regulation source whenever possible.
* Maintain formal legal language.

This significantly improves factual reliability and trustworthiness.

---

# 🌍 Arabic-First User Experience

The application includes:

* Full Right-To-Left (RTL) support
* Arabic legal terminology handling
* Interactive Gradio interface
* Student-friendly conversational experience

---

# 📊 Evaluation

The system was evaluated using multiple legal query scenarios:

### Level 1 — Direct Retrieval

Examples:

* Student disciplinary penalties
* Committee responsibilities
* Administrative procedures

✅ Passed

---

### Level 2 — Context Synthesis

Examples:

* Multi-article reasoning
* Regulation interpretation
* Policy explanation

✅ Passed

---

### Level 3 — Complex Legal Reasoning

Examples:

* Multi-hop legal questions
* Compound disciplinary cases
* Procedural dependencies

✅ Passed

---

# 🛠️ Technologies Used

## AI & LLMs

* Groq API
* Llama 3.3 70B Versatile
* Retrieval-Augmented Generation (RAG)

## NLP

* Sentence Transformers
* Multilingual E5 Large

## Data Engineering

* JSON Tree Parsing
* YAML Metadata Injection
* Legal Document Structuring

## Vector Search

* ChromaDB
* ParentDocumentRetriever

## Backend

* Python
* LangChain

## Interface

* Gradio
* RTL Custom Styling

---

# 📈 Technical Highlights

* Built a complete legal AI pipeline from scratch.
* Engineered a hierarchical Parent-Child retrieval architecture.
* Designed automated metadata extraction workflows.
* Developed custom legal document parsers.
* Implemented dual-storage retrieval systems.
* Reduced legal context fragmentation during retrieval.
* Delivered grounded and explainable legal responses.
* Created an Arabic-first conversational legal assistant.

---

# 🎯 Skills Demonstrated

* Retrieval-Augmented Generation (RAG)
* LLM Application Development
* Prompt Engineering
* Vector Databases
* NLP Engineering
* Data Engineering
* Semantic Search
* Information Retrieval
* Knowledge Base Construction
* Legal AI Systems
* LangChain Ecosystem
* Production-Oriented AI Architecture

---

# 👨‍💻 Author

**Hassan Al-Omari**

Artificial Intelligence & Data Science Student

Tafila Technical University

Jordan

---

# 📄 Academic Project

Developed as part of the Special Topics Project course at Tafila Technical University (2025/2026).
