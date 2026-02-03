# Mês 9: React Intermediário

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 9-12
**Pré-requisito:** Conclusão completa do Mês 7-8
**Status:** Módulo Importante ⭐⭐

## Visão Geral

Este módulo aprofunda o conhecimento em React, focando em gerenciamento de estado complexo, otimização de performance e padrões avançados. Os alunos aprenderão técnicas essenciais para construir aplicações escaláveis e de alta performance.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Dominar hooks avançados (useReducer, useContext, useRef, useCallback, useMemo)
- Implementar gerenciamento de estado com Context API
- Otimizar performance de aplicações React
- Criar custom hooks reutilizáveis
- Trabalhar com refs e DOM imperativo
- Compreender e evitar memory leaks
- Debugar performance issues
- Implementar padrões avançados de composição

## Estrutura de Aprendizado

### SEMANA 1: Hooks Avançados - Parte 1

#### Aula 1: useReducer e Máquinas de Estado (6h)
- Quando useReducer é melhor que useState
- Estrutura reducer (state, action)
- Padrão reducer puro (Pure Functions)
- Dispatch de ações complexas
- Máquinas de estado finitas
- Debuggabilidade e logging
- Comparação com Redux (preview)

**Projeto Prático:** Máquina de estado para formulários

```javascript
const initialState = { count: 0, loading: false };
const reducer = (state, action) => {
  switch(action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 };
    case 'SET_LOADING':
      return { ...state, loading: action.payload };
    default:
      return state;
  }
};
```

#### Aula 2: useContext - State Global (6h)
- Problema do Prop Drilling
- Context API como solução
- createContext e Provider
- useContext para consumir contexto
- Múltiplos contextos em um app
- Performance com Context (quando renderiza)
- Context vs Redux vs outras soluções

**Projeto Prático:** Sistema de temas com Context

```javascript
const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function useTheme() {
  return useContext(ThemeContext);
}
```

#### Aula 3: useRef - Acesso Direto ao DOM (6h)
- Quando precisamos de refs
- useRef para valores persistentes
- Refs vs Estado
- Acessar elementos do DOM
- Integração com bibliotecas terceiras
- Refs em componentes customizados
- Evitar abuso de refs

**Projeto Prático:** Focus management e timers

```javascript
function TextInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current?.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus</button>
    </>
  );
}
```

#### Aula 4: Combinando Hooks (6h)
- useReducer + useContext para estado global
- Custom hooks que combinam múltiplos hooks
- Organização de lógica complexa
- Padrão Compound Components
- Composição vs Herança
- Reutilização de lógica

**Projeto Prático:** App com estado global complexo

### SEMANA 2: Performance e Otimização

#### Aula 5: useCallback e Memoização de Funções (6h)
- Por que funções são recriadas a cada render
- useCallback para memorizar callbacks
- Dependency arrays em callbacks
- Passar callbacks para componentes filhos
- Evitar sobre-otimização
- Measuring performance improvements
- Profiler do React

**Projeto Prático:** Otimizar lista com callbacks

```javascript
const handleClick = useCallback((id) => {
  console.log('Item:', id);
}, []);

// Componentes filhos que recebem esse callback
// só serão renderizados novamente se handleClick mudar
```

#### Aula 6: useMemo e Cálculos Custosos (6h)
- Identificar computações pesadas
- useMemo para memorizar valores
- Quando usar useMemo
- Casos de uso reais
- Medindo impacto de performance
- Evitar anti-patterns
- useCallback internamente usa useMemo

**Projeto Prático:** Dashboard com gráficos pesados

```javascript
const expensiveValue = useMemo(() => {
  return complexCalculation(data);
}, [data]);
```

#### Aula 7: React.memo e Memoização de Componentes (6h)
- Quando componentes re-renderizam desnecessariamente
- React.memo para componentes puros
- Shallow comparison vs Deep comparison
- custom comparator
- Combining React.memo with useCallback
- Performance monitoring
- Pitfalls e quando não usar

**Projeto Prático:** Componentes otimizados

```javascript
const MemoizedComponent = React.memo(function MyComponent(props) {
  // Só renderiza se props mudarem
  return <div>{props.name}</div>;
});
```

