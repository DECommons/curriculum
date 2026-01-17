# Contributing to Open Conduit

First off, thank you for considering contributing to this project! It's people like you that make the open-source community such an amazing place to learn, inspire, and create.

## How Can You Contribute?

### 1. Reporting Issues
Found a typo, a broken link, or a code example that doesn't compile?
* Open a **GitHub Issue**.
* Be specific about which module or lab is affected.
* If possible, include a screenshot or the error message.

### 2. Suggesting Enhancements
Have an idea for a new module or a better way to explain a concept?
* Open an Issue using the **"Feature Request"** label.
* Explain why this change would be useful to other learners.

### 3. Submitting Changes (Pull Requests)
We follow the standard "Fork & Pull" workflow:

1.  **Fork** the repository to your own GitHub account.
2.  **Clone** the project to your machine.
3.  **Create a Branch** for your specific change (e.g., `git checkout -b fix-typo-module-2`).
4.  **Commit** your changes with a clear message.
5.  **Push** to your fork and open a **Pull Request (PR)**.

## Local Development Setup

To preview your changes locally before submitting:

1.  Ensure you have Python installed.
2.  Install the dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3.  Run the local server:
    ```bash
    mkdocs serve
    ```
4.  Open your browser to `http://127.0.0.1:8000`.

## Style Guide

* **Markdown:** We use standard Markdown. Please ensure headers are properly nested.
* **Code Blocks:** Always specify the language for syntax highlighting (e.g., ```python).
* **Images:** Place images in the `docs/assets/images` folder and use relative paths.
* **Tone:** The curriculum is designed to be clear, concise, and professional.

## License Agreement

**Important:** By contributing to this repository, you agree that your contributions will be licensed under the project's licenses:

* **Text & Curriculum Content:** You agree your contributions may be used under the **CC-BY-NC-4.0** (Creative Commons Attribution-NonCommercial) license.
* **Code Samples & Labs:** You agree your code contributions may be used under the **MIT License**.

If you do not agree to these terms, please do not submit a Pull Request.

---
Thank you for helping us build better educational resources!