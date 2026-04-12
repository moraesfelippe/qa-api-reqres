# 🧪 ReqRes API — Testes Manuais com Postman

> Projeto de testes manuais de API REST desenvolvido como parte do portfólio de QA.  
> Ferramenta utilizada: **Postman** | API testada: **ReqRes.in**

---

## 📋 Sobre o Projeto

Este projeto documenta a execução de testes manuais sobre a API pública [ReqRes.in](https://reqres.in), cobrindo cenários positivos e negativos dos módulos de **Usuários** e **Autenticação**.

O objetivo é demonstrar habilidades em:

- Análise e entendimento de contratos de API REST
- Criação e execução de casos de teste manuais
- Validação de status codes, headers e body de resposta
- Documentação técnica de testes

---

## 🗂️ Estrutura do Repositório

```
📁 qa-api-reqres/
├── 📁 docs/
│   └── test-cases.md        # Casos de teste documentados
├── 📁 postman/
│   └── ReqRes_API.postman_collection.json  # Collection exportada
└── README.md
```

---

## 🔍 Escopo dos Testes

| Módulo        | Total de CTs | ✅ Passou | ❌ Falhou |
|---------------|:------------:|:---------:|:---------:|
| Usuários      | 4            | 4         | 0         |
| Autenticação  | 3            | 3         | 0         |
| **Total**     | **7**        | **7**     | **0**     |

---

## 🚀 Como Usar a Collection

1. Instale o [Postman](https://www.postman.com/downloads/)
2. Importe o arquivo `postman/ReqRes_API.postman_collection.json`
3. Crie uma conta gratuita em [app.reqres.in](https://app.reqres.in) para obter sua API Key
4. Configure os headers `x-api-key` e `X-Reqres-Env: prod` na Collection
5. Execute as requisições

---

## 🛠️ Tecnologias

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![REST API](https://img.shields.io/badge/REST-API-blue?style=for-the-badge)

---

## 👤 Autor

**Felipe Martins**  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/moraesfelippe)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/moraesfelippe)
