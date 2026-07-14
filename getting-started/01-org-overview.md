# Visão Geral da Organização

## O que é a coude-jr-26?

A `coude-jr-26` é a organização do GitHub usada pela Coude Jr 2026.1 para centralizar o desenvolvimento do CRM da Escola Coude, a documentação técnica, a governança dos repositórios e a formação dos membros da equipe.

A organização tem três objetivos principais:

1. Desenvolver o CRM da Escola Coude.
2. Padronizar a forma de trabalho da equipe.
3. Apoiar o aprendizado e a evolução técnica dos membros juniores.

## Repositórios principais

| Repositório | Visibilidade | Finalidade |
|---|---|---|
| `.github` | Público | Templates globais de Pull Request, issues e configurações da organização |
| `docs-engineering-handbook` | Público | Manual de engenharia, padrões e documentação interna |
| `crm-backend` | Privado | API do CRM desenvolvida em Laravel |
| `crm-frontend` | Privado | Interface do CRM desenvolvida em React com TypeScript |
| `crm-infra` | Privado | Infraestrutura, Docker, Nginx, PostgreSQL, Redis e deploy |
| `crm-shared-libs` | Privado | Tipos, contratos e bibliotecas compartilhadas entre projetos |

## Padrão de nomes dos repositórios

| Prefixo | Uso |
|---|---|
| `crm-` | Repositórios relacionados ao produto CRM |
| `docs-` | Documentação técnica e organizacional |
| `challenge-` | Desafios técnicos para candidatos |
| `eval-` | Entregas e avaliações de candidatos |
| `sandbox-` | Repositórios de prática para membros juniores |
| `training-` | Repositórios de treinamento estruturado |
| `meta-` | Configurações e automações da organização |
| `archive-` | Repositórios arquivados ou inativos |

## Estrutura de times

A organização usa times pais e times filhos.

Os times pais representam áreas amplas. Os times filhos representam funções específicas dentro dessas áreas.

```text
leadership
  tech-leads
  engineering-mgmt

governance
  github-admins

engineering
  backend
  frontend
  devops
  fullstack
  data-engineering

quality
  qa

documentation
  docs-team

juniors
  junior-devs

recruitment
  recruiters
