# 📄 Product Requirements Document (PRD) - Controle de Estoque Simples

**Projeto:** Controle de Estoque Simples — Sistema Web para Gestão de Produtos e Movimentações  
**Versão:** 1.0.0  
**Status:** 🟢 Definido (MVP)  
**Autores:** João Victor Santos Bacelar  

---

## 🎯 1. Visão Geral e Objetivo

Pequenos negócios frequentemente realizam o controle de estoque de forma manual, utilizando planilhas, anotações em papel ou até memória. Isso gera inconsistências, perdas de produtos, dificuldade de rastreamento e falta de controle sobre entradas e saídas.

O **Controle de Estoque Simples** resolve esse problema centralizando todas as informações em um sistema web acessível, permitindo o gerenciamento eficiente de produtos e suas movimentações.

O sistema é composto por duas frentes:
- **Interface Administrativa:** área autenticada para gerenciamento de produtos e movimentações.
- **API Backend:** responsável pela lógica de negócio, persistência de dados e segurança.

---

## 📖 2. Glossário Ubíquo

| Termo | Definição |
|---|---|
| **Produto** | Item armazenado no estoque com nome, quantidade e preço. |
| **Movimentação** | Registro de entrada ou saída de produtos. |
| **Entrada** | Adição de produtos ao estoque. |
| **Saída** | Remoção de produtos do estoque. |
| **Estoque** | Quantidade atual disponível de um produto. |
| **Administrador** | Usuário com acesso total ao sistema. |
| **JWT** | Token de autenticação utilizado para proteger rotas. |

---

## 👤 3. Personas e Permissões

### 🧑‍💼 Administrador
- Responsável pelo controle do estoque.
- Realiza login no sistema.
- Pode cadastrar, editar e excluir produtos.
- Pode registrar entradas e saídas.
- Possui acesso total ao sistema.

---

## 📝 4. Escopo Funcional, Histórias de Usuário e Critérios de Aceitação (MoSCoW)

---

### 🔴 US01 - Documentação Técnica do Projeto (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero documentar o PRD e o SDD dentro do repositório, para manter organização e rastreabilidade do projeto.

**✅ Critérios de Aceitação:**
- [ ] Existe `docs/prd.md` com histórias e regras.
- [ ] Existe `docs/sdd.md` com modelo de dados e API.
- [ ] Documentação criada com apoio de IA.

> **Requisitos técnicos cobertos:** `ID1`

---

### 🔴 US02 - Estrutura de Monorepo (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero organizar o projeto em monorepo com frontend e backend, para facilitar o gerenciamento.

**✅ Critérios de Aceitação:**
- [ ] Diretórios `backend/` e `frontend/`.
- [ ] Cada parte com seu próprio `package.json`.

> **Requisitos técnicos cobertos:** `ID2`

---

### 🔴 US03 - Backlog no GitHub Projects (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero transformar as histórias em Issues para acompanhar o progresso.

**✅ Critérios de Aceitação:**
- [ ] Issues criadas para cada US.
- [ ] Uso de Kanban no GitHub.

> **Requisitos técnicos cobertos:** `ID3`

---

### 🔴 US04 - GitFlow (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero usar GitFlow para manter organização do código.

**✅ Critérios de Aceitação:**
- [ ] Branches `main` e `develop`.
- [ ] Uso de Pull Requests.

> **Requisitos técnicos cobertos:** `ID4`

---

### 🔴 US05 - Autenticação com JWT (Must Have)

**Ator:** Administrador  
**História:** Como administrador, quero fazer login para acessar o sistema com segurança.

**✅ Critérios de Aceitação:**
- [ ] POST `/auth/login`
- [ ] Retorna JWT
- [ ] Rotas protegidas

> **Requisitos técnicos cobertos:** `ID5`, `ID6`, `ID8`, `ID15`

---

### 🔴 US06 - Gestão de Produtos (Must Have)

**Ator:** Administrador  
**História:** Como administrador, quero gerenciar produtos para controlar o estoque.

