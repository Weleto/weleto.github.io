---
layout: default
title: Obter dados atuais
parent: Usuário
nav_order: 1
---

# Obter dados atuais
## GET /public_api/v1/user

Retornar os dados do usuário atual, utilizando o token de acesso como base.

**Estrutura da URL:** https://weleto.com.br/public_api/v1/user

### Exemplo
```
curl \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer access_token" \
  https://weleto.com.br/public_api/v1/user
```

### Parâmetros
```
{
  access_token: "access_token"
}
```

| Campo | Descrição | Obrigatório? |
|:-------------|:------------------|:-------------|
| access_token | Chave de acesso para o usuário | SIM - Posso ser passado via query string ou header `Authorization` |

### Retorno
```
{
  "id": 123456,
  "email": "email@usuario.com",
  "social_networks": {
    "facebook": "exemplo",
    "whatsapp": "987654321",
    "telegram": "123456789",
    "instagram": "exemplo"
  }
}
```

| Campo | Descrição | Observação |
|:-------------|:------------------|:-------------|
| id | ID do usuário dentro do Weleto | Será sempre um número inteiro |
| email | E-mail do usuário |  |
| social_networks | Redes Sociais do usuário | Será um objeto chave/valor, conforme o exemplo |
