# Mês 12: PostgreSQL e Deploy

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 21-24
**Pré-requisito:** Mês 11 (Node.js e Express) completo
**Status:** Módulo DevOps e Dados ⭐⭐

## Visão Geral

Este módulo aprofunda conhecimento em bancos de dados relacionais com PostgreSQL e prepara aplicações para produção. Os alunos aprenderão SQL avançado, design de banco de dados, indexação, performance tuning e deployment em cloud.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Dominar SQL avançado (joins, CTEs, window functions)
- Projetar bancos de dados escaláveis
- Otimizar queries e índices
- Implementar transações e consistência
- Fazer backup e recovery
- Usar Docker para containerização
- Implementar CI/CD com GitHub Actions
- Fazer deploy em plataformas cloud
- Monitorar aplicações em produção
- Implementar logging centralizado

## Estrutura de Aprendizado

### SEMANA 1: SQL Avançado e Design

#### Aula 1: SQL Intermediário e Avançado (6h)
- JOINs (INNER, LEFT, RIGHT, FULL OUTER)
- Subqueries e CTEs (Common Table Expressions)
- Window functions (ROW_NUMBER, RANK, LAG, LEAD)
- Aggregations (GROUP BY, HAVING)
- Set operations (UNION, INTERSECT, EXCEPT)
- Performance considerations

**Projeto Prático:** Queries complexas e análises

```sql
-- CTE com window functions
WITH ranked_users AS (
  SELECT
    id,
    name,
    registration_date,
    ROW_NUMBER() OVER (ORDER BY registration_date) as rank,
    COUNT(*) OVER () as total_users
  FROM users
  WHERE status = 'active'
)
SELECT * FROM ranked_users WHERE rank <= 10;

-- Subquery correlacionada
SELECT id, name, (
  SELECT COUNT(*) FROM posts WHERE posts.user_id = users.id
) as post_count
FROM users;
```

#### Aula 2: Design e Normalização de Banco de Dados (6h)
- Normal Forms (1NF, 2NF, 3NF, BCNF)
- Denormalization quando apropriado
- Entity-Relationship Diagrams (ERD)
- Constraints (NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY)
- Check constraints
- Defaults
- Triggers

**Projeto Prático:** Projetar banco para aplicação real

```sql
-- Design bem estruturado
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE,
  name VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT email_format CHECK (email LIKE '%@%.%')
);

CREATE TABLE posts (
  id SERIAL PRIMARY KEY,
  user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT post_title_length CHECK (length(title) > 0)
);

CREATE INDEX idx_posts_user_id ON posts(user_id);
CREATE INDEX idx_posts_created_at ON posts(created_at);
```

#### Aula 3: Índices e Performance (6h)
- Tipos de índices (B-tree, Hash, GiST, GIN)
- Query planning (EXPLAIN, EXPLAIN ANALYZE)
- Index strategies
- Evitar full table scans
- Query optimization
- Slow query logging

**Projeto Prático:** Otimizar queries lentas

```sql
-- Análise de query
EXPLAIN ANALYZE
SELECT u.name, COUNT(p.id) as post_count
FROM users u
LEFT JOIN posts p ON u.id = p.user_id
GROUP BY u.id
ORDER BY post_count DESC;

-- Criar índices apropriados
CREATE INDEX idx_posts_user_id_created ON posts(user_id, created_at DESC);

-- Verificar uso de índices
SELECT * FROM pg_stat_user_indexes;
```

#### Aula 4: Transações e Consistência (6h)
- ACID properties
- Transaction isolation levels
- Deadlocks
- Rollback e recovery
- Savepoints
- Distributed transactions
- Long-running transactions

**Projeto Prático:** Implementar transações complexas

```javascript
// Transações em Node.js
const { Pool } = require('pg');
const pool = new Pool();

async function transferMoney(fromId, toId, amount) {
  const client = await pool.connect();

  try {
    await client.query('BEGIN');

    // Débito
    await client.query(
      'UPDATE accounts SET balance = balance - $1 WHERE id = $2',
      [amount, fromId]
    );

    // Crédito
    await client.query(
      'UPDATE accounts SET balance = balance + $1 WHERE id = $2',
      [amount, toId]
    );

    await client.query('COMMIT');
    return { success: true };
  } catch (error) {
    await client.query('ROLLBACK');
    throw error;
  } finally {
    client.release();
  }
}
```

### SEMANA 2: Backup, Recovery e Migrations

#### Aula 5: Backup e Recovery (6h)
- Estratégias de backup (full, incremental, differential)
- pg_dump e pg_restore
- WAL (Write-Ahead Logging)
- Point-in-time recovery
- Backup testing
- Disaster recovery planning

