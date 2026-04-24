# Cognitive PKM Repository

A Git-based Personal Knowledge Management system for tracking software engineering progress, learning, decisions, experiments, and GPT-assisted project planning.

This repository is separate from the actual software project repository.

* `Knowlage/repo_knowlage.` = progress tracking, thinking, GPT chat, decisions, experiments, and synthesis
* `Project/repo_project.` = the real software project implementation

The knowledge repository supports the project repository, but it is not the project itself.

---

## Purpose

Software engineering work creates two different kinds of output:

1. **The actual product** — source code, configuration, tests, assets, deployment files.
2. **The thinking behind the product** — plans, GPT chats, decisions, mistakes, experiments, assumptions, and learning notes.

Most projects only preserve the first one.

This repository is for preserving the second one.

Its purpose is to reduce context loss and make your learning process inspectable over time.

It helps separate:

* raw information
* beliefs
* decisions
* experiments
* resources
* synthesis
* project progress
* GPT chat output

---

## Agent-first clarification

After reviewing the harness engineering / AGENTS.md approach, the cleanest interpretation is this:

This repository should not only be a personal diary of progress. It should become the **agent-legible knowledge base** for your work.

That means the knowledge repo should contain structured, versioned information that a coding agent can later use to understand:

* what the project is
* why decisions were made
* which plans are active
* which experiments succeeded or failed
* which rules should guide implementation
* where the actual project repository lives

The project repository should then contain a short `AGENTS.md` file that points agents to the right instructions and project documentation.

Important rule:

> `AGENTS.md` should be a map, not a giant manual.

Do not put everything into `AGENTS.md`. Keep it short and link to deeper files.

Recommended split:

```text
repo_project./
├── AGENTS.md              # short instructions for coding agents
├── README.md              # human-facing project overview
├── docs/                  # project-local docs needed for implementation
└── src/                   # actual code

repo_knowlage./
├── GPT_Chat/              # raw GPT conversations
├── synthesis/             # processed summaries and plans
├── decisions/             # decision records
├── beliefs/               # assumptions and reasoning models
├── expiriments/           # tested ideas and results
└── resources/             # references
```

So the knowledge repo supports agent work, but the coding agent should primarily operate inside the project repo.

---

## Recommended `AGENTS.md` for the project repo

Create this file in:

```text
Project/repo_project./AGENTS.md
```

Suggested starting content:

````md
# AGENTS.md

## Project overview

This repository contains the actual software implementation for the business website project.

Planning, reasoning, GPT chat extraction, decision records, experiments, and learning notes are tracked separately in:

`../Knowlage/repo_knowlage.`

## Current implementation status

Early stage. Do not assume the stack is final unless a decision record exists in the knowledge repository.

## Before making major changes

Check the knowledge repository for:

- `synthesis/` — current project plans and summaries
- `decisions/` — accepted technical decisions
- `expiriments/` — prototypes and test results
- `beliefs/` — current assumptions
- `GPT_Chat/` — raw GPT source material

## Expected workflow

1. Read the relevant project README and docs.
2. Check related decision records before changing architecture.
3. Make small, focused changes.
4. Add or update tests when possible.
5. Keep implementation details in this repository.
6. Keep reasoning, alternatives, and decision history in the knowledge repository.

## Code style

- Prefer TypeScript when the project stack is initialized.
- Keep files small and readable.
- Use explicit names.
- Avoid hidden magic.
- Prefer boring, maintainable solutions.

## Testing

When test commands exist, run them before finishing work.

Expected future commands may include:

```bash
npm run lint
npm run test
npm run build
````

## Documentation rule

If implementation changes affect project direction, update the knowledge repository with a decision, experiment, or synthesis note.

````

---

## Recommended `AGENTS.md` for the knowledge repo

Create this file in:

```text
Knowlage/repo_knowlage./AGENTS.md
````

Suggested starting content:

````md
# AGENTS.md

## Repository purpose

This repository is a structured knowledge base for tracking software engineering progress, GPT chat extraction, beliefs, decisions, experiments, resources, and synthesis.

It is not the main application source code repository.

The actual project implementation lives in:

`../../Project/repo_project.`

## Main rule

Do not dump information without classifying it.

Every meaningful piece of information should eventually become one of:

- inbox item
- GPT chat source
- belief
- decision
- experiment
- resource
- synthesis

## Folder meanings

- `inbox/` — raw unprocessed notes
- `GPT_Chat/` — raw GPT conversations and source material
- `beliefs/` — assumptions or working beliefs
- `decisions/` — committed choices made under uncertainty
- `expiriments/` — tests, prototypes, results, and lessons
- `resources/` — external references
- `synthesis/` — processed summaries, plans, and reviews
- `docs/` — documentation about the knowledge system itself

