# Mês 11: Node.js e Express

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 17-20
**Pré-requisito:** JavaScript avançado + conceitos HTTP/REST
**Status:** Módulo Essencial Backend ⭐⭐⭐

## Visão Geral

Este módulo introduz o desenvolvimento backend com Node.js e Express. Os alunos aprenderão a criar APIs REST robustas, escaláveis e prontas para produção, implementando autenticação, validação, tratamento de erros e boas práticas.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Compreender arquitetura backend e padrões MVC
- Criar APIs REST com Express
- Implementar middleware customizado
- Trabalhar com autenticação (JWT, Sessions)
- Validar dados com robustez
- Tratar erros elegantemente
- Estruturar código profissionalmente
- Testar APIs
- Documentar com Swagger/OpenAPI
- Implementar rate limiting e segurança

## Estrutura de Aprendizado

### SEMANA 1: Fundamentos Backend e Express

#### Aula 1: Conceitos de Backend e Node.js (6h)
- Client-Server architecture
- HTTP fundamentals (methods, status codes, headers)
- REST principles
- Node.js event loop
- Blocking vs non-blocking
- Callbacks, Promises, async/await
- Module system (CommonJS vs ES6)

**Projeto Prático:** Servidor HTTP nativo Node.js

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/api/users' && req.method === 'GET') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify([{ id: 1, name: 'John' }]));
  }
});

server.listen(3000);
```

#### Aula 2: Introdução ao Express (6h)
- Express fundamentals
- Routing basics
- Request/response objects
- Path parameters
- Query strings
- Body parsing
- Static files
- Error handling básico

**Projeto Prático:** API simples com Express

```javascript
const express = require('express');
const app = express();

app.use(express.json());

app.get('/api/users/:id', (req, res) => {
  const { id } = req.params;
  const { filter } = req.query;
  res.json({ id, filter });
});

app.post('/api/users', (req, res) => {
  const { name, email } = req.body;
  res.status(201).json({ name, email });
});

app.listen(3000);
```

#### Aula 3: Middleware e Arquitetura (6h)
- O que é middleware
- Express middleware pipeline
- Built-in middlewares
- Custom middleware
- Middleware execution order
- req/res/next
- Error-handling middleware
- Estrutura escalável de rotas

**Projeto Prático:** Sistema de middleware customizado

```javascript
const app = express();

// Middleware de logging
app.use((req, res, next) => {
  console.log(`${req.method} ${req.path}`);
  next();
});

// Middleware de autenticação
const auth = (req, res, next) => {
  const token = req.headers.authorization;
  if (!token) return res.status(401).json({ error: 'Unauthorized' });
  req.user = verifyToken(token);
  next();
};

app.get('/api/protected', auth, (req, res) => {
  res.json({ user: req.user });
});

// Error middleware
app.use((err, req, res, next) => {
  console.error(err);
  res.status(500).json({ error: 'Internal Server Error' });
});
```

#### Aula 4: Estrutura MVC (6h)
- Model-View-Controller pattern
- Controllers (business logic)
- Routers (routing)
- Separation of concerns
- File organization
- Modularização de código

**Projeto Prático:** Refatorar app para MVC

```
src/
├── controllers/
│   ├── userController.js
│   └── productController.js
├── routes/
│   ├── userRoutes.js
│   └── productRoutes.js
├── models/
│   ├── User.js
│   └── Product.js
├── middleware/
│   ├── auth.js
│   └── validation.js
└── app.js
```

### SEMANA 2: Validação e Autenticação

#### Aula 5: Validação de Dados (6h)
- Por que validar
- Joi para schema validation
- Zod como alternativa
- Validação em middleware
- Custom validators
- Error messages customizadas
- Sanitização de dados

**Projeto Prático:** Sistema completo de validação

```javascript
const Joi = require('joi');

