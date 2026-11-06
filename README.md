# Aleksa Obradović

Backend developer. I mostly write Node.js and TypeScript: REST APIs on Express, MySQL schemas with Prisma, and the authentication and access rules around them. I run my own projects in Docker on a Linux home server behind Cloudflare Tunnels.

[aleksao.me](https://aleksao.me)

## Projects

All of them are a TypeScript API (Express 5, Prisma, MySQL 8) plus an Angular client, built on the same layered architecture: `routes → controllers → services → repositories`. Each one runs in production on my own server.

**StaffAway** | [staffaway.space](https://staffaway.space) | [backend](https://github.com/aleksa0206/StaffAway-Backend) | [frontend](https://github.com/aleksa0206/StaffAway-Frontend)
Multi-tenant leave management. Employees request time off, managers and HR approve it. Role and per-record authorization (`Employee`, `Manager`, `Hr`), overlap and notice rules, leave balances, S3 attachments, audit log, API keys.

**Focentra** | [focentra.space](https://focentra.space) | [backend](https://github.com/aleksa0206/Focentra-Backend) | [frontend](https://github.com/aleksa0206/Focentra-Frontend)
Study time tracking against goals: a timer, manual entries and pace status (ahead, on track, behind). Shared goals with invite links, statistics computed in the user's time zone, and integration tests for race conditions such as parallel timer starts and overlapping entries.

**HomeWise** | [homewise.live](https://homewise.live) | [backend](https://github.com/aleksa0206/HomeWise-Backend) | [frontend](https://github.com/aleksa0206/HomeWise-Frontend)
A household app: shared monthly budget, recurring bills, chores and shopping lists. Money is stored as `Decimal` and paying a bill records the expense and moves the due date in one transaction.

**Remly** | [remly.space](https://remly.space) | [backend](https://github.com/aleksa0206/Remly-Backend) | [frontend](https://github.com/aleksa0206/Remly-Frontend)
Personal contacts with a meeting history, planned meetings, "keep in touch" reminders and birthdays.

**Portfolio** | [aleksao.me](https://aleksao.me) | [backend](https://github.com/aleksa0206/Portfolio-Backend) | [frontend](https://github.com/aleksa0206/Portfolio-Frontend)
My website, built as a terminal with a virtual file system, backed by a small CMS API with an admin dashboard.

**Prompt-Injection-Classifier** | [repo](https://github.com/aleksa0206/Prompt-Injection-Classifier)
ModernBERT fine-tuned to flag prompt-injection and jailbreak attempts before they reach an LLM, compared against a TF-IDF baseline.

## What the backends have in common

- JWT access tokens kept in memory on the client; opaque refresh tokens stored hashed, rotated on every use and sent only as `httpOnly` cookies
- Optional TOTP two-factor authentication, account lockout, password reset with hashed, expiring tokens
- Rate limiting stored in the database, input validation with Zod, environment checked at startup
- Every query scoped to the tenant or the user; guarded updates and transactions where two requests could race
- Integration tests with Jest and Supertest against a real MySQL database, run in GitHub Actions
- Multi-stage Docker images, Docker Compose stacks, Prometheus metrics and Pino logs

## Tools

**Backend:** Node.js, TypeScript, Express, Prisma, Zod, REST
**Data:** MySQL, SQL, migrations
**Frontend:** Angular (standalone components, signals), SCSS
**Ops:** Docker, Docker Compose, Linux, nginx, Cloudflare Tunnel, GitHub Actions, Prometheus, Grafana
**Testing:** Jest, Supertest, Vitest
**Also:** Python (PyTorch, Hugging Face Transformers, scikit-learn), Django
