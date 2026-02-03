# Mês 5 - JavaScript Avançado

> **Duração**: 4 semanas | **Carga Horária**: 32h | **Nível**: Avançado

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:

- ✅ Dominar closures e escopo avançado
- ✅ Implementar padrões de design (Design Patterns)
- ✅ Trabalhar com módulos ES6
- ✅ Criar eventos customizados
- ✅ Implementar Web APIs avançadas
- ✅ Otimizar performance de aplicações JavaScript

## 📅 Cronograma Semanal

### Semana 1: Closures, Escopo e This Avançado
- **Aula 1**: Closures - conceitos e casos de uso
- **Aula 2**: IIFE (Immediately Invoked Function Expression)
- **Aula 3**: Bind, Call e Apply - controlando contexto
- **Aula 4**: Prática - Aplicando closures e contexto

### Semana 2: Padrões de Design e Módulos
- **Aula 5**: Singleton pattern
- **Aula 6**: Module pattern e namespace
- **Aula 7**: ES6 Modules - import/export
- **Aula 8**: Prática - Organizando código com módulos

### Semana 3: Eventos Avançados e Web APIs
- **Aula 9**: Event delegation e event bubbling
- **Aula 10**: Eventos customizados e disparo
- **Aula 11**: LocalStorage, SessionStorage e IndexedDB
- **Aula 12**: Prática - Web APIs avançadas

### Semana 4: Performance e Projeto Final
- **Aula 13**: Profiling e otimização de performance
- **Aula 14**: Lazy loading e debounce/throttle
- **Aula 15**: Desenvolvimento do projeto final
- **Aula 16**: Code review e apresentações

## 📚 Conteúdo Detalhado

### Bloco 1: Closures e Escopo Avançado

#### Closures
- Definição e conceito
- Funcionar acessando variáveis do escopo externo
- Casos de uso comuns
  - Factory functions
  - Data privacy
  - Callbacks com estado
- Garbage collection e memory leaks
- Padrão de módulo com closures

#### Escopo Léxico
- Escopo determinado em tempo de compilação
- Variable shadowing
- Escopo vs binding do `this`

#### IIFE (Immediately Invoked Function Expression)
- Sintaxe e variações
- Criando escopos isolados
- Padrão de módulo IIFE
- Preservando a global

#### Currying
- Conceito de currying
- Funções curried vs parâmetros múltiplos
- Partial application
- Casos de uso

#### Composição de Funções
- Higher-order functions
- Composição de funções puras
- Pipelines de funções
- Bibliotecas como Lodash

### Bloco 2: This, Bind, Call e Apply

#### This Avançado
- `this` em diferentes contextos
- Arrow functions e `this` léxico
- `this` em eventos
- `this` em métodos vs funções

#### Métodos de Contexto
- `function.call()`: invoca com contexto específico
- `function.apply()`: similiar a call mas com array de argumentos
- `function.bind()`: cria nova função com contexto permanente
- Uso em callbacks e event handlers

#### Exemplos Práticos
- Métodos de array com contexto
- Herança de contexto
- Simulação de métodos em objetos diferentes

### Bloco 3: Padrões de Design

#### Singleton
- Conceito: uma única instância
- Implementação em JavaScript
- Casos de uso: logger, config, conexão
- Vantagens e desvantagens

#### Module Pattern
- Encapsulamento com closures
- Público vs privado
- Revealing module pattern
- Padrão IIFE

#### Factory Pattern
- Criação de objetos
- Funções factory vs new
- Vantagens sobre classes

#### Observer Pattern
- Publicação e subscrição
- Implementação básica
- Caso de uso em event systems

#### Decorator Pattern
- Adicionando funcionalidade a objetos
- Diferença de herança
- Padrão middleware

### Bloco 4: ES6 Modules

#### Módulos ESM
- `export`: exportando funções/classes/dados
- `import`: importando de outro módulo
- Exportação nomeada vs default
- `export *`: re-export
- `import * as`: importing namespace

#### Organisação de Código
- Módulos para cada funcionalidade
- Estrutura de pastas
- Ciclo de vida de módulos
- Module scope

#### Bundlers
- Webpack, Rollup, Vite
- Resolução de módulos
- Tree-shaking
- Code splitting

### Bloco 5: Eventos Avançados

#### Event Bubbling e Capture
- Fases de evento: capture, target, bubbling
- `addEventListener(..., true)`: captura
- `addEventListener(..., false)`: bubbling (padrão)
- `stopPropagation()` e `stopImmediatePropagation()`

#### Event Delegation
- Delegação de eventos
- Benefícios: performance e dinamicidade
- Usando `event.target`
- Casos de uso: listas dinâmicas

#### Eventos Customizados
- `CustomEvent`: criando eventos
- `element.dispatchEvent()`: disparando eventos
- Passando dados com eventos
- Padrão pub/sub com eventos

### Bloco 6: Web APIs Avançadas

#### LocalStorage e SessionStorage
- Diferenças entre os dois
- Armazenando dados (strings)
- JSON.stringify e JSON.parse
- Limitações (5-10MB)
- Casos de uso: preferências, cache

#### IndexedDB
- Banco de dados no navegador
- Object stores e índices
- Transações
- Queries avançadas
- Usado por: Offline storage, grandes volumes