const userSchema = Joi.object({
  name: Joi.string().min(3).required(),
  email: Joi.string().email().required(),
  password: Joi.string().min(8).required(),
  age: Joi.number().integer().min(18)
});

const validateUser = (req, res, next) => {
  const { error, value } = userSchema.validate(req.body);
  if (error) {
    return res.status(400).json({ error: error.details });
  }
  req.validatedData = value;
  next();
};

app.post('/api/users', validateUser, (req, res) => {
  // dados já validados
});
```

#### Aula 6: Autenticação com JWT (6h)
- Tokens vs Sessions
- JWT structure (header, payload, signature)
- Signing e verification
- Refresh tokens
- Token expiration
- Best practices
- Security considerations

**Projeto Prático:** Sistema JWT completo

```javascript
const jwt = require('jsonwebtoken');

// Criar token
function createToken(user) {
  return jwt.sign(
    { id: user.id, email: user.email },
    process.env.JWT_SECRET,
    { expiresIn: '1h' }
  );
}

// Verificar token
const verifyToken = (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];
  if (!token) return res.status(401).json({ error: 'No token' });

  try {
    req.user = jwt.verify(token, process.env.JWT_SECRET);
    next();
  } catch (error) {
    res.status(401).json({ error: 'Invalid token' });
  }
};

// Login endpoint
app.post('/api/auth/login', (req, res) => {
  const user = authenticateUser(req.body);
  const token = createToken(user);
  res.json({ token });
});
```

#### Aula 7: Autenticação com Sessions (6h)
- Sessions vs JWT
- Cookie-based authentication
- express-session
- Session store strategies
- CSRF protection
- Logout handling
- Session security

**Projeto Prático:** App com autenticação por sessão

```javascript
const session = require('express-session');

app.use(session({
  secret: process.env.SESSION_SECRET,
  resave: false,
  saveUninitialized: true,
  cookie: {
    secure: true,
    httpOnly: true,
    sameSite: 'strict'
  }
}));

app.post('/api/auth/login', (req, res) => {
  const user = authenticateUser(req.body);
  req.session.userId = user.id;
  res.json({ message: 'Logged in' });
});

app.get('/api/auth/me', (req, res) => {
  if (!req.session.userId) {
    return res.status(401).json({ error: 'Not authenticated' });
  }
  res.json({ userId: req.session.userId });
});
```

#### Aula 8: Autorização e Controle de Acesso (6h)
- RBAC (Role-Based Access Control)
- ABAC (Attribute-Based Access Control)
- Permissions vs Roles
- Middleware de autorização
- Scopes em JWT
- Protected routes
- Fine-grained access control

**Projeto Prático:** Sistema de roles e permissões

```javascript
const authorize = (roles) => (req, res, next) => {
  if (!req.user || !roles.includes(req.user.role)) {
    return res.status(403).json({ error: 'Forbidden' });
  }
  next();
};

app.delete(
  '/api/users/:id',
  verifyToken,
  authorize(['admin']),
  (req, res) => {
    // deletar usuário
  }
);
```

### SEMANA 3: Banco de Dados e ORM

#### Aula 9: Integração com PostgreSQL (6h)
- Node.js database drivers
- pg library
- Connection pooling
- Query building
- Parameterized queries (preventing SQL injection)
- Transactions
- Error handling

**Projeto Prático:** Conectar e consultar PostgreSQL

```javascript
const { Pool } = require('pg');

const pool = new Pool({
  connectionString: process.env.DATABASE_URL
});

