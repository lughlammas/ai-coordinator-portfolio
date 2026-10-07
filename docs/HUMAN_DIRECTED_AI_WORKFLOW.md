# Human-Directed AI Workflow — English Overview

A concise English summary of the methodology in this repository. It describes **human-directed AI-assisted development**: a person sets direction, assigns work to AI agents and people, checks the results and remains accountable for what ships.

This is a written method made of roles, sequences, templates and rules. It is **not** autonomous infrastructure. The repository contains no agent runtime, scheduler or orchestration service, and it does not run anything by itself.

The detailed source documents are in Brazilian Portuguese, and this overview follows them closely: [ARCHITECTURE](ARCHITECTURE.md), [ROLES](ROLES.md), [PLAYBOOK](PLAYBOOK.md), [prompts/](../prompts/) and [DECISIONS](../DECISIONS.md).

## 1. Who is in charge

The **Coordinator** runs the cycle. The source docs describe this role as "human ± AI", with a human always directing.

- **Responsibilities:** briefing, splitting the work, acceptance between stages, and alignment with the client or stakeholder.
- **Receives:** the request, plus questions and blockers from any agent.
- **Delivers:** the work plan, the decision record and final acceptance.
- **Does not, as a rule,** implement a whole feature alone when specialised roles are available.

## 2. Roles

Each role can be filled by a person, an AI under supervision, or a combination ([ROLES](ROLES.md)).

| Role | Responsible for | Hands off |
|---|---|---|
| Product | Problem, audience, scope, acceptance criteria, priorities | Spec + acceptance criteria → Code; value proposition (no invented metrics) → Commercial |
| Code | Implementation in a repository derived from the agreed base | Branch/PR + what to test + environments → QA |
| QA | Checking acceptance criteria, obvious regressions, release checklist | Reproducible bugs → Code; what is stable → Docs |
| Docs | Technical README, quick start, product README ("clear, without false hype") | Base text for the offer and FAQ → Commercial |
| Commercial | Offer, positioning, next steps; objections answered with facts | Package ready to present → Coordinator |

Any role escalates a blocker or a decision it needs to the Coordinator.

## 3. Delivery sequence

From the [PLAYBOOK](PLAYBOOK.md):

1. **Briefing.** Collect the problem, audience, deadline, constraints and the observable definition of success. The Coordinator checks that the scope fits one short cycle.
2. **Split.** Product turns the briefing into a spec with acceptance criteria. The Coordinator assigns owners and records decisions in the product's own repository.
3. **Derive the base.** Create a new repository from the template. The canonical template is never committed to as part of this flow.
4. **Customise.** Code implements the spec. QA joins early with smoke checks against the acceptance criteria, and new scope goes back to Product and the Coordinator.
5. **Product README.** Docs and Commercial write a value-oriented README: what it is, who it is for, how to run or demo it, and next steps.
6. **Offer and handoff.** The Coordinator presents the delivered scope, what is deferred, and links, then records the feedback.

The usual order is Product → Code → QA → Docs → Commercial.

## 4. Briefing and acceptance criteria

The [briefing template](../prompts/briefing.md) asks the Product role to:

- restate the problem and value proposition;
- list what is **in** and **out** of scope for the cycle;
- write **5–10 verifiable pass/fail acceptance criteria**;
- propose the handoff order;
- list risks and open questions for the Coordinator.

## 5. Handoffs

Every hand-over uses the same [handoff template](../prompts/handoff.md), which records:

- from/to, cycle and date;
- the goal of the handoff;
- links to the spec, the product repository, the PR/branch and relevant decisions;
- what is delivered;
- **known pending items**;
- **the acceptance criteria to validate now**;
- **how to verify** (commands, steps, environments);
- blockers or questions for the Coordinator;
- the suggested next step.

Each pair of roles has a minimum artifact to pass on, defined in the handoff matrix in [ROLES](ROLES.md):

| From → To | Artifact |
|---|---|
| Coordinator → Product | Completed briefing |
| Product → Code | Spec + acceptance criteria |
| Code → QA | PR + checklist |
| QA → Docs | Stable scope |
| Docs → Commercial | Product README + FAQ |
| Commercial → Coordinator | Offer + links |

## 6. Verification

- QA checks the acceptance criteria and the release checklist, then reports pass/fail and known risks.
- The expected output of implementation is a reviewed PR with a green QA checklist, or documented risks ([PLAYBOOK](PLAYBOOK.md), step 4). Acceptance between stages belongs to the Coordinator.
- **Report only checks actually performed and results actually observed.** The kit defines a process; it does not establish that any particular product passed QA.

## 7. Decision records

- Decisions that affect scope or the base template are recorded in a `DECISIONS.md` in the product's repository, not in the template.
- This kit keeps its own [decision record](../DECISIONS.md) for its scope, language and tone, and licence. Each entry records context, decision, consequences and status.

## 8. Guardrails

- No invented metrics, testimonials, results or case studies, in any role.
- The canonical template is read-only; customisation happens only in derived repositories.
- No features outside the acceptance criteria. New scope goes back to Product and the Coordinator.
- Repository visibility is decided according to the project's ownership and IP requirements.

## 9. Applied example

The [GitHub & Project Estate Consolidation case study](../case-studies/github-project-estate-consolidation.md) applies the same principles to a real, self-directed repository audit. It is not client work. In that case:

- the human owner kept every irreversible decision behind explicit approval gates: visibility, licences, deletions, history rewrites and account renaming;
- AI agents did the inventory, comparisons, scans, edits and reports;
- ambiguous projects and a branch conflict between two concurrent agent sessions were treated as stop conditions and reported, not guessed or forced;
- every phase ended with a written handoff report.

## 10. Limits and emerging work

- This is a methodology and set of templates. It does not launch, schedule or supervise agents, and it measures nothing automatically.
- No productivity or quality figures are claimed for the method.
- ARBOCK LABS is also developing an internal framework called Tool-Assisted Work (TAW) for studying how tool use, parallelism, orchestration and verification change the density of human-directed work. Its working unit, the Tool-Assisted Work Hour (TAWH), is an emerging internal concept. It is not an established academic theory or industry standard, and no results from it are reported here.
