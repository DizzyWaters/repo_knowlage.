# Cognitive PKM Repository

> A Git-based Personal Knowledge Management system for tracking the thinking process behind a Software Engineering project.

---

## Overview

This repository is a structured knowledge base for the Software Engineering course.

It is not the actual commercial website project. The actual implementation lives in a separate project repository:

```text
../Project/repo_project.
```

This repository tracks the thinking behind that project:

* how my understanding evolves
* what I learn from GPT chats and research
* which technical and product decisions I make
* which experiments I run
* what results I observe
* how the project direction changes over time

The main project currently supported by this knowledge base is:

```text
Commercial Website Prototype
```

The goal is to build a modern, maintainable, SEO-friendly commercial website prototype with pages for business information, stores, promotions, pricing, and contact forms.

---

## Purpose

Most note systems focus on collecting information.

This repository focuses on structured software engineering thinking.

It is used to:

* separate raw information from processed knowledge
* document decisions before and after implementation
* track assumptions and uncertainty
* record experiments and their outcomes
* preserve useful GPT chat information
* support long-term learning through Git history

The goal is not to create more notes.

The goal is to make better engineering decisions.

---

## Core Principles

### 1. Separate thinking layers

Different types of knowledge should be stored separately.

* `inbox/` → raw unprocessed notes
* `GPT_Chat/` → raw GPT conversations and AI-generated source material
* `beliefs/` → assumptions and current mental models
* `decisions/` → choices made under uncertainty
* `expiriments/` → prototypes, tests, results, and lessons
* `synthesis/` → processed summaries and higher-level conclusions
* `resources/` → useful external references
* `docs/` → documentation about this knowledge system

This prevents mixing opinions, actions, outcomes, and final conclusions.

---

### 2. Write for future understanding

Each entry should be understandable later without needing to remember the full context.

Good entries explain:

* what problem was being considered
* what options existed
* what reasoning was used
* what was decided or learned
* what remains uncertain

---

### 3. Use Git as a learning system

Git is used not only for storing files, but also for tracking how thinking changes.

Commits should describe changes in understanding, not just file edits.

Good examples:

```bash
git commit -m "Add initial commercial website MVP synthesis"
git commit -m "Record decision to start with Next.js"
git commit -m "Add first store page prototype experiment"
```

Avoid vague commits:

```bash
git commit -m "update"
git commit -m "notes"
git commit -m "stuff"
```

---

### 4. Be explicit about uncertainty

Software projects involve uncertainty.

This repository should make uncertainty visible by tracking:

* hypotheses
* assumptions
* open questions
* risks
* observations
* failed attempts
* reconsideration conditions

A wrong assumption is useful if it is recorded clearly and later corrected.

---

### 5. Prefer synthesis over accumulation

Raw notes are only useful when they are processed.

This repository should not become a pile of GPT answers and links.

Important information should eventually be converted into:

* a belief
* a decision
* an experiment
* a resource
* a synthesis note

---

## Repository Structure

Current structure:

```text
repo_knowlage./
├── README.md
├── AGENTS.md
├── inbox/
│   └── README.md
├── GPT_Chat/
│   └── Getting_info/
│       ├── asking_for_plan
│       └── target_info
├── beliefs/
│   └── README.md
├── decisions/
│   └── README.md
├── expiriments/
│   └── README.md
├── synthesis/
│   └── README.md
├── resources/
│   └── README.md
└── docs/
    └── CONCEPT.md
```

Recommended spelling cleanup:

```text
repo_knowlage.  -> repo_knowledge
expiriments     -> experiments
```

If these names are already used in GitHub or course materials, they can stay as they are. If not, it is better to fix them early.

---

## Folder Descriptions

### `inbox/`

Raw, unprocessed information.

Use this folder for:

* quick ideas
* copied notes
* rough requirements
* unclear thoughts
* temporary planning material

The inbox is temporary. Important notes should later be moved into a structured folder.

---

### `GPT_Chat/`

Raw GPT conversation material.

Use this folder for:

* GPT answers
* planning conversations
* extracted project requirements
* architecture suggestions
* implementation advice

GPT output should not be treated as final truth. It should be processed into decisions, beliefs, experiments, resources, or synthesis.

Current GPT chat material is related to planning a commercial website prototype.

---

### `beliefs/`

Current assumptions or mental models.

Examples for this project:

* Next.js is a strong choice for an SEO-friendly commercial website.
* PostgreSQL is suitable for structured business content such as stores, promotions, and pricing.
* The prototype should focus on public pages before complex integrations.

Each belief should explain:

* statement
* context
* evidence
* counterarguments
* status

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

