---
layout: default
title: Atualizar redes sociais
parent: Usuário
nav_order: 1
---

# Atualizar redes sociais
## PATCH /public_api/v1/user

Permitir atualizar as redes sociais do usuário.

**Estrutura da URL:** https://weleto.com.br/public_api/v1/user

### Exemplo
```
curl \
  -d '{"social_networks": { "facebook": "exemplo","whatsapp": "987654321" } }'\
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer access_token" \
  -v -XPATCH https://weleto.com.br/public_api/v1/user
```

### Parâmetros
```
{
  social_networks:
    {
      "facebook": "exemplo",
      "whatsapp": "987654321",
      "telegram": "123456789",
      "instagram": "exemplo"
    }
}
```

| Campo | Descrição | Obrigatório? |
|:-------------|:------------------|:-------------|
| social_networks | Redes sociais do usuário em formato chave valor | SIM - Valores permitidos: `facebook`, `whatsapp`, `telegram` e `instagram` |

### Retorno
```
{
  "id": 1234,
  "email": "email",
  "social_networks": {
    "facebook": "exemplo",
    "whatsapp": "987654321",
    "telegram": "123456789",
    "instagram": "exemplo"
  }
}
```

Segue os mesmos campos mapeados no endpoint de [Obter dados atuais](/user/show)
