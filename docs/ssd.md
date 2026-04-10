# 📐 Software Design Document (SDD) - Controle de Estoque Simples

**Projeto:** Controle de Estoque Simples  
**Versão:** 1.0.0  
**Status:** 🟢 Pronto para Implementação  
**Stack Principal:** NestJS, React, Prisma ORM, PostgreSQL  

---

## 🏗️ 1. Arquitetura do Sistema (Estrutura Monorepo)

O projeto utiliza uma arquitetura de Monorepo. O Agente de IA deve respeitar a seguinte estrutura de pastas:

* **`apps/api`**: Servidor Backend (NestJS)  
* **`apps/web`**: Aplicação Client (React)  

---

## 🤖 2. Orquestração e Ecossistema de Contexto (MCP)

> **Instrução para a IA:** Este projeto utiliza o Model Context Protocol (MCP) para garantir a paridade entre especificação e execução.

* **GitHub Projects MCP:** Sincronizar backlog (Issues) com o desenvolvimento.  
* **Neon.tech MCP:** Gerenciar banco PostgreSQL e validar schema Prisma.  

---

## 📦 3. Stack Tecnológica e Bibliotecas

### Core & Infraestrutura

* **Ambiente:** Node.js v20.x LTS  
* **Banco de Dados:** PostgreSQL (Neon.tech)  
* **Backend:** NestJS v10.x  
* **Frontend:** React (Vite)  
* **ORM:** Prisma v5.x  
* **Testes:** Jest + Supertest  

### Bibliotecas Permitidas

* **Auth:** JWT (`@nestjs/jwt`, `@nestjs/passport`)  
* **Validação:** class-validator + class-transformer  
* **Documentação:** Swagger (`@nestjs/swagger`)  

---

## 🗄️ 4. Arquitetura de Dados

### 📖 4.1. Glossário Técnico

| Termo (PT-BR) | Entidade Técnica | Atributos |
|--------------|----------------|----------|
| Usuário | `User` | id, email, password, role |
| Produto | `Product` | id, name, quantity, price |
| Movimentação | `StockMovement` | id, type, quantity, product_id |

---

### 🗄️ 4.2. Modelagem de Dados

```mermaid
erDiagram
    USER {
        int id PK
        string email
        string password
        string role
        datetime created_at
    }

    PRODUCT {
        int id PK
        string name
        int quantity
        float price
        datetime created_at
    }

    STOCK_MOVEMENT {
        int id PK
        string type "IN | OUT"
        int quantity
        int product_id FK
        datetime created_at
    }

    PRODUCT ||--o{ STOCK_MOVEMENT : "movements"