#### Aula 8: Code Splitting e Lazy Loading (6h)
- Importação dinâmica com import()
- React.lazy para componentes
- Suspense para fallback
- Route-based code splitting
- Component-level code splitting
- Preloading strategies
- Measuring bundle size

**Projeto Prático:** App com routes lazy loaded

```javascript
const HeavyComponent = React.lazy(() => import('./Heavy'));

<Suspense fallback={<Loading />}>
  <HeavyComponent />
</Suspense>
```

### SEMANA 3: State Management Avançado

#### Aula 9: Custom Hooks - Criando Hooks Reutilizáveis (6h)
- Convenção de naming (use*)
- Extrair lógica de componentes
- Hooks que retornam múltiplos valores
- Hooks que combinam outros hooks
- Async operations em custom hooks
- Testes de custom hooks
- Publicar como pacote npm

**Projeto Prático:** Biblioteca de custom hooks

```javascript
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then(r => r.json())
      .then(setData)
      .catch(setError)
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}
```

#### Aula 10: Padrões de Composição (6h)
- Render Props pattern
- Higher-Order Components (HOC)
- Compound Components pattern
- Quando usar cada padrão
- Comparação com hooks
- Refatorar componentes antigos
- Best practices

**Projeto Prático:** Refatorar componentes com padrões

```javascript
// Compound Components
<Form>
  <Form.Field>
    <Form.Input />
    <Form.Error />
  </Form.Field>
</Form>
```

#### Aula 11: Context API em Produção (6h)
- Estruturar contextos em aplicações grandes
- Múltiplos providers
- Evitar re-renders com Context
- Context + useReducer para estado global
- Testing contextos
- Debugging Context issues
- Alternativas (Redux, Zustand, Recoil)

**Projeto Prático:** App com múltiplos contextos

#### Aula 12: Performance Debugging (6h)
- React DevTools Profiler
- Identificar componentes lentos
- why-did-you-render library
- Measuring render times
- Memory leaks e como evitar
- Profiling em produção
- Performance budget

**Projeto Prático:** Debugar e otimizar aplicação lenta

### SEMANA 4: Integração e Projeto

#### Aula 13: Tratamento de Erros Avançado (4h)
- Error Boundaries
- Fallback UI
- Error logging
- Recovery strategies
- Erros síncronos vs assíncronos
- Erros em event handlers
- Erros em promises

**Projeto Prático:** Implementar error boundaries

```javascript
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      return <div>Algo deu errado!</div>;
    }
    return this.props.children;
  }
}
```

#### Aula 14: Dados em Escala (4h)
- Virtualização de listas grandes
- Paginação vs infinite scroll
- Normalizando estado
- Cacheing estratégias
- Quando considerar Redux/MobX
- Bibliotecas de data fetching (React Query, SWR)

**Projeto Prático:** Lista virtualizada com dados grandes

#### Aula 15: Padrões Avançados (4h)
- Dependency injection
- Inversion of Control
- Plugin architecture
- Factory patterns
- Strategy patterns
- Observer patterns

**Projeto Prático:** Implementar padrões de design

#### Aula 16: Projeto Integrador - Dashboard Analytics (8h)
- Arquitetura com múltiplos contextos
- Custom hooks para data fetching
- Otimização de performance
- Error handling robusto
- UI responsiva e moderna

## Conteúdo Técnico Detalhado

### Custom Hooks Essenciais

```javascript
// useAsync
function useAsync(asyncFunction, immediate = true) {
  const [status, setStatus] = useState('idle');
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    if (!immediate) return;

    asyncFunction()
      .then(d => { setData(d); setStatus('success'); })
      .catch(e => { setError(e); setStatus('error'); });
  }, []);

  return { status, data, error };
}

// useLocalStorage
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(error);
      return initialValue;
    }
  });

  const setValue = useCallback((value) => {
    try {
      const valueToStore = typeof value === 'function' ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error(error);
    }
  }, [storedValue]);

  return [storedValue, setValue];
}

// useDebounce
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(handler);
  }, [value, delay]);

  return debouncedValue;
}
```

## Projetos do Módulo

### Projeto 1: Dashboard com Estado Global
**Duração:** 24 horas
**Tecnologias:** React, Context API, useReducer
**Funcionalidades:**
- Dashboard com múltiplos widgets
- Estado compartilhado globalmente
- Filtros e buscas
- Tema claro/escuro com Context
- Performance otimizada

