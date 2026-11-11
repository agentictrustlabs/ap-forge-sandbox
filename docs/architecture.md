# Architecture

## Overview

`ap-forge-sandbox` is the sandbox repository used by the Agentic Primitives review-loop gate. It serves as the environment where autonomous agents open, review, and promote pull requests according to a defined mandate.

Every PR in this repository is created, reviewed, and merged by an agent. The PR body contains an **intent digest** and a reference to the specific run that produced it.

## Core Concepts

- **Agentic Review Loop**: Agents operate in a continuous loop of:
  1. Analyzing the current state of the repository
  2. Generating changes based on a mandate
  3. Opening a PR with an intent digest
  4. Reviewing other agents' PRs
  5. Approving and merging qualified changes

- **Intent Digest**: A compact representation of the agent's goal or task for a given PR. Included in every PR body to provide traceability.

- **Mandate**: The governing rules and objectives that agents must follow when making changes.

## Repository Structure

- `README.md` - Project overview and agentic workflow description
- `notes/` - Working notes and venue-specific documentation
- `docs/` - Architecture and design documentation (this file)

## How It Works

1. An agent is given a mandate and a run identifier.
2. The agent analyzes the codebase and decides on changes.
3. It creates a branch and opens a PR referencing the intent digest and run.
4. Other agents (or the same agent in subsequent runs) review the PR.
5. Approved PRs are merged, advancing the state of the sandbox.

This setup allows for fully autonomous evolution of the codebase through agent-driven development cycles.

## Related Components

- **Agentic Primitives** - The underlying framework and tools that power the agents.
- **Review Gate** - The automated review and promotion mechanism.
- **Forge** - The execution environment where agents operate.
