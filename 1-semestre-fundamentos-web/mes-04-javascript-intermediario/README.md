# Mês 4 - JavaScript Intermediário

> **Duração**: 4 semanas | **Carga Horária**: 32h | **Nível**: Intermediário

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:

- ✅ Entender Promises e async/await
- ✅ Trabalhar com APIs e requisições HTTP
- ✅ Manipular erros e exceções
- ✅ Trabalhar com objetos avançados e protótipos
- ✅ Usar métodos funcionais (map, filter, reduce)
- ✅ Integrar APIs em aplicações web

## 📅 Cronograma Semanal

### Semana 1: Métodos Funcionais e Objetos Avançados
- **Aula 1**: Métodos funcionais - map, filter, reduce, sort
- **Aula 2**: Desestruturação e spread operator
- **Aula 3**: Este (this) e contexto de execução
- **Aula 4**: Prática - Manipulação funcional de dados

### Semana 2: Promises e Assincronismo
- **Aula 5**: Callbacks e Callback Hell
- **Aula 6**: Introdução a Promises
- **Aula 7**: Async/Await - forma moderna
- **Aula 8**: Prática - Programação assíncrona

### Semana 3: APIs e Requisições HTTP
- **Aula 9**: O que são APIs REST
- **Aula 10**: Métodos HTTP - GET, POST, PUT, DELETE
- **Aula 11**: Fetch API - realizando requisições
- **Aula 12**: Prática - Consumindo APIs públicas

### Semana 4: Tratamento de Erros e Projeto
- **Aula 13**: Try/catch/finally - tratamento de erros
- **Aula 14**: Erros customizados e validação
- **Aula 15**: Desenvolvimento do projeto final
- **Aula 16**: Apresentações e integração

## 📚 Conteúdo Detalhado

### Bloco 1: Programação Funcional

#### Métodos de Iteração Avançados
- `map()`: transformação de array
  - Função callback
  - Retornando novo array
  - Casos de uso comuns
- `filter()`: filtragem de elementos
  - Predicados
  - Composição de filtros
- `reduce()`: agregação e transformação
  - Acumulador
  - Valor inicial
  - Exemplos práticos (soma, contagem, agrupamento)
- `sort()`: ordenação customizada
  - Função comparadora
  - Ordem alfabética, numérica
  - Ordem reversa

#### Encadeamento (Chaining)
- Combinando múltiplos métodos
- Melhorando legibilidade
- Pipelines de transformação

#### Imutabilidade
- Conceito de dados imutáveis
- Vantagens da imutabilidade
- Criando cópias com spread `[...array]`

#### Desestruturação
- Array destructuring: `const [a, b] = array`
- Object destructuring: `const { prop } = objeto`
- Renomeação e valores padrão
- Em parâmetros de funções

#### Spread Operator
- Cópia de arrays: `[...array]`
- Cópia de objetos: `{...objeto}`
- Mesclagem: `{...obj1, ...obj2}`
- Argumentos variádicos

### Bloco 2: Objetos Avançados

#### This (Este)
- `this` em funções comuns
- `this` em arrow functions (sem binding próprio)
- `this` em métodos de objeto
- Binding manual: `call()`, `apply()`, `bind()`

#### Protótipos e Herança
- Cadeia de protótipos
- `Object.prototype`
- Herança prototípica
- `Object.create()`

#### Classes ES6
- Sintaxe de classe
- Constructor
- Métodos
- Herança com `extends`
- `super`
- Getters e setters

#### Object Methods
- `Object.keys()`, `Object.values()`, `Object.entries()`
- `Object.assign()`
- `Object.freeze()` e `Object.seal()`
- `Object.defineProperty()`
- `Object.getPrototypeOf()`

### Bloco 3: Promises e Asincronismo

#### Callbacks
- Conceito de callback
- Callbacks em eventos
- Callback Hell (Pyramid of Doom)

#### Promises
- Estados: Pending, Fulfilled, Rejected
- Criando Promises: `new Promise((resolve, reject) => {})`
- Consumindo Promises:
  - `.then()`: sucesso
  - `.catch()`: erro
  - `.finally()`: sempre executado
- Encadeamento de `.then()`
- `Promise.all()`: esperar múltiplas promises
- `Promise.race()`: primeira a resolver
- `Promise.allSettled()`: aguardar todas, independente de erro
- `Promise.any()`: primeira que resolver com sucesso

#### Async/Await
- Sintaxe assíncrona
- `await`: pausando execução
- Try/catch com async/await
- Loops assíncronos
- Parallelismo vs sequência

### Bloco 4: APIs e HTTP

#### Conceitos de API
- O que é uma API
- REST vs SOAP
- HTTP e seus protocolos
- JSON como formato

#### Métodos HTTP
- GET: recuperar dados
- POST: criar dados
- PUT/PATCH: atualizar dados
- DELETE: deletar dados
- HEAD, OPTIONS

#### Headers HTTP
- `Content-Type`
- `Authorization`
- `Accept`
- CORS (Cross-Origin Resource Sharing)

#### Fetch API
- Sintaxe básica
- Requisições GET
- Requisições com método, headers, body
- Parsing de resposta: `.json()`, `.text()`
- Status code e `response.ok`
- Timeout e cancelamento

#### APIs Públicas
- JSONPlaceholder
- OpenWeatherMap
- GitHub API
- Unsplash
- Pokémon API
- Diferenças entre com/sem autenticação