**Critérios de Avaliação:**
- ✓ Context adequadamente estruturado
- ✓ Sem prop drilling
- ✓ Performance mensurável
- ✓ Code bem documentado
- ✓ Handles de erro robustos

### Projeto 2: Aplicação Complexa Otimizada
**Duração:** 32 horas
**Tecnologias:** React, Custom Hooks, Performance Optimization
**Funcionalidades:**
- Múltiplos custom hooks
- Lazy loading de componentes
- Memoização estratégica
- List virtualization
- Error boundaries
- Profiling e otimizações

**Critérios de Avaliação:**
- ✓ Custom hooks bem estruturados
- ✓ Performance mensuravelmente melhorada
- ✓ Code splitting implementado
- ✓ Sem memory leaks
- ✓ Testes básicos inclusos

### Projeto 3: Revisor de Conceitos
**Duração:** 8 horas
**Tipo:** Pequeno app que integra tudo aprendido

## Exercícios Práticos

### Semana 1
1. Refatorar componente com useState para useReducer
2. Implementar Context para tema
3. Criar component com ref
4. Combinar Context + useReducer

### Semana 2
1. Otimizar lista com useCallback
2. Usar useMemo para cálculos
3. Memoizar componente filho
4. Implementar code splitting

### Semana 3
1. Criar 5 custom hooks úteis
2. Refatorar com Compound Components
3. Estruturar múltiplos contextos
4. Debugar performance com Profiler

### Semana 4
1. Implementar Error Boundary
2. Virtualizar lista grande
3. Implementar padrão de design
4. Projeto integrador

## Stack Tecnológico

- React 18+ com Hooks
- React DevTools
- Create React App / Vite
- TypeScript (opcional, recomendado)
- Tailwind CSS
- Jest e React Testing Library (introdução)

## Requisitos de Conhecimento Prévio

- Conclusão completa do Mês 7-8
- Domínio de hooks básicos (useState, useEffect)
- Entendimento profundo de JavaScript ES6+
- Conceitos de closure e scope

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 9 | 24 | useReducer, useContext | Exercícios |
| 10 | 24 | useCallback, useMemo, Memoização | Projeto 1 |
| 11 | 24 | Custom Hooks, Padrões | Projeto 2 |
| 12 | 24 | Performance, Debugging | Projeto Final |

## Recursos de Aprendizado

### Documentação
- [React Hooks Reference](https://react.dev/reference/react)
- [Context API Guide](https://react.dev/learn/passing-data-deeply-with-context)
- [React Performance](https://react.dev/learn/render-and-commit)

### Ferramentas
- React DevTools Profiler
- Chrome DevTools Performance
- why-did-you-render library

### Conteúdo Recomendado
- React Advanced Patterns Course
- Kent C. Dodds - Epic React
- JavaScript.info - Advanced Topics

## Avaliação e Aprovação

### Critérios de Aprovação
- Frequência mínima de 75%
- Participação ativa
- Projetos com nota mínima 7.0
- Código otimizado e bem documentado

### Cálculo de Notas
- Exercícios: 20%
- Projeto 1: 30%
- Projeto 2: 30%
- Performance Improvements: 20%

## Próximas Etapas

Após completar este módulo, o aluno prosseguirá para:
- **Mês 10:** React Avançado (TypeScript, Testes, Patterns)

## Notas Importantes

- Não otimize prematuramente - meça antes
- Nem todo contexto precisa de useReducer
- Refs não devem ser usados para tudo
- Performance é um processo iterativo
- Sempre profile sua aplicação antes de otimizar

## Dúvidas Frequentes

**P: Devo usar Context para tudo?**
R: Não. Use para dados realmente globais. Para muito conteúdo, considere Redux/Zustand.

**P: useCallback sempre melhora performance?**
R: Não. Às vezes piora. Use após medir com Profiler.

**P: Qual a diferença entre useMemo e React.memo?**
R: useMemo memoriza valores, React.memo memoriza componentes.

**P: Quando usar useRef?**
R: Para valores que não causam re-render. Refs devem ser evitadas quando possível.

## Contato e Suporte

- Chat de dúvidas: Comunidade Discord
- Mentorias: Agendar via plataforma
- Office hours: 2x por semana

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Intermediário
