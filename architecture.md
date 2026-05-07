# Architecture Design

## Overview

RL-Research-Agent is designed as a modular literature research agent harness.

The system does not rely on a single large prompt. Instead, it decomposes the literature research process into multiple specialized modules.

## Workflow

```text
User Topic
   ↓
Coordinator Agent
   ↓
Research Planner Agent
   ↓
Query Generator Agent
   ↓
Paper Search Agent
   ↓
Paper Filter Agent
   ↓
Paper Reader Agent
   ↓
Citation Verifier Agent
   ↓
Survey Writer Agent
   ↓
Learning Planner Agent
```

## Module Responsibilities

### 1. Coordinator Agent

The Coordinator Agent controls the overall workflow.

Responsibilities:

- understand the user topic
- decide which modules should be called
- maintain the current research state
- ask for human confirmation when necessary
- collect and merge outputs from other modules

### 2. Research Planner Agent

The Research Planner Agent decomposes the topic into concrete research questions.

Example topic:

> PPO in quadrotor control

Example research questions:

- What quadrotor control tasks are studied?
- Is PPO used for attitude control, trajectory tracking, obstacle avoidance, or navigation?
- What simulation environments are used?
- Are there real-world experiments?
- What algorithms are used as baselines?

### 3. Query Generator Agent

The Query Generator Agent generates search keywords.

Example output:

```text
"PPO quadrotor control"
"proximal policy optimization UAV navigation"
"reinforcement learning drone trajectory tracking"
"deep reinforcement learning quadrotor"
"sim-to-real reinforcement learning UAV"
"Flightmare PPO quadrotor"
```

### 4. Paper Search Agent

The Paper Search Agent searches for candidate papers.

Possible tools in future versions:

- arXiv
- Semantic Scholar
- Crossref
- Google Scholar manual search
- local PDF files
- user-uploaded papers

### 5. Paper Filter Agent

The Paper Filter Agent filters candidate papers by relevance.

Filtering criteria:

- topic relevance
- algorithm relevance
- robotics/control relevance
- publication year
- availability of full text
- citation reliability

### 6. Paper Reader Agent

The Paper Reader Agent reads each paper in a structured way.

Output schema:

```json
{
  "title": "",
  "year": "",
  "authors": "",
  "research_problem": "",
  "method": "",
  "algorithm": "",
  "environment": "",
  "experiments": "",
  "main_results": "",
  "limitations": "",
  "relevance": ""
}
```

### 7. Citation Verifier Agent

The Citation Verifier Agent checks whether a paper is real and whether its metadata is reliable.

Verification items:

- title
- authors
- year
- venue
- DOI or arXiv ID
- official paper link

Rule:

> Unverified papers should be marked as unverified and should not be treated as confirmed references.

### 8. Survey Writer Agent

The Survey Writer Agent writes the final literature review report.

Report structure:

1. Background
2. Research problem
3. Method categories
4. Representative papers
5. Technical comparison
6. Current limitations
7. Future directions
8. Suggested reading path

### 9. Learning Planner Agent

The Learning Planner Agent converts the literature review into a learning plan.

Example output:

1. Learn quadrotor dynamics basics
2. Review PPO and continuous control
3. Read papers about RL for quadrotor control
4. Study simulation environments such as Flightmare and AirSim
5. Reproduce a simple continuous-control baseline
6. Try PPO in a quadrotor simulation environment

## Design Principles

### 1. Research-first workflow

The agent should search and verify information before writing conclusions.

### 2. Modular collaboration

Each module has a clear role and fixed output format.

### 3. Citation safety

The agent should not fabricate papers, authors, years, or venues.

### 4. Human-in-the-loop

The user should confirm candidate papers before deep reading.

### 5. Token control

The agent should avoid reading too many papers at once and should save intermediate results.

## Future Extensions

- API integration with arXiv
- API integration with Semantic Scholar
- PDF parsing
- RAG-based paper Q&A
- Markdown report generation
- token usage tracking
- local research memory
