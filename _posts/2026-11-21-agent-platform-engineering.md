---
title: "Agent Platform Engineering: Running AI Agents in Production"
date: 2026-11-21
tags: [Agent Platform Engineering]
description: "Most companies can build an AI agent. Few can run fifty of them safely. Platform engineering already solved this for services. Here is how it applies to agents: Run, Govern and Trust."
---

Most companies can build an AI agent in a week. Very few can run fifty of them in production.

That gap has a name. I call it **Agent Platform Engineering**: the platform that lets enterprises run AI agents in production, secure, observable and EU-ready.

## An agent is a new kind of workload

A service does what the code says. An agent decides what to do next.

It calls tools and APIs, often through MCP. It reads your data and acts on your systems. It spends tokens, and the cost changes with every run. And for the same input, the output can be different.

So agents need everything a service needs, plus more. The platform questions are the same. The answers are new:

| Concern | Service | Agent |
| --- | --- | --- |
| Identity | Service account | Agent acting for a person |
| Access | Fixed API calls | Tools chosen at runtime |
| Cost | CPU and memory | Tokens per task |
| Quality | Tests pass or fail | Evals, output varies |
| Audit | Request logs | Every decision and action |

Today most teams answer these questions one agent at a time. Every team builds its own access, its own logging, its own way to check the output. That does not scale. It also creates shadow agents: agents with broad access and no audit trail.

This is exactly the problem platform engineering was created to fix. For services, platform teams built golden paths, self-service and guardrails, so developers could ship fast without breaking production. Agents need the same.

## Three pillars: Run, Govern, Trust

### Run: where agents live and how they reach tools

- **Runtimes and sandboxes.** Agents run isolated, with limits on time, network and resources.
- **Gateways.** One entry point for models and MCP tools, with routing by data class. Sensitive data goes only to approved models.
- **Golden paths.** Templates, so a team can ship a new agent in days, not weeks.

### Govern: who the agent is and what it may do

- **Identity and permissions.** Every agent has its own identity and acts with the rights of a person or a role, never with a shared super key.
- **Policies for every action.** Small and reversible actions are allowed. Everything else becomes a proposal, for example a pull request, that a human approves.
- **Regulation.** Traceability for the EU AI Act and DORA, and data that stays where it must stay.

A useful rule here: be careful with the combination of private data, untrusted input and a way to send data out. Each one alone is fine. Together they are dangerous. The platform should block the combination by default.

### Trust: how we know the output is right

- **Evals before and after release.** A change in a prompt, a skill or a model is a change in the product. Test it like one.
- **Tracing, cost and quality per agent.** What did it do, what did it cost, where did it fail?
- **Context as a product.** Instructions and skills have owners, versions and tests. I talked about this at DSC DACH 2026 in "From Code to Context".
- **Human checkpoints.** People stay accountable where it matters.

## Two ways to run the same platform

There is no single stack. I see two paths.

**Managed cloud.** On AWS you can build this with Bedrock, AgentCore, Strands and Cedar policies. It is the fastest start, especially when the client is already on AWS. This is the path I used at the AI Platform Hackathon.

**Portable Kubernetes.** The same building blocks (gateway, runtime, sandboxes, policy, identity, tracing) as open components on Kubernetes. It runs on any cloud, on a sovereign European cloud or on-premises.

The pillars stay the same on both paths. What decides the path is usually Govern: when data must stay in the EU, or inside the company, the portable path wins.

## How to start

Do not start with a big platform project. Start with one workflow.

1. Pick one agent workflow that matters to a team.
2. Put it behind a gateway, with its own identity.
3. Add tracing and a first set of evals.
4. Turn what worked into a golden path for the next team.

Then repeat. The platform grows from real use, not from a slide.

## Build the thing that runs the thing

Peter Steinberger said it well: build the thing that builds the thing. Coding agents are that thing.

My addition: then build the thing that *runs* it. That is Agent Platform Engineering, and it is where I spend my time at SQUER.

If you are running agents in production, or trying to, I would like to hear what is hardest for you. Find me on [LinkedIn](https://www.linkedin.com/in/jmolero/).
