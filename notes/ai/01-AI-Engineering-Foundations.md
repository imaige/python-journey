# AI Engineering Foundations

## Course Context

This repository tracks the AI/LLM Engineering course from foundations toward production-oriented AI systems. The learning workflow is explanation first, then practical experimentation, then GitHub documentation after the topic is understood.

## Large Language Models (LLMs)

An LLM is a large language model trained to work with natural language. It receives text input and generates text output based on learned language patterns.

Typical use cases include:

- question answering
- tutoring
- coding assistance
- summarization
- conversational applications
- commercial AI products

## Cloud LLM vs Local LLM

A cloud LLM runs on remote infrastructure and is accessed over an API. A local LLM runs on the user's own computer and uses local CPU/GPU and RAM/VRAM resources.

```text
Cloud LLM
Python → Internet/API → Remote model → Response

Local LLM
Python → localhost → Local model → Response
```

## Ollama

Ollama is a tool for downloading, running, and interacting with supported language models locally. Ollama is not itself the model.

```bash
ollama run MODEL_NAME
```

A local model can also be exposed through Ollama's local HTTP API.

## Model Size and Parameters

Model sizes may be written as `270M`, `3B`, or `20B`, representing millions or billions of learned parameters. Larger models usually require more compute and memory, but the biggest model is not automatically the best model for every task.

## Frontier Models and Open Models

A frontier model is at or near the leading edge of current AI capability. Open models can often be downloaded and run locally or on self-managed infrastructure.

## Reasoning / Thinking Models

Some models are optimized to spend more computation on multi-step reasoning for planning, calculations, technical analysis, and structured problem solving.

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

## RAG and Fine-Tuning

RAG retrieves relevant external information at request time and provides it to the model as context. Fine-tuning further trains a model on additional examples or data. They solve different problems and are not interchangeable concepts.

## Agentic AI

Agentic systems can move beyond a single prompt-response interaction by planning, using tools, inspecting results, and choosing subsequent actions.

## AI Engineering Course Tracks and Tooling

The course introduced AI Builder, AI Coder, AI Leader, AI Engineer Core Track, AI Engineer Agentic Track, and AI Engineer Production Track.

Future tooling introduced by name includes Hugging Face, Gradio, LangChain, Weights & Biases, and Modal.

# Development Environment

A working AI project depends on more than source code. The environment includes:

- project files
- Git repository
- IDE/editor
- Python environment
- dependencies
- API keys
- environment variables
- notebook kernel

## Git Clone and Project Root

`git clone` creates a local copy of a Git repository, including its project files and Git metadata. The project root is the top-level directory containing the complete project.

## Cursor, Explorer, Markdown, and Terminal

Cursor is the editor used by the course. `View → Explorer` opens the file explorer when repository files are not visible.

Markdown files such as `README.md` can be opened as source or rendered with Preview.

Cursor also has an integrated terminal. The course demonstrates opening it with:

```text
Ctrl + `
```

## Dependency

A dependency is an external package required by a project, such as `openai`, `pandas`, `transformers`, or `gradio`.

## Virtual Environment and `.venv`

A virtual environment isolates a project's Python interpreter and installed packages from other projects.

```text
Project A → environment A
Project B → environment B
```

In this course the environment lives in a `.venv` directory.

## `uv`

The course uses `uv` to manage the Python environment and project dependencies.

```bash
uv --version
uv self update
uv sync
```

`uv sync` synchronizes the project environment from project metadata and lock information when available, creating or updating `.venv` and installing the required dependencies.

```text
dependency → package the project needs
virtual environment → isolated environment for the project
.venv → directory containing that environment
uv → project/package/environment manager
uv sync → synchronizes the environment with project requirements
```

# OpenAI API and Secret Management

## ChatGPT vs OpenAI API

ChatGPT and the OpenAI API are separate product interfaces. ChatGPT is an end-user application, while the API lets software communicate programmatically with OpenAI models.

```text
Python application
       ↓
OpenAI API
       ↓
Model
       ↓
