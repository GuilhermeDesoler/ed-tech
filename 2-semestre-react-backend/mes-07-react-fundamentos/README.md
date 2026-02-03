# Mês 7-8: React Fundamentos

**Carga Horária:** 192 horas (4 semanas × 2 meses)
**Período:** Semanas 1-8
**Status:** Módulo Essencial ⭐⭐⭐

## Visão Geral

Este é o módulo introdutório mais crítico do semestre. Os alunos aprenderão os conceitos fundamentais do React, passando desde o básico (JSX, componentes, props) até a criação de aplicações interativas com estado e efeitos.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Entender o paradigma da programação reativa
- Criar e estruturar componentes React eficientemente
- Trabalhar com props e comunicação entre componentes
- Gerenciar estado local com useState
- Compreender efeitos colaterais com useEffect
- Criar listas dinâmicas e formulários interativos
- Debugar aplicações React efetivamente
- Implementar boas práticas de organização de código

## Estrutura de Aprendizado

### SEMANA 1: Introdução ao React

#### Aula 1: Filosofia e Conceitos Fundamentais (4h)
- O que é React e por que usar
- Componentes como unidade de construção
- Virtual DOM e reconciliação
- Estrutura de um projeto React
- Vantagens e desvantagens
- Comparação com frameworks concorrentes

**Projeto Prático:** Setup de ambiente com Create React App e Vite

#### Aula 2: JSX - Sintaxe Essencial (4h)
- O que é JSX e como funciona
- Transpilação com Babel
- Expressões em JSX
- Condicionalidades ({condition && <div />})
- Loops e renderização de listas
- ClassName e dados customizados
- Limitações de JSX

**Projeto Prático:** Criar componentes simples em JSX

#### Aula 3: Componentes Funcionais e Props (6h)
- Componentes como funções JavaScript
- Props: passando dados ao componentes
- Props.children
- Desestruturação de props
- Validação de tipos (PropTypes)
- Props default
- Componentes puros vs impuros

**Projeto Prático:** Sistema de componentes reutilizáveis

#### Aula 4: Renderização Condicional e Listas (4h)
- Operador ternário
- Operador lógico (&&, ||)
- Componentes condicionais
- Renderização de arrays (map)
- Keys em listas (importance e best practices)
- Evitar índices como keys
- Filtragem e transformação de dados

**Projeto Prático:** Galeria de produtos com filtros

### SEMANA 2: Estado e Interatividade

#### Aula 5: Hook useState - Conceitos Fundamentais (6h)
- O que é um Hook em React
- useState: sintaxe e uso
- Estado como variável reativa
- Atualização de estado (setState)
- Batching de atualizações
- Estado anterior (função vs valor)
- Múltiplos states em um componente

**Projeto Prático:** Contador, Toggle, Lista de Tarefas

#### Aula 6: Formulários e Input Controlado (6h)
- Elementos de formulário em React
- Inputs controlados vs não-controlados
- onChange e gerenciamento de estado
- Múltiplos inputs (otimização)
- Validação de formulários básica
- Submit e preventDefault
- Resete de formulários

**Projeto Prático:** Formulário de cadastro com validação

#### Aula 7: Eventos e Manipulação do DOM (6h)
- Event handling em React
- onClick, onChange, onSubmit, etc.
- Event object e stopPropagation
- Event delegation
- Binding de métodos (arrow functions)
- Passando argumentos para handlers
- Sintaxe de eventos camelCase

**Projeto Prático:** Aplicação interativa com múltiplos eventos

#### Aula 8: Lifting State Up (4h)
- Quando elevar o estado
- Padrão parent-child communication
- Callbacks e comunicação reversa
- Estado compartilhado entre componentes
- Prop drilling awareness
- Estrutura de pastas para escalabilidade

**Projeto Prático:** Aplicação com componentes que compartilham estado

### SEMANA 3: Efeitos e Ciclo de Vida

#### Aula 9: Hook useEffect - Parte 1 (6h)
- O que é um efeito colateral
- useEffect: sintaxe e uso
- Dependency array
- Executar código após renderização
- Cleanup de efeitos
- Evitar memory leaks
- Quando usar useEffect

