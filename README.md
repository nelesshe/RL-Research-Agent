# RL-Research-Agent

RL-Research-Agent is a literature research agent designed for reinforcement learning and robotics learning scenarios.

The project focuses on helping AI / Robotics students conduct structured literature research, especially in topics such as reinforcement learning for robot control, quadrotor control, autonomous navigation, PPO, SAC, TD3, and sim-to-real reinforcement learning.

## Project Goal

The goal of this project is to build a lightweight research agent that can help users complete a literature review workflow:

1. Understand a research topic
2. Decompose it into research questions
3. Generate search keywords
4. Collect candidate papers
5. Read papers in a structured format
6. Verify citations
7. Summarize research trends
8. Generate a literature review report
9. Provide a follow-up learning plan

This project is currently in the MVP design stage. The first version will focus on research planning, paper reading templates, citation verification rules, and structured survey generation.

## Motivation

For undergraduate students learning reinforcement learning and robotics, reading papers is difficult because the process involves many hidden steps:

- choosing the right search keywords
- identifying relevant papers
- understanding the research problem
- comparing algorithms and experimental environments
- avoiding fake or unverifiable citations
- turning scattered papers into a clear learning path

This agent aims to provide a structured workflow for these tasks.

## Agent Harness Design

This project follows the idea of agent harness engineering. Instead of using a single prompt to directly generate a report, the literature research task is divided into several coordinated modules:

- Coordinator Agent
- Research Planner Agent
- Query Generator Agent
- Paper Search Agent
- Paper Reader Agent
- Citation Verifier Agent
- Survey Writer Agent
- Learning Planner Agent

Each module has a clear responsibility and fixed input-output format.

## Core Features

### 1. Research Topic Decomposition

Given a topic such as:

> PPO in quadrotor control

The agent decomposes it into research questions, such as:

- What control tasks are involved?
- Which reinforcement learning algorithms are used?
- What simulation environments are used?
- Is there any sim-to-real transfer?
- What baselines are compared?

### 2. Search Keyword Generation

The agent generates English and Chinese search keywords for paper discovery.

Example:

- PPO quadrotor control
- reinforcement learning UAV navigation
- deep reinforcement learning drone trajectory tracking
- sim-to-real reinforcement learning quadrotor
- PPO Flightmare quadrotor

### 3. Structured Paper Reading

For each paper, the agent extracts:

- Title
- Year
- Research problem
- Method
- Algorithm
- Environment
- Experiments
- Main results
- Limitations
- Relevance to the topic

### 4. Citation Verification

The agent checks whether a paper citation is verifiable before using it in the final report.

Unverified papers should not be included as confirmed references.

### 5. Survey Report Generation

The agent generates a structured literature review report, including:

- Background
- Research problem
- Method categories
- Representative papers
- Technical comparison
- Current limitations
- Future directions
- Suggested reading path

## MVP Scope

The first version will not attempt to build a fully autonomous research system.

The MVP focuses on:

- research topic planning
- keyword generation
- paper reading templates
- citation verification rules
- survey report structure
- learning path generation

Future versions may integrate arXiv, Semantic Scholar, local PDF parsing, RAG, and token usage tracking.

## Example Topic

The initial demo case is:

> PPO in quadrotor control

See `demo_case.md` for the detailed workflow example.

## Project Status

Current stage:

- Repository created
- Basic project structure prepared
- Agent workflow design in progress
- Demo case under construction

Next steps:

1. Complete the architecture design
2. Complete the demo case
3. Build a minimal command-line prototype
4. Test the workflow with Xiaomi MiMo API
