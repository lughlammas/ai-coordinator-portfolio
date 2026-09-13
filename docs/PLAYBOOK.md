# Playbook: do briefing à oferta

Sequência recomendada para um ciclo de produto digital coordenado por IAs (com supervisão humana).

## 1. Briefing

- Colete contexto do cliente: problema, público, prazo, restrições, sucesso desejado.
- Use [`prompts/briefing.md`](../prompts/briefing.md).
- Coordenador valida se o escopo cabe em um ciclo curto (MVP ou fatia clara).

**Saída:** briefing aprovado + papéis atribuídos ([`ROLES.md`](ROLES.md)).

## 2. Dividir

- Produto transforma briefing em spec e critérios de aceite.
- Coordenador atribui Código, QA, Docs, Comercial conforme carga.
- Registre decisões que afetam o template ou o escopo (no repo do **produto**, não no template canônico).

**Saída:** backlog priorizado + donos por item.

## 3. Clonar o template

- Crie um repositório **novo** a partir de [comercial-template](https://github.com/lughlammas/comercial-template).
- Exemplos:
  ```bash
  gh repo create SEU-ORG/NOME-PRODUTO --template lughlammas/comercial-template --public --clone
  ```
  ou clone local + `gh repo create` + push inicial.
- **Nunca** faça commit no repositório `lughlammas/comercial-template` como parte deste fluxo.

**Saída:** URL do repo do produto + branch `main` (ou padrão do time).

## 4. Customizar

- Código aplica a spec no fork.
- Use [`prompts/fork-product.md`](../prompts/fork-product.md).
- QA entra cedo (smoke + critérios de aceite).
- Evite features fora do aceite; devolva escopo novo ao Produto/Coordenador.

**Saída:** PR revisado + checklist QA verde (ou riscos documentados).

## 5. README de venda

- Docs + Comercial produzem um README orientado a valor: o que é, para quem, como rodar/demo, próximos passos.
- Sem métricas inventadas; use apenas dados reais do cliente ou do ciclo.
- Handoff padronizado: [`prompts/handoff.md`](../prompts/handoff.md).

**Saída:** README (e páginas auxiliares se preciso) no repo do produto.

## 6. Oferta

- Comercial fecha one-pager / proposta com escopo entregue, o que fica para depois, e CTA.
- Coordenador apresenta ao cliente com links do portfólio e do produto.
- Portfólio de referência: [lughlammas.github.io](https://lughlammas.github.io/).

**Saída:** oferta enviada + feedback do cliente registrado.

## Checklist rápido do ciclo

- [ ] Briefing aprovado
- [ ] Spec + critérios de aceite
- [ ] Repo derivado do template (template intocado)
- [ ] Implementação + QA
- [ ] README de venda
- [ ] Oferta e handoff final ao cliente
