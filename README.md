
# The CSMVS Advanced RAG

## 0. Overview

The Chhatrapati Shivaji Maharaj Vastu Sangrahalaya, (CSMVS) Advanced RAG Q&A System is a cutting-edge platform designed to provide accurate, context-aware information about Chhatrapati Shivaji Maharaj Vastu Sangrahalaya, (CSMVS). This system leverages a comprehensive knowledge base in combination with Large Language Models (LLMs) to offer users an interactive and informative experience.

## 1. Live project
**CSMVS Advanced RAG Q&A System**: [http://xx.xx.xx.xx:xxxx/](http://xx.xx.xx.xx:xxxx/)

## 2. Dataset

### Dataset Details
- **Name:** ZacJQ/CSMVS-Museum-Img-QA
- **Source:** https://huggingface.co/datasets/ZacJQ/CSMVS-Museum-Img-QA
- **Language:** English


## 3. Technologies Used

### Mage
- Manages and orchestrates data pipelines and workflows.
- Automates data processing, transformation, and loading tasks.
- Enhances the system's scalability and maintainability.

### Elastic Search
- Used for performing vector search on the knowledge base.
- Retrieved results are used to build prompts and context for the LLM.
- Stores questions and answers from the knowledge.csv file in both text and vector formats.

### PostgreSQL
- Stores user questions, assistant answers, and user feedback.
- Database tables are created automatically on first application start.

### Streamlit
- Provides the user interface (UI) for the Q&A system.
- Allows users to input questions and receive answers.
- Includes feedback mechanism (Thumbs Up/Down buttons).

### OpenAI GPT
- LLM used for generating responses based on retrieved context.
- Used for advanced technique rewriting user query.
- Used for evaluation LLM-as-a-judge

### Grafana
- Used for system monitoring and analytics.
- Provides a dashboard to track metrics such as user feedback and LLM cost.

### Docker
- Each component of the application runs in a separate Docker container.
- Containers are started in a specific order to ensure proper system initialization.


## 4. Reproducibility

### Step 1: System Preparation
- Make sure you have installed [Docker](https://docs.docker.com/engine/install/), [Docker Compose](https://docs.docker.com/compose/install/) and [Git](https://git-scm.com/downloads).
### Step 2: Clone the github repository
```
git clone https://github.com/bilozorov/rag.git
```
### Step 3: Update your OPENAI_API_KEY
```
cd rag
cp .env.dev .env
rm .env.dev
nano .env
```

### Step 4: Start all services
```
docker compose up
```

### Step 5: Profit!
**That's it!** Everything will happen automatically:
- **Mage**, **Elasticsearch** and **Postgres** will be running.
- After that **Grafana** will be launched with automatic connection to the database and dashboard creation.
- When all services are started and checks are passed, a pipeline **populate_elasticsearch** will be automatically started in **Mage** for data processing and **Elasticsearch** population.
- The next step will be to automatically generate synthetic user queries and load them into **Postgres** for display in **Grafana** dashboards.
- After all services are started and all automatic triggers are initiated, the user interface will be launched using **Streamlit**.

### Urls for local deployment
- **Mage**: [http://localhost:6789/](http://localhost:6789/)
- **Grafana**: [http://localhost:3000/](http://localhost:3000/)
- **Streamlit**: [http://localhost:8501/](http://localhost:8501/)

### Urls for live deployment example:
- **Streamlit**: [http://xx.xx.xx.xx:xxxx/](http://xx.xx.xx.xx:xxxx/)