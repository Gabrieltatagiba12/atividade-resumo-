# 📌 Resumo --- Arquitetura de Software (Aula 09)

## 1. O que é Arquitetura de Software

-   Define **estrutura do sistema**
-   Organiza **componentes e comunicação**
-   Estabelece **regras de desenvolvimento e evolução**
-   Objetivo: sistemas **manuteníveis, escaláveis e organizados**

------------------------------------------------------------------------

# 🧱 Camadas básicas de um sistema

Ordem correta:

    Apresentação → Negócios → Persistência → Banco de Dados

Se a interface acessar diretamente o banco → **architecture sinkhole
(anti‑padrão)**

Problemas: - Alto acoplamento - Dificuldade de testes - Baixa
escalabilidade - Código desorganizado

------------------------------------------------------------------------

# 🕰️ Evolução das Arquiteturas

## Mainframe

-   Tudo em **um computador central**
-   Terminais burros
-   Baixa flexibilidade

## Cliente‑Servidor

-   Cliente faz requisição
-   Servidor responde
-   Começa separação de responsabilidades

## Arquitetura 2‑Tier

    Cliente (UI + Regras) ↔ Banco de Dados

Problema: atualização precisa instalar em cada computador.

## Arquitetura 3‑Tier

    Cliente (UI)
    ↓
    Servidor de Aplicação
    ↓
    Banco de Dados

Vantagens: - Regras centralizadas - Atualização mais fácil

## Arquitetura 4‑Tier (Web)

    Browser
    ↓
    Servidor Web
    ↓
    Servidor de Aplicação
    ↓
    Banco de Dados

Benefícios: - Sem instalação - Atualizações centralizadas - Melhor
desacoplamento

------------------------------------------------------------------------

# 🧠 Estilo Arquitetural vs Padrão Arquitetural

## Estilo Arquitetural

Define **estrutura geral do sistema**.

Exemplos: - Monolítico - Cliente‑Servidor - Camadas - Microsserviços -
Event‑Driven - Peer‑to‑Peer - Pipe‑and‑Filter

## Padrão Arquitetural

Define **como organizar o código**.

Exemplos: - MVC - MVVM - Hexagonal - Clean Architecture - Onion
Architecture

Resumo:

    Estilo → forma geral do sistema
    Padrão → organização interna do código

------------------------------------------------------------------------

# 🧩 MVC (Model View Controller)

## Model

Dados e acesso ao banco

## View

Interface com usuário

## Controller

Recebe requisições e coordena lógica

Fluxo:

    Usuário → Controller → Model → Banco
    Controller → View → Usuário

Problemas em sistemas grandes:

1.  Reuso difícil
2.  Transações espalhadas
3.  Testes difíceis
4.  Escalabilidade limitada
5.  Conflitos entre equipes

------------------------------------------------------------------------

# 🧱 Arquitetura em 4 Camadas Lógicas

Camadas:

1.  **Apresentação** -- interface
2.  **Aplicação** -- fluxo da aplicação
3.  **Domínio** -- regras de negócio
4.  **Infraestrutura** -- banco, APIs, email

Fluxo:

    Usuário → Interface → Aplicação → Domínio → Infraestrutura

------------------------------------------------------------------------

# 📐 Princípios Importantes

## Alta Coesão

Cada módulo tem **uma responsabilidade clara**.

## Baixo Acoplamento

Módulos **dependem pouco uns dos outros**.

Benefícios: - manutenção fácil - melhor teste - evolução do sistema

------------------------------------------------------------------------

# 🧩 SOLID

Principal citado:

### SRP --- Single Responsibility Principle

Cada classe deve ter **uma única razão para mudar**.

------------------------------------------------------------------------

# 🔌 Injeção de Dependência

Antes:

    Domínio → Banco de Dados

Depois:

    Domínio → Interface ← Infraestrutura

Benefícios: - facilidade de testes - trocar banco sem alterar domínio -
flexibilidade

------------------------------------------------------------------------

# 🚀 Deploy de Aplicação

Arquitetura simples:

    React (Browser)
    ↓
    API REST
    ↓
    Banco

Produção:

    Usuário
    ↓
    Browser
    ↓
    Nginx
    ↓
    Backend API
    ↓
    Banco

------------------------------------------------------------------------

# 🐳 Docker

Usado para: - empacotar aplicação - padronizar ambiente - facilitar
deploy

# ☁️ VPS

Servidor remoto com: - IP público - acesso 24h - ambiente de produção

# 🌐 Nginx

Responsável por: - servidor web - proxy reverso - roteamento

------------------------------------------------------------------------

# 🧠 Qualidade de Código

Objetivos:

## Manutenibilidade

Facilidade de modificar o sistema.

## Escalabilidade

Sistema suporta crescimento.

## Design de Software

Organização de: - classes - interfaces - responsabilidades

------------------------------------------------------------------------

# 🧩 Padrões de Projeto

## Criacionais

-   Factory
-   Builder
-   Singleton

## Estruturais

-   Adapter
-   Facade
-   Decorator

## Comportamentais

-   Strategy
-   Observer
-   Command

------------------------------------------------------------------------

# 🧪 TDD (Test Driven Development)

Processo:

1.  Escrever teste
2.  Implementar código
3.  Refatorar

Benefícios: - menos bugs - melhor design - código mais limpo

------------------------------------------------------------------------

# 🏗️ Arquitetura de Produção

Componentes comuns:

-   Frontend
-   Load Balancer
-   API Gateway
-   Backend
-   Cache
-   Fila de mensagens
-   Workers
-   Banco de dados
-   Object Storage
-   Serviços externos

------------------------------------------------------------------------

# 🔷 Arquitetura Hexagonal

Estrutura:

    Adaptadores → Portas → Núcleo (Domínio)

Vantagens: - domínio isolado - fácil trocar tecnologia - melhor
testabilidade

------------------------------------------------------------------------

# 🧅 Clean Architecture

Camadas:

    Entidades
    ↓
    Casos de Uso
    ↓
    Adaptadores
    ↓
    Frameworks / Infraestrutura

Regra: **Dependências sempre apontam para dentro.**

------------------------------------------------------------------------

# ⚙️ Microserviços

Sistema dividido em serviços independentes.

Exemplos: - autenticação - pagamentos - notificações

Vantagens: - escalabilidade - deploy independente - resiliência

Desafios: - infraestrutura complexa - comunicação entre serviços

------------------------------------------------------------------------

# 📡 Comunicação entre Serviços

## REST API

-   HTTP
-   síncrono

## GraphQL

-   cliente escolhe dados
-   menos requisições

## Mensageria (RabbitMQ / Kafka)

-   comunicação assíncrona
-   maior escalabilidade

------------------------------------------------------------------------

# 📢 Publish‑Subscribe

Fluxo:

    Serviço A → publica evento
    Serviços B C D → reagem ao evento

Benefícios: - desacoplamento - modularidade - escalabilidade

------------------------------------------------------------------------

# 🏢 SOA (Service Oriented Architecture)

Serviços corporativos reutilizáveis.

Exemplos: - pagamento - autenticação - recomendação

Muito usado em **empresas com sistemas legados**.

------------------------------------------------------------------------

# ⚡ CQRS

Separação entre:

## Command

operações de escrita

## Query

operações de leitura

Benefícios: - performance - escalabilidade - clareza nas
responsabilidades

------------------------------------------------------------------------

# 🎯 Ideia Final

Uma boa arquitetura depende de:

-   código organizado
-   princípios de design
-   infraestrutura adequada
-   comunicação eficiente entre serviços

**Arquitetura é uma jornada, não uma solução única.**