**✅ Critérios de Aceitação:**
- [ ] POST `/products`
- [ ] GET `/products`
- [ ] PUT `/products/:id`
- [ ] DELETE `/products/:id`
- [ ] Validação com DTO

> **Requisitos técnicos cobertos:** `ID5`, `ID6`, `ID7`, `ID9`

---

### 🔴 US07 - Controle de Movimentações (Must Have)

**Ator:** Administrador  
**História:** Como administrador, quero registrar entradas e saídas para manter o estoque atualizado.

**✅ Critérios de Aceitação:**
- [ ] POST `/movements`
- [ ] GET `/movements`
- [ ] Atualiza quantidade automaticamente
- [ ] Não permite estoque negativo

> **Requisitos técnicos cobertos:** `ID5`, `ID6`, `ID7`, `ID9`

---

### 🔴 US08 - Validação e Regras de Negócio (Must Have)

**Ator:** Sistema  
**História:** Como sistema, quero validar dados para evitar inconsistências.

**✅ Critérios de Aceitação:**
- [ ] Quantidade não pode ser negativa
- [ ] Campos obrigatórios validados
- [ ] Erros padronizados

> **Requisitos técnicos cobertos:** `ID6`, `ID9`

---

### 🔴 US09 - Testes Automatizados (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero testes para garantir qualidade.

**✅ Critérios de Aceitação:**
- [ ] Testes com Jest
- [ ] Cobertura de sucesso e erro

> **Requisitos técnicos cobertos:** `ID10`, `ID11`

---

### 🔴 US10 - Documentação Swagger (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero documentar a API.

**✅ Critérios de Aceitação:**
- [ ] Swagger disponível
- [ ] Rotas documentadas

> **Requisitos técnicos cobertos:** `ID12`

---

### 🟡 US11 - Interface Web (Should Have)

**Ator:** Administrador  
**História:** Como administrador, quero interface visual para usar o sistema.

**✅ Critérios de Aceitação:**
- [ ] Tela de produtos
- [ ] Tela de movimentações
- [ ] Consome API

> **Requisitos técnicos cobertos:** `ID13`, `ID14`

---

### 🔴 US12 - Variáveis de Ambiente (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero proteger dados sensíveis.

**✅ Critérios de Aceitação:**
- [ ] `.env` ignorado
- [ ] Uso de ConfigModule

> **Requisitos técnicos cobertos:** `ID15`

---

### 🔴 US13 - CI com GitHub Actions (Must Have)

**Ator:** Desenvolvedor  
**História:** Como desenvolvedor, quero automação de testes.

**✅ Critérios de Aceitação:**
- [ ] Pipeline CI configurado
- [ ] Testes rodando automaticamente

> **Requisitos técnicos cobertos:** `ID16`

---

### 🔴 US14 - Deploy (Must Have)

**Ator:** Administrador  
**História:** Como administrador, quero acessar o sistema online.

**✅ Critérios de Aceitação:**
- [ ] Backend publicado
- [ ] Banco em produção

> **Requisitos técnicos cobertos:** `ID17`

---

## 🗺️ 5. Matriz de Rastreabilidade

| ID | User Stories |
|---|---|
| ID1 | US01 |
| ID2 | US02 |
| ID3 | US03 |
| ID4 | US04 |
| ID5 | US05, US06, US07 |
| ID6 | US05, US06, US07 |
| ID7 | US06, US07 |
| ID8 | US05 |
| ID9 | US06, US07, US08 |
| ID10 | US09 |
| ID11 | US09 |
| ID12 | US10 |
| ID13 | US11 |
| ID14 | US11 |
| ID15 | US05, US12 |
| ID16 | US13 |
| ID17 | US14 |

---

## ⚙️ 6. Requisitos Não Funcionais

- **Desempenho:** respostas da API em até 500ms  
- **Segurança:** autenticação via JWT  
- **Usabilidade:** interface simples e intuitiva  
- **Manutenibilidade:** código modular com NestJS  
- **Disponibilidade:** sistema acessível online  