app.get('/api/users', async (req, res) => {
  try {
    const result = await pool.query('SELECT * FROM users');
    res.json(result.rows);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.post('/api/users', async (req, res) => {
  const { name, email } = req.body;
  try {
    const result = await pool.query(
      'INSERT INTO users (name, email) VALUES ($1, $2) RETURNING *',
      [name, email]
    );
    res.status(201).json(result.rows[0]);
  } catch (error) {
    res.status(400).json({ error: error.message });
  }
});
```

#### Aula 10: ORM com Sequelize (6h)
- O que é ORM
- Sequelize basics
- Models e attributes
- Associations (1-to-1, 1-to-many, many-to-many)
- Migrations
- Seeders
- Queries com ORM

**Projeto Prático:** App com Sequelize

```javascript
const { DataTypes } = require('sequelize');
const sequelize = require('./config/database');

const User = sequelize.define('User', {
  name: {
    type: DataTypes.STRING,
    allowNull: false
  },
  email: {
    type: DataTypes.STRING,
    allowNull: false,
    unique: true
  }
});

const Post = sequelize.define('Post', {
  title: DataTypes.STRING,
  content: DataTypes.TEXT
});

User.hasMany(Post);
Post.belongsTo(User);

app.get('/api/users/:id/posts', async (req, res) => {
  const user = await User.findByPk(req.params.id, {
    include: Post
  });
  res.json(user);
});
```

#### Aula 11: Relações Complexas no Banco (6h)
- Many-to-many relationships
- Through tables
- Constraints
- Cascading deletes
- Soft deletes
- Polymorphic associations

**Projeto Prático:** Modelar relacionamentos complexos

#### Aula 12: Testes de API (6h)
- Testes unitários
- Testes de integração
- Supertest para testes HTTP
- Mocking de banco de dados
- Test fixtures
- Coverage

**Projeto Prático:** Suite de testes para API

```javascript
const request = require('supertest');
const app = require('../app');

describe('GET /api/users', () => {
  it('should return all users', async () => {
    const res = await request(app).get('/api/users');
    expect(res.statusCode).toBe(200);
    expect(res.body).toBeInstanceOf(Array);
  });

  it('should return 401 without token', async () => {
    const res = await request(app)
      .get('/api/users/protected')
      .send();
    expect(res.statusCode).toBe(401);
  });
});
```

### SEMANA 4: Produção e Projeto

#### Aula 13: Tratamento de Erros Robusto (4h)
- Tipos de erros (validation, auth, business, DB)
- Error classes customizadas
- Error middleware
- Logging de erros
- Error recovery
- Error responses consistentes

**Projeto Prático:** Sistema completo de tratamento de erros

```javascript
class AppError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.statusCode = statusCode;
  }
}

const errorHandler = (err, req, res, next) => {
  err.statusCode = err.statusCode || 500;

  res.status(err.statusCode).json({
    status: 'error',
    statusCode: err.statusCode,
    message: err.message
  });
};

app.use(errorHandler);
```

#### Aula 14: Documentação com Swagger (4h)
- OpenAPI specification
- Swagger/OpenAPI tools
- Documenting endpoints
- Request/response examples
- Swagger UI
- Auto-generating documentation

**Projeto Prático:** Documentar API com Swagger

```javascript
const swaggerUi = require('swagger-ui-express');
const swaggerJsdoc = require('swagger-jsdoc');

const specs = swaggerJsdoc({
  definition: {
    openapi: '3.0.0',
    info: { title: 'API', version: '1.0.0' },
    servers: [{ url: 'http://localhost:3000' }]
  },
  apis: ['./routes/*.js']
});

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(specs));
```

#### Aula 15: Segurança e Performance (4h)
- Rate limiting
- CORS
- Helmet para headers de segurança
- Input sanitization
- Output encoding
- Caching strategies
- Compression

**Projeto Prático:** Securizar e otimizar API

```javascript
const rateLimit = require('express-rate-limit');
const helmet = require('helmet');
const cors = require('cors');

