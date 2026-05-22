# Contributing to OctaMind

Thanks for your interest in contributing to OctaMind.

OctaMind is built around one idea:

Create lightweight, modular, and collaborative AI reasoning systems without unnecessary complexity.

Before submitting contributions, please review the guidelines below.

---

# Contribution Workflow

Please follow this workflow when contributing:

1. Fork the repository
2. Create a branch from `main`
3. Build and test your contribution
4. Submit a Pull Request

Every Pull Request is reviewed for:

- Code quality
- Logic consistency
- Architectural compatibility
- Thread safety
- Framework design alignment

---

# Lightweight Core Philosophy

OctaMind is intentionally designed to remain lightweight.

The framework core should avoid heavyweight AI SDK dependencies.

Do not add libraries such as:

- langchain
- llama-index
- openai
- anthropic
- transformers

to:

```text
requirements.txt
pyproject.toml
```

The core framework should rely primarily on standard Python libraries.

If integrations or demos require additional dependencies, place them inside:

```text
demo-examples/
```

This keeps the framework clean, modular, and optional.

---

# Project Architecture

OctaMind uses a modular registry-based architecture.

Every component should be properly registered to support clean imports and maintain framework consistency.

---

# Adding a New Agent

Agents live inside:

```text
src/octamind/agents/
```

You may use an existing domain folder or create a new one.

Example:

```text
agents/
├── medical/
├── finance/
├── education/
└── cybersecurity/
```

---

## Agent Requirements

Each agent must:

- Inherit from `Agent`
- Define:
  - role
  - goal
  - input_description
- Accept `llm_callable`
- Implement:

```python
execute(self, problem_data)
```

Use:

```python
self._build_prompt(problem_data)
```

to automatically inject prompts and tool schemas.

Avoid hardcoded LLM providers.

Dependency injection is required.

---

# Agent Registration

After creating a new agent, register it.

Example:

```python
from .your_agent import YourAgent
```

Update the corresponding:

```text
__init__.py
```

Proper registration ensures shorthand imports continue working.

---

# Adding Aggregators

Aggregators belong inside:

```text
src/octamind/aggregators/
```

Requirements:

- Inherit from `Aggregator`
- Process:

```python
Dict[str, str]
```

- Return structured outputs when possible

Preferred formats:

- JSON
- Dictionaries
- Typed models

Structured outputs improve interoperability and API readiness.

---

# Demo Examples

Demo projects help showcase OctaMind capabilities.

To keep the core isolated and lightweight, demos follow strict dependency separation.

Place demos inside:

```text
demo-examples/
```

Example:

```text
demo-examples/02-cybersecurity-analysis
```

Recommended structure:

```text
demo-examples/XX-demo/
├── requirements.txt
├── run_demo.py
└── README.md
```

If your demo uses external libraries, include them only in:

```text
requirements.txt
```

inside the demo folder.

Do not modify core dependency files.

---

# Code Standards

We prioritize maintainable and production-friendly code.

---

## Thread Safety

OctaMind agents may run in parallel.

Avoid:

- Global state
- Mutable shared variables
- Non-thread-safe resources

Agents should remain isolated and stateless.

---

## Type Hinting

Use modern Python typing practices.

All public methods and functions should include type hints.

Preferred LLM signature:

```python
Callable[[str], Any]
```

---

## Documentation

Clear documentation is essential.

Include descriptive docstrings for:

- Classes
- Public methods
- Tools

Tool docstrings directly influence model behavior and execution quality.

Good documentation improves reliability.

---

## Error Handling

Execution failures should not crash the framework.

Use defensive programming and framework safeguards when processing LLM outputs.

Reliable systems fail gracefully.

---

# Licensing

By contributing to OctaMind, you agree that contributions follow the project licensing model.

This includes:

### Business Source License (BSL 1.1)

Contributions remain protected under the project's sustainability model.

### Future Open Source Transition

Contributions transition to Apache 2.0 under the project's predefined change timeline.

Please review licensing terms before contributing.

---

# Need Help?

If you have questions, architecture ideas, or contribution-related discussions:

📩 Email: 2400030209@kluniversity.in

You can also open an Issue for:

- Bugs
- Feature requests
- Technical discussions
- Design questions

---

Build modular reasoning systems together 🚀
