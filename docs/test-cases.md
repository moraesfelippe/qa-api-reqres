# 📄 Casos de Teste — ReqRes API

**Projeto:** QA Portfolio — Testes Manuais de API  
**Analista:** Felipe Martins  
**Ferramenta:** Postman  
**API:** ReqRes.in  
**Data:** Abril/2026  

---

## 🔐 Configuração de Autenticação

Todos os endpoints exigem os seguintes headers:

| Header | Valor |
|--------|-------|
| `x-api-key` | `sua_api_key` |
| `X-Reqres-Env` | `prod` |

> 💡 Obtenha sua API Key gratuita em [app.reqres.in](https://app.reqres.in)

---

## 👥 Módulo: Usuários

---

### CT001 — Listar usuários com sucesso

| Campo | Detalhe |
|-------|---------|
| **Método** | `GET` |
| **Endpoint** | `/api/users?page=1` |
| **Tipo** | Positivo |
| **Status Esperado** | `200 OK` |
| **Status Recebido** | `200 OK` |
| **Resultado** | ✅ PASSOU |

**Critérios de Aceite:**
- Status code `200`
- Body contém campo `data` com lista de usuários
- Campo `page` retorna `1`
- Cada usuário contém `id`, `email`, `first_name`, `last_name`, `avatar`

**Resposta Obtida:**
```json
{
  "page": 1,
  "per_page": 6,
  "total": 12,
  "total_pages": 2,
  "data": [
    {
      "id": 1,
      "email": "george.bluth@reqres.in",
      "first_name": "George",
      "last_name": "Bluth",
      "avatar": "https://reqres.in/img/faces/1-image.jpg"
    }
  ]
}
```

---

### CT002 — Buscar usuário específico com sucesso

| Campo | Detalhe |
|-------|---------|
| **Método** | `GET` |
| **Endpoint** | `/api/users/2` |
| **Tipo** | Positivo |
| **Status Esperado** | `200 OK` |
| **Status Recebido** | `200 OK` |
| **Resultado** | ✅ PASSOU |

**Critérios de Aceite:**
- Status code `200`
- Campo `id` retorna `2`
- Body contém `email`, `first_name`, `last_name`, `avatar`

---

### CT003 — Buscar usuário inexistente

| Campo | Detalhe |
|-------|---------|
| **Método** | `GET` |
| **Endpoint** | `/api/users/999` |
| **Tipo** | Negativo |
| **Status Esperado** | `404 Not Found` |
| **Status Recebido** | `404 Not Found` |
| **Resultado** | ✅ PASSOU |

**Critérios de Aceite:**
- Status code `404`
- Body retorna `{}`

> ⚠️ Se retornar `200`, isso caracteriza um **bug** — a API estaria retornando sucesso para um recurso inexistente.

---

### CT004 — Criar usuário com sucesso

| Campo | Detalhe |
|-------|---------|
| **Método** | `POST` |
| **Endpoint** | `/api/users` |
| **Tipo** | Positivo |
| **Status Esperado** | `201 Created` |
| **Status Recebido** | `201 Created` |
| **Resultado** | ✅ PASSOU |

**Headers adicionais:**
```
Content-Type: application/json
```

**Body Enviado:**
```json
{
  "name": "Felipe",
  "job": "QA Analyst"
}
```

**Critérios de Aceite:**
- Status code `201`
- Body retorna `id` gerado automaticamente
- Campos `name` e `job` refletem os dados enviados
- Campo `createdAt` presente na resposta

---

## 🔑 Módulo: Autenticação

---

### CT005 — Login com sucesso

| Campo | Detalhe |
|-------|---------|
| **Método** | `POST` |
| **Endpoint** | `/api/login` |
| **Tipo** | Positivo |
| **Status Esperado** | `200 OK` |
| **Status Recebido** | `200 OK` |
| **Resultado** | ✅ PASSOU |

**Headers adicionais:**
```
Content-Type: application/json
```

**Body Enviado:**
```json
{
  "email": "eve.holt@reqres.in",
  "password": "cityslicka"
}
```

**Critérios de Aceite:**
- Status code `200`
- Body contém campo `token`
- Token não está vazio

---

### CT006 — Login sem senha

| Campo | Detalhe |
|-------|---------|
| **Método** | `POST` |
| **Endpoint** | `/api/login` |
| **Tipo** | Negativo |
| **Status Esperado** | `400 Bad Request` |
| **Status Recebido** | `400 Bad Request` |
| **Resultado** | ✅ PASSOU |

**Body Enviado:**
```json
{
  "email": "eve.holt@reqres.in"
}
```

**Critérios de Aceite:**
- Status code `400`
- Body retorna `"error": "Missing password"`

> ⚠️ Se retornar `200`, isso caracteriza um **bug crítico de segurança** — login sem senha não pode ser permitido.

---

### CT007 — Login com email inválido

| Campo | Detalhe |
|-------|---------|
| **Método** | `POST` |
| **Endpoint** | `/api/login` |
| **Tipo** | Negativo |
| **Status Esperado** | `400 Bad Request` |
| **Status Recebido** | `400 Bad Request` |
| **Resultado** | ✅ PASSOU |

**Body Enviado:**
```json
{
  "email": "naoexiste@teste.com",
  "password": "123456"
}
```

**Critérios de Aceite:**
- Status code `400`
- Body retorna `"error": "user not found"`

---

## 📊 Resumo da Execução

| Módulo | Total | ✅ Passou | ❌ Falhou | Taxa |
|--------|:-----:|:---------:|:---------:|:----:|
| Usuários | 4 | 4 | 0 | 100% |
| Autenticação | 3 | 3 | 0 | 100% |
| **Total** | **7** | **7** | **0** | **100%** |
