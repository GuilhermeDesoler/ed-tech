# Mês 13: Projeto Full-stack

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 25-26 (condensado em intensivo)
**Pré-requisito:** Conclusão completa dos Mês 7-12
**Status:** Projeto Capstone ⭐⭐⭐

## Visão Geral

Este é o módulo final de integração do semestre, onde os alunos aplicam todos os conhecimentos acumulados para criar uma aplicação full-stack profissional, production-ready. O projeto será desenvolvido em equipes (ou individual) e servirá como portfolio para futuras oportunidades.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Arquitetar aplicação full-stack completa
- Integrar React frontend com Node.js backend
- Gerenciar banco de dados relacional complexo
- Implementar autenticação segura end-to-end
- Otimizar performance frontend e backend
- Implementar testes em toda aplicação
- Fazer deploy production-ready
- Trabalhar em equipe com Git/GitHub
- Documentar projeto profissionalmente
- Apresentar e defender arquitetura

## Escopo do Projeto

### Requisitos Técnicos Obrigatórios

#### Frontend (React)
- ✓ TypeScript em modo strict
- ✓ Mínimo 5 páginas/rotas
- ✓ Estado gerenciado com Context API + useReducer
- ✓ Custom hooks reutilizáveis
- ✓ Formulários com validação completa
- ✓ Testes unitários (50+ cases)
- ✓ Testes E2E (10+ fluxos)
- ✓ Acessibilidade (WCAG AA)
- ✓ Design responsivo (mobile-first)
- ✓ Performance > 90 Lighthouse

#### Backend (Node.js)
- ✓ API REST com Express
- ✓ CRUD completo (mínimo 5 recursos)
- ✓ Autenticação JWT
- ✓ Autorização por roles
- ✓ Validação com Joi/Zod
- ✓ Testes (80%+ cobertura)
- ✓ Documentação Swagger
- ✓ Error handling robusto
- ✓ Rate limiting
- ✓ CORS configurado

#### Banco de Dados
- ✓ PostgreSQL com design normalizado
- ✓ Mínimo 5 tabelas com relacionamentos
- ✓ Índices otimizados
- ✓ Migrations automáticas
- ✓ Seeds para dados de teste

#### DevOps
- ✓ Docker e Docker Compose
- ✓ GitHub Actions (CI/CD)
- ✓ Deploy automatizado
- ✓ Variáveis de ambiente
- ✓ Monitoramento básico

## Temas de Projeto Sugeridos

### Opção 1: E-commerce
**Complexidade:** Alta
**Funcionalidades:**
- Catálogo de produtos com filtros
- Carrinho de compras com persistência
- Checkout com validação
- Pedidos e histórico
- Dashboard administrativo
- Painel de vendedor

**Entidades Principais:** User, Product, Category, Cart, Order, Payment

### Opção 2: Rede Social / Comunidade
**Complexidade:** Média-Alta
**Funcionalidades:**
- Perfil de usuário
- Posts/tweets com comentários
- Likes e compartilhamentos
- Followers/following
- Feed personalizado
- Notificações

**Entidades Principais:** User, Post, Comment, Like, Follow, Notification

### Opção 3: Plataforma de Cursos
**Complexidade:** Média-Alta
**Funcionalidades:**
- Catálogo de cursos
- Aulas e progresso
- Quizzes e avaliações
- Certificados
- Sistema de reviews
- Dashboard do instrutor

**Entidades Principais:** User, Course, Lesson, Quiz, Enrollment, Certificate

### Opção 4: Sistema de Gerenciamento (CRM/ERP Lite)
**Complexidade:** Média
**Funcionalidades:**
- Gestão de clientes/contatos
- Pipeline de vendas
- Tarefas e agendamentos
- Relatórios e análises
- Integração com email
- Exportação de dados

**Entidades Principais:** Contact, Company, Deal, Task, Activity, Report

### Opção 5: Marketplace
**Complexidade:** Alta
**Funcionalidades:**
- Vendedores e compradores
- Listagem de produtos
- Sistema de mensagens
- Reviews e ratings
- Pagamentos
- Disputa de transações

**Entidades Principais:** User, Seller, Product, Order, Message, Review

## Cronograma (4 Semanas)

### SEMANA 1: Planejamento e Setup

#### Dia 1-2: Definiçã do Projeto (16h)
- Escolher tema entre as opções
- Listar requisitos funcionais
- Definir escopo (MVP)
- Criar wireframes/mockups
- Documentar user stories

**Entregável:** Document de requisitos (2-3 páginas)

#### Dia 3-4: Arquitetura e Setup (16h)
- Design de banco de dados (ERD)
- Design de APIs (endpoints)
- Estrutura de diretórios
- Setup de repositório Git
- Setup de ambientes (dev, prod)
- Inicializar projetos (CRA/Vite e Express)