**Projeto Prático:** Setup de backup automático

```bash
# Full backup
pg_dump -U postgres -d mydb > backup.sql

# Compressed backup
pg_dump -U postgres -d mydb | gzip > backup.sql.gz

# Restore
psql -U postgres -d mydb < backup.sql

# Binary format (mais eficiente)
pg_dump -Fc -U postgres -d mydb > backup.dump
pg_restore -Fc -U postgres -d mydb backup.dump
```

#### Aula 6: Migrations com Node.js (6h)
- Versionamento de schema
- Migration tools (Knex, Sequelize migrations)
- Up e down migrations
- Rollback strategies
- Seeding data
- CI/CD com migrations

**Projeto Prático:** Sistema de migrations

```javascript
// Knex migrations
exports.up = function(knex) {
  return knex.schema.createTable('users', table => {
    table.increments('id');
    table.string('email').notNullable().unique();
    table.string('name').notNullable();
    table.timestamp('created_at').defaultTo(knex.fn.now());
  });
};

exports.down = function(knex) {
  return knex.schema.dropTable('users');
};

// Rodando migrations
// npx knex migrate:latest
// npx knex migrate:rollback
// npx knex seed:run
```

#### Aula 7: Monitoramento de Banco de Dados (6h)
- Connection pooling
- Query monitoring
- Statistics
- Autovacuum
- Tablespace management
- Replication setup
- High availability

**Projeto Prático:** Setup monitoring e alertas

```sql
-- Ver conexões ativas
SELECT datname, usename, count(*)
FROM pg_stat_activity
GROUP BY datname, usename;

-- Verificar tamanho de tabelas
SELECT schemaname, tablename, pg_size_pretty(pg_total_relation_size(schemaname||'.'||tablename))
FROM pg_tables
WHERE schemaname = 'public';

-- Autovacuum status
SELECT relname, last_vacuum, last_autovacuum
FROM pg_stat_user_tables;
```

#### Aula 8: PostgreSQL Avançado (6h)
- JSON/JSONB types
- Full-text search
- Array types
- Range types
- Custom data types
- Functions e procedures
- Extensions

**Projeto Prático:** Usar tipos avançados

```sql
-- JSONB para dados não-estruturados
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  metadata JSONB DEFAULT '{}'
);

INSERT INTO users VALUES (1, 'John', '{"phone": "123", "address": "NYC"}');
SELECT metadata->>'phone' FROM users; -- '123'

-- Full-text search
CREATE TABLE articles (
  id SERIAL PRIMARY KEY,
  title VARCHAR(255),
  content TEXT,
  tsv tsvector
);

UPDATE articles SET tsv = to_tsvector(title || ' ' || content);
CREATE INDEX idx_articles_tsv ON articles USING GIN(tsv);

SELECT * FROM articles
WHERE tsv @@ to_tsquery('database & performance');
```

### SEMANA 3: Docker e Containerização

#### Aula 9: Docker Fundamentals (6h)
- Containers vs VMs
- Docker concepts (images, containers, volumes)
- Dockerfile
- Docker Compose
- Container networking
- Volume management

**Projeto Prático:** Containerizar aplicação Node.js

```dockerfile
# Dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

```yaml
# docker-compose.yml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
    environment:
      - DATABASE_URL=postgres://user:pass@db:5432/mydb

  db:
    image: postgres:14
    environment:
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

#### Aula 10: CI/CD com GitHub Actions (6h)
- GitHub Actions concepts
- Workflows e jobs
- Triggers
- Actions reusáveis
- Testing automation
- Building e deploying
- Secrets e environment variables

**Projeto Prático:** Setup CI/CD completo

```yaml
# .github/workflows/ci-cd.yml
name: CI/CD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_PASSWORD: postgres
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v3
        with:
          node-version: '18'

      - run: npm ci
      - run: npm run test
      - run: npm run lint

  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'

    steps:
      - uses: actions/checkout@v3
      - run: npm ci
      - run: npm run build
      - name: Deploy to Railway
        run: |
          curl -X POST ${{ secrets.RAILWAY_WEBHOOK }}
```

#### Aula 11: Deploy em Cloud (6h)
- Opções de hosting (Heroku, Railway, Render, AWS)
- Environment variables
- Secrets management
- Scaling e load balancing
- Database hosting (AWS RDS, Railway, Render)
- CDN e caching

**Projeto Prático:** Deploy em Railway/Render

```bash
# Railway setup
npm install -g @railway/cli
railway login
railway link

# .railway/up.yml
build:
  cmd: npm ci && npm run build
start:
  cmd: npm start

# Render deploy (render.yaml)
services:
  - type: web
    name: api
    plan: starter
    startCommand: npm start

  - type: pserv
    name: database
    plan: starter
    ipAllowList: []
```