#### Geolocation API
- Permissões
- `navigator.geolocation.getCurrentPosition()`
- `watchPosition()`
- Latitude, longitude, acurácia

#### Service Workers (Introdução)
- O que é Service Worker
- Cache estratégias
- Offline first
- PWA basics

### Bloco 7: Performance

#### Otimização
- Critical render path
- Repaint e reflow
- Batching de DOM updates
- Virtual scrolling

#### Debounce e Throttle
- Debounce: esperar antes de executar
- Throttle: executar a intervalos regulares
- Implementação
- Casos de uso: scroll, resize, input

#### Memory Management
- Garbage collection
- Memory leaks
- Referências circulares
- DevTools profiling

#### Lazy Loading
- Carregamento sob demanda
- Intersection Observer API
- Imagens lazy
- Componentes lazy

## 💻 Exercícios Práticos

### Lista de Exercícios
1. [Exercícios de Closures](./exercicios/01-closures.md)
2. [Exercícios de Padrões de Design](./exercicios/02-design-patterns.md)
3. [Exercícios de Módulos](./exercicios/03-modulos.md)
4. [Exercícios de Performance](./exercicios/04-performance.md)

## 🎯 Projetos do Mês

### Projeto 1: Aplicação com Arquitetura Modular (Semana 2)
**Objetivo**: Refatorar/criar aplicação usando módulos e padrões

**Requisitos**:
- Estrutura modular com ES6 modules
- Design patterns aplicados (singleton, factory, observer)
- Separação de concerns (UI, lógica, dados)
- Eventos customizados para comunicação
- LocalStorage para persistência
- Testes básicos

**Tecnologias**: HTML + CSS + JavaScript (Módulos, Patterns)

[Ver especificação completa](./projetos/projeto-01-arquitetura-modular.md)

---

### Projeto 2: Dashboard com Performance Otimizada (Semana 4)
**Objetivo**: Criar dashboard com foco em performance e otimização

**Requisitos**:
- Consumo de API com lazy loading
- Debounce/throttle em filtros
- Virtual scrolling em listas grandes
- Cache inteligente (LocalStorage/IndexedDB)
- Tema customizável com CSS variables
- Offline mode básico
- Métricas de performance

**Tecnologias**: HTML + CSS + JavaScript (APIs, Performance, Storage)

[Ver especificação completa](./projetos/projeto-02-dashboard-otimizado.md)

---

## 📖 Material de Apoio

### Leitura Obrigatória
- [Closures - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Closures)
- [This - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/this)
- [Modules - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Modules)

### Vídeos Complementares
- Closures explicados - Entendendo profundamente
- Design Patterns em JavaScript
- Performance otimization - Techniques
- Event Delegation - Tutorial prático

### Ferramentas Úteis
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/) - Profiling
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - Performance audit
- [JSPerf](https://jsperf.com/) - Benchmark
- [Memory Analysis](https://developer.chrome.com/docs/devtools/memory-problems/)

## ✅ Checklist de Conclusão

Antes de avançar para o Mês 6, certifique-se de que você:

- [ ] Domina closures e casos de uso
- [ ] Entende e aplica padrões de design
- [ ] Trabalha com módulos ES6
- [ ] Implementa eventos customizados
- [ ] Otimiza performance de aplicações
- [ ] Usa Web APIs avançadas (Storage, Geolocation)
- [ ] Completou os 2 projetos do mês
- [ ] Código está altamente profissional

## 🎓 Avaliação do Módulo

### Critérios
- **Participação**: Presença e engajamento nas aulas
- **Exercícios**: Resolução das listas propostas
- **Projetos**: Qualidade arquitetural e performance
- **Código**: Padrões e boas práticas
- **Otimização**: Demonstração de técnicas de performance

### Entregáveis
1. Repositório GitHub com projetos
2. Documentação de arquitetura
3. Análise de performance (Lighthouse)
4. README com explicações de padrões utilizados

---

## 📂 Estrutura de Arquivos

```
mes-05-javascript-avancado/
├── README.md (este arquivo)
├── aulas/
│   ├── aula-01-closures.md
│   ├── aula-02-iife.md
│   ├── aula-03-this-avancado.md
│   ├── aula-04-pratica-closures.md
│   ├── aula-05-singleton.md
│   ├── aula-06-module-pattern.md
│   ├── aula-07-es6-modules.md
│   ├── aula-08-pratica-modulos.md
│   ├── aula-09-event-bubbling.md
│   ├── aula-10-eventos-customizados.md
│   ├── aula-11-web-apis.md
│   ├── aula-12-pratica-apis.md
│   ├── aula-13-performance.md
│   ├── aula-14-otimizacao.md
│   ├── aula-15-desenvolvimento-projeto.md
│   └── aula-16-apresentacoes.md
├── exercicios/
│   ├── 01-closures.md
│   ├── 02-design-patterns.md
│   ├── 03-modulos.md
│   └── 04-performance.md
├── projetos/
│   ├── projeto-01-arquitetura-modular.md
│   └── projeto-02-dashboard-otimizado.md
└── recursos/
    ├── cheatsheet-closures.md
    ├── cheatsheet-patterns.md
    ├── cheatsheet-modules.md
    ├── performance-tips.md
    └── links-uteis.md
```

---

**Pronto para dominar JavaScript avançado? Vamos para a [Aula 1](./aulas/aula-01-closures.md)!** 🚀
