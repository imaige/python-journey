# AI Engineering Foundations

## Course Context

The AI Engineering course has started. The current material introduces the LLM engineering landscape, local model execution, the course roadmap, and the development environment used for the upcoming labs.

The AI course workflow is different from the Python workflow: course transcripts are explained first, then understanding is checked with questions, and GitHub notes are updated when the user asks.

## Large Language Models (LLMs)

An LLM is a large language model trained to work with natural language. It receives text input and generates text output based on learned language patterns.

Examples of LLM use cases include:

- question answering
- tutoring
- coding assistance
- summarization
- conversational applications
- commercial AI products

## Cloud LLM vs Local LLM

### Cloud-hosted LLM

A cloud-hosted model runs on remote infrastructure.

```text
User device
    ↓
Internet / API
    ↓
Remote infrastructure
    ↓
LLM
    ↓
Response
```

The user's device sends the request and receives the result, while model inference happens remotely.

### Local LLM

A local LLM is downloaded and executed on the user's own computer.

```text
Local computer
    ├── model files
    ├── CPU / GPU
    ├── RAM / VRAM
    └── local inference
```

Local models can be useful for experimentation, privacy, offline workflows, and learning how model serving works.

## Ollama

Ollama is a tool used to download, run, and interact with supported language models locally.

Important distinction:

```text
Ollama != LLM
```

A model such as Gemma is the AI model. Ollama is the software used to run that model locally.

General command pattern:

```bash
ollama run MODEL_NAME
```

## Model Size and Parameters

Model sizes may be written using abbreviations such as:

```text
270M = 270 million parameters
3B   = 3 billion parameters
20B  = 20 billion parameters
```

Parameters are learned numerical values inside a model. Larger parameter counts generally require more compute and memory, although larger does not automatically mean better for every task.

A practical model-selection mindset is:

```text
best model for the task != biggest available model
```

Production model selection may depend on:

- capability
- speed
- latency
- RAM / VRAM requirements
- storage
- cost
- privacy
- deployment constraints

## LLM Applications and Roles

An LLM can be instructed to behave according to a role and goal.

Example:

```text
Role: Spanish tutor
User level: beginner
Goal: conduct a beginner-friendly conversation
```

This illustrates an important AI Engineering transition:

```text
using an LLM
    ↓
building an application around an LLM
```

A commercial AI product can expose a simple interface while an LLM works behind the scenes.

## Reasoning / Thinking Models

Some models are designed to spend more computation on multi-step reasoning before producing a final answer.

Reasoning-heavy tasks may include:

- multi-step calculations
- complex decision making
- planning
- technical analysis
- structured problem solving

The visible "thinking" text shown by a product should not automatically be assumed to be the model's complete internal reasoning process.

## Eight-Week LLM Engineering Roadmap

The course roadmap introduced the following progression:

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

## Frontier Models

A frontier model is a model at or near the leading edge of current AI capability.

The course uses frontier models to introduce high-capability commercial LLM workflows before later comparing them with open models.

## Open Models

Open models can often be downloaded and run on local or self-managed infrastructure.

Examples discussed in the course include model families such as Gemma and other locally runnable models.

## RAG

RAG stands for Retrieval-Augmented Generation.

The core pattern is:

```text
User question
    ↓
Retrieve relevant external information
    ↓
Provide retrieved context to the LLM
    ↓
Generate an answer grounded in that context
```

RAG is especially useful when an LLM must answer using private, current, or domain-specific information that is not reliably available from the model alone.

Example enterprise sources:

- internal documentation
- incident reports
- policies
- procedures
- PDF collections
- knowledge bases

## Fine-Tuning vs RAG

These are different techniques.

### RAG

Relevant information is retrieved at request time and added to the model context.

### Fine-tuning

The model is further trained on additional examples or data to adapt its behavior or capabilities.

```text
RAG != Fine-Tuning
```

## Agentic AI

An agentic system goes beyond a single prompt-response interaction.

A simplified pattern is:

```text
Goal
  ↓
Agent
  ↓
Plan
  ↓
Use tool
  ↓
Inspect result
  ↓
Choose next action
  ↓
Final result
```

Future topics mentioned include agent loops, OpenAI Agents SDK, MCP, and autonomous workflows.

## AI Engineering Course Tracks

The curriculum described six complementary courses.

### AI Builder

Focuses on building agents and voice agents with little or no code.

### AI Coder

Focuses on using coding agents to build software and products faster.

### AI Leader

Focuses on delivering AI projects, business transformation, and commercial impact.

### AI Engineer Core Track

Focuses on:

- LLMs
- APIs
- open models
- RAG
- fine-tuning
- model selection
- optimization

### AI Engineer Agentic Track

Focuses on autonomous AI agents, agent loops, SDKs, and MCP.

### AI Engineer Production Track

Focuses on deploying LLM and agent systems at scale using cloud platforms such as AWS, GCP, and Azure, with attention to resiliency, observability, and security.

## AI Engineering Tooling Introduced

The course mentioned several tools that will appear later:

- Hugging Face
- Gradio
- LangChain
- Weights & Biases
- Modal

These are only introductory mentions at this stage.

## Development Environment

The course setup introduces the development environment used for future labs.

Core components include:

```text
GitHub repository
Git
PowerShell / terminal
IDE or code editor
Python environment
Dependencies
API keys
Environment variables
```

## Git Clone

`git clone` creates a local copy of a Git repository, including project files and Git metadata.

```bash
git clone REPOSITORY_URL
```

The course recommends keeping projects under a dedicated projects directory.

Example Windows workflow:

```powershell
mkdir projects
cd projects
git clone REPOSITORY_URL
```

## Project Root

The project root is the top-level directory that contains the project.

Example:

```text
llm-engineering/    ← project root
├── week1/
├── week2/
├── README.md
└── project configuration files
```

Opening the correct project root in the IDE is important because paths, Git state, environment files, and project configuration are interpreted relative to this structure.

## Cursor and IDEs

Cursor is an AI-assisted code editor based on the VS Code ecosystem.

The course recommends Cursor, but other IDEs or editors can also be used, including VS Code and PyCharm.

## Python Environment and Dependencies

A Python environment isolates project-specific Python versions and packages.

Example:

```text
Project A
└── Python environment A

Project B
└── Python environment B
```

A dependency is an external package required by a project.

Examples:

```text
openai
pandas
transformers
gradio
```

The course introduces `uv` as the tool that will be used to manage the Python environment and dependencies.

## API Keys

An API key is a credential used by software to authenticate with an external service.

Example pattern:

```text
Python application
    ↓
API
    ↓
LLM provider
```

API keys should be treated as secrets and should not be hard-coded into source code or committed to GitHub.

## `.env` and Environment Variables

Sensitive configuration values can be stored outside the main source code.

Example `.env` entry:

```env
OPENAI_API_KEY=your_key_here
```

A useful principle is:

```text
code != secret
```

The exact variable name matters because application code looks up environment variables by name.

## Troubleshooting Principles

The course emphasizes a documentation-first workflow.

A useful order is:

```text
Problem
  ↓
Project README / setup documentation
  ↓
Troubleshooting guide
  ↓
Error message analysis
  ↓
LLM assistance
  ↓
Verify before applying the suggestion
```

LLMs can help debug setup problems, but their recommendations should be checked rather than followed blindly.

## Current Status

AI Engineering study is temporarily paused after the initial foundations and PC environment-setup material. Python study continues using the existing workflow.