## Writing rules

- Keep raw GPT output separate from processed synthesis.
- Do not treat GPT output as final truth.
- Convert useful GPT output into structured files.
- Record why decisions were made, not only what was chosen.
- Record experiment results, including failures.
- Prefer short, clear markdown files over large monolithic documents.

## Commit style

Use descriptive commit messages, for example:

```bash
git commit -m "Add initial stack decision"
git commit -m "Summarize GPT chat into MVP plan"
git commit -m "Record Next.js prototype experiment"
````

````

---

## Relationship between the two repositories

Current local structure:

```text
Software_Engineering/
├── Knowlage/
│   └── repo_knowlage./
│       ├── beliefs/
│       ├── decisions/
│       ├── docs/
│       ├── expiriments/
│       ├── GPT_Chat/
│       ├── inbox/
│       ├── resources/
│       ├── synthesis/
│       └── README.md
│
└── Project/
    └── repo_project./
        └── README.md
````

### `repo_knowlage.`

This repo tracks the learning and reasoning process.

Use it for:

* GPT chat exports
* project plans
* business analysis
* technical research
* architecture reasoning
* stack decisions
* experiment logs
* learning notes
* progress reviews
* mistakes and corrections
* weekly synthesis

### `repo_project.`

This repo is the actual implementation.

Use it for:

* source code
* application README
* package configuration
* frontend/backend code
* database schema
* tests
* deployment configuration
* project-specific documentation needed by users or developers

The project repo should contain what is needed to build and run the product.

The knowledge repo should contain why you built it that way.

---

## Core idea

This repository is not a dump of random notes.

It is a structured cognitive environment for software engineering work.

The main rule is:

> Do not mix raw notes, beliefs, decisions, experiments, and final synthesis.

Each type of knowledge has a different purpose.

---

## Repository layers

### `inbox/`

Temporary capture area.

Use this for information that has not been processed yet.

Examples:

* quick thoughts
* raw GPT answers
* copied requirements
* links
* unclear ideas
* notes from a conversation

Inbox content should later be moved into a better location.

---

### `GPT_Chat/`

Raw or lightly edited GPT conversation material.

Current example:

```text
GPT_Chat/Getting_info/
├── asking_for_plan
└── target_info
```

This folder is source material, not final truth.

Use GPT chat files to extract:

* project goals
* requirements
* technical options
* architecture ideas
* implementation steps
* risks
* open questions
* future tasks

Then move the useful conclusions into `beliefs/`, `decisions/`, `expiriments/`, or `synthesis/`.

---

### `beliefs/`

Things you currently think are true or useful.

A belief is not a decision. It can change when evidence changes.

Examples:

* TypeScript is a good choice for this project because it reduces frontend/backend mismatch.
* PostgreSQL is probably better than MongoDB for structured business data.
* The MVP should focus on public pages and admin editing before loyalty features.

Each belief should include:

* statement
* context
* evidence
* assumptions
* counterarguments
* status
* revision history

Suggested statuses:

```text
hypothesis
active
tested
stable
deprecated
```

---

### `decisions/`

Commitments made under uncertainty.

A decision should explain what you chose and why.

Examples:

* Choose Next.js for the public website.
* Use PostgreSQL as the database.
* Start with a minimal admin panel instead of a full CMS.
* Delay loyalty features until after the MVP.

Each decision should include:

* question
* context
* options considered
* chosen option
* reasoning
* risks
* expected outcome
* reconsideration conditions

Example file name:

```text
decisions/001-choose-nextjs.md
```

---

### `expiriments/` / `experiments/`

Logs of tests and results.

Experiments are where learning becomes concrete.

Examples:

* Try a Next.js page prototype.
* Compare Strapi with a custom admin panel.
* Test Prisma schema for stores and promotions.
* Deploy a small prototype to Vercel.

Each experiment should include:

* question
* hypothesis
* setup
* steps
* result
* interpretation
* next action

---

### `resources/`

External references.

Use this for:

* documentation links
* tutorials
* competitor websites
* API references
* hosting notes
* database references
* design examples

A resource is not automatically a belief or decision. If a resource changes your direction, extract that change into the correct folder.

---

### `synthesis/`

Processed summaries and progress reviews.

This is where scattered information becomes direction.

Use it for:

* weekly progress summaries
* project direction summaries
* MVP plans
* architecture summaries
* lessons learned
* current open questions
* next-step plans

This is one of the most important folders. Without synthesis, the repository becomes note hoarding.

---

### `docs/`

Documentation about the knowledge system itself.

