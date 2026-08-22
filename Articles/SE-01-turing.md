# The Turing Test Was Passed. It Turned Out Not to Matter.

*Article 1 of 4 — on what modern software engineering actually is*

---

In 1936, Alan Turing described a machine that does not exist.

It has an infinite tape, a head that reads and writes one symbol at a time, and a finite table of rules. It is slower than any computer ever built and simpler than a pocket calculator. Nobody has ever manufactured one.

It is also one of the foundations modern computer science rests on.

This series starts there, because any serious argument about AI and software engineering needs to be precise about what Turing's two famous ideas actually claim.

They are usually discussed together.

They should not be.

* One is a formal model of computation.
* The other is an empirical test for a question about machine intelligence.

One is foundational. The other was always a proxy.

---

## The definition

Peter Linz defines a Turing machine as a seven-tuple:

**M = (Q, Σ, Γ, δ, q₀, □, F)**

where:

* **Q** — the set of internal states
* **Σ** — the input alphabet
* **Γ** — the tape alphabet
* **δ** — the transition function
* **□** — the blank symbol
* **q₀** — the initial state
* **F** — the set of final states

The transition function carries the whole machine:

**δ: Q × Γ → Q × Γ × {L, R}**

Read it as an engineer rather than a mathematician and it is very familiar. Given the state you are in and the symbol under the head, it determines:

* what state comes next,
* what symbol gets written,
* which direction the head moves.

That is a state machine with unbounded storage. Nothing more.

The simplicity is the point.

The Church-Turing thesis connects this small model to the general idea of an effective procedure: roughly, anything that can be computed by a mechanical procedure can be computed by a Turing machine.

Modern software is far more complicated in engineering terms. We have languages, databases, networks, message brokers, containers, orchestrators, GPUs and distributed systems.

The computations those systems perform can, in principle, be represented within a Turing-complete model.

It is worth being precise about what that does and does not say. It is a claim about **computability**, not about engineering. It says nothing about time, cost, concurrency, real-time deadlines, or a system that keeps interacting with the world while it runs — and those are exactly the things that make distributed systems hard.

But on the narrow question of what can be computed at all, the model underneath stays remarkably small.

---

## The part everyone skips

Once you have a formalism powerful enough to express general computation, you can ask that formalism questions about computations themselves.

That is where the limits appear.

**The halting problem is undecidable.** No algorithm can take every arbitrary program and input and correctly decide whether that program will terminate.

**Rice's theorem generalizes it.** Non-trivial semantic properties of arbitrary programs are, in general, undecidable.

So Turing did not give us a universal solution.

He gave us a universal *model* of computation, and then used that model to prove precise limits on what can be decided algorithmically.

---

## What that actually means for engineers

It does not mean you cannot reason about a program without running it.

Plenty of techniques establish real properties without execution:

* type systems
* static analysis
* model checking
* symbolic execution
* abstract interpretation
* formal verification
* plain code review

All of them are worth the hours you put into them.

The precise claim is narrower — and stronger for being narrow:

> For arbitrary programs, no general algorithm can determine every interesting property of runtime behavior from the source alone.

That is why engineering practice does not stop at reading code. We also:

* test
* instrument
* deploy gradually
* measure behavior under real load
* keep a way back

These are not compensation for sloppiness. They are the working response to a limit that was proved in 1936.

Hold onto that. It matters later in this series, when the program producing our code is itself something we cannot fully reason about.

---

## Turing's other idea

Fourteen years after the machine, Turing proposed something completely different in character.

In *Computing Machinery and Intelligence* (1950), he took the vague question "can machines think?" and replaced it with an operational one.

Instead of defining thinking, he proposed an imitation game: a human judge tries to tell a machine from a person through written conversation.

Russell and Norvig open *Artificial Intelligence: A Modern Approach* with this test, and then do something useful — they break it down. To pass, a machine needs:

* natural language processing
* knowledge representation
* automated reasoning
* machine learning

