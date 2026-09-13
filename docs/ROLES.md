# Papéis dos agentes e handoffs

Cada papel abaixo pode ser uma pessoa, uma IA sob supervisão, ou uma combinação. O **Coordenador** mantém o fio e decide handoffs.

## Coordenador

- **Responsabilidade:** briefing, divisão de trabalho, aceite entre etapas, alinhamento com o cliente.
- **Não faz (salvo exceção):** implementar feature completa sozinho quando há agentes especializados.
- **Recebe:** demanda do cliente, dúvidas de qualquer agente.
- **Entrega:** plano de trabalho, decisões (`DECISIONS.md` do projeto do cliente), aceite final.

## Agente Produto

- **Responsabilidade:** problema, personas, escopo, critérios de aceite, priorização.
- **Recebe:** briefing do Coordenador.
- **Entrega:** spec curta, backlog priorizado, definição de “pronto”.
- **Handoff para Código:** spec + critérios de aceite + restrições técnicas conhecidas.
- **Handoff para Comercial:** proposta de valor e diferenciais (sem inventar métricas).

## Agente Código

- **Responsabilidade:** implementar a partir do **fork/clone** do `comercial-template` (ou base acordada).
- **Recebe:** spec + critérios de aceite.
- **Entrega:** PRs, código funcional, notas de setup.
- **Handoff para QA:** branch/PR + o que testar + ambientes.
- **Regra:** não pushar alterações no repositório canônico `comercial-template`.

## Agente QA

- **Responsabilidade:** verificar critérios de aceite, regressões óbvias, checklist de release.
- **Recebe:** PR/build + lista de aceite do Produto.
- **Entrega:** relatório de bugs/passou, riscos conhecidos.
- **Handoff para Código:** bugs reproduzíveis; **para Docs:** o que está estável para documentar.

## Agente Docs

- **Responsabilidade:** README técnico, guia rápido, README de venda (claro, sem hype falso).
- **Recebe:** produto estável + notas de Código/QA + proposta de valor do Produto/Comercial.
- **Entrega:** documentação no repo do produto (não no template canônico).
- **Handoff para Comercial:** texto base da oferta e FAQ.

## Agente Comercial

- **Responsabilidade:** oferta, posicionamento, próximos passos com o cliente.
- **Recebe:** proposta de valor + README de venda + demo/links.
- **Entrega:** one-pager ou proposta, call-to-action, objeções cobertas com fatos.
- **Handoff para Coordenador:** pacote pronto para apresentação ao cliente.

## Matriz de handoff (resumo)

| De → Para | Artefato mínimo |
|-----------|-----------------|
| Coordenador → Produto | Briefing preenchido |
| Produto → Código | Spec + aceite |
| Código → QA | PR + checklist |
| QA → Docs | Escopo estável |
| Docs → Comercial | README venda + FAQ |
| Comercial → Coordenador | Oferta + links |
| Qualquer → Coordenador | Bloqueio ou decisão necessária |

Use [`prompts/handoff.md`](../prompts/handoff.md) para padronizar a mensagem entre agentes.