#### Aula 12: Monitoramento em Produção (6h)
- Error tracking (Sentry)
- Performance monitoring (New Relic, DataDog)
- Logging agregado (ELK Stack, LogRocket)
- Alertas
- Status pages
- Incident response

**Projeto Prático:** Setup monitoramento completo

```javascript
// Sentry setup
const Sentry = require("@sentry/node");

Sentry.init({
  dsn: process.env.SENTRY_DSN,
  environment: process.env.NODE_ENV,
  tracesSampleRate: 1.0,
});

app.use(Sentry.Handlers.requestHandler());

// Capture errors
try {
  // code
} catch (error) {
  Sentry.captureException(error);
}

app.use(Sentry.Handlers.errorHandler());

// Winston para logging
const winston = require('winston');

const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || 'info',
  format: winston.format.json(),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' })
  ]
});
```

### SEMANA 4: Segurança e Projeto Final

#### Aula 13: Segurança em Produção (4h)
- Secrets management (dotenv, Vault)
- SSL/TLS setup
- Database credentials
- API key rotation
- Backup encryption
- Access control

**Projeto Prático:** Securizar aplicação

```javascript
// Environment variables com validação
const joi = require('joi');

const schema = joi.object({
  NODE_ENV: joi.string().valid('dev', 'prod').required(),
  DATABASE_URL: joi.string().uri().required(),
  JWT_SECRET: joi.string().min(32).required(),
  API_PORT: joi.number().default(3000),
}).unknown();

const { value, error } = schema.validate(process.env);

if (error) {
  throw new Error(`Config validation error: ${error.message}`);
}
```

#### Aula 14: Troubleshooting e Debugging (4h)
- Log analysis
- Database query debugging
- Memory leaks
- Connection issues
- Performance bottlenecks
- Recovery procedures

**Projeto Prático:** Debug aplicação com problemas

#### Aula 15: Scalability Planning (4h)
- Database sharding
- Read replicas
- Caching strategies
- Message queues
- Microservices considerations
- Load testing

**Projeto Prático:** Planejamento de escalabilidade

#### Aula 16: Projeto Final - Deploy Full-stack (8h)
- Backend Node.js/Express completo
- PostgreSQL otimizado
- Docker e Docker Compose
- CI/CD com GitHub Actions
- Deploy em cloud
- Monitoramento e alertas
- Documentação completa

## Projetos do Módulo

### Projeto 1: Database Design e Optimization
**Duração:** 20 horas
**Foco:** SQL avançado, índices, performance
**Funcionalidades:**
- Design de banco de dados complexo
- Queries otimizadas
- Índices estratégicos
- Transações seguras
- Análise com EXPLAIN

### Projeto 2: Full-stack com Docker e CI/CD
**Duração:** 40 horas
**Stack:** Node.js, Express, PostgreSQL, Docker, GitHub Actions
**Funcionalidades:**
- Backend completo
- Banco de dados otimizado
- Migrations automáticas
- Docker Compose local
- CI/CD com testes
- Deploy automatizado
- Monitoramento

### Projeto 3: Revisor
**Duração:** 8 horas

## Stack Tecnológico

- **PostgreSQL 14+**
- **Node.js 18+**
- **Docker e Docker Compose**
- **GitHub Actions**
- **Railway/Render** (hosting)
- **Sentry** (error tracking)
- **Winston** (logging)

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 21 | 24 | SQL Avançado, Design | Exercícios |
| 22 | 24 | Migrations, Backup, Monitoramento | Projeto 1 |
| 23 | 24 | Docker, CI/CD | Projeto 2 |
| 24 | 24 | Deploy, Segurança | Projeto Final |

## Requisitos de Conhecimento Prévio

- SQL básico
- Mês 11 (Node.js/Express) completo
- Conceitos de deployment
- Terminal/CLI intermediário

## Recursos de Aprendizado

### Documentação
- [PostgreSQL Official Docs](https://www.postgresql.org/docs)
- [Docker Docs](https://docs.docker.com)
- [GitHub Actions Docs](https://docs.github.com/actions)

### Ferramentas Recomendadas
- pgAdmin (interface PostgreSQL)
- DBeaver (client universal)
- GitHub Actions Runner
- Railway CLI

## Avaliação

### Critérios
- Frequência 75%+
- Projetos nota 7.0+
- Deploy funcional
- Documentação completa

### Cálculo de Notas
- Projeto 1: 30%
- Projeto 2: 40%
- Query Optimization: 30%

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Avançado DevOps
