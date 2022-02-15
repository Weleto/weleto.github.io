---
layout: default
title: Login
parent: Autenticação
nav_order: 2
---

# Login
## POST /oauth/token

Cria um token de acesso OAuth, o qual será utilizado para realizar as requisições na API do Weleto.

**Estrutura da URL:** https://weleto.com.br/oauth/token

### Exemplo
```
curl \
  -d '{"email":"fulano@email.com", "password":"senha123", "grant_type":"password", "client_id":"chave_codigo_do_cliente", "client_secret":"chave_segredo"}'\
  -H "Content-Type: application/json"\
  -X POST https://weleto.com.br/oauth/token
```

### Parâmetros
```
{
  "email":"fulano@email.com",
  "password": "senha123",
  "grant_type": "password",
  "client_id": "chave_codigo_do_cliente",
  "client_secret": "chave_segredo"
}
```

Caso não possua o `client_id` e o `client_secret` entrar em contato através do e-mail [contato@weleto.com.br](mailto:contato@weleto.com.br).

| Campo | Descrição | Obrigatório? |
|:-------------|:------------------|:-------------|
| email | E-mail do usuário cadastrado no Weleto | SIM |
| password | Senha do usuário do Weleto | SIM |
| grant_type | Tipo de concessão | SIM - utilizar `password` |
| client_id | Chave única gerada para acessar os recursos do Weleto | SIM |
| client_secret | Chave segredo gerada para acessar os recursos do Weleto | SIM |

### Retorno
```
{
  "access_token": "...",
  "token_type": "Bearer",
  "expires_in": 7200,
  "refresh_token": "...",
  "created_at": "..."
}
```

| Campo | Descrição | Observação |
|:-------------|:------------------|:-------------|
| access_token | Token de acesso gerado | Será utilizado para realizar as requisições na API |
| token_type | Tipo do token | Sempre será `Bearer` |
| expires_in | Tempo de expiração do token (em segundos) | Por padrão, será 7200 |
| created_at | Data e Hora de criação do token | formato unix timestamp |
