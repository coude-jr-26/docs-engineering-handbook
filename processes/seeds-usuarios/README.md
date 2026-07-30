# Seeds - Usuário de Desenvolvimento

## O que foi feito

Criação do `UserSeeder`, responsável por popular automaticamente a tabela `users` com um usuário de desenvolvimento/teste, eliminando a necessidade de um fluxo de cadastro (Register) no ambiente.

## Como foi feito

O Seeder foi construído utilizando a estrutura padrão do Laravel:

- `namespace Database\Seeders` — localiza o arquivo dentro da pasta de Seeders do projeto.
- `use Illuminate\Database\Seeder` — importa a classe base que fornece a funcionalidade de "alimentar" o banco de dados.
- `use App\Models\User` — conecta o código diretamente ao model `User`, que representa a tabela `users` no banco.
- `class UserSeeder extends Seeder` — define a classe do Seeder.
- `public function run()` — método principal; todo o código dentro dele é executado ao rodar o comando de seed.
- `User::create([...])` — cria e salva o novo registro na tabela `users`, com a senha armazenada de forma criptografada (`bcrypt`).

O `DatabaseSeeder.php` (arquivo "mestre" que registra todos os seeders do projeto) já existia previamente e não precisou ser criado.

## Executando

```bash
php artisan migrate
php artisan db:seed --class=UserSeeder
```

## Usuário criado

| Campo | Valor |
|---|---|
| Nome | Wagner |
| Email | wagner@gmail.com |
| Senha | Wagner.123 |

## Validação do Seeder

Após executar o comando, verificar:

- O comando foi executado sem erros.
- O usuário foi criado corretamente na tabela `users`.
- A senha foi armazenada criptografada (Hash/bcrypt), nunca em texto puro.
- Não existem registros duplicados caso o Seeder seja executado mais de uma vez.

## Observações

- Este Seeder cria **1 usuário** de desenvolvimento. A criação de usuários adicionais de teste é escopo do card SCRUM-29 (responsabilidade de outra pessoa da equipe).
- A UserFactory (SCRUM-27) ainda está pendente; este Seeder, por ora, insere os dados diretamente via `User::create()`.

## Referências

- Card Jira: [SCRUM-30](https://limalipe355.atlassian.net/browse/SCRUM-30)
- Cards relacionados: SCRUM-27 (UserFactory), SCRUM-28 (Seeder), SCRUM-29 (Usuários de teste)