# Arquitetura do CRM Escola Coude

Este documento descreve a arquitetura técnica do CRM da Escola Coude, os principais repositórios, os módulos do sistema, as tecnologias adotadas e as regras que devem orientar decisões técnicas.

A arquitetura deve ser simples o suficiente para um time júnior conseguir contribuir, mas organizada o bastante para suportar evolução, manutenção e uso real em produção.

## Objetivos da arquitetura

A arquitetura do CRM tem os seguintes objetivos:

1. Permitir desenvolvimento em equipe com várias pessoas trabalhando ao mesmo tempo.
2. Reduzir acoplamento entre áreas do sistema.
3. Facilitar testes, revisão de código e manutenção.
4. Evitar decisões complexas demais para o estágio atual do projeto.
5. Preparar o sistema para produção real.
6. Manter segurança, rastreabilidade e organização dos dados da escola.
7. Permitir evolução futura sem reescrever o sistema do zero.

## Visão geral dos repositórios

A organização usa uma estrutura multi-repo.

| Repositório | Responsabilidade |
|---|---|
| `.github` | Templates globais da organização, como Pull Requests e issues |
| `docs-engineering-handbook` | Manual de engenharia, padrões e processos |
| `crm-backend` | API principal do CRM usando Laravel |
| `crm-frontend` | Interface do CRM usando React com TypeScript |
| `crm-infra` | Docker, Nginx, PostgreSQL, Redis, scripts e deploy |
| `crm-shared-libs` | Tipos, contratos e utilitários compartilhados |

## Stack principal

| Camada | Tecnologia |
|---|---|
| Backend | Laravel com PHP 8.2 ou superior |
| Autenticação | Laravel Sanctum |
| Frontend | React com TypeScript e Vite |
| Banco de dados | PostgreSQL |
| Cache e filas | Redis |
| Servidor web | Nginx |
| Ambiente local | Docker e Docker Compose |
| Versionamento | Git e GitHub |
| Gestão | Jira |
| Testes backend | PHPUnit ou Pest |
| Testes frontend | Vitest, React Testing Library ou Playwright |

## Observação sobre o frontend

A documentação inicial do projeto citava Next.js como possibilidade. Porém, o estado atual do repositório `crm-frontend` usa React com Vite e TypeScript.

Para a Sprint 1, a decisão prática é manter React com Vite, pois o foco é estabilizar autenticação, infraestrutura e fluxo de trabalho.

Se futuramente a equipe quiser migrar para Next.js, essa mudança deve ser registrada antes em uma decisão arquitetural.

## Estilo arquitetural

O sistema deve seguir uma arquitetura simples e modular.

No backend, usamos um monolito modular. Isso significa que o sistema roda como uma única aplicação Laravel, mas o código deve ser organizado por domínios de negócio.

Exemplos de módulos futuros:

```text
Auth
Contacts
Students
Courses
Enrollments
Conversations
Pipeline
Payments
Reports
Notifications
```

## Por que monolito modular?

O monolito modular é a melhor escolha para o estágio atual do projeto porque:

1. É mais simples para um time júnior entender.
2. Evita a complexidade de microsserviços.
3. Facilita debug local.
4. Permite deploy mais simples.
5. Mantém o sistema organizado por domínio.
6. Pode evoluir no futuro se o volume crescer.

Microsserviços, Kubernetes e arquiteturas distribuídas não devem ser usados neste momento.

## Fluxo geral do sistema

```text
Usuário acessa o frontend
  Frontend chama a API Laravel
    Laravel valida autenticação com Sanctum
      Laravel executa regra de negócio
        Laravel lê ou grava dados no PostgreSQL
        Laravel usa Redis para cache ou filas quando necessário
          API retorna resposta JSON
            Frontend atualiza a interface
```

## Fluxo de autenticação