The "total Turing test" adds a video channel and physical objects, and with them computer vision and robotics.

Replacing a property you cannot define with a proxy you can measure is a legitimate engineering move. We make it constantly.

But a proxy is still a proxy.

* The Turing machine is a formal model. You can prove things about it.
* The Turing test is a behavioral benchmark. You can only run it.

They are not the same kind of object.

---

## So: did we pass it?

Yes. There is now a controlled result that deserves to be taken seriously.

Cameron Jones and Benjamin Bergen ran randomized, pre-registered three-party Turing tests. A judge held simultaneous five-minute conversations with a real person and a machine, then chose which was which.

The results:

* **GPT-4.5** with a humanlike persona prompt — judged human **73%** of the time
* **LLaMa-3.1-405B** with a persona prompt — **56%**, roughly chance
* **ELIZA**, a pattern-matching script from 1966 — **23%**
* **GPT-4o** without a persona prompt — **21%**

GPT-4.5 was judged human more often than the actual person it was competing against.

The caveats matter, and are worth stating plainly:

* Five minutes is short.
* The persona prompt did substantial work.
* The experiment measured human identification — not understanding, consciousness, or general intelligence.

But within the property being tested, the result is unambiguous.

---

## And then nothing happened

Here is the genuinely interesting part.

A benchmark proposed seventy-five years ago was finally passed under controlled conditions, and the software industry did not acquire a new engineering objective.

* No architecture review became easier.
* No production system became more reliable.
* Nobody started paying for software because it could convincingly imitate a person.

Why?

Because indistinguishability from a human was never the property anyone was buying.

Software gets paid for when it is:

* correct
* available
* affordable
* secure
* maintainable
* fixable at 3 a.m.

Russell and Norvig anticipated this long before today's models. AI research has mostly focused on the underlying principles of intelligence, rather than on reproducing human behavior closely enough to fool an evaluator.

Their analogy is the one that sticks: aeronautical engineering does not define its goal as building machines that fly so much like pigeons that they fool other pigeons.

We did not get flight by imitating birds.

We got it by understanding lift.

Passing a behavioral benchmark tells you something about the behavior. It does not tell you the benchmark was measuring the property you actually cared about.

---

## What this leaves us with

Strip away the mythology and two lessons remain.

**From the machine:**
A universal model of computation, together with precise limits on what can be decided about arbitrary programs from their source.

**From the test:**
A machine can produce language that humans, under controlled conditions, cannot reliably tell apart from a person's.

Put those side by side and a sharper question appears.

For the whole history of computing, the path from intent to behavior looked like this:

> human intent → specification → source code → compiler → machine behavior

We built programming languages precisely so people could express instructions at higher and higher levels of abstraction.

Now something new has appeared. A machine takes instructions in ordinary English and returns executable software.

And we already know a few things:

* We know what a compiler is.
* We know what guarantees a traditional compiler provides.
* We know there are hard limits on what can be decided about a program's behavior from its source.

So:

**If the source language can now be English — what exactly have we built?**

That is the question for the next article.

---

## References

1. Turing, A. M. *On Computable Numbers, with an Application to the Entscheidungsproblem.* Proceedings of the London Mathematical Society, s2-42(1), 230–265. https://doi.org/10.1112/plms/s2-42.1.230
   *(Read to the Society in November 1936; printed in the 1937 volume. Universally cited as the 1936 paper.)*
2. Turing, A. M. (1950). *Computing Machinery and Intelligence.* Mind, LIX(236), 433–460. https://doi.org/10.1093/mind/LIX.236.433
3. Linz, P. *An Introduction to Formal Languages and Automata.* Jones & Bartlett Learning.
4. Russell, S. J. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach*, 4th edition. Pearson.
5. Jones, C. R. & Bergen, B. K. (2025). *Large language models pass a standard three-party Turing test.* PNAS.
   https://www.pnas.org/doi/10.1073/pnas.2524472123 — preprint: https://arxiv.org/abs/2503.23674
