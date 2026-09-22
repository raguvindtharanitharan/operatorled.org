# Manifesto for Operator-Led Software Development

## Why a new development process for AI agents?

AI agents can now perform substantial development work, but the processes around them still largely assume humans do the work and review the results. As agents produce more code, review alone becomes an increasingly difficult way to maintain control.

**The proposed method**

**Operator-Led Software Development** is a way of building software in which a human operator sets intent, grants bounded authority to AI agents, judges the evidence, and accepts the outcome. AI agents may do the work, but the operator remains accountable for every change that is accepted into the codebase. **Nothing closes without the operator's verdict.**

> **The operator is in command** — the final authority, whether or not their hands are on the controls.

Proposed and authored by **Raguvind Tharanitharan** · [raguvind.com](https://raguvind.com)
The term **Operator-Led Software Development** is coined in this document
First written **19 August 2026**, while running two real projects
Published **7 September 2026** · version 1.0
Last revised **21 September 2026**

[Read the incidents that produced this →](https://raguvind.com/writing/faster-than-you-can-follow)

*This is the same text as [operatorled.org](https://operatorled.org), in Markdown. The page is canonical; the two change together.*

---

## 1 · Why this exists: what changed, and what broke

Today, we use these agents within familiar development workflows: assign a task, let the agent implement it, review the changes, run tests, and approve the result.

But this workflow leaves important questions unanswered. What decisions was the agent authorized to make? Did it stay within the agreed scope? What evidence proves the intended outcome was achieved? Who explicitly accepted the result?

The missing piece is not another coding agent. It is an operating model that connects intent, authority, execution, evidence, and acceptance.

Every software process is built around two questions: who does the work, and what needs coordinating. For decades, the first answer stayed the same: **people**. What changed was how their work was coordinated. **AI agents** change the first answer.

- **Waterfall** (1970s →) — Coordinates development through planned phases, documents, and handoffs.
- **Agile** (2001 →) — Coordinates iterative development through teams, collaboration, and feedback.
- **DevOps** (2009 →) — Connects development and operations through automation, continuous integration, and delivery.
- **AI agents** (now) — AI agents can perform substantial development work. The challenge increasingly includes establishing authority, verifying outcomes, and preserving accountability.

### Why existing development processes are not enough for AI agents

Existing tools solve important parts of the development process. But they do not automatically establish an end-to-end record of authority and acceptance.

| Existing tool | What it provides | What it does not automatically establish |
|---|---|---|
| Issue trackers | Record what needs to be done. | What decisions an agent is authorized to make. |
| Coding agents | Plan and execute development work. | Coding agents may provide permission controls, approval prompts, and activity logs. These do not, by themselves, establish an end-to-end process connecting what was authorized, what the agent did, the evidence produced, and the operator's final verdict. |
| Pull requests | Present changes for review. | Visibility into every consequential decision made during implementation. |
| CI/CD | Runs automated checks and delivery workflows. | Proof that the original product outcome was achieved. |

These are useful tools. The gap is not that they lack controls, but that those controls do not automatically form a single, durable chain from what was intended to what was authorized, executed, proven, and accepted.

**What broke is review as the mechanism of control.** AI agents can now plan, implement, test, review, and document work faster than one person can read it. In one four-day stretch on my own project, agents produced 144 small scripts against a live system. Each one carried a decision nobody had reviewed, because nobody reviews 144 of anything. Every skimmed *"looks good"* accepts decisions the operator did not actually judge, and nothing records that it happened. Tickets and chat transcripts were built to coordinate humans. They preserve the conversation, but not a durable record of intent, authority, action, and evidence.

> Trust changes hands one reflexive approval at a time, until the person accountable for the project no longer knows what is in it.

### What Operator-Led Software Development changes

The answer is not to watch every keystroke or make agents wait for permission at every step. A human operator sets the intent and approves a Plan that names, before work begins, the outcome and the evidence that will prove it. Approval grants a bounded Lease: the agent executes within it, makes the ordinary decisions the work requires, and returns to the operator when a boundary is crossed. Its actions and evidence stay on the record. The operator judges the result against the approved Plan and records a verdict.

**Agentic tools determine what an agent *can* do. This method establishes what it *may* do, under whose authority, and what must be proven before the outcome is accepted.** It does not replace coding agents, issue trackers, or CI/CD; it is the operating model for using them when agents perform the work.

**Two bets I am making**

**First:** most of the code that will exist in ten years has not been written yet, and most of it will not be written by hand. AI agents will produce software at a volume no human development process was designed to absorb.

**Second:** much of the software written over the last fifty years will be rewritten, replaced, or retired in the same window, and AI will supply both the pressure and the means: it will find weaknesses in old code faster than people can patch them by hand, and it will make translating that code cheap.

Both bets lead to the same place: code will arrive faster than humans can reasonably inspect it. [Security research](https://www.veracode.com/resources/analyst-reports/2025-genai-code-security-report/) has identified vulnerabilities in AI-generated code, reinforcing the need to verify changes before accepting them. Whoever is accountable for a codebase will need a way to decide which changes are accepted into it. That's what this is for.

## 2 · What we value

The items on the right can be useful. They must not substitute for the items on the left.

| We value | over |
|---:|:---|
| **accepted outcomes** | completed activity |
| **explicit authority** | assumed permission |
| **evidence** | confidence |
| **durable decisions** | conversational memory |
| **dependency clarity** | collision discovery |
| **bounded autonomy** | constant intervention |
| **economic visibility** | token anxiety |
| **durable learning** | ceremonial compliance |
| **a small process that is followed** | a complete process that is ignored |

## 3 · Twelve principles

Each one stands on its own. Each has its own anchor (`#p1` … `#p12`), so it can be quoted directly.

<a id="p1"></a>
### p1 · The operator is in command.

> "AI agents may propose and execute. The human operator alone sets direction, grants authority, and accepts outcomes."

Responsibility does not travel with the work. Aviation has the right phrase for it: the pilot in command is *"directly responsible for, and the final authority as to, the operation"* of the aircraft, whether or not their hands are on the controls. The operator remains accountable for every change they accept, even when agents did all the typing.

<a id="p2"></a>
### p2 · Authority is a lease: granted, bounded, and temporary.

An assignment is a lease, not ownership. It names the agent, the piece of work, what they may touch, and the conditions under which they have to come back to the operator. It does not last forever, and it does not stretch to cover whatever seems related. **Having access to a system is not permission to change it.**

<a id="p3"></a>
### p3 · AI agents propose and execute; the operator decides what they may decide.

AI agents are capable contributors. They are not the authority on the product. They can investigate, propose, build, test, review, document, and argue with the framing. Inside a lease, an agent makes the ordinary decisions the work requires. What it cannot do on its own is change the goal or the priority, widen the scope in any meaningful way, take on new risk, or accept its own result on the operator's behalf: those decisions return to the operator. Different agents have different capabilities. None has authority by default. Whatever authority an agent exercises was granted by the operator.

<a id="p4"></a>
### p4 · One question, one recommendation.

When a decision goes to the operator, it should be one question with a recommended answer. An agent that hands over a menu of options, instead of weighing them and recommending one, is passing its work upward, not asking for authority. Enough of those menus and a perfectly sound process starts to feel unbearable. We learned this the hard way.

<a id="p5"></a>
### p5 · Decisions arrive in product language.

The operator should not have to turn intent into technical instructions. Decisions come to them in the language of the product: what is changing, why it matters, what it costs, what could go wrong, and what they are being asked to decide. The technical detail lives behind the interface, where the operator can go looking for it but does not trip over it.

<a id="p6"></a>
### p6 · Challenge the framing before it gets expensive.

An AI agent should push back on weak framing while the work is still being shaped, when changing course is cheap. Once implementation starts, changing the framing gets expensive. A proposal with nothing under "where the framing is wrong" usually has not looked hard enough.

<a id="p7"></a>
### p7 · "It should work" is not evidence.

Evidence should match the risk: tests, observed behaviour, measurements, review findings, a demonstration someone else can reproduce. Evidence must be inspectable or reproducible, not merely reported by the agent. Decide what will count as proof before the work starts, and make sure the checks can actually fail. A confident sentence in an approved plan is not evidence, however well it is written.

<a id="p8"></a>
### p8 · Work is closed by evidence and acceptance, not by saying so.

Work is not finished because an agent stopped working on it. Implementation and acceptance are two different states: *implemented, awaiting acceptance* is an honest description; *done* is not. Technical checks can be automated and reviews can be delegated. Accepting the result is a human act. A rejection says what is missing and sends the work back with its history intact.

<a id="p9"></a>
### p9 · Nothing is hidden.

Failed attempts, rework, uncertainty, and cost all stay on the record. When a number is unknown, it is recorded as unknown, not as zero. Tokens consumed are not productivity. Cost is read against what was accepted, what had to be redone, and what was learned. Cost is context, not a score.

<a id="p10"></a>
### p10 · Durable decisions over conversational memory.

Any decision that changes direction, scope, authority, priority, or accepted risk has to survive outside the conversation it was made in: the question, the options, the operator's choice and their reason, when it took effect, and what it touched. A chat log is not a place to keep facts you will need next month.

<a id="p11"></a>
### p11 · No process theatre.

Every field, status, meeting, and metric has to help someone authorize, execute, prove, accept, or learn. If it does not, remove it. The method has no sprints or recurring ceremonies of its own; the work itself creates the events. A template filled in for form's sake is the theatre this document is trying to get rid of. A small process people follow beats a complete one they ignore.

<a id="p12"></a>
### p12 · It governs how a system is built, not how it behaves once it is running.

This method covers proposing, authorizing, executing, proving, and accepting. Its job ends when an outcome is accepted. What the finished system does in production is the business of that system's own controls, which have to work whether or not the build tooling is reachable. That is a boundary, not a gap. A method that also tried to govern every system it helped build would be an opinion about running a business bolted onto an opinion about building one.

## 4 · The loop: seven phases

Work moves through seven phases. Each marks a real change in certainty or authority, not merely a change in status. Two belong to the operator alone.

**Capture → Shape → Authorize** (operator) **→ Execute → Prove → Accept** (operator) **→ Learn**

*The loop is not strictly linear. A rejection returns work for correction with its history intact — in the record it then shows Needs Revision, not Backlog.*

1. **Capture** — An idea, request, defect, or concern is recorded without pretending it is ready. Capture protects the thought from being lost; it does not authorize work.
2. **Shape** — The problem, desired outcome, proposed scope, dependencies, risks, alternatives, and acceptance evidence are made clear enough for a decision. Shape is finished when there is a proposal: a document the operator can decide on, not a form someone filled in.
3. **Authorize** *(record state: Backlog)* — The operator chooses whether the work should proceed, its priority, its owner, its boundaries, and its investment appetite. What the operator authorizes is a Plan: the proposal Shape produced, read in full. Without a Plan there is nothing to authorize. Authorization creates a lease. Until authorization, the record shows the work as *Backlog*: captured, but not yet authorized. The label describes a condition. It is not an instruction to the operator.
4. **Execute** *(record state: In Progress)* — The assigned AI agent works within the lease and may make the ordinary implementation decisions the outcome requires. Any material scope expansion, new risk, collision with another agent, or exhausted investment appetite returns control to the operator.
5. **Prove** *(record state: Awaiting Verdict)* — The agent produces the evidence required by the authorized proposal, appropriate to the risk. A submitted result puts the record in *Awaiting Verdict*; the judgment that follows is the operator's alone.
6. **Accept** — The operator determines whether the evidence proves the authorized outcome. A rejection states what evidence or outcome is missing and sends the work back without erasing its history. In the record the work then shows *Needs Revision*, not Backlog: rejected work has been authorized, done and found wanting, and the state says so.
7. **Learn** — Material surprises become durable knowledge: a decision, a new rule, a defect, a changed acceptance condition, or an improvement to this process. Learning is complete only when it can change future behaviour.

**The Plan is the spine of the loop.** Shape produces it. Authorize approves it and fixes what was authorized. The lease grants authority to execute it. Activity records what was done under it. Prove produces the evidence it required. Accept judges the result against the outcome it named. A Plan authorizes nothing by itself; it becomes binding only when the operator approves it.

**An example, not a template.** An agent is asked to improve login performance without changing authentication behaviour.

- **Plan:** Reduce login latency below an agreed threshold without changing authentication behaviour. The Plan names, before work begins, the measurements and regression tests that will count as evidence.
- **Authorize:** The operator approves the Plan and grants a bounded Lease: this agent, this change, this scope.
- **Execute:** The agent implements the change within the authorized scope. A change to authentication behaviour is outside it and returns to the operator.
- **Prove:** The agent submits its performance measurements and regression test results against the conditions the Plan named.
- **Accept:** The operator judges the evidence against the approved Plan and records a verdict.

> **What Accept does not mean.** Accept is a judgement about proof, not about delivery. Nothing here records whether the work ever reached anyone, so an outcome that is accepted and never released is not yet a product outcome. Release is not an eighth phase, on purpose: until there is something to release, a release record would be a field nobody reads. Better to say the limit out loud than have someone discover it during an incident.

## 5 · The operating model

### The operator owns the product

- defines product intent and goals;
- chooses which Features matter and their order;
- authorizes work and assigns agents;
- resolves ambiguity, conflicts, and risk decisions;
- changes or stops work when the expected value no longer justifies the investment;
- accepts or rejects outcomes based on evidence;
- remains accountable for every change they accept, even when agents performed the work.

### The AI agents are capable contributors

- investigate and explain; propose designs, plans, and decompositions;
- implement authorized changes; test, review, and document;
- identify new work, defects, risks, and dependencies;
- challenge framing when the requested work would not achieve the goal.

**Without operator authority, never:** change the goal or priority · expand scope materially · take on new risk.

**Never, under any authority:** accept their own outcome.

**Never hide:** failed attempts · rework · uncertainty · cost.

**Evidence governs claims:** an agent does not declare a dependency resolved without evidence.

**Access is not authority:** having access to a system does not give an agent permission to change it.

### The structure of work

Every meaningful item leads upward to the intent it serves. Product purpose, the reason the product exists, is context a project may record; it is not a level of this structure. The method begins when purpose becomes a concrete product outcome worth pursuing. The structure is Feature → Story → Task and Bug; a Spec is an optional design record attached to a Feature, not a level of its own.

- **Feature** — A product-level outcome worth pursuing, stated with a clear goal, why it matters, and a way to recognize success. Its state is derived from the work below it, and that work exists to advance the outcome.
- **Spec** *(optional artifact)* — A short design record attached to a Feature when important decisions need to survive across multiple Stories. It carries no authority on its own. Once the operator freezes it, changing it requires a visible amendment.
- **Story** — A bounded, verifiable outcome that advances one Feature, and the unit the operator authorizes and accepts. User-facing or technical, it states what becomes true when it is done, not how; it defines what it includes, what it excludes, and the conditions the operator will judge its evidence against. Delivered through an operator-approved Plan, one approved and current at a time; rejected and superseded Plans keep their history. Not a change, and not sized by a sprint: as large as one decision to authorize, never estimated in points.
- **Task** — Bounded work with a stated expected result. Work outside the approved scope becomes a new Task, not an extra step slipped into the current one.
- **Bug** — A record that the software did something other than what was intended. Bugs keep their own history, because they show where both the product and the process are going wrong.

### The anatomy of a proposal

Shape produces a document, not a form. Its parts, in the order a reader meets them. The last three are written during and after the build. The depth of a proposal should match the scope and risk of the work. The obligation is to make the decision possible, not to fill every heading.

1. **In plain words**, before any detail: a story a non-technical reader can follow.
2. **Measurements taken today**, at a named commit, not impressions.
3. **The one idea this turns on**, argued against the alternative it beat.
4. **The boundaries, decided**, including the procedures the work will follow, by name.
5. **Deliberately not changed**, with the reason each thing stays as it is.
6. **Where the framing is wrong**: the proposal pushes back on itself first.
7. **How success is proven**, with checks that can actually fail.
8. **What the build found**: discoveries and corrections, left visible.
9. **Done when, as it finished**: gates that were not met are marked, not passed over.
10. **What this does not fix**: the limit, stated plainly.

Two rules go with it. **The contract freezes but the document lives**: approval fixes the scope, boundaries, and acceptance conditions. The Plan may accumulate implementation notes, discoveries, and evidence. Changing the approved contract requires a new operator Decision, and the authorized change is recorded in the Plan. Acceptance is judged against the approved contract, including any authorized amendments. **A proposal earns trust through evidence, not formatting.** Numbers taken from a real commit, a correction left visible, a gate marked as not met: those are what make it trustworthy.

### Two ledgers beside the work

The work hierarchy records what is being done and why. Two append-only ledgers record what happened around it. The **activity ledger** holds every AI agent run against a work item: which agent acted, under which Plan, when it started and finished, how it ended, what it cost where the cost is known, and what evidence it produced (or why it produced none). The **decision ledger** holds every decision that changed direction, scope, authority, priority, or accepted risk, with the question, the options, the operator's choice and reason, and what it affected. The method requires these two records. How they are filled is an implementation matter: in the reference implementation, Ingee, the activity ledger also records the provider and model, and cost can be collected automatically only when an agent runs through an API that reports usage. An agent working in a terminal records its own runs, so the ledger holds what the agent reported, and a cost the provider did not report stays unknown rather than zero. That is why hiding cost or rework is on the short list of things an agent may never do.

### Two kinds of dependency

One work item has at most one executing owner unless collaboration is explicitly authorized. Several agents may investigate or review the same item, but their activities stay separately visible. And two kinds of dependency must not be confused. A **product dependency** means one outcome genuinely requires another outcome first. An **execution collision** means two activities may alter the same files, data, or external state. The first affects product order. The second affects safe coordination. Neither should be inferred only after a merge conflict occurs.

### Practices deliberately rejected

- **Backlog as authority.** Being recorded does not mean being approved.
- **Agent self-assignment without operator intent.** Availability is not priority.
- **Permanent assignments.** Leases expire or return for a decision.
- **Hidden rework.** A failed approach remains part of the history.
- **Conversation as memory.** Durable facts and decisions belong in the project.
- **Completion by assertion.** Evidence and acceptance close work.
- **One status for everything.** Execution, blockage, and acceptance are different facts.
- **Provider comparison by raw tokens.** Token systems are not economically or technically equivalent.
- **Process theatre.** A field, status, meeting, or metric must help authorize, execute, prove, accept, or learn — or be removed.
- **Premature platform building.** Abstraction is earned through repeated use.
- **The process as its own client.** Using the method to govern its own tooling produces ceremony about ceremony. The one day this process was pointed at its own development, it generated fifteen operator decisions and came close to being abandoned. It has to earn its keep on real work.

We also reject, as measures of success on their own: agent utilization, tokens per task, story points, velocity, burndown, and the number of items closed. Every one of them can improve while the product gets worse. What we look at instead: accepted outcomes and what they changed, time spent waiting for a decision, how often work is accepted the first time, rework as a share of total investment, defects found after acceptance, and how old the active leases and blocked items are.

## 6 · The vocabulary

A short glossary. These are the terms the rest of this document assumes.

- **Operator** — The one human who sets intent, grants authority, and accepts outcomes. Accountable for every change they accept, even when agents did the work.
- **AI agent** — A capable contributor — software that plans, writes, tests, and reviews under a human's direction — that may propose and execute, and decides only inside the authority it was granted.
- **Intent** — What the operator is trying to accomplish, stated as an outcome rather than a task and recorded in the structure of work. A Feature records the product outcome being pursued; a Story records the bounded outcome beneath it. Every piece of work leads upward to the intent it serves. Intent is what authority is granted for.
- **Plan** — A proposal, written to the anatomy, that an agent submits and the operator decides on. Proposed until decided; authorizes nothing by itself.
- **Lease** — Authority with edges: who may act, on what, within what scope, and until when. Created when the operator approves a plan; closed by the verdict.
- **Activity** — One recorded action by an agent under a lease, against the Plan it executes. Not a log line: an authorized action with its provenance attached.
- **Evidence** — Proof appropriate to the risk, attached to the acceptance conditions fixed before the work began.
- **Submission** — The agent's account of a result: what was done, what was not, and the evidence for each condition. Puts the work in Awaiting Verdict.
- **Verdict** — The operator's judgment on a submission: accept, reject, redirect, or stop, with a reason in the operator's own words.
- **Decision** — Any recorded operator act that changes direction, scope, authority, priority, or accepted risk. Append-only. The reason is part of the record.
- **The loop** — Capture → Shape → Authorize → Execute → Prove → Accept → Learn. Authorize and Accept are the operator's alone.
- **Backlog · In Progress · Awaiting Verdict · Needs Revision** — The four record states a work item shows: captured with nothing authorized; executing under a lease; submitted and awaiting the operator; rejected and waiting for a new Plan.
- **Feature · Story · Task · Bug** — The structure of work, top to bottom — every item leading upward to the intent it serves. A Feature may also carry an optional Spec when design decisions need to survive across multiple Stories.

## 7 · The final test

At any moment, the operator should be able to answer:

- Why are we doing this work?
- Who authorized it, and under what lease?
- Which agent is acting, and within what boundary?
- What does it depend on or collide with?
- What has it cost?
- What evidence has it produced?
- What decision is required from me?
- How will we know the outcome is accepted?

## 8 · How this manifesto changes

This is a governing document, not scripture. A change must record the observed problem that prompted it, which principle or practice changes, why the replacement is expected to work better, and the date and operator decision. AI agents may propose amendments. They may not quietly change the operating model while implementing the tooling.

> **The log below is this document's own history, with the project names left in.** It was written while running two real projects: a small algorithmic trading firm called ATAM, and Ingee, the tool that implements the method. Every entry started as a problem somebody actually hit. The entries have not been cleaned up after the fact.

### 21 September 2026 — A fourth record state, Needs Revision.

Observed problem: Backlog is defined as "captured, nothing authorized", and the lifecycle returned rejected work to it. A Story that had consumed a Plan, a Lease and a verdict then read as if none of that had happened; the record hid an authorization cycle and its investment behind the word for work never started.

What changes: a rejection derives **Needs Revision**, the record's fourth state beside Backlog, In Progress and Awaiting Verdict. It holds until a new Plan is approved, when the work is In Progress again, or until a later verdict stops or redirects it. It is derived from the newest verdict and the Plans after it, never stored.

Why this is expected to work better: the operator and the agent read what happened from the state alone, without opening the history, and Backlog keeps its one meaning.

### 21 September 2026 — The Initiative is renamed the Story.

Observed problem: in Jira and the portfolio tools this document's readers come from, an Initiative sits *above* Epics and Features — a quarter-long effort spanning many of them. This document put it below the Feature, so the word pointed the wrong way on first sight, and the reference implementation was about to give that level a permanent identifier.

What changes: the level is the **Story**, `STORY-001`. A Story is a bounded, verifiable outcome that advances one Feature, and the unit the operator authorizes and accepts. It may be user-facing or technical; either way it states what becomes true when it is done, not how. It defines what it includes, what it excludes, and the conditions the operator will judge its evidence against. It is delivered through an operator-approved Plan; only one Plan may be approved and current for a Story at a time, and rejected and superseded Plans keep their history. Two corrections were made on the way, both to the author's own first draft: a Story is an outcome, not a change, because a change names a mechanism; and what must change belongs to the Plan, not the Story, or the Story becomes a small Plan nobody read. Approving a Plan is not accepting the Story; the outcome is judged on evidence, afterwards. Records on the old store keep their `INIT` identifiers; history is not renamed, and the earlier entries below still say Initiative.

Why this is expected to work better: to the people this method is for, Story already means the bounded, owned, accepted unit under a Feature, with the outcome sentence and the acceptance criteria they know. Its one piece of baggage — sprint sizing — is named and refused: a Story is as large as one decision to authorize, and is never estimated in points. A borrowed word with the opposite meaning cost every new reader an unlearning; a familiar word with one stated difference costs them a sentence.

### 17 September 2026 — The problem before the method, and the Plan as a contract.

Observed problem: the first reader from outside the two projects could not tell from the page what problem this solves or how it differs from the agentic coding tools people already use. The argument for it was spread across Section 1 and repeated itself; "seven states" and the three record states still shared a word the 23 August entry had separated; the structure of work was drawn as a row of five cards, with the optional Spec looking like a level of its own; and the two-ledgers passage could still be read as claiming automatic cost tracking, which the 20 August entry had corrected once already.

What changes: the page opens by asking why a new development process is needed for AI agents, and states the problem before the definition. Section 1 runs in one order — what changed, the historical comparison (with the absolute claims about Agile and DevOps removed), what existing tools provide and do not automatically establish, the 144-script incident, what this method changes, the two bets — and the security citation is framed as evidence of a specific risk rather than a universal comparison. The loop is seven *phases* with three record states, a note says it is not strictly linear, and one worked example follows the Plan-as-spine paragraph. The anatomy of a proposal gains proportionality: the obligation is to make the decision possible, not to fill every heading. Its two rules now say what freezes at approval, that changing the approved contract is a new operator Decision recorded in the Plan, and that acceptance is judged against the approved contract including authorized amendments. Principle 7 adds that evidence must be inspectable or reproducible, not merely reported by the agent. The structure of work is drawn as a tree with the Spec attached to the Feature. The ledgers passage separates what the method requires from what the reference implementation records.

Why this is expected to work better: a reader meets the problem, the gap, and the method in that order and in one place, and the document uses its own terms — phases, record states, contract, Decision — the way the record does. What is given up: the concluding paragraphs after the two bets, whose scope statements already lived in the operating model and the vocabulary. Same day, presentation only: section links open from a Contents button on narrow screens, headings clear the sticky bar when navigated to, the permalink says *copied!* or *copy failed*, and readers who prefer reduced motion get none. Date and decision: 17 September 2026, operator RT, after the first external review.

### 8 September 2026 — The Plan is the spine of the loop.

Observed problem: the method described Shape, authorization, leases, evidence, and acceptance, but did not clearly name the object connecting them. What changes: the Plan is now explicitly the thing the operator authorizes. Shape produces it; authorization fixes it; the lease grants authority to execute it; Prove produces the evidence it requires; and Accept judges the result against the outcome it names. A Plan authorizes nothing by itself — it becomes binding only when approved by the operator. Why this is expected to work better: there is now one durable reference for what was proposed, what was authorized, what was executed, and what must be proven. Date and decision: 8 September 2026, operator RT.

Note, same day: the Activity vocabulary entry said an Activity is recorded "against one plan step." That is the reference implementation's discipline, not the method's. The method requires that an Activity happen under the authority of the approved Plan; the entry now says "against the Plan it executes."

### 7 September 2026 — The structure of work is rooted at the Feature.

Observed problem: the structure of work was drawn with a North Star at its top, as though product purpose were a level of the hierarchy. It never was. It is not authorized, leased, executed, proved, accepted, or closed; the reference implementation records it as text on the project, not as work. Meanwhile the method had begun treating "intent" as its first concept, and placing product purpose above the Feature blurred where actionable intent is actually recorded.

What changes: the structure of work is Feature → Initiative → Task and Bug, with a Spec as an optional design record attached to a Feature. The Feature is the root of recorded intent and must state why it matters in its own words; that is where "why are we doing this work?" is answered. Product purpose remains context a project may record, outside the structure of work; the method begins when purpose becomes a concrete product outcome worth pursuing. What is given up: the recorded criterion above the Feature ("does it move the product toward the North Star?"). Choosing which Features matter was always the operator's act, and it now rests on the operator's judgment and the Feature's recorded reason rather than on a test against a higher record.

Why this is expected to work better: every level of the tree is now something that moves through the loop, the method stops prescribing a product-purpose artifact it never governed, and the reference implementation and the description finally match. Date and decision: 7 September 2026, operator RT.

### 6 September 2026 — Two values, tested against the method.

Observed problem: preparing the values for a public reader, each pair was checked against what the rest of this document actually says. Two did not hold up. "Dependency clarity over a crowded task list" contrasted a real value with the wrong failure: the claim is not about visualization but about *when* structure is known — declared beforehand, or discovered through a merge conflict — and the "two kinds of dependency" principle had been left out of this page entirely, so the value stood there with nothing under it. "Learning over ceremonial compliance" set a state against a vice, and "learning" alone did not say which kind: a retrospective also counts, and the seventh state requires more than that.

What changed: "dependency clarity over **collision discovery**"; "**durable** learning over ceremonial compliance," borrowing the word already carried by "durable decisions" two lines up; the two-kinds principle restored under the operating model. "Economic visibility over token anxiety" was examined and kept: it names a specific anti-pattern this document rejects. All nine values now describe things the method can defend line by line. Date and decision: 6 September 2026, operator RT.

### 5 September 2026 — The name.

Observed problem: the working name, "Operator-Led PDLC," was an adjective carrying a non-standard acronym the reader had to decode before caring, and the bare adjective carries an unrelated private-equity meaning. Two days of research — registry checks, collision searches, the naming histories of Agile, Lean, DevOps, and the OODA loop — and one deliberate re-opening settled the formal name as **Operator-Led Software Development**: the template Agile itself used, whose founding document was the *Manifesto for Agile Software Development*.

What changed: the title, and every "PDLC" that named the concept now names it; every "PDLC" that meant the seven states now says "the lifecycle," which is what it always meant. The concept names the discipline; the reference implementation covers the whole lifecycle from intent to acceptance. Date and decision: 5 September 2026, operator RT.

### 30 August 2026 — The scope, stated plainly.

Observed problem: a conversation about what the reference implementation is worth building and selling as drifted into framing it as a governance platform for ATAM's production system. The operator corrected it: the method governs how a project gets *built*; ATAM's own governance — the order gate, the authority rules, the data guard — runs its production behaviour entirely on its own, with or without the build tooling reachable. Nothing in this document said that boundary plainly before.

What changed: a new section states it directly. Why this is expected to work better: without it, the document invites exactly the conflation that just happened — mistaking build-time authorization for runtime governance, which are different jobs with different owners. Date and decision: 30 August 2026, operator RT.

### 29 August 2026 — The Feature Spec, and Steps before a new Task.

Observed problem: retiring one employee (the control) produced three separate Plans in a row — TASK-037, then BUG-026, then BUG-027 — each re-arguing the same wind-down design because nothing durable held it above the Plan level; earlier the same week, an agent stopped mid-investigation because a Task did not yet exist for it, the same over-ceremony this document already names as a risk. Research into how other agent-native teams work confirmed the fix is not a heavier document — one such team moved to *less* upfront design, not more, once agentic coding became the default — but a short, optional Spec above the Initiative, and a clear line between foreseen sub-work and genuinely new work.

What changed: a Feature may carry a Spec — short, optional, proportional, never mandatory. Separately, a Task's Plan may grow more Steps for foreseen work inside its already-approved scope with no new authorization; work outside that scope is always a new Task or Bug with its own Plan. That line is the operator's, drawn by what was already approved — never the agent's, drawn by convenience. Why this is expected to work better: it removes the repeated re-argument without removing the checkpoint that matters — the moment the operator names a specific agent for a specific slice of work. Date and decision: 29 August 2026, operator RT.

### 23 August 2026 — Capture opens to agents.

The operator, after the create fence stalled three fully-drafted records behind copy-paste ceremony: "this is just creating too many roadblocks." The ruling stands on this document's own line — capture does not authorize work. Agents may now create initiatives, tasks and bugs directly: attributed, Backlog, unranked, and inert until the operator approves a plan — the gate where the conditions they wrote are read before they are armed. What stays the operator's alone: projects and features, plan approval, verdicts, resume, waive, and the order. The honest cost, accepted knowingly: the backlog can now grow without the operator's keystroke — agent opinions accumulate as records, kept legible by attribution and the unranked tail.

### 23 August 2026 — States are states, not commands.

The operator: "Authorize feels more like an action rather than a state." The lifecycle labels the record shows were renamed — Authorize became **Backlog**, Execute became **In Progress**, Verdict became **Awaiting Verdict** — because a verb in a state column reads as an order, and the worst offender read as an order to the operator. The phase names keep their verbs: phases are acts, states are conditions, and the two had been sharing words they should not share. Landed as one change across the stored values, the code gates, both agent surfaces, the screens and these documents, because a record that says one word while the screen says another is a record-versus-report defect of our own making.

### 21 August 2026 — The boundaries name the procedures.

Observed problem: the operator asked where a plan says which skill to use, and nothing did — the anatomy named files but not the skills, house patterns or rituals the work would follow. The best proposal on record did it by instinct ("this is the house style, not a new invention"), which is exactly the kind of instinct that should be a requirement instead. Part four of the anatomy now demands the procedures by name, and departures from one argued like any other design decision.

### 20 August 2026 — Five changes, after two days of lived use.

Proposed by the agent in a review of this document against two days of lived use, and carried in the decision by which operator RT made this file the single source of the operating model:

1. *The activity ledger and AI investment sections stopped claiming automatic tracking.* Across the sixteen activities ever recorded, every one was self-reported, every usage Unknown, and a dollar cost was calculated zero times — the sections described a system that has never existed. Naming the precondition marks what must change before the economics become real instead of letting a reader build on a falsehood.
2. *"The process as its own client" joined the rejected practices.* The one day this process governed its own development produced fifteen operator decisions, nearly all about the tool, and ended with the operator close to abandoning it. The model survived by finding a real client; the list now says so before anyone repeats the mistake.
3. *One question, one recommendation.* Decisions arrived as three- and four-option menus, and their accumulated weight was the other half of why a sound process felt unbearable.
4. *An Initiative's outcome names who can do what, and why.* The operator called Initiatives too difficult to understand. The readable ones already followed this shape; nothing required it, so the imported ones did not.
5. *The anatomy of a proposal.* Shape listed nouns — problem, boundary, risks — and the operator supplied a real proposal as the actual bar. Nothing in this document captured what makes such a document decidable, so the anatomy is now distilled from a proposal that worked rather than left to be rediscovered.

### 19 August 2026 — What Accept does not mean.

Observed problem: the operator asked how this process tracks releases and it does not, in any document or record. What changes: the lifecycle no longer implies that Accept is the end of the story. Why this is expected to work better: naming the limit stops the model claiming a completeness it does not have, and marks the point at which it must be designed rather than assumed. Date and decision: 19 August 2026, operator RT, who directed that the gap be recorded now and left unbuilt until there is something to release.

### Propose an amendment

The same rule applies to people: **anyone can propose a change, I decide, and the log records what happened.** If you disagree with a principle, or you work this way and want to say so, open an issue or a pull request against [the public repository](https://github.com/raguvindtharanitharan/operatorled.org), or write to me through [raguvind.com](https://raguvind.com). Changes that are accepted show up as dated entries in the log above, with the problem that prompted them.

---

**Manifesto for Operator-Led Software Development** · version 1.0 · published 7 September 2026 · last revised 21 September 2026
Proposed and authored by Raguvind Tharanitharan · [raguvind.com](https://raguvind.com). First written 19 August 2026.
This document may be freely copied in any form, in whole or in part, with attribution to its author and this address. Licensed under [Creative Commons Attribution 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