**Projeto Prático:** Requisições HTTP simples com fetch

#### Aula 10: Hook useEffect - Parte 2 (6h)
- useEffect sem dependency (executa sempre)
- useEffect com [] (executa uma vez)
- useEffect com deps (executa quando deps mudam)
- Múltiplos useEffects
- Ordenação e dependências
- Otimização de performance
- Debugging de effects

**Projeto Prático:** Aplicação com múltiplos efeitos

#### Aula 11: Integração com APIs (6h)
- Requisições HTTP com fetch
- Promises e async/await
- Tratamento de erros (try/catch)
- Estados de carregamento (loading, error, success)
- Cancelamento de requisições (AbortController)
- Race conditions e ordem de requisições
- Headers e autenticação básica

**Projeto Prático:** App que consome API pública

#### Aula 12: Gerenciamento de Complexidade (4h)
- Quando o estado fica complexo
- useReducer como alternativa
- Introdução ao Context (preview)
- Evitar re-renders desnecessários
- React DevTools
- Debugging avançado

**Projeto Prático:** Todo App com funcionalidades avançadas

### SEMANA 4: Prática Integrada e Revisão

#### Aula 13: Padrões e Boas Práticas (4h)
- Naming conventions
- Organização de pastas
- Estrutura de componentes
- Componentes aninhados vs externos
- Lógica de negócio vs apresentação
- DRY (Don't Repeat Yourself)
- SOLID principles em React

**Projeto Prático:** Refatoração de código anterior

#### Aula 14: Performance em React (4h)
- React.memo para memoização de componentes
- useMemo para valores custosos
- useCallback para funções estáveis
- Evitar re-renders
- Análise com React DevTools Profiler
- Lazy Loading (preview)
- Code Splitting (preview)

**Projeto Prático:** Aplicação com otimizações

#### Aula 15: Estilização em React (6h)
- Inline styles
- CSS Modules
- Tailwind CSS (introdução)
- Styled-components (preview)
- ClassNames dinâmicas
- Temas e variáveis CSS
- Responsividade

**Projeto Prático:** Interface completa estilizada

#### Aula 16: Projeto Integrador (8h)
- Planejamento e arquitetura
- Implementação completa
- Debugging e testes manuais
- Deploy local

**Projeto Prático:** Blog interativo completo

## Conteúdo Detalhado

### Conceitos-Chave

```javascript
// 1. Componentes Funcionais
function Welcome() {
  return <h1>Bem-vindo ao React</h1>;
}

// 2. Props
function Greeting({ name, age }) {
  return <p>Olá {name}, você tem {age} anos</p>;
}

// 3. Estado
function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Contagem: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Incrementar
      </button>
    </div>
  );
}

// 4. Efeitos
function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data && <p>{data.message}</p>}</div>;
}

// 5. Lifting State
function Parent() {
  const [value, setValue] = useState('');

  return (
    <>
      <Child value={value} onChange={setValue} />
      <Display value={value} />
    </>
  );
}
```

## Projetos do Módulo

### Projeto 1: Aplicação Todo List (Básico)
**Duração:** 16 horas
**Tecnologias:** React, CSS básico
**Funcionalidades:**
- Adicionar tarefas
- Marcar como concluída
- Deletar tarefas
- Listar tarefas dinamicamente
- Persistência em localStorage

**Critérios de Avaliação:**
- ✓ Componentes bem estruturados
- ✓ Estado gerenciado adequadamente
- ✓ Código limpo e legível
- ✓ Sem console.errors
- ✓ Interface responsiva

### Projeto 2: Blog Interativo
**Duração:** 32 horas
**Tecnologias:** React, Tailwind CSS, JSON Server
**Funcionalidades:**
- Listagem de artigos com paginação
- Página de detalhe do artigo
- Busca e filtros de categorias
- Comentários em artigos
- Interface responsiva e moderna
- Integração com API mockada

**Critérios de Avaliação:**
- ✓ Arquitetura escalável
- ✓ Props bem tipadas
- ✓ Efeitos otimizados
- ✓ Performance adequada
- ✓ UX/UI profissional
- ✓ Git commits bem documentados

### Projeto 3: Revisor Final
**Duração:** 8 horas
**Tecnologias:** React, Conceitos aprendidos
**Funcionalidades:**
- Pequeno app que revisa todos os conceitos
- Avaliação prática

## Exercícios Práticos

### Semana 1
1. Hello World em React
2. Criar componente reutilizável
3. Renderizar lista dinâmica
4. Componentizar página existente

### Semana 2
1. Contador com useState
2. Formulário controlado
3. Todo list com adicionar/remover
4. Event handling avançado

### Semana 3
1. Fetching de dados com useEffect
2. Loading states
3. Error handling
4. Cleanup de efeitos

### Semana 4
1. Otimizar componente lento
2. Refatorar código antigo
3. Implementar tema claro/escuro
4. Integração API real

## Stack Tecnológico

- **Node.js 18+**
- **npm ou yarn**
- **Create React App** ou **Vite**
- **React 18+**
- **Tailwind CSS** (opcional, básico)
- **VS Code** (editor recomendado)

## Ferramentas de Desenvolvimento

- React Developer Tools (Chrome/Firefox)
- Prettier (formatação)
- ESLint (linting)
- JSON Server (mock API)
- Insomnia (testes de requisições)

## Requisitos de Conhecimento Prévio

- HTML5 intermediário
- CSS3 intermediário
- JavaScript ES6+ completo
- Terminal/CLI básico
- Git básico

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 1-2 | 48 | JSX, Props, Estado | Exercícios |
| 3-4 | 48 | UseEffect, APIs | Projeto 1 |
| 5-6 | 48 | Otimização, Estilo | Projeto 2 |
| 7-8 | 48 | Integração, Revisão | Projeto Final |

## Recursos de Aprendizado

### Documentação
- [React Official Docs](https://react.dev)
- [React Hooks API Reference](https://react.dev/reference/react)
- [MDN - React Basics](https://developer.mozilla.org/pt-BR/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started)

### Vídeos Recomendados
- Traversy Media - React Crash Course
- The Net Ninja - React Tutorial
- Tech With Tim - React Basics

### Artigos
- React Docs Deep Dive
- Understanding Hooks
- React Patterns

### Praticar Online
- CodePen
- Stackblitz
- Codesandbox

## Avaliação e Aprovação

### Critérios de Aprovação
- Frequência mínima de 75%
- Participação em aulas
- Projetos com nota mínima 7.0
- Código seguindo padrões de qualidade

### Cálculo de Notas
- Exercícios: 20%
- Projeto 1: 30%
- Projeto 2: 30%
- Participação: 20%

### Feedback e Revisão
- Code review detalhado em cada projeto
- Mentorias individuais conforme necessário
- Oportunidade de resubmissão com melhorias

## Próximas Etapas

Após completar este módulo, o aluno prosseguirá para:
- **Mês 9:** React Intermediário (Hooks avançados, Context API)
- **Mês 10:** React Avançado (TypeScript, Testes, Otimizações)

## Notas Importantes

- Não pule etapas - cada conceito é fundação para o próximo
- Pratique TODOS os exercícios, não apenas veja resolvidos
- Use React DevTools para debugar
- Leia a documentação oficial
- Faça perguntas - não há perguntas bobas
- Refatore seu código constantemente

## Dúvidas Frequentes

**P: Preciso memorizar a API do React?**
R: Não, você vai consultar a documentação sempre. O importante é entender conceitos.

**P: Qual a melhor forma de organizar pastas?**
R: Não há um padrão único. Comece simples e escale conforme necessário.

**P: Quando usar State vs Props?**
R: Props para passar dados, State para dados que mudam. Props é imutável, State é mutável.

**P: UseEffect com [] executa sempre?**
R: Não, executa uma vez na montagem. Sem [] executa sempre após renderização.

## Contato e Suporte

- Chat de dúvidas: Comunidade Discord
- Mentorias: Agendar via plataforma
- Email: suporte@programa.edu.br

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Iniciante a Intermediário