```text
Usuário informa e-mail e senha
  Frontend envia POST /api/login
    Backend valida credenciais
      Backend cria token com Sanctum
        Backend retorna token e dados básicos do usuário
          Frontend armazena credenciais conforme estratégia definida
            Usuário acessa áreas protegidas do CRM
```

## Camadas recomendadas no backend

O backend deve evitar regras de negócio diretamente nos controllers.

Fluxo recomendado:

```text
Route
  Controller
    Form Request
      Service ou Action
        Model
          Database
    Resource
      Response JSON
```

## Responsabilidade de cada camada

| Camada | Responsabilidade |
|---|---|
| Route | Definir o endpoint |
| Controller | Receber a requisição e delegar |
| Form Request | Validar entrada de dados |
| Service ou Action | Executar regra de negócio |
| Model | Representar entidades e relacionamentos |
| Migration | Criar ou alterar estrutura do banco |
| Seeder | Criar dados iniciais ou de desenvolvimento |
| Resource | Padronizar resposta da API |
| Test | Garantir que o comportamento funciona |

## Exemplo de organização backend

```text
app/
  Http/
    Controllers/
    Requests/
    Resources/
  Models/
  Services/
  Actions/
database/
  migrations/
  seeders/
routes/
  api.php
tests/
  Feature/
  Unit/
```

Se a estrutura modular for adotada em uma etapa posterior, o backend poderá evoluir para algo como:

```text
app/
  Modules/
    Auth/
      Controllers/
      Requests/
      Services/
      Resources/
    Contacts/
    Enrollments/
    Conversations/
```

## Regras para backend

1. Controllers devem ser pequenos.
2. Validações devem ficar em Form Requests quando aplicável.
3. Regras de negócio devem ficar em Services ou Actions.
4. Respostas da API devem ser padronizadas.
5. Endpoints privados devem exigir autenticação.
6. Migrations devem ser usadas para toda alteração no banco.
7. Seeders devem ser usados para dados iniciais.
8. Não usar SQL manual sem necessidade.
9. Não retornar dados sensíveis na API.
10. Testes devem ser adicionados para fluxos críticos.

## Camadas recomendadas no frontend

O frontend deve separar interface, lógica de formulário, chamadas à API e tipos.

Fluxo recomendado:

```text
Page
  Components
    Hooks
      API Client
        Backend
```

## Exemplo de organização frontend

```text
src/
  app/
  components/
  modules/
    auth/
      components/
      pages/
      services/
      schemas/
      types/
  lib/
    api/
  routes/
  styles/
  types/
```

## Regras para frontend

1. Componentes devem ter responsabilidade clara.
2. TypeScript deve ser usado corretamente.
3. Evitar `any` sem justificativa.
4. Estados de loading devem ser tratados.
5. Estados de erro devem ser tratados.
6. Formulários devem ter validação.
7. Chamadas HTTP devem usar cliente centralizado.
8. Dados sensíveis não devem ser armazenados de forma insegura.
9. A interface deve ser testada no navegador antes do Pull Request.
10. Mudanças visuais devem ter evidência no Pull Request.

## Banco de dados

O banco principal do CRM é PostgreSQL.

Ele deve armazenar dados como:

```text
users
contacts
students
courses
enrollments
pipeline_stages
conversations
messages
payments
events
reports
```

## Regras para banco de dados

1. Toda alteração deve ser feita via migration.
2. Campos obrigatórios devem ter constraints.
3. Relacionamentos devem usar foreign keys quando aplicável.
4. Campos frequentemente consultados devem ter índices.
5. Dados sensíveis devem ser tratados com cuidado.
6. Nunca apagar dados importantes sem alinhamento com Tech Lead.
7. Seeds não devem conter dados reais de alunos ou leads.
8. Backups devem ser planejados antes de produção.

## Redis

Redis será usado principalmente para:

1. Cache.
2. Filas.
3. Sessões, se essa estratégia for adotada.
4. Rate limiting.
5. Processamento assíncrono futuro.

Na Sprint 1, o foco é deixar Redis disponível na infraestrutura. O uso avançado pode ficar para sprints posteriores.

