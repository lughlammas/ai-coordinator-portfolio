# AI Coordinator Portfolio

Documented methodology for human-directed AI coordination across product, implementation, QA, handoffs, and documentation.

**Contents:** playbooks, role definitions, prompts, acceptance criteria and decision records. This is a documentation starter kit; it contains no executable agent runtime, automated scheduler or multi-agent orchestration service.

**Status:** methodology and reusable documents. The opening guide is English-first; the detailed playbooks and prompt templates are currently in Brazilian Portuguese. No automated execution or benchmark is claimed.

Maintained by [Guilherme Cavalcanti](https://github.com/lughlammas) within **ARBOCK LABS**, an independent software and applied-AI lab currently being structured.

## Read the methodology

- [Architecture](docs/ARCHITECTURE.md): coordinator, roles, repositories and delivery flow.
- [Roles](docs/ROLES.md): responsibilities, acceptance and handoff boundaries.
- [Playbook](docs/PLAYBOOK.md): briefing, scope, implementation, QA and delivery sequence.
- [Prompts](prompts/): briefing, product adaptation and handoff templates.
- [Decisions](DECISIONS.md): the kit's decision record.

## Case studies

- [GitHub & Project Estate Consolidation](case-studies/github-project-estate-consolidation.md): self-directed audit, classification and consolidation of my own repositories and workspace (not paid client work).

## Use the kit

1. Define the problem, constraints and acceptance criteria with the [briefing](prompts/briefing.md).
2. Assign responsibilities using the [role definitions](docs/ROLES.md).
3. Work in the appropriate product repository, with changes reviewed under human direction.
4. Record deliverables, unresolved issues and decisions in each [handoff](prompts/handoff.md).
5. Inspect implementation, check acceptance criteria and document the delivered scope and limitations.

The kit defines a process for using tools and agents. It does not launch them, execute tests, or establish that a particular product passed QA. Report only checks actually performed and results actually observed.

## Related public work

- [comercial-template](https://github.com/lughlammas/comercial-template): application implementation used as a customization example in the playbooks.
- [Portfolio](https://lughlammas.github.io/): professional presentation.

Using this kit does not modify those repositories. Adapt the prompts to the project and decide repository visibility according to its ownership and IP requirements.

## License

[MIT](LICENSE). Original playbooks, role definitions and decision history are preserved.
