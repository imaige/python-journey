# AI Engineering Foundations

## Course Context

The AI Engineering course has started. The current material introduces the LLM engineering landscape, local model execution, the course roadmap, and the development environment used for the upcoming labs.

The AI course workflow is different from the Python workflow: course transcripts are explained first, then understanding is checked with questions, and GitHub notes are updated when the user asks.

## Large Language Models (LLMs)

An LLM is a large language model trained to work with natural language. It receives text input and generates text output based on learned language patterns.

Examples of LLM use cases include question answering, tutoring, coding assistance, summarization, conversational applications, and commercial AI products.

## Cloud LLM vs Local LLM

A cloud-hosted model runs on remote infrastructure, while a local LLM is downloaded and executed on the user's own computer. Local execution uses local CPU/GPU and RAM/VRAM resources.

## Ollama

Ollama is a tool used to download, run, and interact with supported language models locally. Ollama is not itself the LLM.

```bash
ollama run MODEL_NAME
```

## Model Size and Parameters

Model sizes may be written as `270M`, `3B`, or `20B`, representing millions or billions of learned parameters. Larger models generally require more compute and memory, but the biggest model is not automatically the best model for every task.

## LLM Applications and Roles

An LLM can be instructed to behave according to a role and goal, such as acting as a beginner Spanish tutor. This illustrates the transition from simply using an LLM to building an application around an LLM.

## Reasoning / Thinking Models

Some models are optimized to spend more computation on multi-step reasoning for tasks such as planning, calculations, technical analysis, and structured problem solving.

## Eight-Week LLM Engineering Roadmap

```text
Week 1  → Foundations
Week 2  → Frontier Models
Week 3  → Open Models
Week 4  → Model Selection
Week 5  → RAG
Week 6  → Fine-Tuning a Frontier Model
Week 7  → Fine-Tuning an Open Model
Week 8  → Agentic AI
```

## Frontier Models and Open Models

A frontier model is at or near the leading edge of current AI capability. Open models can often be downloaded and run on local or self-managed infrastructure.

## RAG and Fine-Tuning

RAG retrieves relevant external information at request time and provides it to the model as context. Fine-tuning further trains a model on additional examples or data. They are different techniques.

## Agentic AI

Agentic systems can move beyond a single prompt-response interaction by planning, using tools, inspecting results, and choosing subsequent actions.

## AI Engineering Course Tracks

The curriculum introduced AI Builder, AI Coder, AI Leader, AI Engineer Core Track, AI Engineer Agentic Track, and AI Engineer Production Track.

## AI Engineering Tooling Introduced

Future tools mentioned include Hugging Face, Gradio, LangChain, Weights & Biases, and Modal. These have only been introduced by name so far.

## Development Environment

The development environment includes the project files, Git repository, IDE/editor, Python environment, dependencies, API keys, and environment variables.

## Git Clone and Project Root

`git clone` creates a local copy of a Git repository, including project files and Git metadata. The project root is the top-level directory containing the complete project.

## Cursor and Explorer

Cursor is the editor recommended by the course, although other IDEs can be used. If repository files are not visible in Cursor, `View → Explorer` opens the Explorer panel.

## Markdown and README Preview

The course repository contains `README.md` and guides locally after cloning. Markdown is a lightweight formatted-text syntax used by `.md` files.

In Cursor, a Markdown file can be opened normally to see its source syntax or opened with `Open Preview` to see the rendered formatting. Because the repository was cloned, the README and guides can be read locally without returning to the GitHub website for each instruction.

## Cursor Integrated Terminal

Cursor includes an integrated terminal. The course demonstrates opening it with:

```text
Ctrl + `
```

Multiple terminals can be opened. This lets project commands run directly inside the editor while the current working directory is the project.

## Dependency

A dependency is an external package required by a project. Examples in an AI/Python project may include packages such as `openai`, `pandas`, `transformers`, or `gradio`.

## Virtual Environment

A virtual environment is an isolated Python environment for one project. It prevents different projects from unnecessarily sharing and conflicting over the same installed package versions.

```text
Project A → environment A
Project B → environment B
```

In this course, the project environment is created in a `.venv` directory.

## `uv`

The course uses `uv` to manage the Python environment and project dependencies. It replaces the Anaconda-based setup used in an earlier version of the course.

```text
Project requirements
        ↓
       uv
        ↓
