# AI Coordinator Portfolio — Starter Kit

Kit de partida para **coordenar IAs** na construção de produtos digitais: playbooks, papéis de agentes, handoffs e prompts prontos para colar.

Complementa:

| Recurso | URL | Papel |
|---------|-----|-------|
| Portfólio ao vivo | [lughlammas.github.io](https://lughlammas.github.io/) | Vitrine e narrativa do coordenador |
| Template de produto | [comercial-template](https://github.com/lughlammas/comercial-template) | Base clonável para ofertas comerciais |
| **Este repositório** | [ai-coordinator-portfolio](https://github.com/lughlammas/ai-coordinator-portfolio) | Metodologia: como orquestrar agentes |

> **Importante:** este kit **não altera** o `comercial-template`. Use-o apenas como referência ou clone; a customização acontece em repositórios derivados.

## O que você encontra aqui

- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — fluxo Coordenador → agentes → repos → cliente
- [`docs/ROLES.md`](docs/ROLES.md) — papéis, responsabilidades e handoffs
- [`docs/PLAYBOOK.md`](docs/PLAYBOOK.md) — do briefing à oferta
- [`prompts/`](prompts/) — prompts copy-paste (briefing, fork de produto, handoff)
- [`DECISIONS.md`](DECISIONS.md) — registro de decisões do kit

## Quick start para o coordenador

1. **Leia o contexto do cliente** e abra [`prompts/briefing.md`](prompts/briefing.md). Preencha o briefing com o agente de produto.
2. **Divida o trabalho** com [`docs/ROLES.md`](docs/ROLES.md): produto, código, QA, docs, comercial.
3. **Clone o template** (sem modificar o original):
   ```bash
   gh repo create NOME-DO-PRODUTO --template lughlammas/comercial-template --public
   # ou: git clone + criar repo novo a partir da cópia
   ```
4. **Customize** o fork com [`prompts/fork-product.md`](prompts/fork-product.md).
5. **Handoffs** entre agentes com [`prompts/handoff.md`](prompts/handoff.md).
6. **Feche com README de venda** e oferta — ver etapa final em [`docs/PLAYBOOK.md`](docs/PLAYBOOK.md).

## Princípios

- Coordenação humana (ou humano + IA) no centro; agentes especializados nas pontas.
- Sem métricas inventadas: documente o que foi feito, não o que “parece bom”.
- Template comercial permanece estável; produtos nascem em repos próprios.
- Português (PT-BR) como idioma padrão dos artefatos deste kit.

## Licença

MIT — veja [`LICENSE`](LICENSE).

---

Mantido por [Guilherme Cavalcanti (lughlammas)](https://github.com/lughlammas) · Homepage: [lughlammas.github.io](https://lughlammas.github.io/)