**Entregável:** Arquitetura documentada + repositório estruturado

#### Dia 5: Revisão e Planejamento de Sprint (8h)
- Code review da arquitetura
- Feedback de mentores
- Ajustes conforme feedback
- Divisão de tasks
- Planejamento de sprints

**Entregável:** Sprint board atualizado

### SEMANA 2: Backend Development

#### Dia 1-2: Modelos e Banco de Dados (16h)
- Criar modelos com Sequelize
- Criar migrations
- Criar seeds para dados de teste
- Setup conexão PostgreSQL
- Validar design com dados reais

**Entregável:** Banco de dados funcional com dados

#### Dia 3-4: API Core (16h)
- Implementar CRUD para recursos principais (3-4)
- Middleware de validação
- Autenticação JWT (login/register)
- Error handling
- Começar testes

**Entregável:** API com testes básicos

#### Dia 5: Testes e Documentação Backend (8h)
- Testes unitários
- Testes de integração
- Documentação Swagger
- Code review interno

**Entregável:** 80%+ cobertura de testes + Swagger docs

### SEMANA 3: Frontend Development

#### Dia 1-2: Setup e Autenticação (16h)
- Setup React com TypeScript
- Routing com React Router
- Context API para autenticação
- Login/Register pages
- Protected routes
- Persistência de token

**Entregável:** Fluxo de autenticação completo

#### Dia 3-4: Páginas e Componentes (16h)
- Listar página (com filtros)
- Detalhe página
- CRUD pages (criar, editar, deletar)
- Custom hooks para API calls
- Validação de formulários

**Entregável:** Mínimo 5 páginas completas

#### Dia 5: Styling e Responsividade (8h)
- Tailwind CSS
- Layout responsivo
- Dark mode (bonus)
- Acessibilidade básica
- Performance optimization

**Entregável:** Interface polida e responsiva

### SEMANA 4: Integração e Deploy

#### Dia 1-2: Testes e Integração (16h)
- Testes unitários React (50+ cases)
- Testes E2E com Cypress (10+ fluxos)
- Testes de integração frontend-backend
- Debugging de issues
- Refatoração se necessário

**Entregável:** Testes passando > 90%

#### Dia 3: Docker e CI/CD (16h)
- Dockerfile para backend
- Dockerfile para frontend
- docker-compose.yml
- GitHub Actions workflow
- Testes automáticos
- Deploy preview

**Entregável:** CI/CD funcional

#### Dia 4-5: Deploy e Documentação (16h)
- Deploy backend (Railway/Render)
- Deploy frontend (Vercel)
- Documentação (README, API docs, setup)
- Demo video
- Preparação para apresentação

**Entregável:** Aplicação live em produção

## Estrutura de Repositório Recomendada

```
projeto-fullstack/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── utils/
│   │   ├── migrations/
│   │   ├── seeders/
│   │   └── app.js
│   ├── tests/
│   ├── .env.example
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── context/
│   │   ├── utils/
│   │   ├── styles/
│   │   ├── tests/
│   │   └── App.tsx
│   ├── public/
│   ├── .env.example
│   ├── Dockerfile
│   └── package.json
│
├── .github/
│   └── workflows/
│       ├── backend-tests.yml
│       ├── frontend-tests.yml
│       └── deploy.yml
│
├── README.md
├── ARCHITECTURE.md
└── docker-compose.yml
```

## Critérios de Avaliação

### Funcionalidade (30%)
- ✓ Todas as funcionalidades planejadas implementadas
- ✓ Sem bugs críticos
- ✓ Performance adequada
- ✓ Responsividade completa

### Código (25%)
- ✓ TypeScript strict mode
- ✓ Testes abrangentes (80%+)
- ✓ Sem console.errors/warnings
- ✓ Padrões de design adequados
- ✓ DRY e SOLID principles

### DevOps (15%)
- ✓ Docker funcional
- ✓ CI/CD automático
- ✓ Deploy bem-sucedido
- ✓ Variáveis de ambiente
- ✓ Documentação de setup

### Documentação (15%)
- ✓ README completo
- ✓ API documentada (Swagger)
- ✓ Arquitetura explicada
- ✓ Setup instructions claras
- ✓ Troubleshooting guide

### Apresentação (15%)
- ✓ Demo funcional
- ✓ Explicação clara da arquitetura
- ✓ Insights técnicos compartilhados
- ✓ Responder perguntas
- ✓ Evidência de aprendizado

## Entregas Esperadas

### Entrega 1: Arquitetura (Fim da Semana 1)
- Documento de requisitos
- ERD (Entity-Relationship Diagram)
- API endpoints documentados
- Repositório Git estruturado
- Trello/GitHub Projects com tasks

### Entrega 2: MVP Backend (Fim da Semana 2)
- API funcionando
- Banco de dados criado
- Testes implementados
- Documentação Swagger

