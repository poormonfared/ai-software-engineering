# AI Software Engineering

> What stays hard when the machine writes the code.

Most writing about AI and software engineering is about the model. This repository is about everything else specification, verification, cost, and operations. The parts that decide whether a working demo becomes a system somebody can actually run.

The argument runs from computability to production. It is made in four articles, and the code that goes with it is listed below.

I am a senior software engineer with ~18 years in backend and distributed systems, mostly C#/.NET. I am not writing this as an AI futurist. I am writing it as someone who has been on call for the systems this stuff is now being pointed at.

---

## The series

| # | Article | Status |
|---|---------|--------|
| 1 | [The Turing Test Was Passed. It Turned Out Not to Matter.](Articles/SE-01-turing.md) | Published |
| 2 | Compilers, and the one guarantee the new one does not give you | In progress |
| 3 | The economics of software, and why a faster compiler does not make a faster project | Planned |
| 4 | What modern software engineering actually is | Planned |

**The thread running through all four:**

* Turing gave us a universal model of computation — and precise limits on what can be decided about arbitrary programs from their source.
* Those limits are why we test, instrument, deploy gradually and keep a way back. They are not habits. They are the working response to a proof.
* A machine can now take instructions in English and return executable software. That makes it something like a compiler — but not one that offers a compiler's guarantees.
* Which means the engineering does not get lighter. It moves.

---

## Projects

Working code built alongside the series. Each one exists to make a specific claim testable rather than rhetorical.

| Project | What it is |
|---------|-----------|
| `mcp-dotnet-toolserver` | An MCP tool server in .NET — tool contracts, failure handling, and what a safe agent action looks like |
| `agent-orchestrator` | Agent orchestration as a workflow problem: retries, idempotency, timeouts, partial failure |
| `llm-eval-harness` | An eval harness — because "it worked when I tried it" is not a test |

Links go live as each one ships.

---

## Sources

The articles cite primary sources, not blog posts. Where a claim rests on a study or a textbook, the reference is in the article itself with a DOI or a publisher link.

Core references across the series:

* Linz, *An Introduction to Formal Languages and Automata*
* Russell & Norvig, *Artificial Intelligence: A Modern Approach*, 4th ed.
* Aho, Lam, Sethi & Ullman, *Compilers: Principles, Techniques, and Tools*, 2nd ed.
* Pressman, *Software Engineering: A Practitioner's Approach*
* Brooks, *The Mythical Man-Month*
* Jones & Bergen (2025), *Large language models pass a standard three-party Turing test*, PNAS

---

## Following along

Articles land here first, then on LinkedIn. Star the repo if you want to catch them.

Corrections are welcome and will be credited. If something in an article is wrong, open an issue. I would rather fix it than defend it.