Python environment + dependencies
```

### Check `uv`

```bash
uv --version
```

This checks whether `uv` is installed and available to the current terminal. After installing `uv`, a new terminal may need to be opened so environment/PATH changes are picked up.

### Update `uv`

```bash
uv self update
```

This updates `uv` itself.

### Synchronize the Project Environment

```bash
uv sync
```

`uv sync` synchronizes the project's environment with its dependencies and configuration. The project-specific `.venv` virtual environment is created and required packages are installed/downloaded as needed.

```text
dependency → package the project needs
virtual environment → isolated environment for the project
.venv → directory containing that environment
uv → tool managing the environment and dependencies
uv sync → command that builds/synchronizes the environment
```

## Step 3 — OpenAI API and API Key

ChatGPT and the OpenAI API are not the same product interface. ChatGPT is an end-user application, while the API lets software communicate programmatically with OpenAI models.

```text
Python application
       ↓
OpenAI API
       ↓
Model
       ↓
Response
```

An API is an interface that allows software systems to communicate. An API key is a secret credential used by an application to authenticate with an API service and associate requests with the relevant account/project.

API keys must be treated as secrets. They should not be shared publicly, hard-coded into source code, or committed to GitHub.

## Step 4 — `.env` and Secret Management

A `.env` file is used to keep secret/configuration values separate from application source code. For this project it belongs in the project root.

```env
OPENAI_API_KEY=your_secret_key
```

The exact variable name matters because application code later looks up that specific name. The key principle is:

```text
code != secret
```

## Step 5 — Cursor Extensions and Jupyter Setup

The final environment setup step prepares Cursor to work with Python and Jupyter notebooks.

### Python Extension

A Python extension is installed in Cursor so the editor can properly support Python code, including syntax highlighting and code checking. The course notes that either the Cursor/Anysphere Python extension or Microsoft's Python extension can be used.

### Jupyter Extension

The Jupyter extension is also installed. It enables interactive Jupyter notebook support inside Cursor.

After installation, the Explorer is reopened and the first notebook is opened from the Week 1 directory:

```text
week1/day1.ipynb
```

### Jupyter Notebook (`.ipynb`)

A Jupyter Notebook is an interactive document that can contain both formatted explanatory text and executable code.

```text
Notebook
├── text / explanation
├── code cell
├── output
├── more text
└── another code cell
```

Notebook files use the `.ipynb` extension. The course also refers to these notebooks as labs.

### Cell

A notebook is divided into individual sections called cells. Code cells can be executed separately instead of running the entire document at once. This makes experimentation and incremental learning easier.

### Kernel

The kernel is the Python process running behind the notebook and executing its code.

```text
Jupyter Notebook
       ↓
     Kernel
       ↓
Python executes code
       ↓
     Output
```

### Selecting the Project Environment as the Kernel

The notebook must use the Python environment created for this project. In Cursor:

```text
Select Kernel
      ↓
Python Environments
      ↓
.venv / recommended project Python
```

The selected environment should point to the project's `.venv` Python installation. This connects the environment created earlier by `uv sync` with the Jupyter notebook:

```text
uv sync
   ↓
.venv
   ↓
project Python + dependencies
   ↓
Jupyter kernel selection
   ↓
Notebook runs inside that environment
```

If the expected `.venv` environment does not appear as a kernel option, the course directs students to the troubleshooting notebook in the `setup` folder.

## How the Labs Are Intended to Be Used

The notebooks are designed as interactive learning documents rather than material to copy mechanically. The recommended workflow is to read the explanations, run the code, add print statements, modify examples, experiment, and create variations.

The course notebooks are living documents and may be updated over time with newer models, explanations, and material.

## First LLM Project — Web Page Summarizer

With the setup complete, the first LLM project begins. The goal is to build a small application that accepts a web address/URL, retrieves or scrapes the web page, sends relevant content to an underlying GPT model through an API call, and displays a formatted summary.

Conceptual flow:

```text
URL
 ↓
Retrieve/scrape web page
 ↓
Extract relevant content
 ↓
