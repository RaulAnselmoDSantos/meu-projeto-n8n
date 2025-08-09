# Projeto n8n + Evolution API + Postgres + Redis

## 📌 Visão Geral
Este projeto é um ambiente local de estudo e desenvolvimento utilizando **Docker Compose** para orquestrar múltiplos serviços que se integram entre si.  
O objetivo é hospedar o **n8n** como ferramenta principal de automações, utilizando **PostgreSQL** como banco de dados, **Redis** para cache, e a **Evolution API** para integração com WhatsApp e outros canais.

---

## 🛠️ Tecnologias Utilizadas
- [Docker](https://www.docker.com/) — Containerização
- [Docker Compose](https://docs.docker.com/compose/) — Orquestração de múltiplos containers
- [PostgreSQL](https://www.postgresql.org/) — Banco de dados para o n8n e Evolution API
- [Redis](https://redis.io/) — Armazenamento de cache
- [n8n](https://n8n.io/) — Plataforma de automação de fluxos
- [Evolution API](https://doc.evolution-api.com) — API de integração para automações via WhatsApp

---

## 📂 Estrutura dos Serviços
- **n8n**
  - Conectado ao Postgres
  - Persistência configurada em volume `n8n_data`
  - Autenticação básica ativa (`N8N_BASIC_AUTH_USER` e `N8N_BASIC_AUTH_PASSWORD`)
  
- **PostgreSQL**
  - Banco `n8n_db` para o n8n
  - Banco `evo_db` para Evolution API
  - Persistência configurada no volume `postgres_data`

- **Redis**
  - Usado como cache para n8n e Evolution API
  
- **Evolution API**
  - Configurada com Postgres
  - Porta exposta `8080`
  - Autenticação por `AUTHENTICATION_API_KEY`
  - Migrations automáticas aplicadas no start

---

## 🚀 Como Rodar o Projeto

### 1️⃣ Pré-requisitos
- Docker instalado
- Docker Compose instalado
- VSCode ou editor de preferência
- Arquivo `.env` configurado com as variáveis necessárias

Exemplo de `.env`:
```env
POSTGRES_USER=n8nPG
POSTGRES_PASSWORD=minhasenha
POSTGRES_DB=n8n_db
N8N_BASIC_AUTH_USER=meuusuario
N8N_BASIC_AUTH_PASSWORD=minhasenha
AUTHENTICATION_API_KEY=chave_da_evolution
