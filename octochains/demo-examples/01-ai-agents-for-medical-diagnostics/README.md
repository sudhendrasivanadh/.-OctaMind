# 🩺 Demo 01: AI Agents for Medical Diagnostics

This demo showcases how **OctaMind** can be applied to **high-stakes medical reasoning** using **Parallel Multi-Agent Intelligence**.

Rather than relying on a single diagnostic pathway, the system uses **collaborative isolated reasoning**, where specialized AI agents independently evaluate the same patient report before producing a collective clinical consensus.

This approach helps reduce **diagnostic tunnel vision** and encourages **multi-perspective medical analysis**.

<p align="center">
  <img src="https://github.com/user-attachments/assets/c02eff1e-70dd-4edb-b378-9baa06772276" width="900"/>
</p>

---

# Getting Started

Each OctaMind demo is intentionally designed to be **standalone** with its own dependencies.

This keeps the **core framework lightweight** while allowing demos to use specialized tooling.

---

## 1. Install Dependencies

Navigate into this demo directory and install the required packages inside your virtual environment:

```bash
pip install -r requirements.txt
```

**Note:**  
This demo uses:

- **LangChain**
- **LangChain OpenAI**
- **OpenAI models**

for agent orchestration and reasoning.

---

## 2. Configure Environment Variables

This demo uses **OpenAI models** such as **GPT-4o**.

Create a `.env` file inside this demo directory.

Add your API key:

```bash
OPENAI_API_KEY=your_api_key_here
```

This allows OctaMind to authenticate and run the reasoning pipeline.

---

# System Architecture

This demo simulates a **multidisciplinary medical reasoning team**.

Instead of one AI attempting diagnosis alone, multiple expert agents analyze the same clinical data independently.

The final outcome is produced through **consensus-driven reasoning**.

---

## Building the Agents

The medical team is created by extending the **`octamind.Agent`** base class.

Each agent receives:

- A defined **Role**
- A focused **Goal**
- A specialized **Reasoning Scope**

This mirrors how real-world medical teams operate.

### **Cardiologist**

Focuses on:

- ECG findings
- Cardiac markers
- Echocardiograms
- Structural heart abnormalities

The agent evaluates possible **cardiovascular conditions** and associated risks.

---

### **Psychologist**

Focuses on:

- Anxiety indicators
- Trauma patterns
- Depression signals
- Somatic symptom presentation

This specialist investigates **psychological contributors** that may influence or mimic physical symptoms.

---

### **Pulmonologist**

Focuses on:

- Respiratory conditions
- Asthma
- COPD
- Pulmonary infections
- Breathing abnormalities

The goal is to identify potential **lung-related causes** affecting patient health.

---

Each specialist implements an **`execute()`** method.

When the **OctaMind Engine** runs, all agents execute **simultaneously in parallel threads**.

This guarantees:

- **Independent reasoning**
- **Zero peer influence**
- **Reduced confirmation bias**
- **Cleaner medical analysis**

---

# The Consensus Aggregator

Once specialist evaluations are complete, their findings are forwarded to the **MultidisciplinaryTeam Aggregator**.

This component acts as the system's **Consensus Layer**.

Unlike individual agents, the aggregator does not perform primary diagnosis.

Instead, it:

- Reviews specialist reports
- Identifies agreement
- Detects conflicting conclusions
- Produces a structured final assessment

The aggregator functions as a **clinical synthesis layer** responsible for collaborative decision-making.

---

# 📥 Input & Output Flow

OctaMind follows a **Broadcast → Analyze → Aggregate** workflow.

---

## System Input

The system accepts a **raw medical case report** in text format.

By default, the demo analyzes reports located inside:

```text
medical_reports/
```

These files simulate realistic patient case data.

---

## System Output

The reasoning workflow produces several stages of output.

### **Parallel Execution**

The OctaMind Engine broadcasts patient data to all specialists simultaneously.

Each agent analyzes the case using **domain-specific reasoning**.

---

### **Expert Reports**

Every specialist produces an **independent diagnostic assessment**.

These reports remain isolated during execution.

---

### **Final Consensus**

The **Consensus Aggregator** synthesizes findings into:

- Likely medical conditions
- Supporting reasoning
- Structured clinical summaries

The final report emphasizes **reasoned consensus rather than single-agent certainty**.

---

### **Persistence**

Results are:

- Printed to terminal
- Saved automatically

Output location:

```text
results/Final_Report.txt
```

This enables repeatable evaluation and easier debugging.

---

# 🤝 Contributing New Demos

OctaMind encourages **community-driven demo development**.

New demos help demonstrate how **Parallel Multi-Agent Reasoning** can be applied across industries.

Examples:

- **Legal Analysis**
- **Finance**
- **Cybersecurity**
- **Research Systems**
- **Business Strategy**

---

## Demo Contribution Guidelines

To maintain consistency:

### **Isolated Dependencies**

Every demo should include its own:

```text
requirements.txt
```

This preserves core framework simplicity.

---

### **Clear Entry Point**

Provide:

```text
run_demo.py
```

showing the complete workflow:

```text
Broadcast
→ Parallel Reasoning
→ Consensus Aggregation
→ Final Output
```

---

### **Sample Data**

Include reproducible datasets whenever possible.

Examples:

- `.txt`
- `.csv`
- reports
- case files

Good demos should run with minimal setup.

---

> ⚠️ **Disclaimer**
>
> This demo is intended for **research**, **learning**, and **technical experimentation** only.
>
> It does **not** provide medical advice and should never be used as a substitute for professional diagnosis, treatment, or clinical decision-making.
