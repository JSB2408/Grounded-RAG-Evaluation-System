
# 📚 Citation-Grounded RAG Evaluation System

A Retrieval-Augmented Generation (RAG) system that retrieves technical documentation, generates citation-linked answers, validates responses, and handles questions when sufficient evidence is unavailable.

Built with **Python, FastAPI, BM25, and pytest**, this project explores reliable and traceable question answering over technical documents.

## 🚀 Features

- **Document Retrieval:** Retrieves relevant text chunks using BM25.
- **Citation-Grounded Answers:** Connects generated answers to retrieved evidence.
- **Evidence Validation:** Validates answer structure and citation references.
- **Insufficient-Evidence Handling:** Refuses to answer certain questions when usable evidence is unavailable.
- **Lexical Relevance Safeguard:** Uses a lightweight word-overlap heuristic to reject selected irrelevant matches.
- **Automated Testing:** Includes regression tests for retrieval, generation, validation, and API behavior.
- **Evaluation Pipeline:** Evaluates answer generation, evidence handling, citations, and end-to-end behavior.
- **REST API:** Exposes endpoints through FastAPI and interactive Swagger documentation.

## 🧠 How It Works

```text
User Question
     |
     v
Document Retrieval (BM25)
     |
     v
Retrieved Evidence Chunks
     |
     v
Lexical Relevance Safeguard
     |
     v
Answer Generation
     |
     v
Citation and Output Validation
     |
     v
Grounded Answer or Refusal
```

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| FastAPI | REST API |
| BM25 | Lexical document retrieval |
| FAISS / Dense Retrieval | Dense retrieval support, where configured |
| pytest | Automated testing |
| Pydantic | Structured data validation |
| Uvicorn | API server |

## 📂 Project Structure

```text
citation-grounded-rag/
├── src/
│   └── rag_mvp/
│       ├── bm25.py
│       ├── generator.py
│       ├── answer_validation.py
│       ├── service.py
│       └── ...
├── tests/
│   ├── test_bm25.py
│   ├── test_generator.py
│   ├── test_service.py
│   ├── test_evaluator.py
│   └── ...
├── README.md
├── requirements.txt
└── ...
```

*Note: The structure above highlights the main modules. Refer to the repository for the complete file structure.*

## ⚙️ Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Replace the repository URL with your actual GitHub repository URL.

### 2. Create a Virtual Environment

**Windows (PowerShell):**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Run the Tests

```bash
python -m pytest -q
```

The test suite checks key behaviors across retrieval, answer generation, citation validation, and API services.

## ▶️ Running the API

Start the application using the command supported by your project configuration. For the configured `rag-api` command, run:

```bash
rag-api
```

Then open the interactive API documentation:

```text
http://127.0.0.1:8000/docs
```

If the command is unavailable in your environment, check the project's entry-point configuration and installation instructions.

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Checks whether the service is running |
| GET | `/ready` | Checks service readiness |
| POST | `/v1/retrieve` | Retrieves evidence for a question |
| POST | `/v1/answer` | Generates an answer using retrieved evidence |

Use Swagger UI at `/docs` to inspect request schemas and try the endpoints.

## 💬 Example

**Question:**

```text
What is the capital of Mars?
```

**Expected behavior:**

```text
Insufficient evidence in the provided context.
```

The system should avoid generating an unsupported answer when its evidence and relevance checks do not justify one.

**Relevant question:**

```text
What does gradient accumulation do?
```

The system can return an answer based on relevant retrieved technical documentation, with citations when supported by the configured pipeline.

## 🛡️ Relevance and Evidence Handling

Traditional lexical retrieval can return text that shares words with a question without actually answering it.

To address selected cases, this project includes a lightweight lexical relevance safeguard that checks for overlap between question terms and retrieved evidence.

This safeguard is intentionally simple. It is **not a semantic relevance model** and does not guarantee that every answer is factually supported. A future version could incorporate cross-encoder reranking, semantic relevance evaluation, and claim-level entailment checking.

## 🧪 Testing and Evaluation

Run the automated test suite:

```bash
python -m pytest -q
```

The tests cover areas such as:

- BM25 retrieval behavior
- Answer generation
- Citation and output validation
- Insufficient-evidence handling
- API service behavior
- Evaluation logic
- Regression cases for irrelevant evidence

The repository also includes evaluation workflows for measuring retrieval and answer quality. Refer to the evaluation configuration and results for the exact dataset, metrics, and scores.

## 📊 Key Learnings

Through this project, I explored:

- How RAG combines document retrieval with language generation.
- Why lexical relevance does not necessarily mean semantic relevance.
- Why citations alone do not prove that an answer is supported.
- How to handle questions with insufficient evidence.
- How automated tests can catch regressions in RAG pipelines.
- How to evaluate RAG behavior beyond simply checking whether an answer was generated.

## 🔮 Future Improvements

- Implement semantic reranking.
- Add claim-level evidence verification.
- Improve cross-document reasoning and synthesis.
- Expand the evaluation dataset with difficult negative examples.
- Add retrieval precision and recall metrics.
- Add latency, token usage, and cost tracking.
- Improve production monitoring, security, and scalability.

## ⚠️ Limitations

- The lexical relevance safeguard relies on word overlap and can miss valid paraphrases.
- Relevant-looking words do not guarantee that retrieved evidence supports an answer.
- Cross-document synthesis and complex reasoning require further evaluation.
- Performance depends on the corpus, retrieval configuration, and generation profile.
- This project is an experimental RAG system, not a fully production-hardened service.

## 👨‍💻 Author

**Your Name**


## 👨‍💻 Author

**Jasmeet Singh Bhatia**

- GitHub: [JSB2408](https://github.com/JSB2408)
- LinkedIn: [Jasmeet Singh Bhatia](https://www.linkedin.com/in/jasmeet-singh-bhatia-4a3b74353/)


Replace the placeholders with your actual profile details.



Please retain appropriate attribution and comply with the original repository's license. Clearly distinguish your own modifications from the original implementation.
