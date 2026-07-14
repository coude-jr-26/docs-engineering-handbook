# Recursos do Projeto

Este documento reúne links úteis, glossário, comandos frequentes e materiais de apoio para os membros da Coude Jr 2026.1 que estão trabalhando no CRM da Escola Coude.

Use este arquivo como ponto de consulta rápida durante o desenvolvimento.

## Links internos

| Recurso | Link |
|---|---|
| Organização GitHub | https://github.com/coude-jr-26 |
| Manual de engenharia | https://github.com/coude-jr-26/docs-engineering-handbook |
| Backend | https://github.com/coude-jr-26/crm-backend |
| Frontend | https://github.com/coude-jr-26/crm-frontend |
| Infraestrutura | https://github.com/coude-jr-26/crm-infra |
| Shared libs | https://github.com/coude-jr-26/crm-shared-libs |
| Templates globais | https://github.com/coude-jr-26/.github |

## Documentações oficiais

### Backend

| Tecnologia | Link |
|---|---|
| Laravel | https://laravel.com/docs |
| Laravel Sanctum | https://laravel.com/docs/sanctum |
| Eloquent ORM | https://laravel.com/docs/eloquent |
| Migrations | https://laravel.com/docs/migrations |
| Validation | https://laravel.com/docs/validation |
| Queues | https://laravel.com/docs/queues |
| Cache | https://laravel.com/docs/cache |
| PHPUnit | https://phpunit.de/documentation.html |
| Pest | https://pestphp.com/docs |

### Frontend

| Tecnologia | Link |
|---|---|
| React | https://react.dev |
| TypeScript | https://www.typescriptlang.org/docs |
| Vite | https://vitejs.dev/guide |
| React Router | https://reactrouter.com |
| Axios | https://axios-http.com/docs/intro |
| React Hook Form | https://react-hook-form.com |
| Zod | https://zod.dev |
| Vitest | https://vitest.dev |
| Testing Library | https://testing-library.com |

### Infraestrutura

| Tecnologia | Link |
|---|---|
| Docker | https://docs.docker.com |
| Docker Compose | https://docs.docker.com/compose |
| Nginx | https://nginx.org/en/docs |
| PostgreSQL | https://www.postgresql.org/docs |
| Redis | https://redis.io/docs |
| GitHub Actions | https://docs.github.com/actions |

### Git e GitHub

| Recurso | Link |
|---|---|
| Git | https://git-scm.com/doc |
| GitHub Docs | https://docs.github.com |
| GitHub Teams | https://docs.github.com/en/organizations/organizing-members-into-teams |
| Pull Requests | https://docs.github.com/en/pull-requests |
| GitHub CLI | https://cli.github.com/manual |

### Segurança e LGPD

| Recurso | Link |
|---|---|
| LGPD | https://www.gov.br/anpd |
| ANPD | https://www.gov.br/anpd/pt-br |
| OWASP Top 10 | https://owasp.org/www-project-top-ten |
| OWASP Cheat Sheet Series | https://cheatsheetseries.owasp.org |

### Integrações futuras

| Recurso | Link |
|---|---|
| Meta for Developers | https://developers.facebook.com |
| WhatsApp Cloud API | https://developers.facebook.com/docs/whatsapp/cloud-api |
| Webhooks WhatsApp | https://developers.facebook.com/docs/whatsapp/cloud-api/webhooks |

## Glossário