### Entrega 3: MVP Frontend (Fim da Semana 3)
- Frontend conectado ao backend
- Autenticação funcional
- Páginas principais implementadas
- Styling básico

### Entrega 4: Produto Final (Fim da Semana 4)
- Aplicação completa e testada
- Deploy em produção
- Documentação completa
- Demo video
- Apresentação

## Exemplo de Funcionalidades por Semana

### E-commerce Example

**Semana 1 (Planejamento)**
- Requisitos: Catálogo, carrinho, checkout, admin panel
- Design: 10+ páginas prototipadas
- API: 20+ endpoints planejados
- DB: 8 tabelas com relacionamentos

**Semana 2 (Backend)**
```
Controllers: ProductController, CartController, OrderController, UserController
Models: User, Product, Category, Cart, Order, Payment
Routes: /api/v1/products, /api/v1/cart, /api/v1/orders, /api/v1/auth
Tests: 100+ testes de API
```

**Semana 3 (Frontend)**
```
Pages: Home, Products, ProductDetail, Cart, Checkout, Orders, Admin
Components: ProductCard, Filter, Cart, CheckoutForm, OrderList
Hooks: useFetch, useCart, useAuth, useOrder
State: AuthContext, CartContext, FilterContext
```

**Semana 4 (Deploy)**
- Docker: Backend + PostgreSQL + Frontend
- CI/CD: GitHub Actions com testes e deploy
- Deployment: Railway (backend), Vercel (frontend)
- Monitoramento: Sentry para errors

## Recursos e Ferramentas

### Desenvolvimento
- VS Code com extensões
- Git e GitHub
- Postman/Insomnia
- DBeaver (PostgreSQL)
- Swagger UI

### Testing
- Jest
- Supertest
- React Testing Library
- Cypress

### DevOps
- Docker
- GitHub Actions
- Railway/Render
- Vercel

### Documentação
- Markdown
- Swagger/OpenAPI
- Figma (design)
- Miro (arquitetura)

## Dicas para Sucesso

### Planejamento
- Defina escopo claro (MVP)
- Não tente fazer tudo
- Priorize funcionalidades
- Documente tudo desde o início

### Desenvolvimento
- Commits frequentes e descritivos
- Teste enquanto desenvolve
- Refatore constantemente
- Comunique com a equipe

### Qualidade
- TypeScript strict desde o início
- Testes durante desenvolvimento
- Code reviews internos
- Linting e formatação automática

### Comunicação
- Daily standups
- GitHub Issues para tracking
- Code reviews construtivos
- Documentação atualizada

## Apresentação Final

### Estrutura da Apresentação (15-20 minutos)

1. **Visão Geral** (2 min)
   - O que foi construído
   - Problema que resolve
   - Stack utilizado

2. **Demo** (8 min)
   - Fluxo do usuário
   - Funcionalidades principais
   - Performance

3. **Arquitetura Técnica** (5 min)
   - Estrutura do projeto
   - Decisões importantes
   - Desafios e soluções

4. **Aprendizados** (3 min)
   - O que aprendeu
   - Desafios superados
   - Próximos passos

5. **Q&A** (5 min)
   - Perguntas da banca
   - Discussão

## Critério de Aprovação

- Projeto submetido e funcional
- Mínimo 70% de funcionalidades implementadas
- Deploy bem-sucedido
- Documentação adequada
- Apresentação clara
- Evidência de aprendizado individual

## Recursos de Aprendizado

### Documentação Referência
- [React Docs](https://react.dev)
- [Express Docs](https://expressjs.com)
- [PostgreSQL Docs](https://postgresql.org/docs)
- [Docker Docs](https://docs.docker.com)

### Inspiração
- GitHub Awesome lists
- Producthunt
- Dribbble (design)
- Real startups

## Próximos Passos Após o Semestre

- Publicar projeto no GitHub (portfolio)
- Fazer blog post técnico
- Aplicar para jobs Junior
- Começar 3º Semestre (Python + Mobile)
- Contribuir em open source

## Mentorias e Suporte

- Mentor de projeto: 2h por semana
- Office hours: 4h por semana
- Code reviews: feedback diário
- Help desk: disponível quando necessário
- Demo sessions: showcase semanal

## Notas Importantes

- Este é o seu portfolo - dedique-se!
- Qualidade > quantidade de features
- Documentação é tão importante quanto código
- Use Git e GitHub adequadamente
- Colaboração é valorizada
- Aprenda com os erros

## Sucesso esperado

Ao terminar este projeto, você terá:
- Portfolio profissional
- Experiência full-stack real
- Código pronto para produção
- Compreensão profunda de todo stack
- Confiança para novos desafios

Boa sorte e bom desenvolvimento!

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Profissional
