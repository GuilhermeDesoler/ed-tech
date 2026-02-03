# Mês 3 - JavaScript Fundamentos

> **Duração**: 4 semanas | **Carga Horária**: 32h | **Nível**: Iniciante

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:

- ✅ Dominar variáveis, tipos e operadores JavaScript
- ✅ Trabalhar com estruturas de controle (if/else, loops)
- ✅ Entender funções e escopo
- ✅ Manipular arrays e objetos
- ✅ Interagir com o DOM
- ✅ Criar páginas interativas com JavaScript

## 📅 Cronograma Semanal

### Semana 1: Fundamentos e Tipos
- **Aula 1**: Introdução ao JavaScript - história e ambientes
- **Aula 2**: Variáveis e tipos de dados - let, const, var
- **Aula 3**: Operadores - matemáticos, lógicos, comparação
- **Aula 4**: Prática - Calculadora simples

### Semana 2: Estruturas de Controle
- **Aula 5**: Condicional if/else/else if
- **Aula 6**: Switch case - alternativa aos if
- **Aula 7**: Loops - for, while, do-while
- **Aula 8**: Prática - Algoritmos com loops

### Semana 3: Funções e Escopo
- **Aula 9**: Funções - declaração e expressão
- **Aula 10**: Parâmetros e retorno
- **Aula 11**: Escopo - global, local, function, block
- **Aula 12**: Prática - Funções reutilizáveis

### Semana 4: Arrays, Objetos e DOM
- **Aula 13**: Arrays - criação, índices, métodos básicos
- **Aula 14**: Objetos - propriedades, métodos, notação literal
- **Aula 15**: DOM - seleção e manipulação de elementos
- **Aula 16**: Projeto - Aplicação interativa com DOM

## 📚 Conteúdo Detalhado

### Bloco 1: Fundamentos de JavaScript

#### Introdução
- História do JavaScript
- Ambientes: navegador vs Node.js
- Console do navegador
- Ferramentas de desenvolvimento

#### Variáveis e Tipos de Dados
- `var` (obsoleto): hoisting, function-scoped
- `let` (moderno): block-scoped, reassignável
- `const` (moderno): block-scoped, imutável
- Tipos primitivos: number, string, boolean, null, undefined, symbol, bigint
- Tipagem dinâmica vs estática
- Conversão de tipos (coerção)

