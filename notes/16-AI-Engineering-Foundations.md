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

The basic flow is:

```text
Python application
       ↓
OpenAI API
       ↓
Model
       ↓
Response
```

### API

An API is an interface that allows software systems to communicate. In this course, our Python application will use an API to send requests to a model service and receive responses.

### API Key

An API key is a secret credential used by an application to authenticate with an API service and associate requests with the relevant account/project.

```text
Python application
       ↓
API key
       ↓
OpenAI API
       ↓
Model
```

API keys must be treated as secrets. They should not be shared publicly, hard-coded into source code, or committed to GitHub.

## Step 4 — `.env` and Secret Management

A `.env` file is used to keep secret/configuration values separate from application source code.

For this project it belongs in the project root:

```text
llm_engineering/
├── week1/
├── week2/
├── README.md
└── .env
```

The filename must be `.env`, not `.env.txt` or another variation.

### `OPENAI_API_KEY`

The OpenAI API key is stored using an environment-variable name:

```env
OPENAI_API_KEY=your_secret_key
```

Here:

```text
OPENAI_API_KEY → variable name
your_secret_key → secret value
```

The exact variable name matters because application code later looks up that specific name.

### Why Secrets Stay Outside Source Code

Hard-coding a credential like this is unsafe:

```python
api_key = "real-secret-key"
```

If the source code is pushed to a repository, the secret may be exposed. The safer design is:

```text
.env
 │
 └── OPENAI_API_KEY=secret
          ↓
     Python application
          ↓
       OpenAI API
          ↓
         Model
```

The key principle is:

```text
code != secret
```

The `.env` file also needs to be saved after editing so the value exists on disk for the application to read.

## Troubleshooting Principles

The course emphasizes a documentation-first workflow: check the project README/setup documentation and troubleshooting guides, analyze the actual error, and use LLM assistance carefully while verifying suggestions before applying them.

## Setup Progress

```text
Step 1 → Git + clone repository + Cursor + project root       ✅
Step 2 → Markdown/README + Cursor terminal + uv + .venv      ✅
Step 3 → OpenAI API + API key                                ✅
Step 4 → .env + OPENAI_API_KEY + secret management           ✅
Step 5 → final editor/Jupyter setup                           next
```

The course is currently ready to continue with Step 5.