Python application
 ↓
OpenAI API
 ↓
GPT model
 ↓
Generated summary
 ↓
Formatted result
```

This is the first point where the environment setup components begin working together in a real LLM application.

## Running Notebook Cells

A Jupyter code cell is executed with:

```text
Shift + Enter
```

If imports fail or the cell appears stuck, the first thing to verify is that the notebook kernel points to the local project `.venv` Python environment.

## Loading `.env` and Reading the API Key

The notebook loads the project's `.env` file and reads the `OPENAI_API_KEY` environment variable. This is the practical use of the secret-management setup completed earlier.

```text
.env
 ↓
OPENAI_API_KEY
 ↓
Python notebook
 ↓
OpenAI API
```

If the key is not found, likely checks include the `.env` filename and location, the exact variable name, whether the file was saved, and whether the notebook is running from the expected project environment.

## OpenAI Message Structure — List of Dictionaries

The course introduces the message structure expected by the Chat Completions API. A simple user message is represented as a Python list containing a dictionary:

```python
message = "Hello GPT, this is my first ever message to you. Hi."

messages = [
    {
        "role": "user",
        "content": message
    }
]
```

This connects Python fundamentals directly to LLM Engineering:

```text
messages → list
    ↓
item → dictionary
    ↓
role/content → keys
user/message → values
```

## First LLM API Call from Python

The course creates an OpenAI client object and makes the first request to a cloud GPT model using the Chat Completions API. The exact syntax will be revisited later, so the important idea at this stage is the flow:

```text
Prepare message
      ↓
Put it into OpenAI message format
      ↓
Send API request
      ↓
Cloud model processes it
      ↓
Receive response
      ↓
Read response content in Python
```

This is the first real LLM call executed directly from Python code rather than through the ChatGPT product interface.

## Web Scraping Before AI

The course provides a helper function called `fetch_website_contents()` in `scraper.py`. It uses BeautifulSoup to perform a simple server-side fetch/scrape of a web page.

Important distinction:

```text
web scraping
→ retrieves website content
→ not AI by itself
```

AI becomes involved when the extracted website content is later sent to the LLM for summarization.

## System Prompt and User Prompt

Two prompt roles are introduced.

### System Prompt

The system prompt defines the overall behavior, task, context, tone, or response format expected from the model.

Example intent:

```text
You analyze website contents.
Provide a short summary.
Ignore navigation-related text.
Respond in Markdown.
```

A useful mental model is:

```text
system prompt
→ Who are you?
→ What is your overall task?
→ How should you behave/respond?
```

### User Prompt

The user prompt is the concrete request from the end user that the model should answer within the framework established by the system prompt.

```text
user prompt
→ What do I want you to do right now?
```

## Multiple Messages — System + User

The message list can contain multiple dictionaries, each with its own role and content:

```python
messages = [
    {
        "role": "system",
        "content": system_prompt
    },
    {
        "role": "user",
        "content": user_prompt
    }
]
```

Conceptually:

```text
messages = list
│
├── dictionary 1
│   ├── role → system
│   └── content → system prompt
│
└── dictionary 2
    ├── role → user
    └── content → user prompt
```

## Why the System Prompt Matters

The course demonstrates that the same user question can produce different tone and behavior when the system prompt changes.

```text
Same user prompt
       +
Different system prompt
       ↓
Different tone / character / behavior
```

For example, changing the system instruction from a helpful assistant to a snarky assistant changes the style of the answer while the user's question stays the same.

This introduces a core prompting principle: the system message frames the model's mission and behavior, while the user message provides the immediate task.

## Troubleshooting Principles

The course emphasizes a documentation-first workflow: check the project README/setup documentation and troubleshooting guides, analyze the actual error, and use LLM assistance carefully while verifying suggestions before applying them.

## Current Course Status

```text
Environment setup                                      ✅
First notebook and .venv kernel                        ✅
.env loaded and API key detected                       ✅
First cloud LLM API call from Python                   ✅
Web scraping helper introduced                         ✅
System prompt vs user prompt introduced                ✅
Web Page Summarizer implementation                     in progress
```

The course is now inside the first hands-on LLM project and is moving from environment setup into prompt construction and web-page summarization logic.
