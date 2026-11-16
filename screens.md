# Screens

[← Overview](README.md) · [Capabilities](capabilities.md)

Sixteen screens that cover the main parts of Agentica, each in a light and a dark theme. Every image comes from the running product, with demo data.

| # | Screen | Area |
|---|---|---|
| 1 | [Agents](#1-agents) | Build |
| 2 | [Agent editor](#2-agent-editor) | Build |
| 3 | [Playground](#3-playground) | Build |
| 4 | [Run trace](#4-run-trace) | Observe |
| 5 | [Workflow editor](#5-workflow-editor) | Build |
| 6 | [Knowledge search](#6-knowledge-search) | Knowledge |
| 7 | [Tools](#7-tools) | Tools |
| 8 | [Models](#8-models) | Platform |
| 9 | [Evaluation run](#9-evaluation-run) | Evaluate |
| 10 | [Publish gate](#10-publish-gate) | Evaluate |
| 11 | [Chat](#11-chat) | Chat |
| 12 | [Approvals inbox](#12-approvals-inbox) | Chat |
| 13 | [Budgets and usage](#13-budgets-and-usage) | Admin |
| 14 | [Audited session access](#14-audited-session-access) | Admin |
| 15 | [Members and roles](#15-members-and-roles) | Admin |
| 16 | [Guardrail settings](#16-guardrail-settings) | Platform |

---

## 1. Agents
Every agent and workflow in the workspace in one list. Each row shows:
- its type;
- its status and live version;
- its health;
- its owner;
- when it last changed.

You can filter by type, status, health, owner and tag.

| Light | Dark |
|---|---|
| ![Agents, light](agentica/light/01-agents.png) | ![Agents, dark](agentica/dark/01-agents.png) |

## 2. Agent editor
The agent's definition in sections: basics, instructions, model, tools, knowledge, limits, output and guardrail extras. Starter prompts appear as buttons in chat. Problems are shown at the field they belong to, and a version can be created from a valid draft.

| Light | Dark |
|---|---|
| ![Agent editor, light](agentica/light/02-agent-editor.png) | ![Agent editor, dark](agentica/dark/02-agent-editor.png) |

## 3. Playground
Try the draft before it is published. The steps of each answer arrive live on the right: the guardrail check, assembling the context, model calls and tool calls, then the final answer, which cites the knowledge-base passage it used. Each step shows its duration and cost, and the session total is kept.

| Light | Dark |
|---|---|
| ![Playground, light](agentica/light/03-playground.png) | ![Playground, dark](agentica/dark/03-playground.png) |

## 4. Run trace
One run in full: who started it, from where, which version and model, its duration, tokens and cost, and every step with its timing. A run can be copied as JSON or saved as an evaluation case.

| Light | Dark |
|---|---|
| ![Run trace, light](agentica/light/04-run-trace.png) | ![Run trace, dark](agentica/dark/04-run-trace.png) |

## 5. Workflow editor
A workflow is an ordered list of steps: agent steps that run a published agent pinned to a version, branches, approval steps and end steps. Here, an agent drafts a reply, a branch decides whether it needs sign-off, and an approval step (assigned here to the person in the session) lets them approve or decline before the workflow ends.

| Light | Dark |
|---|---|
| ![Workflow editor, light](agentica/light/05-workflow-editor.png) | ![Workflow editor, dark](agentica/dark/05-workflow-editor.png) |

## 6. Knowledge search
Try a knowledge base before an agent relies on it. Ask a question and choose hybrid, keyword or vector search. Each result shows its passage with keyword, vector and fused scores, and can be copied into an evaluation case.

| Light | Dark |
|---|---|
| ![Knowledge search, light](agentica/light/06-knowledge-search.png) | ![Knowledge search, dark](agentica/dark/06-knowledge-search.png) |

## 7. Tools
The tools agents in this workspace may be given: built-in tools, and tools from approved MCP servers marked read or write. Any read tool can be tried here, with your own permissions, before it is attached to an agent.

| Light | Dark |
|---|---|
| ![Tools, light](agentica/light/07-tools.png) | ![Tools, dark](agentica/dark/07-tools.png) |

## 8. Models
Every model from every provider, configured as data:
- its provider and kind (chat or embedding);
- its approval status and health;
- its context window;
- its price per million tokens.

A platform admin adds and approves models, and each workspace's admin then chooses which approved models its agents may use.

| Light | Dark |
|---|---|
| ![Models, light](agentica/light/08-models.png) | ![Models, dark](agentica/dark/08-models.png) |

## 9. Evaluation run
The result of running a suite against one version:
- the score against its threshold;
- the cases passed;
- the cost against its ceiling, and the duration;
- what changed since the previous run;
- exactly which definition the evidence is for.

| Light | Dark |
|---|---|
| ![Evaluation run, light](agentica/light/09-evaluation-run.png) | ![Evaluation run, dark](agentica/dark/09-evaluation-run.png) |

## 10. Publish gate
A request to publish a version. Each gate rule is listed with the evaluation runs it rests on, including second-person approval, the safety suite and the critical cases. There is no override: a version goes live only when every rule passes and someone other than the requester approves.

| Light | Dark |
|---|---|
| ![Publish gate, light](agentica/light/10-publish-gate.png) | ![Publish gate, dark](agentica/dark/10-publish-gate.png) |

## 11. Chat
What an end user sees. Here the email address in the question was replaced before it was stored or sent to a model, and the notice says so. The answer cites the passage it came from, and its steps can be opened or hidden.

| Light | Dark |
|---|---|
| ![Chat, light](agentica/light/11-chat.png) | ![Chat, dark](agentica/dark/11-chat.png) |

## 12. Approvals inbox
An agent wants to use a write tool, so the run is paused. The approver sees what will happen and the exact arguments the tool will receive, then approves or rejects. Nothing runs until a person decides.

| Light | Dark |
|---|---|
| ![Approvals inbox, light](agentica/light/12-approvals.png) | ![Approvals inbox, dark](agentica/dark/12-approvals.png) |

## 13. Budgets and usage
The workspace's monthly cap, with what is spent, held for runs in progress and remaining. It also shows the separate evaluation budget, usage by person, agent or model, and each person's own cap. Caps are hard limits.

| Light | Dark |
|---|---|
| ![Budgets and usage, light](agentica/light/13-budgets.png) | ![Budgets and usage, dark](agentica/dark/13-budgets.png) |

## 14. Audited session access
A workspace admin opens someone else's conversation, read-only. They must give a reason first. The reason, their name and the time are recorded, and the person whose conversation it is can see the view.

| Light | Dark |
|---|---|
| ![Audited session access, light](agentica/light/14-session-access.png) | ![Audited session access, dark](agentica/dark/14-session-access.png) |

## 15. Members and roles
Who is in the workspace and what each person may do: end user, builder, evaluator or workspace admin. A person can hold several roles.

| Light | Dark |
|---|---|
| ![Members and roles, light](agentica/light/15-members-and-roles.png) | ![Members and roles, dark](agentica/dark/15-members-and-roles.png) |

## 16. Guardrail settings
The checks every agent passes through:
- **Personal-data recognisers.** Values are replaced with placeholders in every message, tool call, document and answer.
- **Secret detection.** Always on.
- **Optional extras.** Defaults for each new agent.
- **Size limits.** For messages, tool results, answers and documents.

| Light | Dark |
|---|---|
| ![Guardrail settings, light](agentica/light/16-guardrails.png) | ![Guardrail settings, dark](agentica/dark/16-guardrails.png) |