Documented choices made under uncertainty.

Examples:

* choosing the initial technology stack
* defining MVP scope
* deciding whether to use a CMS or custom admin panel
* deciding which features are not part of the first prototype

Each decision should include:

* context
* alternatives
* decision
* reasoning
* expected outcome
* risks
* reconsideration conditions

Example file:

```text
decisions/001-choose-initial-stack.md
```

---

### `expiriments/`

Prototype and testing logs.

Use this folder for:

* feature prototypes
* technology tests
* deployment tests
* database experiments
* failed attempts
* lessons learned

Example experiments:

* testing a static Next.js store page
* testing mock data structure for promotions
* comparing Strapi with a custom admin panel
* deploying a prototype to Vercel

Example file:

```text
expiriments/001-nextjs-static-prototype.md
```

---

### `synthesis/`

Higher-level summaries and conclusions.

Use this folder for:

* weekly progress summaries
* project direction summaries
* MVP plans
* architecture summaries
* lessons learned
* current open questions

This is where scattered information becomes useful direction.

Recommended first file:

```text
synthesis/business-website-mvp-plan.md
```

---

### `resources/`

Useful references.

Use this folder for:

* documentation links
* tutorials
* competitor examples
* articles
* API references
* hosting notes
* design references

Resources should be summarized when they influence the project direction.

---

### `docs/`

Documentation about this knowledge system.

Use this folder for:

* concept explanation
* workflow rules
* templates
* Git usage notes
* agent usage notes

Current file:

```text
docs/CONCEPT.md
```

---

## Project Connection

This knowledge base supports the development of:

```text
Commercial Website Prototype
```

The actual implementation is stored separately in:

```text
../Project/repo_project.
```

This knowledge repository documents:

* project planning
* stack choices
* MVP scope
* technical trade-offs
* GPT chat extraction
* prototype results
* learning progress

The project repository should contain:

* source code
* application README
* package configuration
* tests
* deployment files
* environment examples

Simple rule:

```text
Project repo   = what is built
Knowledge repo = why it is built that way
```

---

## Current Project Direction

The current project idea is a commercial website prototype.

Expected early stack:

```text
Frontend: Next.js
Language: TypeScript
Styling: Tailwind CSS
Database: PostgreSQL later
ORM: Prisma later
Hosting: Vercel or similar later
```

Prototype MVP:

* home page
* about page
* stores / locations page
* store detail page
* promotions or news page
* pricing page
* contact form
* responsive design
* SEO metadata

Not first priority:

* loyalty system
* barcode/account integration
* push notifications
* analytics dashboard
* payment system

---

## Workflow

Use this repository with the following loop:

```text
Capture -> Classify -> Decide -> Build -> Test -> Synthesize -> Commit
```

### 1. Capture

Put raw notes or GPT output into `inbox/` or `GPT_Chat/`.

### 2. Classify

Decide what type of knowledge it is:

* belief
* decision
* experiment
* resource
* synthesis

### 3. Decide

Record major technical or product choices in `decisions/`.

### 4. Build

Implement the decision in the project repository.

### 5. Test

Record results and lessons in `expiriments/`.

### 6. Synthesize

Summarize what changed in `synthesis/`.

### 7. Commit

Commit both the knowledge update and the project implementation.

---

## Agent Usage

This repository should also be readable by coding agents.

The file `AGENTS.md` should give agents a short map of the repository and explain where to find:

* active plans
* decisions
* experiments
* GPT chat material
* project repository location

`AGENTS.md` should stay short. It should point to deeper files instead of duplicating everything.

---

## Usage During the Course

This repository will be used to:

* document software engineering learning
* preserve GPT-assisted planning
* track progress on the commercial website prototype
* record technical and product decisions
* analyze implementation attempts
* improve future iterations

---

## Immediate TODO

* [ ] Create `AGENTS.md`
* [ ] Create `synthesis/business-website-mvp-plan.md`
* [ ] Create `decisions/001-choose-initial-stack.md`
* [ ] Create `beliefs/commercial-website-architecture.md`
* [ ] Create `expiriments/001-nextjs-static-prototype.md`
* [ ] Process `GPT_Chat/Getting_info/target_info`
* [ ] Process `GPT_Chat/Getting_info/asking_for_plan`
* [ ] Start implementation in `../Project/repo_project.`

---

## Goal

The goal is not to collect more notes.

The goal is to:

* improve engineering thinking
* make better technical decisions
* learn from real implementation
* keep project reasoning visible
* build a reusable knowledge system for future projects

---

## Author

Maksims Kulvanovskis

Computer Science Student
