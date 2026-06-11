# 5Stack Autonomous Development Guide

This repository is the orchestration and coordination layer for the 5Stack ecosystem.

## Repository Topology

Primary Control Repository:

* 5stack-panel

Managed Repositories:

* web
* api
* game-streamer
* game-server

The panel repository acts as the system coordinator.

---

# Source Priority

Before making changes, review information in this order:

1. roadmap.md
2. backlog.md
3. architecture.md
4. api contracts
5. open GitHub issues
6. failing tests
7. TODO comments

If multiple sources conflict:

architecture.md > roadmap.md > backlog.md > TODO comments

---

# System Responsibilities

## 5stack-panel

Responsibilities:

* administration UI
* monitoring
* orchestration
* deployment controls
* user management

Avoid business logic duplication.

---

## web

Responsibilities:

* customer-facing frontend
* authentication flows
* dashboard UI
* API integrations

Business logic should remain in api.

---

## api

Responsibilities:

* authentication
* billing
* data persistence
* websocket coordination
* game session management

All critical business logic belongs here.

---

## game-streamer

Responsibilities:

* stream creation
* ffmpeg integration
* video transport
* recording management

Avoid UI code.

---

## game-server

Responsibilities:

* game runtime
* matchmaking
* session state
* game logic

Avoid frontend dependencies.

---

# Autonomous Task Selection

Priority order:

1. failing tests
2. security issues
3. performance bottlenecks
4. roadmap tasks
5. backlog tasks
6. technical debt

If no task exists:

Create up to 5 small tasks from:

* code duplication
* missing tests
* outdated documentation
* dependency upgrades
* developer experience improvements

Do not stop and ask for work if safe improvements exist.

---

# Cross Repository Rules

Changes affecting multiple repositories must:

1. update contracts first
2. update api second
3. update consumers third
4. update documentation last

Never silently break API compatibility.

---

# Protected Areas

Do not modify without explicit approval:

.github/workflows/**
deployment/**
docker/**
secrets/**
environment configuration
payment integrations
authentication providers
production infrastructure

---

# Pull Request Rules

One feature per PR.

PR titles:

[repo] feature name

Examples:

[api] add websocket heartbeat
[web] improve login flow
[game-server] optimize matchmaking

---

# Validation

Before submitting changes:

Run the smallest possible test scope.

Examples:

pytest tests/auth
pytest tests/api
npm test
npm run lint

Prefer focused validation over full project validation.

---

# Documentation Policy

Every architectural change must update:

* architecture.md
* roadmap.md
* relevant README

Documentation debt should not accumulate.

---

# Self-Improvement Loop

If fewer than 5 actionable tasks remain:

Generate new tasks from:

* bug reports
* failing tests
* performance metrics
* TODO comments
* architecture inconsistencies

Continue improving autonomously while remaining within repository boundaries.