Response
```

An API key is a secret credential used to authenticate API requests and associate them with the relevant account/project.

API keys must not be hard-coded into source code or committed to GitHub.

## API Billing Is Separate

ChatGPT subscription billing and API billing are separate. A ChatGPT subscription does not automatically provide API credits.

A request can therefore have a valid API key but still fail later because the API account has no remaining credit or quota.

Conceptual request stages:

```text
DNS
 ↓
TCP connection
 ↓
TLS handshake
 ↓
HTTP request
 ↓
API authentication
 ↓
quota / billing checks
 ↓
model execution
```

This distinction is useful during troubleshooting because a TLS failure happens before billing or model execution is reached.

## `.env`

A `.env` file keeps secrets and configuration values separate from application source code.

```env
OPENAI_API_KEY=your_secret_key
```

Core principle:

```text
code != secret
```

# Jupyter Notebook Setup

## Jupyter Notebook (`.ipynb`)

A Jupyter Notebook is an interactive document containing explanatory text, executable code, and outputs.

```text
Notebook
├── text / explanation
├── code cell
├── output
├── more text
└── another code cell
```

## Cell

A notebook is divided into cells. Code cells can be executed independently.

```text
Shift + Enter
```

executes the current cell.

## Kernel

The kernel is the Python process running behind the notebook and executing code.

```text
Jupyter Notebook
       ↓
     Kernel
       ↓
Python executes code
       ↓
     Output
```

The selected kernel should point to the project's `.venv` environment so the notebook uses the correct Python interpreter and dependencies.

## Imported Modules and Kernel State

A Jupyter kernel keeps imported modules in memory. If a `.py` module is edited after it was imported, the notebook may still use the old version until the module is reloaded or the kernel is restarted.

Example:

```python
import importlib
import scraper

importlib.reload(scraper)
```

This is an important notebook debugging concept: editing a source file does not automatically guarantee that the running kernel is using the new code.

# First LLM Project — Web Page Summarizer

The first practical LLM application accepts a website URL, retrieves the page content, extracts useful text, builds prompts, sends that text to an LLM, and displays a summary.

Final conceptual flow:

```text
Website URL
    ↓
Retrieve HTML
    ↓
BeautifulSoup parsing / cleanup
    ↓
Website text
    ↓
Prompt construction
    ↓
LLM inference
    ↓
Summary
```

A useful engineering decomposition is:

```text
Data acquisition
      +
Prompt construction
      +
LLM inference
      =
AI application
```

## Web Scraping Is Not AI

The scraper retrieves and cleans website content. That part is ordinary software engineering, not AI.

```text
Website → scraper → text
```

The LLM becomes involved after the extracted text is provided as model input:

```text
text → LLM → summary
```

The model did not browse the website by itself in this project. The program retrieved the data first and explicitly supplied it to the model.

## BeautifulSoup

BeautifulSoup parses the returned HTML. The helper removes irrelevant page elements such as scripts and styles, extracts visible text, and sends a limited amount of content onward for summarization.

## Restricted TLS Environments — General Lesson

Python HTTPS clients may reject a connection when a local security product, proxy, or TLS inspection layer presents a certificate that does not satisfy Python/OpenSSL's active security policy.

The important troubleshooting lesson is to identify the failing layer instead of immediately disabling certificate verification.

```text
Application code
      ↓
HTTP client
      ↓
TLS layer
      ↓
Network / inspection layer
      ↓
Remote service
```

A successful request through one OS-native client does not automatically prove that a different Python TLS stack will accept the same connection.

For the course lab, an OS-native `curl.exe` transport was used to retrieve public HTML while keeping the parsing logic in Python. This was a local environment workaround, not a change to the conceptual web-scraping architecture.

Example helper:

```python
import subprocess


def fetch_html(url):
    result = subprocess.run(
        ["curl.exe", "-L", "-sS", url],
        capture_output=True,
        check=True,
    )
    return result.stdout
```

Then BeautifulSoup continues normally:

```python
html = fetch_html(url)
soup = BeautifulSoup(html, "html.parser")
```

# Prompt Construction

## OpenAI Message Structure — List of Dictionaries

Chat-style model input is represented as a Python list containing dictionaries:

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

This connects Python fundamentals directly to LLM Engineering:

```text
messages → list
    ↓