## Infraestrutura local

O ambiente local deve ser executado com Docker Compose.

Serviços esperados:

```text
backend
frontend
nginx
postgres
redis
```

Em etapas futuras, podem ser adicionados:

```text
queue-worker
horizon
mailpit
pgadmin
```

## Fluxo de infraestrutura

```text
Navegador
  Nginx
    Frontend
    Backend Laravel
      PostgreSQL
      Redis
```

## Segurança

O CRM será usado em produção real. Por isso, segurança deve ser considerada desde o início.

Regras essenciais:

1. Não enviar arquivos `.env` para o Git.
2. Não enviar tokens, senhas ou chaves de API.
3. Usar `.env.example` para documentar variáveis.
4. Proteger endpoints privados com autenticação.
5. Validar todos os dados de entrada.
6. Não expor dados sensíveis em logs.
7. Não retornar informações internas de erro para o usuário final.
8. Seguir boas práticas relacionadas à LGPD.

## LGPD

Como o CRM pode armazenar dados de leads, alunos e responsáveis, o projeto deve respeitar princípios da LGPD.

Cuidados básicos:

1. Coletar apenas dados necessários.
2. Evitar exposição indevida de informações pessoais.
3. Controlar acesso por perfil de usuário.
4. Manter rastreabilidade de alterações importantes.
5. Evitar dados reais em ambientes de desenvolvimento.
6. Planejar exportação e exclusão de dados quando necessário.

## Decisões arquiteturais

Toda decisão técnica relevante deve ser registrada.

Exemplos de decisões que precisam de registro:

1. Troca de tecnologia principal.
2. Mudança na estratégia de autenticação.
3. Criação de novo módulo relevante.
4. Introdução de nova dependência crítica.
5. Alteração importante na infraestrutura.
6. Mudança no modelo de dados principal.
7. Integração com serviços externos.

## Modelo simples de decisão arquitetural

Use este modelo quando precisar registrar uma decisão:

```markdown
# ADR 0000: Título da decisão

## Status

Proposta, aceita, rejeitada ou substituída.

## Contexto

Explique o problema e por que a decisão precisa ser tomada.

## Opções consideradas

1. Opção A
2. Opção B
3. Opção C

## Decisão

Explique a opção escolhida.

## Justificativa

Explique por que essa opção foi escolhida.

## Consequências

Liste impactos positivos, negativos e riscos.
```

## Decisões já aceitas

| Código | Decisão |
|---|---|
| ADR 001 | Backend em Laravel |
| ADR 002 | Frontend atual com React, Vite e TypeScript |
| ADR 003 | Banco de dados PostgreSQL |
| ADR 004 | Redis para cache e filas |
| ADR 005 | Arquitetura inicial em monolito modular |
| ADR 006 | Autenticação com Laravel Sanctum |
| ADR 007 | Docker Compose para ambiente local |
| ADR 008 | Multi-repo para separar backend, frontend, infra e documentação |
| ADR 009 | Git Flow simplificado com Pull Requests |
| ADR 010 | WhatsApp oficial via Meta Cloud API em fase futura |

## O que evitar neste momento

Evite adicionar complexidade antes da necessidade real.

Não usar agora:

1. Microsserviços.
2. Kubernetes.
3. Elasticsearch.
4. Mensageria complexa com RabbitMQ.
5. Múltiplos bancos de dados.
6. Autenticação própria escrita do zero.
7. Deploy manual sem documentação.
8. Bibliotecas sem manutenção ou sem documentação.

## Critério para aprovar mudanças técnicas

Uma mudança técnica deve responder a estas perguntas:

1. Resolve um problema real do CRM?
2. O time consegue manter essa solução?
3. A solução é segura?
4. A solução é testável?
5. A solução é simples o suficiente para o estágio atual?
6. Existe documentação oficial confiável?
7. O impacto na sprint foi considerado?
8. O Tech Lead aprovou quando necessário?
