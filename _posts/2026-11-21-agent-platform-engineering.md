---
title: "Agent Platform Engineering: Running AI Agents in Production"
date: 2026-11-21
tags: [Agent Platform Engineering]
description: "Agents and software factories build the software. Someone has to build the platform they run on: production-ready, enterprise-ready, on Kubernetes you own. Here is how: Run, Govern and Trust."
---

Most companies can build an AI agent in a week. Very few can run fifty of them in production.

That gap has a name. I call it **Agent Platform Engineering**: the production-ready platform where teams run their agents and software factories, on Kubernetes they own, in any cloud or on-premises.

## Build the thing that runs the thing

Coding agents and software factories build the software. That is the thing that builds the thing.

But they need a place to run. A runtime, sandboxes, access to models and tools, limits, and a way to check their work. Today every team builds this again, one agent at a time.

I build that place once, as a platform. Teams bring their own agents and factories and run them on top.

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

This is exactly the problem platform engineering was created to fix. For services, platform teams built golden paths, self-service and guardrails, so developers could ship fast without breaking production. Agents need the same.

## Three pillars: Run, Govern, Trust

### Run: where any agent or factory runs

- **Runtime and sandboxes.** Every agent runs isolated, with limits on time, network and resources. The agent never holds the keys.
- **Gateways.** One entry point for models, MCP tools and other agents.
- **Bring your own agent.** The platform does not care which framework or factory sits on top.
- **Golden paths.** From the first agent to production in days, not months.

### Govern: who the agent is and what it may do

- **Identity and permissions.** Every agent has its own identity and acts with the rights of a person or a role, never with a shared super key.
- **Budgets and limits.** Per task and per team, so an agent cannot run forever or spend without limit.
- **Policies for every action.** Small and reversible actions are allowed. Everything else needs a human.
- **Ownership.** It runs on Kubernetes, so the company owns the platform: any cloud or on-premises, no lock-in.

### Trust: a result counts only with proof

- **Evidence before acceptance.** A result is accepted only when the checks pass and an independent review agrees.
- **Tracing, cost and quality per agent.** What did it do, what did it cost, where did it fail?
- **Evals for every change.** A change in a prompt, a skill or a model is a change in the product. Test it like one. I talked about this at DSC DACH 2026 in "From Code to Context".
- **Human checkpoints.** People stay accountable where it matters.

## Why Kubernetes

You can start on a managed cloud. On AWS you can build a lot of this with Bedrock, AgentCore, Strands and Cedar policies. This is the path I used at the AI Platform Hackathon, and it is a fast start.

But for a platform that many teams depend on, I prefer Kubernetes:

- **Ownership.** The company owns the platform, not a single vendor.
- **Any cloud or on-premises.** The same platform runs where the company already runs its software.
- **Open components.** Each building block (agent runtime, sandboxes, gateways, policies, tracing) is an open-source piece you can swap.
- **Enterprise-ready by design.** Kubernetes already has what enterprises need: identity, network policies, admission control, GitOps.

## How to start

Do not start with a big platform project. Start with one workflow.

1. Pick one agent workflow, or one software factory, that matters to a team.
2. Run it on the platform: sandbox, gateway, its own identity and budget.
3. Add tracing and a first set of evals.
4. Turn what worked into a golden path for the next team.

Then repeat. The platform grows from real use, not from a slide.

## The thing that runs the thing

Peter Steinberger said it well: build the thing that builds the thing. Coding agents and software factories are that thing.

My part: build the thing that *runs* it. That is Agent Platform Engineering, and it is where I spend my time at SQUER.

If you are running agents in production, or trying to, I would like to hear what is hardest for you. Find me on [LinkedIn](https://www.linkedin.com/in/jmolero/).