| Termo | Significado |
|---|---|
| API | Interface que permite comunicação entre sistemas |
| Endpoint | URL específica de uma API, como `/api/login` |
| Backend | Parte do sistema responsável por regras de negócio, banco e API |
| Frontend | Parte visual do sistema acessada pelo usuário |
| Banco de dados | Local onde os dados do sistema são armazenados |
| PostgreSQL | Banco de dados relacional usado no projeto |
| Redis | Banco em memória usado para cache e filas |
| Docker | Ferramenta para rodar aplicações em containers |
| Docker Compose | Ferramenta para subir vários containers juntos |
| Container | Ambiente isolado onde uma aplicação roda |
| Nginx | Servidor web usado como proxy ou servidor HTTP |
| Laravel | Framework PHP usado no backend |
| Sanctum | Pacote Laravel usado para autenticação via token |
| Migration | Arquivo que cria ou altera estrutura do banco |
| Seeder | Arquivo que insere dados iniciais ou de teste no banco |
| Model | Classe que representa uma tabela ou entidade |
| Controller | Classe que recebe requisições HTTP |
| Form Request | Classe Laravel usada para validar entrada de dados |
| Service | Classe que concentra regra de negócio |
| Resource | Classe que padroniza resposta da API |
| React | Biblioteca usada para criar interfaces |
| TypeScript | Superset do JavaScript com tipagem |
| Vite | Ferramenta de build usada no frontend |
| Pull Request | Solicitação para revisar e integrar código |
| Code Review | Revisão de código feita por outra pessoa |
| Branch | Linha separada de desenvolvimento no Git |
| Commit | Registro de uma alteração no Git |
| Merge | Integração de uma branch em outra |
| CI | Integração contínua, usada para rodar validações automáticas |
| CD | Entrega ou deploy contínuo |
| Jira | Ferramenta usada para organizar tarefas |
| Sprint | Ciclo de trabalho com objetivo definido |
| Backlog | Lista de tarefas ainda não executadas |
| Critério de aceite | Condição que define se uma tarefa está correta |
| Definition of Done | Lista de critérios para considerar uma tarefa pronta |
| Staging | Ambiente de teste parecido com produção |
| Produção | Ambiente real usado pelos usuários finais |
| Hotfix | Correção urgente feita diretamente para produção |
| LGPD | Lei Geral de Proteção de Dados |
| Token | Credencial usada para autenticação |
| Webhook | Requisição enviada automaticamente por um serviço externo |
| Cache | Armazenamento temporário para acelerar consultas |
| Fila | Estrutura para processar tarefas assíncronas |

## Comandos comuns

### Git

Clonar repositório:

```bash
git clone https://github.com/coude-jr-26/NOME-DO-REPOSITORIO.git
```

Ver branch atual:

```bash
git branch
```

Atualizar branch local:

```bash
git pull origin main
```

Criar branch:

```bash
git checkout -b feature/scrum-2-criar-docker-compose
```

Adicionar arquivos:

```bash
git add .
```

Criar commit:

```bash
git commit -m "chore(infra): adiciona docker-compose inicial"
```

Enviar branch:

```bash
git push origin feature/scrum-2-criar-docker-compose
```

Ver status:

```bash
git status
```

Ver histórico:

```bash
git log --oneline
```

### Docker

Ver containers em execução:

```bash
docker ps
```

Subir ambiente:

```bash
docker compose up -d
```

Parar ambiente:

```bash
docker compose down
```

Parar ambiente e remover volumes:

```bash
docker compose down -v
```

Ver logs:

```bash
docker compose logs -f
```

Ver logs de um serviço específico:

```bash
docker compose logs -f app
```

Validar arquivo Docker Compose:

```bash
docker compose config
```

Acessar container:

```bash
docker compose exec app bash
```

### Laravel

Instalar dependências:

```bash
composer install
```

Gerar chave da aplicação:

```bash
php artisan key:generate
```

Rodar migrations:

```bash
php artisan migrate
```

Rodar migrations com seeders:

```bash
php artisan migrate --seed
```

Limpar cache:

```bash
php artisan optimize:clear
```

Rodar testes:

```bash
php artisan test
```

Criar controller:

```bash
php artisan make:controller Auth/LoginController
```

Criar request:

```bash
php artisan make:request LoginRequest
```

Criar seeder:

```bash
php artisan make:seeder UserSeeder
```

### Frontend

Instalar dependências:

```bash
npm install
```

Rodar ambiente local:

```bash
npm run dev
```

Rodar build:

```bash
npm run build
```

Rodar lint:

```bash
npm run lint
```

Rodar testes:

```bash
npm test
```

### PostgreSQL

Acessar PostgreSQL pelo Docker:

```bash
docker compose exec postgres psql -U postgres -d crm_coude
```

Listar tabelas:

```sql
\dt
```

Sair do psql:

```sql
\q
```

## Problemas comuns

### Não consigo acessar o repositório

Possíveis causas:

1. Você ainda não aceitou o convite da organização.
2. Você está no time errado.
3. O time ainda não recebeu permissão no repositório.
4. Você está usando a conta GitHub errada.

Envie ao Tech Lead:

```text
Nome:
Username GitHub:
Repositório:
Erro exibido:
Time esperado:
```

### Docker não sobe

Tente:

```bash
docker compose down
docker compose up -d
```

Se ainda falhar:

```bash
docker compose logs -f
```

Verifique:

1. Se o Docker Desktop está aberto.
2. Se alguma porta já está em uso.
3. Se o arquivo `.env` existe.
4. Se o arquivo `docker-compose.yml` está válido.

### Porta já está em uso

Verifique se outro processo está usando a porta.

Portas comuns:

| Serviço | Porta |
|---|---|
| Frontend | 3000 ou 5173 |
| Backend | 8000 |
| PostgreSQL | 5432 |
| Redis | 6379 |
| Nginx | 80 ou 8080 |

Solução rápida:

```bash
docker compose down
docker ps
```

### Laravel não conecta no banco

Verifique o `.env`.

Exemplo esperado:

```text
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=crm_coude
DB_USERNAME=postgres
DB_PASSWORD=secret
```

Depois rode:

```bash
php artisan optimize:clear
php artisan migrate
```

### Frontend não chama a API

Verifique a variável de ambiente.

Exemplo:

```text
VITE_API_URL=http://localhost:8000/api
```

Verifique também:

1. Se o backend está rodando.
2. Se a URL está correta.
3. Se há erro de CORS.
4. Se o endpoint existe.
5. Se o token está sendo enviado quando necessário.

### Erro de permissão em arquivos Laravel

Tente:

```bash
chmod -R 775 storage bootstrap/cache
```

Se estiver usando Docker, rode dentro do container correto.

### Fiz commit errado

Se ainda não enviou para o GitHub:

```bash
git reset --soft HEAD~1
```

Se já enviou, peça orientação ao Tech Lead antes de alterar histórico.

## Como pedir ajuda corretamente

Use este modelo:

```text
Estou trabalhando na task:
SCRUM-000

O que estou tentando fazer:
descreva o objetivo

O que aconteceu:
descreva o erro

O que eu já tentei:
liste tentativas

Erro completo:
cole o erro aqui

Arquivo ou trecho relevante:
cole o trecho aqui
```

## Materiais de estudo recomendados

### Para backend

1. Laravel Routing.
2. Laravel Controllers.
3. Laravel Requests.
4. Laravel Eloquent.
5. Laravel Sanctum.
6. Migrations e seeders.
7. Testes com PHPUnit ou Pest.

### Para frontend

1. React básico.
2. TypeScript básico.
3. Componentização.
4. React Router.
5. Axios.
6. Formulários com React Hook Form.
7. Validação com Zod.

### Para infraestrutura

1. Docker básico.
2. Docker Compose.
3. PostgreSQL básico.
4. Redis básico.
5. Nginx básico.
6. Variáveis de ambiente.

### Para QA

1. Casos de teste.
2. Teste manual.
3. Teste de regressão.
4. Teste de API.
5. Evidências de bug.
6. Critérios de aceite.

## Regra dos 30 minutos

Se você ficar travado por mais de 30 minutos no mesmo problema, peça ajuda.

Não espere horas em silêncio.

Pedir ajuda cedo evita bloqueio da sprint e ajuda o time a aprender mais rápido.
