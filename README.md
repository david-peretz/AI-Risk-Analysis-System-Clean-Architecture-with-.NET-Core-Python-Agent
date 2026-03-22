# AI Risk Analysis System

### Clean Architecture with .NET Core + Python AI Agent

---

## 🚀 Overview

This project demonstrates a **production-oriented AI-powered Risk Decision System** built using:

* **.NET Core (Clean Architecture)** for orchestration and business logic
* **Python AI Service** for statistical analysis and AI reasoning
* **LangChain Agent** for dynamic decision orchestration
* **Statistical tools (Pandas / NumPy)** for deterministic computations

The system analyzes customer data and returns a **risk score + business decision** (Approve / Review / Reject).

---

## 🎯 Key Features

* ✅ Clean Architecture (Domain-driven design)
* ✅ AI Agent orchestration (tool-based reasoning)
* ✅ Deterministic statistical calculations
* ✅ Business decision layer (not just AI output)
* ✅ Guardrails to prevent invalid AI responses
* ✅ Retry & resilience for external AI calls
* ✅ Scalable microservice-ready design

---

## 🧠 Architecture

```
Client
   │
   ▼
.NET Core API
   │
   ▼
Application Layer (Use Cases)
   │
   ▼
Domain Layer (Business Rules)
   │
   ▼
Infrastructure Layer
   │
   ├── Python AI Service
   ├── Caching (Redis-ready)
   └── Messaging (Queue-ready)
        │
        ▼
LangChain Agent
        │
        ▼
Statistical Tools (Pandas / NumPy)
```

---

## 🏗️ Project Structure

### .NET Core

```
src/
 ├── Domain/
 │     ├── Entities/
 │     ├── Enums/
 │     └── Rules/
 │
 ├── Application/
 │     ├── Interfaces/
 │     ├── Services/
 │     └── UseCases/
 │
 ├── Infrastructure/
 │     ├── AiClient/
 │     ├── Caching/
 │     └── Messaging/
 │
 └── API/
       ├── Controllers/
       └── DTOs/
```

---

### Python AI Service

```
python-service/
 ├── api/
 ├── agents/
 ├── tools/
 ├── services/
 └── models/
```

---

## 🔍 How It Works

1. Client sends customer data
2. .NET Core API validates input
3. Application layer orchestrates the use case
4. Infrastructure calls Python AI service
5. AI Agent decides which statistical tools to execute
6. Tools perform deterministic calculations
7. Result returns with:

   * Risk Score
   * Decision
   * Explanation

---

## 📊 Example Input

```json
{
  "age": 45,
  "claims": 3,
  "amount": 12000
}
```

---

## 📈 Example Output

```json
{
  "score": 0.68,
  "decision": "Review",
  "reason": "Moderate claim frequency with high claim amount"
}
```

---

## 🧠 AI Design Principles

### 1. Separation of Concerns

* AI handles **reasoning**
* Python tools handle **calculations**
* .NET handles **business logic**

---

### 2. Deterministic Business Rules

AI does NOT make final decisions.

```
Score > 0.7   → Reject  
0.4 – 0.7     → Review  
< 0.4         → Approve  
```

---

### 3. Guardrails

* Input validation before AI
* Output validation after AI
* Prevents hallucinations and invalid responses

---

### 4. Tool-Based Architecture

The AI Agent dynamically selects tools such as:

* Risk scoring
* Anomaly detection
* Trend analysis

---

## ⚙️ Technologies

### Backend

* .NET Core Web API
* Dependency Injection
* Clean Architecture

### AI Service

* Python
* LangChain
* Pandas / NumPy

### Infrastructure (Planned / Extendable)

* Redis (caching)
* RabbitMQ / Service Bus (async processing)

---

## 🚀 Running the Project

### 1. Run Python AI Service

```bash
cd python-service
pip install -r requirements.txt
uvicorn main:app --reload
```

---

### 2. Run .NET API

```bash
cd src/API
dotnet run
```

---

### 3. Test Endpoint

```
POST /api/risk
```

---

## 📌 Design Decisions

### Why separate AI service?

* Independent scaling
* Isolated failures
* Better control over latency and cost

---

### Why not let AI decide everything?

To ensure:

* Deterministic outcomes
* Regulatory compliance (important in insurance/finance)
* Explainability

---

### Why LangChain?

To enable:

* Tool orchestration
* Dynamic reasoning
* Extensible AI workflows

---

## 🔮 Future Improvements

* Add real ML models (not only statistical rules)
* Introduce feedback loop for continuous learning
* Implement full async pipeline with message queue
* Add observability (metrics, tracing, dashboards)
* Integrate real insurance datasets

---

## 🧠 What This Project Demonstrates

* Full-stack system design with AI integration
* Clean Architecture principles in real-world use
* AI as an orchestrator, not a black box
* Production-oriented thinking (scalability, reliability, control)

---

## 💬 Interview Talking Point

> "The system separates AI reasoning from deterministic business rules to maintain control, reliability, and explainability — especially critical in risk-based domains like insurance."

---

## 👨‍💻 Author

David Peretz

---

## 📄 License

MIT
