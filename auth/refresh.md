---
layout: default
title: Atualização do Token
parent: Autenticação
nav_order: 2
---

# Atualização do Token
## POST /oauth/token

Cria um novo token, caso esteja expirado, utilizando o a estratégia refresh token do padrão OAuth2.

**Estrutura da URL:** https://weleto.com.br/oauth/token

### Exemplo
```
curl \
  -d '{"refresh_token":"refresh_token", grant_type":"refresh_token", "client_id":"chave_codigo_do_cliente", "client_secret":"chave_segredo"}'\
  -H "Content-Type: application/json"\
  -X POST https://weleto.com.br/oauth/token
```

### Parâmetros
```
{
  "grant_type": "refresh_token",
  "refresh_token": "refresh_token",
  "client_id": "client_id",
  "client_secret": "client_secret"
}
```

Caso não possua o `client_id` e o `client_secret` entrar em contato através do e-mail [contato@weleto.com.br](mailto:contato@weleto.com.br).

| Campo | Descrição | Obrigatório? |
|:-------------|:------------------|:-------------|
| grant_type | Tipo de concessão | SIM - utilizar `refresh_token` |
| refresh_token | Valor é retornado ao efetuar [login](/auth/login) | SIM - utilizar o atributo `refresh_token` |
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
