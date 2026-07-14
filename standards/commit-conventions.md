# Convenção de Commits

Usamos o padrão Conventional Commits para manter o histórico do projeto organizado, legível e fácil de revisar.

Documentação oficial:

```text
https://www.conventionalcommits.org
```

## Formato

Todo commit deve seguir este formato:

```text
<tipo>(<escopo>): <descrição curta>

[corpo opcional]

[rodapé opcional]
```

Exemplo com rodapé:

```text
feat(auth): adiciona endpoint de login com Sanctum

Implementa autenticação inicial para usuários internos do CRM.

Closes #123
```

## Tipos permitidos

| Tipo | Quando usar |
|---|---|
| `feat` | Nova funcionalidade |
| `fix` | Correção de bug |
| `docs` | Alterações somente em documentação |
| `style` | Formatação de código sem mudança de lógica |
| `refactor` | Refatoração sem mudança de comportamento |
| `test` | Adição ou atualização de testes |
| `chore` | Tarefas de manutenção, dependências ou configuração |
| `perf` | Melhoria de performance |
| `ci` | Alterações em CI/CD |
| `revert` | Reversão de um commit anterior |

## Escopos recomendados

O escopo indica a área afetada pelo commit.

Escopos recomendados para o CRM:

```text
auth
users
contacts
students
courses
enrollments
pipeline
payments
whatsapp
api
db
ui
infra
docker
redis
postgres
qa
docs
deps
```

## Exemplos corretos

```bash
feat(auth): adiciona endpoint de login com Sanctum
fix(auth): corrige retorno de credenciais inválidas
docs(readme): atualiza instruções de execução local
chore(deps): atualiza dependências do frontend
test(auth): adiciona testes para login inválido
refactor(auth): move validação para LoginRequest
feat(ui): cria tela de login integrada com a API
chore(infra): adiciona configuração inicial do Docker Compose
```

## Exemplos incorretos

```bash
arrumei bug
commit
teste
wip
subindo alterações
login pronto
fix stuff
```

## Regras

1. A descrição deve ser curta e objetiva.
2. Use letras minúsculas na descrição.
3. Não coloque ponto final na descrição.
4. O limite recomendado é de 72 caracteres na primeira linha.
5. Cada commit deve representar uma única mudança.
6. Não misture alterações não relacionadas no mesmo commit.
7. Não envie commits com senhas, tokens ou arquivos `.env`.
8. Não use `wip` como mensagem final de commit.
9. O corpo do commit deve explicar o motivo da mudança quando necessário.
10. O rodapé deve referenciar a issue ou task quando existir.

## Commits atômicos

Prefira vários commits pequenos e claros em vez de um commit grande e confuso.

Errado:

```bash
feat(auth): adiciona login, logout, seeders, testes e tela
```

Correto:

```bash
feat(auth): adiciona endpoint de login
feat(auth): adiciona endpoint de logout
chore(auth): cria seeders de usuários internos
test(auth): adiciona testes de autenticação
feat(ui): integra tela de login com a API
```

## Relação com o Jira

Quando uma tarefa tiver código no Jira, use o número da task na branch ou no Pull Request.

Exemplo:

```text
SCRUM-2
SCRUM-9
SCRUM-15
```

Exemplo de commit:

```bash
chore(infra): adiciona docker-compose inicial
```

Exemplo de branch:

```bash
feature/scrum-2-criar-docker-compose
```
