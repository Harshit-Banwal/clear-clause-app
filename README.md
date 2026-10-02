# Clear-Clause — AI-Powered Employment Agreement Analysis Platform

Clear-Clause is an AI-powered document analysis platform focused initially on **employment agreements**. It helps users identify potentially risky clauses and understand them through contextual AI-generated explanations.

The project combines **Angular, Java 21, Spring Boot, PostgreSQL with pgvector, FastAPI, Sentence Transformers, and Retrieval-Augmented Generation (RAG)** to analyze employment agreements using semantic retrieval and AI-generated insights.

> **Current Scope:** Clear-Clause currently supports **employment agreements only**. The long-term goal is to expand the platform to support a broader range of legal document types.

---

## 📌 Overview

Employment agreements often contain complex clauses related to compensation, termination, confidentiality, non-compete restrictions, intellectual property, notice periods, and other contractual obligations. Clear-Clause helps users analyze these clauses using semantic retrieval and AI-assisted analysis.

---

## 🎯 Current Scope

Clear-Clause is currently designed and optimized specifically for **employment agreements**.

The initial version intentionally focuses on a single document category so that the document processing, semantic retrieval, and RAG pipeline can be developed around a well-defined legal-document domain.

### Currently Supported

- Employment agreement upload
- Employment agreement processing
- Clause-level semantic retrieval
- Vector-based similarity search
- Identification of potentially risky clauses
- Contextual AI-generated explanations
- Document Summary with AI-generated.
- Document management
- User authentication and protected resources

### Future Vision

The long-term goal is to expand Clear-Clause beyond employment agreements and support multiple categories of legal documents, such as:

- Non-disclosure agreements (NDAs)
- Rental / lease agreements
- Service agreements
- Vendor agreements
- Partnership agreements
- Other commonly used legal documents

Support for additional document types will be introduced incrementally as the document-processing, retrieval, and analysis capabilities evolve.

---

## 📸 Screenshots

![Home Page](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/home.jpg?raw=true)

### Login

![Login](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/login.jpg?raw=true)

### Signup

![Sign up](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/signup.jpg?raw=true)

### Dashboard

![MyDoc page](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/mydoc.jpg?raw=true)

### Upload Employment Agreement

![Upload Document page](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/upload.jpg?raw=true)

### Document Analysis

![Document Analysis page](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/document1.jpg?raw=true)
![Document Analysis page](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/document2.jpg?raw=true)

---

## ✨ Key Features

### 🔐 Authentication & Security

- JWT-based stateless authentication
- Spring Security integration
- BCrypt password hashing
- Custom JWT authentication filter
- Protected REST APIs
- User-specific access to protected resources

### 📄 Employment Agreement Analysis

- Upload employment agreements
- Process agreement content
- Retrieve relevant clauses
- Analyze potentially risky clauses
- Generate contextual explanations using AI

### 🔍 Semantic Search

- Generate vector embeddings for document content
- Store embeddings using PostgreSQL and pgvector
- Perform semantic similarity search
- Retrieve relevant clauses based on meaning rather than only exact keywords

### 🤖 AI-Powered Analysis

- Retrieval-Augmented Generation (RAG) pipeline
- Context-aware employment agreement analysis
- AI-assisted identification of potentially risky clauses
- LLM-based explanations using retrieved agreement context

### 🧩 Service-Based Architecture

The application consists of multiple components:

- Angular frontend
- Spring Boot backend
- Dedicated FastAPI embedding service
- PostgreSQL database with pgvector
- OpenRouter-based LLM integration

---

## 🛠️ Tech Stack

### Frontend

- Angular
- TypeScript
- HTML5
- CSS3

### Backend

- Java 21
- Spring Boot
- Spring Security
- JWT
- REST APIs
- Maven

### Database

- PostgreSQL
- pgvector

### AI / RAG

