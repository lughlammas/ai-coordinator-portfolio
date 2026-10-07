# Human-Directed AI Workflow — English Overview

A concise English summary of the methodology in this repository. It describes **human-directed AI-assisted development**: a person sets the objective, assigns work to AI agents and people, inspects the results and remains accountable for what ships.

This is a written method made of roles, sequences, templates and rules. It is **not** autonomous infrastructure. The repository contains no agent runtime, scheduler or orchestration service, and it does not run anything by itself.

The detailed source documents are in Brazilian Portuguese, and this overview follows them closely: [ARCHITECTURE](ARCHITECTURE.md), [ROLES](ROLES.md), [PLAYBOOK](PLAYBOOK.md), [prompts/](../prompts/) and [DECISIONS](../DECISIONS.md). For an applied example, see the [GitHub & Project Estate Consolidation case study](../case-studies/github-project-estate-consolidation.md), a real self-directed repository audit that is not client work.

## 1. Human objective and authority

- The **Coordinator** owns the cycle: the briefing, splitting the work, acceptance between stages, and alignment with the client or stakeholder. The source docs describe the role as "human ± AI", with a human always directing.
- The Coordinator receives the request and every blocker or decision that needs escalating. The Coordinator delivers the work plan, the decision record and final acceptance.
- Repository visibility is decided according to the project's ownership and IP requirements.
- In practice (case study): irreversible actions stayed behind explicit owner approval. These were visibility, licences, deletions, history rewrites and account renaming.

## 2. Problem decomposition

Following the [briefing template](../prompts/briefing.md) and [PLAYBOOK](PLAYBOOK.md) steps 1–2:

- Capture the problem, audience, deadline, technical and business constraints, what already exists, and an **observable** definition of success.
- The Coordinator checks that the scope fits one short cycle, either an MVP or a clear slice.
- The Product role restates the problem and value proposition, lists scope **in** and **out**, and writes **5–10 verifiable pass/fail acceptance criteria**, plus risks and open questions.
- **Output:** an approved briefing, a spec and a prioritised backlog with an owner for each item.

## 3. Agent and tool assignment

Each role can be filled by a person, an AI under supervision, or a combination ([ROLES](ROLES.md)). The Coordinator assigns Code, QA, Docs and Commercial according to workload, and does not, as a rule, implement a whole feature alone when specialised roles are available.

| Role | Responsible for |
|---|---|
| Product | Problem, audience, scope, acceptance criteria, priorities |
| Code | Implementation in a repository derived from the agreed base |
| QA | Acceptance criteria, obvious regressions, release checklist |
| Docs | Technical README, quick start, product README |
| Commercial | Offer, positioning, next steps; objections answered with facts |

## 4. Parallel work where useful

- The default order is Product → Code → QA → Docs → Commercial. The architecture shows the Coordinator assigning to all roles, and the playbook brings QA in **early**, with smoke checks against the acceptance criteria while implementation is under way.
- The source docs do not prescribe a parallel schedule. Parallelism is a Coordinator decision based on workload.
- In practice (case study), two agent sessions worked on the same repositories at once and one release branch ran into a conflict. The working rule that came out of it: fetch before changing anything, never overwrite newer work, and stop on a conflict instead of forcing it.

## 5. Handoff structure

Every hand-over uses the [handoff template](../prompts/handoff.md), which records:

- from/to, cycle and date;
- the goal of the handoff;
- links to the spec, the product repository, the PR/branch and relevant decisions;
- what is delivered;
- known pending items;
- **the acceptance criteria to validate now**;
- **how to verify** (commands, steps, environments);
- blockers or questions for the Coordinator;
- the suggested next step.

Each pair of roles has a minimum artifact to pass on ([ROLES](ROLES.md)):

| From → To | Artifact |
|---|---|
| Coordinator → Product | Completed briefing |
| Product → Code | Spec + acceptance criteria |
| Code → QA | PR + checklist |
| QA → Docs | Stable scope |
| Docs → Commercial | Product README + FAQ |
| Commercial → Coordinator | Offer + links |
| Any → Coordinator | Blocker or decision needed |

## 6. Inspection and rejection

- QA sends **reproducible bugs** back to Code.
- Work outside the acceptance criteria is not accepted. The [code prompt](../prompts/fork-product.md) forbids inventing features beyond the criteria, and new scope or doubts go back to Product and the Coordinator.
- The Coordinator inspects the implementation against the acceptance criteria before accepting a stage.
- In practice (case study), ambiguous project identities and branch conflicts were treated as stop conditions: work halted on that item and the problem was reported, without guessing or forcing.

## 7. Testing / QA

- QA verifies the acceptance criteria, checks for obvious regressions and runs the release checklist. It delivers a pass/bug report with known risks.
- The expected output of implementation is a reviewed PR with a green QA checklist, or documented risks ([PLAYBOOK](PLAYBOOK.md), step 4).
- **Report only checks actually performed and results actually observed.** The kit defines a process; it does not establish that any particular product passed QA.

## 8. Documentation

- Code documents the minimal setup in the technical README, without false metrics.
- Docs writes the technical README, a quick start and a product README covering what it is, who it is for, how to run or demo it, and next steps. The source docs ask for these to be "clear, without false hype".
- Documentation lives in the product repository, never in the canonical template.
- No invented metrics, testimonials, results or case studies, in any role.

## 9. Version control

- Each product starts as a **new repository derived from the template**, for example with `gh repo create --template`. The canonical template is never committed to as part of this flow.
- Code works in small commits with clear messages, then hands over through a branch or PR. Releases are versioned in the product repository.
- Decisions that affect scope or the base template go in the product repository's `DECISIONS.md`. This kit keeps its own [decision record](../DECISIONS.md), whose entries record context, decision, consequences and status.

## 10. Human acceptance

- Final acceptance belongs to the Coordinator.
- The Coordinator presents the delivered scope, what is deferred, and the links to the product and portfolio, then records the stakeholder's feedback ([PLAYBOOK](PLAYBOOK.md), step 6).
- The cycle closes against the playbook checklist: approved briefing, spec and acceptance criteria, a derived repository with the template untouched, implementation and QA, a product README, and the offer and final handoff.

## Limits and emerging work

- This is a methodology and set of templates. It does not launch, schedule or supervise agents, and it measures nothing automatically.
- No productivity or quality figures are claimed for the method.
- ARBOCK LABS is also developing an internal framework called Tool-Assisted Work (TAW) for studying how tool use, parallelism, orchestration and verification change the density of human-directed work. Its working unit, the Tool-Assisted Work Hour (TAWH), is an emerging internal concept. It is not an established academic theory or industry standard, and no results from it are reported here.
