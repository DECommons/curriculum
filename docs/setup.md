# Environment Setup

The Open Conduit curriculum is designed to be **reproducible**. To achieve this, we rely on containerization rather than asking you to install dozens of tools directly on your machine.

Before starting any module, you must ensure your host machine is configured correctly.

## 1. Operating System Requirements
This curriculum assumes a **Unix-like environment**.

* **macOS:** Fully supported (Terminal).
* **Linux:** Fully supported (Bash/Zsh).
* **Windows:** You **must** use [WSL2 (Windows Subsystem for Linux)](https://learn.microsoft.com/en-us/windows/wsl/install).
    * *Note: We do not support PowerShell or Command Prompt for these labs.*

## 2. Install Docker
We use Docker to package the specific databases, tools, and languages required for each course. This ensures that if it runs on our machine, it runs on yours.

1.  **Download & Install:** [Get Docker Desktop](https://www.docker.com/products/docker-desktop/) (or Docker Engine for Linux).
2.  **Verify Installation:**
    Open your terminal and run:
    ```bash
    docker --version
    ```
    *If you use Windows WSL2, ensure Docker Desktop is configured to use the WSL2 backend.*

## 3. Kaggle API Key
We use real-world datasets for our labs. Many of our automated ingestion scripts verify your identity and pull data directly from Kaggle.

1.  Log in to [Kaggle](https://www.kaggle.com/).
2.  Go to your **Account Settings**.
3.  Scroll to the **API** section and click **"Create New Token"**.
4.  This will download a `kaggle.json` file.
5.  **Save this file.** You will need to provide this key (or its values) to the lab environments to authorize data downloads.

## 4. Course Styles & The Lab Repository
We do not host code in the documentation. Instead, we split our curriculum into two distinct styles:

### "Theory" Modules
Courses focused on architecture and concepts (e.g., *Dimensional Modeling*) are text-based.
* **Requirement:** No special environment needed.
* **Goal:** To build your mental model of data systems.

### "Practical" Modules
Courses focused on implementation (e.g., *Structured Query Language*) are hands-on. These modules require you to run code against actual databases.
* **Requirement:** A dedicated Docker environment.
* **Goal:** To build muscle memory with the tools.

### How to use the Practical Labs
All exercises and Docker environments are located in our dedicated repository:

**[Click here to view the Labs Repository](https://github.com/OpenConduit/labs)**

**The Workflow:**

1.  **Clone the Repository** (Do this once):
    ```bash
    git clone [https://github.com/OpenConduit/labs.git](https://github.com/OpenConduit/labs.git)
    cd labs
    ```

2.  **Navigate to the Course Module**:
    Find the folder matching your module (e.g., `databases-and-sql`).
    ```bash
    cd databases-and-sql
    ```

3.  **Build the Environment**:
    Inside the module folder, you will find a `Dockerfile` tailored to that specific topic.
    ```bash
    # Example build command
    docker-compose up --build

    # To rerun the lab environment (without rebuilding it)
    docker-compose up
    ```

4.  **Run the Lab**:
    Specific instructions on how to run the container (and how to pass in your Kaggle credentials) are provided in the `README.md` inside each module's folder.