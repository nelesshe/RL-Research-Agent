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
