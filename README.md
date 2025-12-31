# Open Data Engineering Academy

> **From "Hello World" to Database Internals.**
> A comparative deep dive into SQL, Internals, and Performance Tuning using PostgreSQL (Row-Oriented) and DuckDB (Column-Oriented).

## 🏗️ Architecture
This repository is a **Monorepo** containing both the curriculum (Textbook) and the environment (Lab).

* **The Lab:** A Dockerized JupyterLab environment with JupySQL, Postgres 15, and DuckDB pre-wired.
* **The Textbook:** A local website built with MkDocs that explains the theory while you code.

---

## 🚀 Quick Start

### 1. Prerequisites
* [Docker Desktop](https://www.docker.com/products/docker-desktop/) (For the Lab)
* [Python 3.10+](https://www.python.org/downloads/) (For the Textbook)

### 2. Configure Secrets
Copy the example environment file. You can leave the defaults for local learning.
```bash
cp .env.example .env
```

## 🧪 Track 1: The Lab (Write Code)
This spins up your "Workstation." It includes a Postgres database (OLTP) and a Jupyter environment with DuckDB (OLAP).
1. Start the Engine:
```Bash
docker-compose up -d
```
2. Enter the Lab:
    - Open your browser to: http://localhost:8888
    - Password: dataengineer (or check your .env file)
3. Start Coding:
    - Open notebooks/00_Start_Here.ipynb.
    - Run the cells to generate the 1-Million Row datasets needed for the advanced modules.


## 📚 Track 2: The Textbook (Read Theory)
We use MkDocs to serve the curriculum locally. This gives you a beautiful, dark-mode enabled textbook running right alongside your code.
1. Create a Virtual Environment (One time only):
```Bash
python3 -m venv .venv
source .venv/bin/activate  # Windows: .\.venv\Scripts\Activate
```
2. Install Dependencies:
```Bash
pip install -r requirements.txt
```
3. Serve the Book:
```Bash
mkdocs serve
```
4. Read:
    - Open your browser to: http://localhost:8000

## 🛠️ Troubleshooting
"Port 5432 is already in use" You likely have a local Postgres instance running on your laptop. Stop it, or modify docker-compose.yml to map to a different port (e.g., "5433:5432").

"Magic %sql not found" Make sure you ran the initialization cell at the top of the notebook. It loads the jupysql extension.

"MkDocs command not found" Ensure your virtual environment is active. Your terminal prompt should start with (.venv).
