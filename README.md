# Manual de Engenharia da coude-jr-26

Este repositório é a fonte oficial de orientação técnica, organização de trabalho, padrões de contribuição e processos da equipe Coude Jr 2026.1.

Ele deve ser consultado por todos os membros antes de iniciar qualquer atividade nos repositórios do CRM da Escola Coude.

## Por onde começar

Se você acabou de entrar no projeto, siga esta ordem:

1. Leia a visão geral da organização: [Visão Geral da Organização](getting-started/01-org-overview.md)
2. Leia a convenção de commits: [Convenção de Commits](standards/commit-conventions.md)
3. Leia as diretrizes de Pull Request: [Diretrizes de Pull Request](standards/pr-guidelines.md)
4. Leia a definição de pronto: [Definição de Pronto](standards/definitions-of-done.md)

## Conteúdo

| Seção | Descrição |
|---|---|
| [Getting Started](getting-started/) | Orientações iniciais para novos membros |
| [Standards](standards/) | Padrões de commits, Pull Requests, revisão e entrega |
| [Architecture](architecture/) | Decisões arquiteturais e desenho técnico do CRM |
| [Processes](processes/) | Fluxo de sprint, cerimônias, releases e incidentes |
| [Resources](resources/) | Links úteis, glossário e materiais de apoio |

## Regras essenciais

Antes de contribuir com qualquer repositório, siga estas regras:

1. Não faça commit direto na branch `main`.
2. Trabalhe sempre em uma branch própria.
3. Todo código deve entrar por Pull Request.
4. Não envie senhas, tokens, chaves de API ou arquivos `.env`.
5. Faça Pull Requests pequenos e focados.
6. Se ficar travado por mais de 30 minutos, peça ajuda.
7. Leia os critérios de aceite da sua tarefa antes de começar.
8. Atualize a documentação sempre que alterar fluxo, configuração ou endpoint.

## Repositórios principais

| Repositório | Finalidade |
|---|---|
| `.github` | Templates globais da organização |
| `docs-engineering-handbook` | Manual de engenharia e documentação técnica |
| `crm-backend` | API do CRM em Laravel |
| `crm-frontend` | Interface do CRM em React com TypeScript |
| `crm-infra` | Docker, infraestrutura e deploy |
| `crm-shared-libs` | Tipos, contratos e utilitários compartilhados |

## Responsáveis pela manutenção

Este documento é mantido pelos Tech Leads do projeto.

Mudanças neste repositório devem ser feitas por Pull Request e precisam de pelo menos uma revisão de Tech Lead.