Current file:

```text
docs/CONCEPT.md
```

Suggested future files:

```text
docs/CONCEPT.md
docs/WORKFLOW.md
docs/TEMPLATES.md
docs/GIT_USAGE.md
docs/PROJECT_LINKING.md
```

---

## How this repo should support the project repo

When working on the actual project, use this loop:

```text
Capture -> Process -> Decide -> Build -> Test -> Reflect -> Commit
```

### 1. Capture

Put raw GPT output, ideas, or requirements into `inbox/` or `GPT_Chat/`.

### 2. Process

Extract useful information from raw notes.

Ask:

* Is this a belief?
* Is this a decision?
* Is this an experiment?
* Is this a resource?
* Is this synthesis?

### 3. Decide

If something affects the implementation in `repo_project.`, create a decision record here first.

### 4. Build

Implement the decision in the project repo.

### 5. Test

Record important tests, prototypes, failures, or results in `expiriments/`.

### 6. Reflect

Write a short synthesis note explaining what changed in your understanding.

### 7. Commit both repos

Example:

```bash
# In knowledge repo
git add .
git commit -m "Record initial stack decision"

# In project repo
git add .
git commit -m "Initialize Next.js project"
```

---

## Suggested first knowledge outputs

Based on the current GPT chat files, create these files in the knowledge repo:

```text
synthesis/business-website-mvp-plan.md
decisions/001-choose-initial-stack.md
beliefs/web-project-architecture-beliefs.md
expiriments/001-nextjs-postgres-prototype.md
resources/web-project-stack-links.md
```

These files should summarize and organize the GPT chat material before major implementation begins in `repo_project.`.

---

## Suggested first project outputs

In the project repo, create the actual software project only after the first synthesis and decision files exist.

Possible starting structure:

```text
repo_project./
├── README.md
├── package.json
├── src/
├── public/
├── prisma/
└── docs/
```

The project README should be much more practical than this knowledge README.

It should answer:

* What is the app?
* How do I install it?
* How do I run it?
* What stack does it use?
* How do I configure environment variables?
* How do I deploy it?

---

## Current GPT-derived project direction

The GPT chat information points toward a business website project.

The likely direction:

```text
Frontend: Next.js + TypeScript
Backend: Next.js API routes first, NestJS later if needed
Database: PostgreSQL
ORM: Prisma
Admin: custom admin or Strapi
Hosting: Vercel + managed PostgreSQL
Storage: Cloudflare R2 or S3-compatible storage
CDN/DNS: Cloudflare
SEO: SSR, metadata, schema markup, sitemap
```

Possible MVP features:

* multilingual pages
* store list
* store detail pages
* news/promotions
* pricing tables
* contact forms
* collaboration forms
* admin panel
* SEO metadata
* sitemap
* image optimization

Not first priority:

* loyalty system
* barcode/account integrations
* push notifications
* analytics dashboard

---

## Immediate TODO for this repo

* [ ] Decide whether to rename `Knowlage` to `Knowledge`
* [ ] Decide whether to rename `repo_knowlage.` to `repo_knowledge`
* [ ] Decide whether to rename `expiriments` to `experiments`
* [ ] Create `synthesis/business-website-mvp-plan.md`
* [ ] Create `decisions/001-choose-initial-stack.md`
* [ ] Create `beliefs/web-project-architecture-beliefs.md`
* [ ] Create `expiriments/001-nextjs-postgres-prototype.md`
* [ ] Extract useful points from `GPT_Chat/Getting_info/`
* [ ] Keep raw GPT files, but do not rely on them as final documentation

---

## Immediate TODO for the project repo

* [ ] Write the project README
* [ ] Choose exact stack after the first decision record
* [ ] Initialize the app
* [ ] Add environment example file
* [ ] Add first database schema draft
* [ ] Add first public page prototype

---

## Commit message examples

Knowledge repo:

```bash
git commit -m "Add business website MVP synthesis"
git commit -m "Record initial stack decision"
git commit -m "Add Next.js prototype experiment plan"
```

Project repo:

```bash
git commit -m "Initialize Next.js application"
git commit -m "Add initial Prisma schema"
git commit -m "Create store listing page prototype"
```

---

## Anti-patterns

Avoid:

* using the knowledge repo as the project repo
* dumping GPT output without processing it
* making project decisions without recording why
* mixing beliefs and decisions in one file
* coding before defining the MVP
* collecting resources without synthesis
* changing beliefs silently without revision notes
* treating GPT answers as final authority

---

## Final principle

The project repo stores the product.

The knowledge repo stores the reasoning that creates the product.

Together, they let you track both what you built and how your thinking improved while building it.