app.use(helmet());
app.use(cors({
  origin: process.env.ALLOWED_ORIGINS.split(','),
  credentials: true
}));

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
  message: 'Too many requests'
});
app.use('/api/', limiter);
```

#### Aula 16: Projeto Final - API Completa (8h)
- CRUD completo
- Autenticação JWT
- Autorização por roles
- Validação robusta
- Banco de dados relacional
- Testes 80%+
- Documentação Swagger
- Deploy

## Conteúdo Técnico Detalhado

### REST API Best Practices

```javascript
// Rotas bem estruturadas
app.get('/api/v1/users', getAllUsers);           // GET
app.get('/api/v1/users/:id', getUserById);       // GET
app.post('/api/v1/users', createUser);           // POST
app.put('/api/v1/users/:id', updateUser);        // PUT
app.patch('/api/v1/users/:id', partialUpdate);   // PATCH
app.delete('/api/v1/users/:id', deleteUser);     // DELETE

// Responses consistentes
{
  "status": "success",
  "data": { /* dados */ },
  "message": "Operation successful"
}

{
  "status": "error",
  "statusCode": 400,
  "message": "Invalid input",
  "errors": { /* detalhes */ }
}
```

### Estrutura de Projeto Profissional

```
src/
├── config/
│   ├── database.js
│   ├── env.js
│   └── constants.js
├── controllers/
│   ├── userController.js
│   ├── postController.js
│   └── authController.js
├── models/
│   ├── User.js
│   ├── Post.js
│   └── index.js
├── routes/
│   ├── userRoutes.js
│   ├── postRoutes.js
│   └── authRoutes.js
├── middleware/
│   ├── auth.js
│   ├── validation.js
│   ├── errorHandler.js
│   └── cors.js
├── utils/
│   ├── errors.js
│   ├── validation.js
│   └── jwt.js
├── migrations/
│   ├── 001-create-users.js
│   └── 002-create-posts.js
├── seeds/
│   ├── seed-users.js
│   └── seed-posts.js
├── tests/
│   ├── user.test.js
│   ├── auth.test.js
│   └── setup.js
├── app.js
├── server.js
├── .env.example
└── package.json
```

## Projetos do Módulo

### Projeto 1: Task API com Express
**Duração:** 20 horas
**Tecnologias:** Express, PostgreSQL, JWT
**Funcionalidades:**
- CRUD de tarefas
- Autenticação com JWT
- Validação com Joi
- Testes com Supertest
- Documentação Swagger

### Projeto 2: Blog API Completa
**Duração:** 32 horas
**Tecnologias:** Express, Sequelize, PostgreSQL, JWT
**Funcionalidades:**
- Posts, comentários, usuários
- Autenticação e autorização
- Relacionamentos complexos
- Rate limiting
- Testes 80%+
- Deploy pronto

### Projeto 3: Revisor de Conceitos
**Duração:** 8 horas

## Stack Tecnológico

- **Node.js 18+**
- **Express 4.x**
- **PostgreSQL 14+**
- **Sequelize** (ORM)
- **JWT** (jsonwebtoken)
- **Joi** (validation)
- **Helmet** (segurança)
- **Jest/Supertest** (testes)
- **Swagger** (documentação)

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 17 | 24 | Express Basics, MVC | Exercícios |
| 18 | 24 | Validação, Auth | Projeto 1 |
| 19 | 24 | Banco de Dados | Projeto 2 |
| 20 | 24 | Testes, Deploy | Projeto Final |

## Recursos de Aprendizado

### Documentação
- [Express.js Guide](https://expressjs.com)
- [Node.js API Docs](https://nodejs.org/api)
- [Sequelize Docs](https://sequelize.org)

### Artigos Recomendados
- REST API Best Practices
- Node.js Security
- Database Design Patterns

## Requisitos de Conhecimento Prévio

- JavaScript avançado
- Async/await
- Conceitos de HTTP/REST
- Terminal/CLI

## Avaliação e Aprovação

### Critérios
- Frequência 75%+
- Projetos nota 7.0+
- 80%+ cobertura de testes
- API bem documentada

### Cálculo de Notas
- Projeto 1: 30%
- Projeto 2: 40%
- Testes e Qualidade: 30%

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Intermediário