- Python
- FastAPI
- Sentence Transformers
- `sentence-transformers/all-MiniLM-L6-v2`
- Vector embeddings
- Semantic similarity search
- OpenRouter API
- Retrieval-Augmented Generation (RAG)

### Development Tools

- Git
- GitHub
- Postman / Swagger / OpenAPI
- Eclipse IDE
- Visual Studio Code

---

## 🏗️ System Architecture

![System Achitecture Design](https://github.com/Harshit-Banwal/clear-clause-app/blob/main/assets/architecture.jpg?raw=true)

Clear-Clause is composed of three primary application components.

### 1. Angular Frontend

The Angular frontend provides the user interface for:

- User registration and login
- Employment agreement upload
- Document management
- Triggering document analysis
- Displaying analysis results

### 2. Spring Boot Backend

The Spring Boot application acts as the primary backend service and is responsible for:

- REST API development
- Authentication and authorization
- JWT processing
- User management
- Document management
- Database interaction
- Communication with the embedding service
- Semantic retrieval
- RAG workflow
- Communication with the LLM through OpenRouter

### 3. FastAPI Embedding Service

The FastAPI service handles embedding generation using a Sentence Transformers model.

Separating embedding generation into an independent service keeps the embedding workload isolated from the primary Spring Boot application and allows the model-serving component to evolve independently.

---

## 🔄 How Clear-Clause Works

The overall employment agreement analysis workflow is:

```text
User
 │
 ▼
Login / Authentication
 │
 ▼
Upload Employment Agreement
 │
 ▼
Spring Boot Backend
 │
 ▼
Document Processing
 │
 ▼
Text Extraction / Chunking
 │
 ▼
Embedding Generation
 │
 ▼
FastAPI Embedding Service
 │
 ▼
Store Embeddings
 │
 ▼
PostgreSQL + pgvector
 │
 ▼
Semantic Similarity Search
 │
 ▼
Retrieve Relevant Clauses
 │
 ▼
Construct RAG Context
 │
 ▼
OpenRouter LLM
 │
 ▼
AI-Generated Analysis
 │
 ▼
Angular Frontend
```

---

## 🧠 Retrieval-Augmented Generation (RAG) Pipeline

Clear-Clause uses a **Retrieval-Augmented Generation (RAG)** pipeline to provide contextual analysis of employment agreements.

### 1. Employment Agreement Upload

The user uploads an employment agreement through the Angular frontend.

The document is sent to the Spring Boot backend through a REST API.

### 2. Document Processing

The backend processes the uploaded agreement and extracts its textual content.

The content is divided into smaller chunks to make semantic retrieval more effective.

### 3. Embedding Generation

Document chunks are sent to the dedicated FastAPI embedding service.

The embedding service uses:

```text
sentence-transformers/all-MiniLM-L6-v2
```

to convert text into numerical vector representations.

### 4. Vector Storage

The generated embeddings are stored in PostgreSQL using the `pgvector` extension.

This allows the system to perform similarity searches over the agreement content.

### 5. Semantic Retrieval

When analysis is requested, the system performs semantic similarity search to retrieve the document sections most relevant to the analysis.

Unlike traditional keyword matching, semantic search allows conceptually similar text to be retrieved even when the wording differs.

### 6. Context Construction

The retrieved clauses are assembled into contextual information for the language model.

### 7. LLM Analysis

The relevant context is sent to an LLM through the OpenRouter API.

The model uses the retrieved employment-agreement context to generate the analysis.

### 8. Result

The Spring Boot backend returns the analysis to the Angular frontend, where the results are presented to the user.

### RAG Flow

```text
Employment Agreement
        │
        ▼
  Text Extraction
        │
        ▼
     Chunking
        │
        ▼
 Sentence Transformer
        │
        ▼
 Vector Embeddings
        │
        ▼
 PostgreSQL + pgvector
        │
        │ Semantic Search
        ▼
 Relevant Clauses
        │
        ▼
  Retrieved Context
        │
        ▼
   OpenRouter LLM
        │
        ▼
   AI Analysis
```

---

## 🔐 Authentication & Security

Clear-Clause uses **Spring Security with stateless JWT-based authentication**.

### Authentication Flow

```text
User Login
    │
    ▼
Authentication API
    │
    ▼
Validate Credentials
    │
    ▼
Generate JWT
    │
    ▼
Return Token
    │
    ▼
Client Sends JWT
    │
    │ Authorization: Bearer <JWT>
    ▼
JwtAuthFilter
    │
    ▼
Validate JWT
    │
    ▼
Extract User ID
    │
    ▼
SecurityContext
    │
    ▼
Protected Controller
```

### Security Implementation

- Spring Security
- Stateless session management
- JWT-based authentication
- BCrypt password hashing
- Custom `JwtAuthFilter`
- Protected REST endpoints
- Public authentication endpoints
- Public Swagger/OpenAPI endpoints

For authenticated requests, the JWT filter validates the token and extracts the user ID.

The authenticated user is then placed in Spring Security's `SecurityContext` for the current request.

---

## 🗄️ Database & Vector Search

Clear-Clause uses **PostgreSQL** as the primary relational database.

The application uses the **pgvector** extension to store and query vector embeddings generated from employment agreement content.

### Why Vector Search?

Traditional keyword search may fail when two pieces of text have similar meanings but use different words.

For example:

```text
"Employee cannot work for competing organizations."

vs.

"Employee is prohibited from joining a competitor."
```

Although the wording differs, the underlying concept is similar.

Vector embeddings allow the system to represent text semantically and retrieve relevant content based on similarity.

### Vector Search Flow

```text
Document Chunk
      │
      ▼
Embedding Model
      │
      ▼
Vector Representation
      │
      ▼
PostgreSQL + pgvector
      │
      ▼
Similarity Search
      │
      ▼
Relevant Agreement Context
```

This retrieval layer forms a core part of the application's RAG pipeline.

---

## 📁 Project Structure

```text
clear-clause-app/
│
├── eas_frontend/
│   └── Angular frontend application
│
├── eas_backend/
│   └── Spring Boot backend application
│
├── embedding-service/
│   └── FastAPI embedding service
│
├── assets/
│   ├── screenshots/
│   └── architecture/
│
└── README.md
```

---

## 📚 API Documentation

The Spring Boot backend exposes REST APIs documented using **OpenAPI/Swagger**.

The API is organized into the following categories:

### Authentication

- Registration
- Login

### Documents

- Upload
- Retrieve Summary
- List My Documents
- Retrieve Clauses

### AI Analysis

- Explain Risk
- Explain Clause

---

## ⚠️ Limitations

- The current version supports **employment agreements only**.
- AI-generated analysis may contain inaccurate or incomplete interpretations.
- Analysis quality depends on the quality and structure of the uploaded agreement.
- LLM responses may vary depending on the retrieved context and selected model.

---

## 🔮 Future Roadmap

The long-term goal of Clear-Clause is to evolve from an employment-agreement analysis platform into a broader legal-document analysis platform.

Planned improvements include:

### Document Coverage

- Add support for NDAs
- Add support for rental and lease agreements
- Add support for service agreements
- Add support for vendor agreements
- Add support for partnership agreements
- Gradually expand support to other legal document types

### AI / RAG Improvements

- Improve document chunking strategies
- Improve semantic retrieval quality
- Introduce document-type-specific retrieval strategies
- Improve risk categorization
- Add clause-level citations and source references
- Introduce automated RAG evaluation metrics
- Improve response grounding

### Engineering Improvements

- Increase automated test coverage
- Containerize services using Docker
- Introduce CI/CD automation
- Improve scalability of the embedding service
- Improve observability and logging
- Optimize document processing for larger agreements

---

> **Note:** Clear-Clause provides AI-assisted analysis for informational purposes and is not a substitute for professional legal advice.
