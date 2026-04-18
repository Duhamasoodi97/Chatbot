# 🤖 SQL AI Agent using LangChain & Google PaLM

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![LangChain](https://img.shields.io/badge/LangChain-Agent-orange)
![LLM](https://img.shields.io/badge/LLM-Google%20PaLM-green)
![Database](https://img.shields.io/badge/Database-MS%20SQL%20Server-lightgrey)

An intelligent AI-powered system that converts **natural language queries into optimized Microsoft SQL queries** and retrieves results from a connected database.

---

## 📌 Overview

This project showcases how to build a **production-style AI data assistant** that:

* Understands user questions in plain English
* Translates them into SQL queries
* Executes queries on a **Microsoft SQL Server database**
* Returns accurate, context-aware results

Designed with scalability and real-world enterprise use cases in mind.

---

## 🏗️ Architecture Diagram

```
+-------------------+
|   User Query      |
| ("List analysts") |
+--------+----------+
         |
         v
+------------------------+
|   LangChain Agent      |
| (Reasoning + Planning) |
+--------+---------------+
         |
         v
+------------------------+
|   Google PaLM (LLM)    |
| Natural Language فهم   |
+--------+---------------+
         |
         v
+------------------------+
|  SQL Query Generator   |
| (Prompt + Toolkit)     |
+--------+---------------+
         |
         v
+------------------------+
|   SQL Database (MSSQL) |
|   64+ Tables           |
+--------+---------------+
         |
         v
+------------------------+
|   Query Results        |
+------------------------+
         |
         v
+------------------------+
|   Final Answer Output  |
+------------------------+
```

---

## ⚙️ Tech Stack

* **LangChain** – Agent orchestration
* **Google PaLM API** – Large Language Model
* **SQLAlchemy** – Database connectivity
* **Microsoft SQL Server** – Data storage
* **Python** – Core language

---

## 📂 Project Structure

```
project/
│
├── main.py              # Core implementation
├── config.py            # API keys & DB config (recommended)
├── requirements.txt     # Dependencies
└── README.md            # Documentation
```

---

## 🚀 Getting Started

### 🔧 Prerequisites

* Python 3.8+
* Google PaLM API Key
* SQL Server with ODBC Driver 18

---

### 📦 Installation

```bash
pip install langchain sqlalchemy pyodbc chromadb sentence-transformers
```

---

## 🔑 Configuration

### 1. LLM Setup

```python
from langchain.llms import GooglePalm

llm = GooglePalm(
    google_api_key="YOUR_API_KEY",
    temperature=0.2
)
```

---

### 2. Database Connection

```python
from sqlalchemy import create_engine

connection_string = (
    'mssql+pyodbc:///?odbc_connect='
    'DRIVER={ODBC Driver 18 for SQL Server};'
    'SERVER=YOUR_SERVER;'
    'DATABASE=YOUR_DB;'
    'UID=YOUR_USER;'
    'PWD=YOUR_PASSWORD;'
)

engine = create_engine(connection_string)
```

---

## 🧠 Prompt Engineering

Custom prompt ensures:

* ✅ Microsoft SQL syntax (NOT MySQL)
* ✅ Intelligent joins across 64+ tables
* ✅ Context-aware query generation

---

## 🤖 Agent Setup

```python
from langchain.agents import create_sql_agent
from langchain.agents.agent_toolkits import SQLDatabaseToolkit
from langchain.agents.agent_types import AgentType

toolkit = SQLDatabaseToolkit(db=db, llm=llm)

agent = create_sql_agent(
    llm=llm,
    toolkit=toolkit,
    agent_type=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)
```

---

## ▶️ Usage

```python
agent.run("List all regulatory authorities")
```

---

## 💬 Example Queries

* List regulatory authorities
* Regulations in the United Kingdom
* Show analysts
* Regulations applicable to India
* Controls related to risk
* Segments containing "risk"

---

## 📸 Screenshots (Add Yours)

> Replace with actual screenshots from your project

### 🔹 Example Query Execution

```
Input: "List analysts"
Output: SELECT * FROM analysts;
```

### 🔹 Terminal Output

```
> Running SQL Query...
> Fetching results...
> Returning structured response
```

---

## ✨ Key Features

* 🧠 Natural Language → SQL conversion
* ⚡ Handles complex joins automatically
* 📊 Works with large enterprise databases
* 🔍 Context-aware query reasoning
* 🔄 Extensible agent architecture

---

## 📊 Why This Project Stands Out (Recruiter Section)

* Demonstrates **LLM + real database integration**
* Uses **agent-based reasoning (LangChain)**
* Applies **prompt engineering in production context**
* Shows **understanding of SQL + AI systems design**
* Easily extendable to **chatbots / BI tools / dashboards**

---

## 📈 Future Enhancements

* 🌐 Streamlit / React frontend
* 🧾 Query history & logging
* ⚡ Caching layer (Redis)
* 🔐 Role-based access control
* 📊 Visualization dashboards

---

## ⚠️ Best Practices

* Never expose API keys publicly
* Validate generated SQL in production
* Use environment variables for secrets

---

## 🤝 Contributing

1. Fork the repo
2. Create a new branch
3. Commit changes
4. Submit a Pull Request

---

## 📄 License

MIT License

---

## 👤 Author

**Your Name**

---

## ⭐ Show Your Support

If you found this project useful:

👉 Star the repo
👉 Share it
👉 Build on top of it

---

🚀 *This project is a strong example of combining AI + data engineering for real-world applications.*