item → dictionary
    ↓
role/content → keys
```

## System Prompt

The system prompt defines the model's overall behavior, task, context, tone, or response format.

```text
System Prompt
→ Who are you?
→ What is your overall task?
→ How should you behave?
→ How should the answer be formatted?
```

## User Prompt

The user prompt contains the concrete request for the current interaction.

```text
User Prompt
→ What should you do right now?
```

Changing the system prompt while keeping the user prompt the same can change the model's tone, style, focus, and behavior.

## f-Strings in Prompt Construction

Python f-strings let application data be inserted directly into a prompt.

```python
user_prompt = f"""
Please summarize this website:

{website_text}
"""
```

The expression inside `{...}` is replaced by the current Python value before the prompt is sent to the model.

# LLM Calls and Responses

## Cloud Client Concept

A normal cloud OpenAI client uses the OpenAI API endpoint and a real API key.

```python
from openai import OpenAI

openai = OpenAI()
```

The course introduced the cloud API call syntax, but successful model execution in the current lab environment was completed through a local OpenAI-compatible Ollama endpoint.

## Local Ollama Through the OpenAI Python Client

Ollama exposes an OpenAI-compatible local endpoint. This means the same `openai` Python package and familiar message structure can be reused while the model runs locally.

```python
from openai import OpenAI

local_ai = OpenAI(
    base_url="http://localhost:11434/v1/",
    api_key="ollama"
)
```

The key idea is the `base_url`:

```text
Default cloud client
Python → api.openai.com → cloud model

Local client
Python → localhost:11434 → Ollama → local model
```

The local `api_key="ollama"` is only a placeholder required by the client interface. The local Ollama server does not use it as a real OpenAI secret.

## First Successful Local LLM Call

A local model call uses the same chat-completion structure:

```python
response = local_ai.chat.completions.create(
    model="gpt-oss:latest",
    messages=messages
)
```

This successfully demonstrated:

- Python calling an LLM programmatically
- an OpenAI-compatible client interface
- local model inference through Ollama
- system and user messages
- response handling

## Reading the Model Response

The generated text is retrieved from:

```python
response.choices[0].message.content
```

Mental model:

```text
response
   ↓
choices
   ↓
[0]
   ↓
message
   ↓
content
```

# Completed Web Page Summarizer

The final project flow now works end to end:

```text
Website
   ↓
OS-native HTTP retrieval
   ↓
BeautifulSoup
   ↓
clean website text
   ↓
f-string user prompt
   ↓
system + user messages
   ↓
local OpenAI-compatible client
   ↓
Ollama
   ↓
gpt-oss
   ↓
summary
```

The practical lesson is bigger than the specific model or provider. The application consists of replaceable layers:

```text
Data source
   ↓
Data retrieval
   ↓
Data preparation
   ↓
Prompt
   ↓
Model interface
   ↓
Model
   ↓
Output handling
```

A cloud provider or a local model can be swapped while much of the surrounding application logic remains the same.

# Troubleshooting Principles Learned

1. Read the exact exception instead of guessing.
2. Identify which layer failed: DNS, TCP, TLS, authentication, billing, model access, or application code.
3. A connection error is different from a billing/quota error.
4. Avoid disabling TLS verification as a first response.
5. Compare clients and TLS stacks when behavior differs between terminal tools and Python.
6. Remember that Jupyter kernels cache imports and state.
7. Verify each fix with one small test before changing more code.

# Current Course Status

```text
Environment setup                                      ✅
Jupyter Notebook and .venv kernel                      ✅
.env and API key concepts                              ✅
OpenAI API request flow                                ✅
API billing vs ChatGPT billing distinction             ✅
OpenAI message structure                               ✅
System prompt vs user prompt                           ✅
f-string prompt construction                           ✅
Web scraping and BeautifulSoup                         ✅
Local LLM workflow with Ollama                         ✅
OpenAI-compatible local client                         ✅
Jupyter module reload / kernel-state lesson            ✅
Web Page Summarizer                                    ✅
```

The next course material can now continue beyond the first working LLM application.