#### CORS
- Conceito e restrições
- Requisições simples vs preflight
- Solução: proxy
- Lado do servidor: headers CORS

### Bloco 5: Tratamento de Erros

#### Try/Catch/Finally
- Bloco try
- Bloco catch
- Bloco finally
- Aninhamento
- Tipos de erro

#### Erros Nativos
- `Error`
- `TypeError`
- `ReferenceError`
- `SyntaxError`
- `RangeError`

#### Erros Customizados
- Criando classes de erro
- Estendendo Error
- Propriedades customizadas

#### Validação
- Validação de entrada
- Validação de resposta API
- Mensagens de erro úteis
- Logging de erros

## 💻 Exercícios Práticos

### Lista de Exercícios
1. [Exercícios de Métodos Funcionais](./exercicios/01-metodos-funcionais.md)
2. [Exercícios de Promises e Async](./exercicios/02-promises-async.md)
3. [Exercícios de Fetch API](./exercicios/03-fetch-api.md)
4. [Exercícios de Tratamento de Erros](./exercicios/04-tratamento-erros.md)

## 🎯 Projetos do Mês

### Projeto 1: Aplicação de Clima (Semana 2)
**Objetivo**: Integrar API de clima em tempo real

**Requisitos**:
- Buscar clima por cidade
- Exibir temperatura, umidade, vento
- Previsão de 5 dias
- Interface responsiva
- Tratamento de erros
- Cache local
- Pesquisa com sugestões

**Tecnologias**: HTML + CSS + JavaScript (Fetch, Promises, DOM)

[Ver especificação completa](./projetos/projeto-01-app-clima.md)

---

### Projeto 2: Galeria de Imagens Dinâmica (Semana 4)
**Objetivo**: Criar galeria consumindo API de imagens

**Requisitos**:
- Buscar imagens por palavras-chave
- Paginação ou infinite scroll
- Lightbox para visualizar em detalhe
- Favoritos (salvar em localStorage)
- Filtros
- Loading states
- Tratamento de erros e retry

**Tecnologias**: HTML + CSS + JavaScript (Async/Await, Fetch, DOM)

[Ver especificação completa](./projetos/projeto-02-galeria-imagens.md)

---

## 📖 Material de Apoio

### Leitura Obrigatória
- [Promises - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async/Await - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/async_function)
- [Fetch API - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API)

### Vídeos Complementares
- Promises em detalhes - Tutorial completo
- Async/Await - Como funciona
- Fetch API - Consumindo APIs

### Ferramentas Úteis
- [Postman](https://www.postman.com/) - Teste de APIs
- [JSONPlaceholder](https://jsonplaceholder.typicode.com/) - API fake para praticar
- [REST Countries API](https://restcountries.com/) - API de países
- [Insomnia](https://insomnia.rest/) - Alternativa a Postman

## ✅ Checklist de Conclusão

Antes de avançar para o Mês 5, certifique-se de que você:

- [ ] Domina métodos funcionais (map, filter, reduce)
- [ ] Entende Promises e sua cadeia
- [ ] Trabalha com async/await confortavelmente
- [ ] Consegue fazer requisições com Fetch API
- [ ] Trata erros adequadamente
- [ ] Trabalha com APIs REST
- [ ] Completou os 2 projetos do mês
- [ ] Código está bem estruturado e documentado

## 🎓 Avaliação do Módulo

### Critérios
- **Participação**: Presença e engajamento nas aulas
- **Exercícios**: Resolução das listas propostas
- **Projetos**: Qualidade, funcionalidade e user experience
- **Código**: Legibilidade e boas práticas
- **Tratamento de Erros**: Robustez das aplicações

### Entregáveis
1. Repositório GitHub com projetos
2. Links para aplicações publicadas
3. Documentação de APIs utilizadas

---

## 📂 Estrutura de Arquivos

```
mes-04-javascript-intermediario/
├── README.md (este arquivo)
├── aulas/
│   ├── aula-01-metodos-funcionais.md
│   ├── aula-02-desestruturacao-spread.md
│   ├── aula-03-this-contexto.md
│   ├── aula-04-pratica-funcional.md
│   ├── aula-05-callbacks.md
│   ├── aula-06-promises.md
│   ├── aula-07-async-await.md
│   ├── aula-08-pratica-async.md
│   ├── aula-09-rest-api.md
│   ├── aula-10-metodos-http.md
│   ├── aula-11-fetch-api.md
│   ├── aula-12-pratica-apis.md
│   ├── aula-13-try-catch.md
│   ├── aula-14-validacao-erros.md
│   ├── aula-15-desenvolvimento-projeto.md
│   └── aula-16-apresentacoes.md
├── exercicios/
│   ├── 01-metodos-funcionais.md
│   ├── 02-promises-async.md
│   ├── 03-fetch-api.md
│   └── 04-tratamento-erros.md
├── projetos/
│   ├── projeto-01-app-clima.md
│   └── projeto-02-galeria-imagens.md
└── recursos/
    ├── cheatsheet-promises.md
    ├── cheatsheet-async-await.md
    ├── cheatsheet-fetch.md
    ├── apis-publicas.md
    └── links-uteis.md
```

---

**Pronto para avançar para JavaScript intermediário? Vamos para a [Aula 1](./aulas/aula-01-metodos-funcionais.md)!** 🚀
