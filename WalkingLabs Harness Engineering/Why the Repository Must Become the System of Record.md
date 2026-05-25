
# Lecture 03 — Why the Repository Must Become the System of Record

This lecture’s main idea was that if an agent is doing engineering work, then the **repository should become the source of truth**.

- Not Slack.
- Not someone’s memory.
- Not random chat history.
- Not “we discussed this last week.”

If important information exists outside the repo, the agent is effectively blind to it.

The lecture argues that people often treat repositories as storage for code only, but for agent-based work the repository needs to contain enough information for someone (human or agent) to understand and continue the work without external help.

A sentence that stuck:

> If it matters to execution, it should exist in the repo.

---

One problem discussed was that humans are very good at carrying invisible context.

Example:

Developer knows:

* why a feature exists
* which approach already failed
* where docs are
* what not to touch

But none of that may exist in code/docs.

When an agent enters the project, all of that hidden knowledge disappears.

So the repo must start storing decisions, instructions and progress explicitly.

---

The lecture separates **record of work** from **conversation about work**.

Chats are temporary.

Repositories persist.

If a discussion leads to a decision, the decision should move into the repo.

Example:

Bad:

```txt
Slack:
"Let's use Redis instead."
```

Good:

```txt
docs/decisions/use-redis.md
```

Because later nobody remembers why that happened.

---

Another important idea was reducing dependency on context windows.

People sometimes think:

> Bigger context = smarter agent.

But the lecture pushes the opposite direction.

Instead of giving agents huge conversations, structure information so they can discover only what matters.

Examples:

* README
* architecture docs
* feature specs
* task files
* ADRs
* progress logs

The repo becomes searchable memory instead of one giant prompt.

---

The lecture talked about **externalized cognition**.

Basically:

Move thinking out of heads and into artifacts.

Examples:

Instead of remembering:

```txt
We rejected option B because performance was bad
```

write:

```txt
docs/decisions/rejected-option-b.md
```

Instead of remembering:

```txt
Migration incomplete
```

write:

```txt
progress/current-state.md
```

This reduces rework.

---

One thing I liked was the idea that repositories should answer questions automatically.

Someone opening the repo with a fresh session, the agent should quick be able to find:

```txt
What is this?
How does it run?
What are we building?
What already happened?
What should happen next?
```

If these answers require asking someone, repository quality is weak.

---

The lecture also mentioned that state should survive.

Agents shouldn’t restart every session like a new employee.

Useful files become things like:

```txt
/README.md
/docs
/architecture
/decisions
/tasks
/progress
```

The repo starts behaving more like an operating system for work instead of a folder of code.

---

One thing I wrote down:

Code explains **what exists**.

Repository explains **why it exists**.

That distinction felt important.

---

Small takeaway for myself:

> Don’t optimize for giving the agent more context. Optimize for making context permanent and discoverable inside the repository.

