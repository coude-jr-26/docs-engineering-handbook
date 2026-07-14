# Diretrizes de Pull Request

Pull Request é o processo usado para revisar e integrar mudanças ao projeto.

Todo código deve entrar por Pull Request. Isso protege o projeto contra erros, melhora a qualidade e permite que o time aprenda com revisão de código.

## Antes de abrir um Pull Request

Antes de abrir o Pull Request, confirme:

- [ ] Sua branch foi criada a partir da branch correta.
- [ ] Sua branch está atualizada com `develop`.
- [ ] A tarefa no Jira está clara.
- [ ] Os critérios de aceite foram atendidos.
- [ ] Os testes locais foram executados.
- [ ] Não há erros de lint.
- [ ] Não há código de debug.
- [ ] Não há senhas, tokens ou credenciais.
- [ ] A documentação foi atualizada quando necessário.
- [ ] O Pull Request está pequeno e focado.

Se o repositório ainda não tiver branch `develop`, confirme com o Tech Lead qual branch deve ser usada como base.

## Nome de branches

Use este padrão:

```text
<tipo>/<codigo-da-task>-<descricao-em-kebab-case>
```

Exemplos:

```text
feature/scrum-2-criar-docker-compose
feature/scrum-10-adicionar-login-api
fix/scrum-15-corrigir-validacao-login
docs/scrum-9-documentar-execucao-local
test/scrum-20-adicionar-testes-auth
chore/scrum-30-configurar-env-example
```

## Tipos de branch

| Tipo | Uso |
|---|---|
| `feature` | Nova funcionalidade |
| `fix` | Correção de bug |
| `docs` | Alteração de documentação |
| `test` | Criação ou ajuste de testes |
| `chore` | Configuração, dependências ou manutenção |
| `refactor` | Refatoração sem mudança de comportamento |
| `hotfix` | Correção urgente em produção |

## Tamanho do Pull Request

Pull Requests pequenos são mais fáceis de revisar e têm menos risco.

| Tamanho | Linhas alteradas | Recomendação |
|---|---|---|
| Pequeno | Menos de 200 linhas | Ideal |
| Médio | Entre 200 e 500 linhas | Aceitável com boa descrição |
| Grande | Mais de 500 linhas | Evite ou justifique |

Se a tarefa for grande, divida em Pull Requests menores.

Exemplo de divisão:

```text
PR 1: cria estrutura base
PR 2: implementa endpoint
PR 3: adiciona testes
PR 4: atualiza documentação
```

## Título do Pull Request

O título deve seguir o padrão de commits.

Exemplos:

```text
feat(auth): adiciona endpoint de login
fix(ui): corrige mensagem de erro no login
docs(infra): documenta execução local com Docker
chore(infra): adiciona configuração inicial do Redis
test(auth): adiciona testes para credenciais inválidas
```

## Descrição do Pull Request

Use este modelo:

```markdown
## O que foi feito?

Descreva de forma objetiva o que este Pull Request altera.

## Por que isso é necessário?

Explique o motivo da mudança e o problema que ela resolve.

## Como testar?

Liste o passo a passo para testar.

1.
2.
3.

## Evidências

Inclua prints, logs, respostas da API ou observações relevantes quando necessário.

## Checklist

- [ ] Testei localmente
- [ ] Atualizei a documentação quando necessário
- [ ] Não deixei código de debug
- [ ] Não enviei segredos ou credenciais
- [ ] A task do Jira foi atualizada

## Issues ou tasks relacionadas

Closes SCRUM-000
```

## Processo de revisão

1. Abra o Pull Request como `Draft` enquanto ainda estiver trabalhando.
2. Quando terminar, mude para `Ready for review`.
3. Solicite revisão das pessoas corretas.
4. Responda todos os comentários da revisão.
5. Faça os ajustes necessários.
6. Depois dos ajustes, solicite nova revisão.
7. Não faça merge do seu próprio Pull Request sem autorização.

## Quem deve revisar

| Tipo de mudança | Revisor recomendado |
|---|---|
| Backend | Alguém do time backend ou Tech Lead |
| Frontend | Alguém do time frontend ou Tech Lead |
| Infraestrutura | Alguém do time devops ou Tech Lead |
| Testes e QA | Alguém do time qa ou Tech Lead |
| Documentação | Alguém do docs-team ou Tech Lead |
| Mudança crítica | Tech Lead obrigatório |

## Como pedir revisão

Exemplo de mensagem:

```text
Pessoal, abri o PR da task SCRUM-2.

Resumo:
Criei o docker-compose inicial com PostgreSQL e Redis.

Link:
https://github.com/coude-jr-26/crm-infra/pull/1

Podem revisar quando possível?
```

## Como fazer uma boa revisão

Ao revisar, seja claro, técnico e respeitoso.

Use estes prefixos:

```text
bloqueante: precisa ser corrigido antes do merge
sugestão: melhoria recomendada, mas não obrigatória
pergunta: dúvida sobre a implementação
elogio: ponto positivo da solução
nit: ajuste pequeno de estilo ou legibilidade
```

Exemplos:

```text
bloqueante: essa variável de ambiente não pode ter valor fixo no código. Use .env.

sugestão: considere extrair essa lógica para uma função separada.

pergunta: por que optou por armazenar esse valor no localStorage?

elogio: boa separação entre validação e regra de negócio.

nit: ajustar nome da variável para ficar mais descritivo.
```

## O que verificar em revisão de backend

- [ ] Controller está simples.
- [ ] Validação está em Form Request quando aplicável.
- [ ] Regras de negócio não estão misturadas no Controller.
- [ ] Respostas HTTP estão corretas.
- [ ] Autenticação foi aplicada quando necessário.
- [ ] Não há dados sensíveis em logs.
- [ ] Migrations estão coerentes.
- [ ] Testes foram adicionados quando necessário.

## O que verificar em revisão de frontend

- [ ] Componentes estão bem organizados.
- [ ] Tipos TypeScript estão corretos.
- [ ] Não há `any` sem justificativa.
- [ ] Estados de loading foram tratados.
- [ ] Estados de erro foram tratados.
- [ ] Formulários têm validação.
- [ ] Não há dados sensíveis salvos de forma insegura.
- [ ] A interface foi testada no navegador.

## O que verificar em revisão de infraestrutura

- [ ] Docker Compose está válido.
- [ ] Containers sobem corretamente.
- [ ] Variáveis de ambiente estão documentadas.
- [ ] Volumes estão definidos corretamente.
- [ ] Networks estão definidas corretamente.
- [ ] O README explica como executar.
- [ ] O ambiente foi testado localmente.

## Estratégia de merge

| Origem | Destino | Estratégia |
|---|---|---|
| `feature/*` | `develop` | Squash and merge |
| `fix/*` | `develop` | Squash and merge |
| `docs/*` | `develop` | Squash and merge |
| `test/*` | `develop` | Squash and merge |
| `develop` | `main` | Merge commit |
| `hotfix/*` | `main` | Squash and merge |

Depois de um hotfix em `main`, a correção deve ser aplicada também em `develop`.

## Regras finais

1. Não faça merge com CI quebrado quando houver CI configurado.
2. Não faça merge sem aprovação.
3. Não resolva comentários sem responder.
4. Não use Pull Request para juntar várias tarefas sem relação.
5. Não altere arquivos fora do escopo da task sem explicar.
6. Se o Pull Request ficou grande demais, converse com o Tech Lead.
7. Se houver dúvida técnica importante, registre a decisão na documentação.
