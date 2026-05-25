
# Lecture 02 — What a Harness Actually Is

The biggest point of this lecture was that a harness is **not a prompt file**. People often say “I built a harness” when they mean they wrote a long instruction file, but that’s only one small piece. A harness is basically the entire environment around the model that helps it do useful work. ([walkinglabs.github.io][1])

The lecture started with an analogy that made sense.

Imagine being hired into a codebase with no README, no docs, nobody tells you how tests run, and everything important is hidden. Even if you’re a good engineer, most of your time would go into understanding the environment instead of solving the task.

Agents have the same problem except worse. Humans can ask teammates questions. Agents only know what exists inside the environment they’re given. ([walkinglabs.github.io][1])

The main takeaway:

> Model capability and task success are not the same thing.

A strong model inside a bad harness performs badly.

A decent model inside a good harness can perform surprisingly well. ([OpenAI][2])

The lecture defines harness as having **five subsystems**.

### Instructions

This is not just prompts.

Instructions mean:

* rules
* docs
* project structure
* how work should happen

Examples:

* `AGENTS.md`
* `CLAUDE.md`
* feature lists
* architecture docs

The important idea was:

If information isn’t inside the repo, the agent basically doesn’t know it exists. ([walkinglabs.github.io][1])

### Tools

Tools are what allow the model to act.

Without tools:
Agent = intelligent autocomplete.

With tools:
Agent = can execute.

Examples:

* shell commands
* file editing
* APIs
* browser
* testing tools

Interesting thought:
An agent without tools doesn’t build software, it only talks about building software. ([Viblo][3])

### Environment

This is the world the agent runs inside.

Things like:

* installed dependencies
* permissions
* repo structure
* runtime setup

If environment setup is broken, even perfect instructions won’t help.

Example:
Agent knows tests should run but dependencies are missing → task appears impossible. ([walkinglabs.github.io][1])

### State

This one felt important.

Agents lose context.

So state exists to preserve progress between sessions.

Examples:

* progress files
* feature lists
* logs
* task tracking
* session handoff

The lecture referenced that long-running agents need explicit recovery paths and persistence. Otherwise every session starts from zero again. ([walkinglabs.github.io][1])

This reminded me:

Chat history is not memory.

Stored state is memory.

### Feedback / Verification

This is how the agent knows whether it actually succeeded.

Examples:

* tests
* lint
* type checks
* smoke tests

Without verification:

Agent:

> I think this is done.

With verification:

System:

> prove it.

This idea keeps showing up:
“done” should not be subjective. ([walkinglabs.github.io][1])

One sentence I wrote down:

> A harness does not make the model smarter. It makes the model usable.

Another useful idea:

Instead of asking:

> Which model should I switch to?

Ask:

> Which subsystem is weak?

* instructions?
* tools?
* environment?
* state?
* verification?

A lot of failures that look like “AI is bad” are actually missing infrastructure around the model. ([Data Science Dojo][4])

[1]: https://walkinglabs.github.io/learn-harness-engineering/en/lectures/lecture-02-what-a-harness-actually-is/?utm_source=chatgpt.com "Lecture 02. What Harness Actually Means"
[2]: https://openai.com/index/harness-engineering/?utm_source=chatgpt.com "Harness engineering: leveraging Codex in an agent-first ..."
[3]: https://viblo.asia/p/learn-harness-engineering-by-building-a-mini-claude-code-bNVQGoYpJvR?utm_source=chatgpt.com "Learn Harness Engineering by Building a Mini Claude Code"
[4]: https://datasciencedojo.com/blog/harness-engineering/?utm_source=chatgpt.com "Harness Engineering: Uncovering What It Is ..."