#### Operadores
- Aritméticos: `+`, `-`, `*`, `/`, `%`, `**` (exponenciação)
- Atribuição: `=`, `+=`, `-=`, `*=`, `/=`, etc
- Comparação: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`
- Lógicos: `&&`, `||`, `!`
- Ternário: `condition ? true : false`
- Spread: `...` (cópia e expansão)

#### Coerção e Conversão
- Truthy e falsy values
- `Number()`, `String()`, `Boolean()`
- `parseInt()`, `parseFloat()`
- Comportamento de `==` vs `===`

### Bloco 2: Estruturas de Controle

#### Condicional if/else
- Sintaxe e fluxo
- Estrutura if/else if/else
- Nesting (condições aninhadas)
- Escrita limpa e legível

#### Switch Case
- Sintaxe switch
- Cases e break
- Default
- Quando usar switch vs if

#### Loops
- `for`: loop tradicional com inicialização, condição, incremento
- `while`: repetição enquanto condição é true
- `do-while`: executa uma vez, depois verifica
- `for...of`: iteração sobre valores
- `for...in`: iteração sobre chaves/propriedades
- `break` e `continue`: controle de fluxo

#### Boas Práticas
- Evitar loops infinitos
- Usar const/let ao invés de var
- Fazer loops legíveis e bem estruturados

### Bloco 3: Funções e Escopo

#### Declaração de Funções
- Function declaration: `function nome() { }`
- Function expression: `const nome = function() { }`
- Arrow functions: `const nome = () => { }`
- Diferenças de `this` em arrow vs regular functions

#### Parâmetros e Argumentos
- Parâmetros nomeados
- Argumentos passados vs parâmetros definidos
- Argumentos padrão (default parameters)
- Rest parameters: `function(...args)`
- Destructuring de parâmetros

#### Retorno
- Instrução `return`
- Retorno implícito em arrow functions
- Múltiplos retornos

#### Escopo
- Global scope (window no navegador)
- Function scope (escopo da função)
- Block scope (escopo do bloco com let/const)
- Closure: funções acessando variáveis do escopo externo
- Variable shadowing

#### Callbacks
- Funções como argumentos
- Callbacks em eventos
- Nested callbacks (callback hell)

### Bloco 4: Estruturas de Dados

#### Arrays
- Criação: `[]`, `new Array()`
- Índices e tamanho
- Métodos de acesso: `length`, `[index]`
- Métodos de modificação:
  - `push()`: adiciona ao final
  - `pop()`: remove do final
  - `shift()`: remove do início
  - `unshift()`: adiciona no início
  - `splice()`: adiciona/remove no meio
- Métodos de iteração:
  - `forEach()`: função para cada elemento
  - `map()`: transforma elementos
  - `filter()`: filtra elementos
  - `reduce()`: reduz a um valor único
  - `find()`: encontra primeiro elemento
  - `some()`: verifica se alguns elementos atendem condição
  - `every()`: verifica se todos elementos atendem condição
- Métodos de busca: `indexOf()`, `includes()`, `findIndex()`
- Métodos de transformação: `join()`, `slice()`, `concat()`
- Métodos de ordenação: `sort()`, `reverse()`

#### Objetos
- Criação: `{}` (literal), `new Object()`
- Propriedades e valores
- Acesso: notação ponto vs bracket
- Modificação e exclusão
- Métodos de objetos
- `Object.keys()`, `Object.values()`, `Object.entries()`
- `Object.assign()`: cópia de propriedades
- Destructuring: `const { propriedade } = objeto`

#### JSON
- JSON vs JavaScript objects
- `JSON.stringify()`: objeto para string
- `JSON.parse()`: string para objeto

### Bloco 5: Interação com DOM

#### Seleção de Elementos
- `document.getElementById()`
- `document.querySelector()`
- `document.querySelectorAll()`
- `document.getElementsByClassName()`
- `document.getElementsByTagName()`
- NodeList vs HTMLCollection

#### Manipulação de Elementos
- `element.textContent`: texto sem HTML
- `element.innerHTML`: texto com HTML
- `element.innerText`: texto visível
- Criação: `document.createElement()`
- Adição: `appendChild()`, `insertBefore()`
- Remoção: `removeChild()`, `remove()`
- Substituição: `replaceChild()`

#### Atributos
- `getAttribute()`, `setAttribute()`
- `removeAttribute()`
- `classList`: manipulação de classes
  - `add()`, `remove()`, `toggle()`, `contains()`
- `style`: acesso inline a CSS

#### Eventos
- AddEventListener vs onclick
- Tipos de evento: click, submit, input, change, keypress, etc
- Event object e propagação
- `preventDefault()` e `stopPropagation()`

## 💻 Exercícios Práticos

### Lista de Exercícios
1. [Exercícios de Variáveis e Tipos](./exercicios/01-variaveis-tipos.md)
2. [Exercícios de Estruturas de Controle](./exercicios/02-estruturas-controle.md)
3. [Exercícios de Funções](./exercicios/03-funcoes.md)
4. [Exercícios de Arrays e Objetos](./exercicios/04-arrays-objetos.md)

## 🎯 Projetos do Mês

### Projeto 1: Calculadora Interativa (Semana 2)
**Objetivo**: Criar uma calculadora funcional com interface amigável

**Requisitos**:
- Interface com botões de números (0-9)
- Operações: +, -, *, /, %
- Botões: =, C (clear), Delete
- Display mostrando expressão e resultado
- Suportar decimais
- Prevenir erros (divisão por zero)

**Tecnologias**: HTML + CSS + JavaScript (Eventos, DOM)

[Ver especificação completa](./projetos/projeto-01-calculadora.md)

---

### Projeto 2: To-do List Interativa (Semana 4)
**Objetivo**: Criar um gerenciador de tarefas com persistência

**Requisitos**:
- Adicionar novas tarefas
- Marcar como concluída/incompleta
- Deletar tarefas
- Listar tarefas por status
- Salvar em LocalStorage
- Interface intuitiva e responsiva
- Contador de tarefas

**Tecnologias**: HTML + CSS + JavaScript (Arrays, DOM, LocalStorage)

[Ver especificação completa](./projetos/projeto-02-todo-list.md)

---

## 📖 Material de Apoio

### Leitura Obrigatória
- [JavaScript Basics - MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [JavaScript Guide - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide)
- [DOM Introduction - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model/Introduction)

### Vídeos Complementares
- JavaScript em 100 segundos
- Fundamentos de JavaScript - Curso completo
- DOM Manipulation - Tutorial prático

### Ferramentas Úteis
- [JSFiddle](https://jsfiddle.net/) - Editor online
- [CodePen](https://codepen.io/) - Comunidade de código
- [Console do Navegador](about:blank) - Teste seu código
- [QuokkaJS](https://quokkajs.com/) - Plugin de feedback rápido

## ✅ Checklist de Conclusão

Antes de avançar para o Mês 4, certifique-se de que você:

- [ ] Compreende variáveis, tipos e operadores
- [ ] Domina estruturas de controle (if/else, loops)
- [ ] Consegue criar e usar funções efetivamente
- [ ] Trabalha bem com arrays e objetos
- [ ] Manipula o DOM com confiança
- [ ] Trabalha com eventos e listeners
- [ ] Completou os 2 projetos do mês
- [ ] Código está limpo e bem comentado

## 🎓 Avaliação do Módulo

### Critérios
- **Participação**: Presença e engajamento nas aulas
- **Exercícios**: Resolução das listas propostas
- **Projetos**: Qualidade e funcionalidade dos 2 projetos
- **Código**: Legibilidade e boas práticas
- **Debugging**: Capacidade de encontrar e corrigir erros

### Entregáveis
1. Repositório GitHub com projetos
2. Links para aplicações publicadas
3. README.md explicando funcionalidades

---

## 📂 Estrutura de Arquivos

```
mes-03-javascript-fundamentos/
├── README.md (este arquivo)
├── aulas/
│   ├── aula-01-intro-javascript.md
│   ├── aula-02-variaveis-tipos.md
│   ├── aula-03-operadores.md
│   ├── aula-04-pratica-operadores.md
│   ├── aula-05-condicional.md
│   ├── aula-06-switch-case.md
│   ├── aula-07-loops.md
│   ├── aula-08-pratica-loops.md
│   ├── aula-09-funcoes.md
│   ├── aula-10-parametros-retorno.md
│   ├── aula-11-escopo.md
│   ├── aula-12-pratica-funcoes.md
│   ├── aula-13-arrays.md
│   ├── aula-14-objetos.md
│   ├── aula-15-dom-eventos.md
│   └── aula-16-apresentacoes.md
├── exercicios/
│   ├── 01-variaveis-tipos.md
│   ├── 02-estruturas-controle.md
│   ├── 03-funcoes.md
│   └── 04-arrays-objetos.md
├── projetos/
│   ├── projeto-01-calculadora.md
│   └── projeto-02-todo-list.md
└── recursos/
    ├── cheatsheet-javascript.md
    ├── cheatsheet-dom.md
    ├── console-tricks.md
    └── links-uteis.md
```

---

**Pronto para dominar JavaScript? Vamos para a [Aula 1](./aulas/aula-01-intro-javascript.md)!** 🚀
