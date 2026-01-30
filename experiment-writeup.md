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
