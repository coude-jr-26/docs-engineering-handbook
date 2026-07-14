# Processos de Trabalho

Este documento define como a equipe trabalha no dia a dia, como as tarefas são organizadas, como as sprints funcionam, como Pull Requests são revisados, como releases são feitos e como incidentes devem ser tratados.

O objetivo é dar previsibilidade ao time e reduzir confusão durante o desenvolvimento do CRM da Escola Coude.

## Princípios do processo

1. Clareza antes de velocidade.
2. Comunicação antes de suposição.
3. Pull Request antes de merge.
4. Tarefas pequenas antes de grandes entregas.
5. Revisão antes de produção.
6. Documentação junto com a entrega.
7. Ajuda rápida antes de bloqueio silencioso.

## Fluxo de trabalho no Jira

As tarefas devem passar por um fluxo simples.

```text
Backlog
  To Do
    In Progress
      Code Review
        QA
          Done
```

## Significado de cada status

| Status | Significado |
|---|---|
| Backlog | Tarefa ainda não planejada para execução imediata |
| To Do | Tarefa planejada para a sprint |
| In Progress | Alguém está trabalhando na tarefa |
| Code Review | Existe Pull Request aberto aguardando revisão |
| QA | A tarefa está sendo validada |
| Done | A tarefa foi concluída e validada |

## Regras de movimentação no Jira

1. Só mova uma tarefa para `In Progress` quando começar de fato.
2. Não deixe tarefa em `In Progress` se você não está trabalhando nela.
3. Ao abrir Pull Request, mova a tarefa para `Code Review`.
4. Após aprovação técnica, mova para `QA` quando houver validação.
5. Só mova para `Done` quando os critérios de aceite forem cumpridos.
6. Se estiver bloqueado, sinalize no Jira e no canal do squad.

## Definição de pronto para iniciar

Antes de alguém começar uma tarefa, ela deve estar clara.

Uma tarefa está pronta para iniciar quando:

- [ ] Tem descrição objetiva.
- [ ] Tem critérios de aceite.
- [ ] Tem responsável definido.
- [ ] Tem squad definido.
- [ ] Tem prioridade definida.
- [ ] Tem dependências conhecidas.
- [ ] O membro sabe qual repositório deve alterar.

## Definição de pronto para concluir

Uma tarefa está pronta para concluir quando:

- [ ] O código foi implementado.
- [ ] O Pull Request foi aberto.
- [ ] O Pull Request foi revisado.
- [ ] Os ajustes solicitados foram feitos.
- [ ] Os testes necessários foram executados.
- [ ] A documentação foi atualizada quando necessário.
- [ ] A validação foi feita.
- [ ] A task foi atualizada no Jira.

Consulte também:

```text
standards/definitions-of-done.md
```

## Duração das sprints

O padrão recomendado é trabalhar com sprints de 1 a 2 semanas.

Para a Sprint 1, o foco é estabilização inicial:

1. Organização do GitHub.
2. Infraestrutura local.
3. Autenticação no backend.
4. Tela de login no frontend.
5. Validação de QA.
6. Documentação mínima de execução.

## Rotina sugerida da sprint

### Início da sprint

1. Revisar backlog.
2. Confirmar prioridades.
3. Dividir tarefas por squad.
4. Validar dependências.
5. Definir responsáveis.
6. Confirmar critérios de aceite.

### Durante a sprint

1. Atualizar o Jira.
2. Fazer commits pequenos.
3. Abrir Pull Requests pequenos.
4. Pedir ajuda quando houver bloqueio.
5. Revisar Pull Requests de colegas.
6. Testar entregas integradas.

### Final da sprint

1. Validar tarefas concluídas.
2. Apresentar o que foi entregue.
3. Registrar problemas encontrados.
4. Fazer retrospectiva.
5. Planejar melhorias para a próxima sprint.

## Cerimônias

### Planning

Objetivo:

```text
Definir o que será feito na sprint e quem será responsável por cada tarefa.
```

Participantes:

```text
Tech Leads
Squads envolvidos
QA quando houver validação relevante
```

Pauta recomendada:

1. Objetivo da sprint.
2. Tarefas principais.
3. Dependências.
4. Responsáveis.
5. Riscos.
6. Critérios de aceite.

### Daily assíncrona

A daily pode ser feita de forma assíncrona no canal do squad.

Formato recomendado:

```text
O que fiz desde a última atualização:
- 

O que vou fazer agora:
- 

Bloqueios ou dúvidas:
- 
```

Regra importante:

```text
Se ficar travado por mais de 30 minutos, peça ajuda.
```

### Review

Objetivo:

```text
Mostrar o que foi entregue na sprint.
```

Pauta recomendada:

1. O que foi concluído.
2. O que ficou pendente.
3. Demonstração rápida das entregas.
4. Problemas encontrados.
5. Próximos passos.

### Retrospectiva

Objetivo:

```text
Melhorar o processo de trabalho.
```

Formato simples:

```text
O que funcionou bem?
O que não funcionou?
O que devemos melhorar na próxima sprint?
```

## Processo de Pull Request

Todo código deve entrar por Pull Request.

Fluxo recomendado:

