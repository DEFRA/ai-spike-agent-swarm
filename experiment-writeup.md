# AI Agent Swarm Spike - Writeup

Status: Completed

## Need
Complex tasks—such as drafting a comprehensive policy document, responding to a nuanced multi-faceted query, or creating a business case—rarely follow a straight line. They require distinct types of expertise (researching, drafting, fact-checking, legal review) and, crucially, iteration. Rigid agentic workflows can fail at these if the requests are suitably dynamic. There is a need for a system that can "self-correct" and loop back when quality standards aren't met.

## Hypothesis

We can achieve higher quality scores by using multi-agent systems with critic-driven feedback loops instead of single-agent approaches.

## What we aim to discover
- Can a swarm of AI agents, each with specialized roles, collaborate effectively to complete complex tasks?
- Does incorporating feedback loops and self-correction mechanisms improve the quality of the output?
- How does the performance of a multi-agent swarm compare to that of a single-agent system in terms of efficiency and output quality?
- What frameworks could we recommend to other teams looking to implement similar multi-agent systems?

## Assumptions
- AutoGen which was used in a previous spike seems to be getting replaced by other frameworks, so we should explore alternatives.
- Pydantic AI looks promising due to its structured output capabilities, which could be beneficial for orchestrating multiple agents.

## Outcomes
Successfully implemented a managed agent swarm pattern using Pydantic AI to analyze farming policy documents. An orchestrator agent dynamically coordinated three specialist agents (Critique, Gap Analysis, Ambiguity) through tool-based communication, with human-in-the-loop approval gates controlling handoff to final report generation.

### Key Findings
- Pydantic AI successfully coordinated three specialist agents (Critique, Gap Analysis, Ambiguity) using tool-based communication and structured outputs
- Orchestrator made context-aware decisions about which specialist to engage rather than following a fixed sequence
- Shared message history enabled agents to reference and build on each other's observations, creating dialogue rather than isolated responses
- Handoff mechanism with human approval gates allowing quality control before finalizing outputs, with feedback loops for iterative refinement
- Proved tool call limits (25 per run) prevented runaway execution while allowing reset between feedback rounds

## Shortcomings

- Only two models used (Claude Haiku and Sonnet) - broader model comparison needed to assess framework compatibility and performance differences
- OpenTelemetry integration might not be possible within our environment due to infrastructure constraints - further investigation required
- No validation metrics produced yet - awaiting finalisation of validation PoCs to establish quality benchmarks
- Interaction design patterns for agent/swarm applications need development, particularly for human-in-the-loop workflows and observability interfaces
