

# Lecture 01 — Why Capable Agents Still Fail

The main idea of this lecture was that strong models do not automatically mean reliable results.

A common mistake is assuming that if a model performs well on benchmarks or demos then it should perform equally well on real work. But real tasks are messy. They require understanding context, using tools, remembering state, verifying results, and working across multiple steps. That’s where agents often break. ([Walking Labs][1])

The lecture introduces the idea of a **capability gap**.

A model can look extremely capable in evaluation environments but struggle in actual engineering tasks. Example given was benchmarks like SWE-bench where even strong systems still fail a large portion of tasks. Real work is not “answer one question”; it is more like understanding a repo, making changes, testing, debugging, and finishing correctly. ([Walking Labs][1])

The most interesting idea was the concept of a **harness**.

Harness = everything around the model.

Not the model weights themselves.

This includes:

* instructions
* available tools
* environment
* memory/state
* verification
* execution flow

Basically the model is only one part of the system. The harness is the thing helping the model operate correctly. ([Walking Labs][1])

## The Horse Analogy

The model is like a powerful horse. Making the horse stronger doesn’t guarantee reaching the destination. The harness (saddle, reins, guidance) is what turns capability into reliable movement. ([miraflow.ai][2])

Another term introduced was **harness-induced failure**.

Meaning:
the model may actually be capable enough, but the surrounding system causes failure.

Example:
Instead of saying:

> Claude failed.

Ask:

* Were instructions unclear?
* Did the agent lack context?
* Were tests missing?
* Was environment setup broken?
* Did previous progress disappear?

The failure might not be intelligence related at all. ([Walking Labs][1])

The lecture breaks failures into layers.

1. Task specification → requirements unclear
2. Context provision → important info not visible
3. Execution environment → tools/setup/dependencies bad
4. Verification feedback → no way to know success
5. State management → no persistence between sessions

When something breaks, the recommendation is not to immediately switch to a stronger model. First figure out which layer failed. ([DEV Community][3])

One idea I liked was the **verification gap**.

Agents often say:

> Done.

But nothing actually confirms that.

Confidence ≠ correctness.

So “definition of done” should be explicit and machine-checkable.

Examples:

* tests pass
* lint passes
* type checks pass
* expected output exists

Otherwise the agent invents its own stopping point. ([Walking Labs][1])

The practical loop from the lecture:

Execute task → observe failure → identify harness layer → improve harness → retry.

Over time the system improves instead of endlessly changing prompts or upgrading models. ([Walking Labs][1])

Small takeaway I wrote for myself:

> Don’t ask “Which model should I use?” first. Ask “What environment am I giving the model to succeed in?”

[1]: https://walkinglabs.github.io/learn-harness-engineering/en/lectures/lecture-01-why-capable-agents-still-fail/?utm_source=chatgpt.com "Lecture 01. Strong Models Don't Mean Reliable Execution"
[2]: https://miraflow.ai/blog/harness-engineering-why-88-percent-ai-agents-fail?utm_source=chatgpt.com "Harness Engineering: Why 88% of AI Agents Fail - Miraflow AI"
[3]: https://dev.to/truongpx396/harness-engineering-quick-actionable-guide-2b93?utm_source=chatgpt.com "🛠️ Harness Engineering — Quick Actionable Guide 🤖"