```text
Criar branch
  Implementar tarefa
    Fazer commits
      Abrir Pull Request
        Solicitar revisão
          Ajustar comentários
            Aprovar
              Fazer merge
```

Regras:

1. Não fazer commit direto na `main`.
2. Não fazer merge sem revisão.
3. Não fazer merge do próprio Pull Request sem autorização.
4. Manter Pull Requests pequenos.
5. Explicar como testar.
6. Atualizar documentação quando necessário.

Consulte também:

```text
standards/pr-guidelines.md
```

## Branches

Padrão recomendado:

```text
main
develop
feature/*
fix/*
docs/*
test/*
chore/*
hotfix/*
```

## Uso das branches

| Branch | Uso |
|---|---|
| `main` | Código estável ou produção |
| `develop` | Integração das entregas da sprint |
| `feature/*` | Nova funcionalidade |
| `fix/*` | Correção de bug |
| `docs/*` | Documentação |
| `test/*` | Testes |
| `chore/*` | Configuração ou manutenção |
| `hotfix/*` | Correção urgente |

## Observação sobre branch protection

No plano gratuito do GitHub, repositórios privados podem não permitir proteção de branch.

Enquanto isso, a proteção deve ser operacional:

```text
Ninguém commita direto na main.
Todo código entra por Pull Request.
Tech Leads devem monitorar merges.
```

## Processo de release

Release é o processo de preparar uma versão estável do sistema.

Fluxo recomendado:

```text
feature/* entra em develop
  develop é validada
    release é criada
      main recebe merge
        tag de versão é criada
          deploy é executado
```

## Versionamento

Use versionamento semântico quando o projeto tiver releases formais.

Formato:

```text
vMAJOR.MINOR.PATCH
```

Exemplos:

```text
v0.1.0
v0.2.0
v1.0.0
```

Significado:

| Parte | Significado |
|---|---|
| MAJOR | Mudança grande ou incompatível |
| MINOR | Nova funcionalidade compatível |
| PATCH | Correção de bug |

## Checklist de release

Antes de uma release:

- [ ] Todas as tarefas planejadas foram revisadas.
- [ ] Os testes principais foram executados.
- [ ] O fluxo de login funciona.
- [ ] O backend sobe corretamente.
- [ ] O frontend sobe corretamente.
- [ ] O Docker Compose funciona.
- [ ] O `.env.example` está atualizado.
- [ ] Não há segredos no repositório.
- [ ] O README foi atualizado.
- [ ] QA validou os fluxos principais.

## Processo de incidente

Incidente é qualquer problema que bloqueia o uso, quebra o ambiente ou ameaça dados.

## Níveis de severidade

| Nível | Descrição | Exemplo |
|---|---|---|
| P0 | Crítico | Sistema fora do ar em produção |
| P1 | Alto | Login indisponível ou perda de funcionalidade crítica |
| P2 | Médio | Bug importante com alternativa temporária |
| P3 | Baixo | Problema menor ou melhoria |

## Como reportar incidente

Use este modelo:

```text
Título:
Severidade:
Ambiente:
Horário identificado:
Quem identificou:
Descrição:
Passos para reproduzir:
Impacto:
Evidências:
Ação tomada até agora:
Responsável atual:
```

## Fluxo de resposta a incidente

```text
Identificar
  Classificar severidade
    Comunicar responsáveis
      Investigar causa
        Aplicar correção
          Validar
            Documentar aprendizado
```

## Regras para incidentes

1. Não esconder problema.
2. Avisar rapidamente o Tech Lead.
3. Evitar mexer em produção sem alinhamento.
4. Registrar o que foi feito.
5. Validar a correção.
6. Documentar a causa quando for relevante.

## Comunicação

Canais de comunicação devem ser usados com clareza.

Regras:

1. Dúvidas técnicas devem ir para o canal do squad.
2. Bloqueios devem ser informados rapidamente.
3. Decisões importantes devem ser registradas.
4. Conversas críticas devem virar documentação ou comentário no Jira.
5. Ninguém deve ficar travado por horas em silêncio.

## Como pedir ajuda

Pedido ruim:

```text
Não funciona.
```

Pedido bom:

```text
Estou tentando executar a task SCRUM-2.

O objetivo é subir o Docker Compose.
O erro acontece ao iniciar o PostgreSQL.
Já tentei rodar docker compose down -v e subir novamente.

Erro exibido:
cole o erro aqui

Alguém consegue revisar comigo?
```

## Papéis principais

| Papel | Responsabilidade |
|---|---|
| Tech Lead | Direção técnica, revisão crítica e desbloqueio |
| Backend | API, autenticação, banco e regras de negócio |
| Frontend | Interface, integração com API e experiência do usuário |
| DevOps | Docker, infraestrutura, ambiente e deploy |
| QA | Testes, validação e regressão |
| Documentação | Guias, padrões e organização do conhecimento |

## Regras finais

1. Atualize o Jira.
2. Trabalhe em branch.
3. Abra Pull Request.
4. Peça revisão.
5. Teste antes de entregar.
6. Documente mudanças relevantes.
7. Avise bloqueios cedo.
8. Respeite os padrões do projeto.
