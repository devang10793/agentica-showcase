# Capabilities

[← Overview](README.md) · [Screens](screens.md)

## The problem it solves
A company that wants to use AI agents needs more than a chat box. Someone has to build the agents and decide what they may do. Someone has to prove they are good enough before anyone relies on them. Personal data has to stay out of places it should not go, spending has to be capped, and afterwards there has to be a record of exactly what each agent did.

Agentica puts all of that in one platform, so building an agent and governing it are the same workflow.

## Build
- **Agents.** Each agent has:
  - instructions, with variables;
  - a model and its parameters;
  - tools and knowledge bases;
  - limits on steps, tool calls, time and tokens;
  - plain-text or JSON-schema output.
- **Drafts and versions.**
  - Drafts can be saved even with problems, and every problem is listed at the field it belongs to.
  - Versions are numbered and carry change notes. Any two can be compared side by side, and you can roll back in one step.
- **Playground.** Try the draft and watch each step arrive as it happens: guardrail check, retrieval, model call, tool call and answer. Every step shows its duration, tokens and cost.
- **Workflows.** An ordered list of steps (agent, branch, human approval, end), with a read-only graph of the flow. Each agent step runs a published agent, pinned to a version.
- **Access.** Each agent has its own access list and its own feedback inbox.

## Knowledge
- Upload text, Markdown, HTML, PDF (with text) or Word files, up to 20 MB each.
- Documents are parsed, chunked, masked and indexed for both keyword and vector search. Only the masked chunks are kept, not the uploaded file.
- Try retrieval before any agent relies on it: keyword, vector or hybrid search, with each score shown.
- Answers carry numbered citations that open the exact passage.

## Tools
- **Built-in tools:** a calculator, the current time and knowledge search. Published agents can also be called as tools.
- **Remote MCP servers.** A platform admin registers the server, then reviews and classifies each of its tools as read or write before any agent can use it. If a tool's definition changes, it is switched off until it is reviewed again.
- **Write tools never run on their own.**
  - Every call to a tool that changes something pauses the run.
  - The approver sees the exact arguments the tool will receive, with personal values already replaced.
  - Once approved, the run carries on, and the decision is recorded.

## Models
- Providers and models are configuration, not code. Adapters exist for Google models on Vertex AI and for OpenAI-compatible endpoints. The screens and videos use a scripted model; the adapters have not yet been run against live providers.
- A platform admin approves each provider and model, sets its price (with an effective-dated history) and can check it on demand. Models are health-checked on a schedule.
- A workspace admin chooses which approved models the workspace may use.
- Credentials are stored only as references to the server's environment, never as values.

## Evaluate
- **Suites.** Versioned suites of cases with rule-based scorers, plus blind human review against a rubric.
- **Safety suite.** A mandatory suite covering prompt injection, data leaks and tool misuse.
- **Evaluation runs.** Each run scores every case against a chosen version under a cost ceiling, and shows what changed since the previous run.
- **The publish gate.** A version goes live only when:
  - its required suites meet their thresholds;
  - the safety suite passes in full;
  - every critical case passes;
  - human reviews are graded;
  - the evidence is for this exact version;
  - a second person approves.

  There is no override, and nobody can approve their own request.
- **Agent health.** When something a live agent depends on changes (a knowledge base, the guardrails, the safety suite), the agent is marked for a re-check automatically.

## Chat
- End users see only the agents published to them.
- Answers show their steps, citations and cost. People can rate and correct answers.
- People can export or delete their own conversations, and see their own usage.
- **Who viewed my sessions:** every time someone else opens one of your conversations, you can see who, when, and the reason any admin gave.

## Governance
- **Roles.** End user, builder, evaluator and workspace admin, plus platform admin. A person may hold several. Every permission is enforced by the server, and isolation is enforced in the database.
- **Data masking.** Before anything is stored or sent to a model, Agentica replaces e-mail addresses, phone numbers, card and bank account numbers, UPI IDs, IFSC codes, and Aadhaar and PAN numbers with placeholders. Keys, tokens and passwords are always removed.
- **Budgets.** Hard monthly caps for the workspace, for each person and for each agent. The budget is checked before every model call, and a run that would go over a cap stops.
- **Audited access.** Every time someone opens another person's conversation (an approver, a builder reading a trace, an admin), the view is recorded and the owner can see it. An admin must also give a reason.
- **Audit log.** Sensitive actions go into a hash-chained audit log.
- **Retention.** Conversations expire after about six months of inactivity.

## Identity and access
- Google sign-in (OpenID Connect) with an allowed-domains list. It is built and switched off by default, and has not yet been run against a live Google client.
- Personal API keys with scopes (chat, evaluate, full), an expiry date and revocation. A key is shown once, when it is created.

## Observe
- A trace of every run: each step with its timing, tokens and cost, which can be saved as an evaluation case.
- Usage per agent and per person, with spending against each cap.
- In-app alerts for approvals waiting, budgets, agent health and provider problems.

## How it fits together
- **Web app.** A display layer only; it holds no business logic.
- **API.** Every request goes through it: permissions, validation, the publish gate and budgets.
- **Worker.** Runs agents and workflows, ingests documents and runs scheduled checks. A run interrupted by a crash is recovered, and a write that may already have happened is never repeated blindly.
- **PostgreSQL** holds everything, including keyword and vector search.
- It is self-hosted: you run it on your own infrastructure.

## Not in this release
- SQL and data-catalog tools.
- Scheduled runs and long-term memory.
- Parallel workflow steps.
- More than one workspace, and an audit-log screen.
- An SDK and a command-line tool.
- Recognition of personal names and street addresses.
- Tools that need a real personal value, such as an e-mail address to send to. Tools only ever receive placeholders.
