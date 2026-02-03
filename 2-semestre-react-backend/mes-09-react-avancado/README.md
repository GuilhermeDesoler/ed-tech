# Mês 10: React Avançado

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 13-16
**Pré-requisito:** Conclusão dos Mês 7-8 e 9
**Status:** Módulo Avançado ⭐⭐⭐

## Visão Geral

Este é o último módulo de React puro, focando em TypeScript, testes automatizados, padrões de design avançados e preparação para produção. Os alunos aprenderão técnicas enterprise e best practices da indústria.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Integrar TypeScript com React de forma profissional
- Escrever testes unitários e de integração
- Implementar testes E2E
- Aplicar design patterns avançados
- Trabalhar com Server Components e Suspense
- Internacionalização (i18n)
- Acessibilidade (a11y)
- Criar libraries e componentes reutilizáveis
- Preparar aplicações para produção

## Estrutura de Aprendizado

### SEMANA 1: TypeScript com React

#### Aula 1: TypeScript Fundamentos para React (6h)
- Tipos básicos e avançados
- Interfaces vs Types
- Generics para componentes
- Utility types
- Type inference
- Type guards
- Configuração do tsconfig.json

**Projeto Prático:** Refatorar app simples para TypeScript

```typescript
interface Props {
  name: string;
  age: number;
  onSubmit: (data: FormData) => void;
}

function Component<T extends { id: string }>({ items }: { items: T[] }) {
  return <div>{items.map(item => item.id)}</div>;
}
```

#### Aula 2: Tipagem de Componentes React (6h)
- Tipagem de props
- Tipagem de state
- Tipagem de events
- useState com tipos
- useRef com tipos
- useCallback com tipos
- Extending HTMLElement properties

**Projeto Prático:** Biblioteca de componentes tipados

```typescript
type ButtonProps = React.ButtonHTMLAttributes<HTMLButtonElement> & {
  variant?: 'primary' | 'secondary';
  loading?: boolean;
};

const Button: React.FC<ButtonProps> = ({
  variant = 'primary',
  loading,
  ...rest
}) => (
  <button className={`btn-${variant}`} {...rest} />
);
```

#### Aula 3: Tipagem Avançada de Hooks (6h)
- Generic hooks
- Constrained generics
- Conditional types
- useCallback type safety
- useReducer type safety
- Custom hooks com tipos
- Inferência de tipos

**Projeto Prático:** Custom hooks tipados e reutilizáveis

```typescript
function useAsync<T, E = string>(
  asyncFunction: () => Promise<T>,
  immediate = true
): { status: 'idle' | 'pending' | 'success' | 'error'; data: T | null; error: E | null } {
  // implementação
}
```

#### Aula 4: TypeScript em Produção (6h)
- Strict mode (recomendado)
- Declaration files (.d.ts)
- Type-safe APIs
- Error boundaries com tipos
- Context com tipos
- Module augmentation
- Testing types

**Projeto Prático:** Publicar componente com tipos

### SEMANA 2: Testes Automatizados

#### Aula 5: Fundamentos de Testes (6h)
- Pirâmide de testes (unitário, integração, E2E)
- TDD (Test-Driven Development)
- Jest fundamentals
- Estrutura de testes (AAA pattern)
- Mocking
- Setup e teardown
- Coverage e metrics

**Projeto Prático:** Testes básicos de componentes

```javascript
describe('Button', () => {
  it('should render with correct text', () => {
    const { getByText } = render(<Button>Click</Button>);
    expect(getByText('Click')).toBeInTheDocument();
  });

  it('should call onClick when clicked', () => {
    const onClick = jest.fn();
    const { getByText } = render(<Button onClick={onClick}>Click</Button>);
    fireEvent.click(getByText('Click'));
    expect(onClick).toHaveBeenCalled();
  });
});
```

#### Aula 6: React Testing Library (6h)
- Testing de componentes React
- Queries (getBy, queryBy, findBy)
- User interactions
- Async testing
- Mocking modules
- Custom render function
- Best practices

**Projeto Prático:** Testes de componentes complexos

```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import userEvent from '@testing-library/user-event';

it('should update input value', async () => {
  const user = userEvent.setup();
  render(<Input />);

  const input = screen.getByPlaceholderText('Enter name');
  await user.type(input, 'John');

  expect(input).toHaveValue('John');
});
```

#### Aula 7: Testes de Hooks e Estado (6h)
- Renderização de hooks em testes
- @testing-library/react-hooks
- Testing custom hooks
- Testing contexts
- Testing async operations
- Mocking fetch/axios
- Testing error scenarios

**Projeto Prático:** Testes de custom hooks

```javascript
import { renderHook, act } from '@testing-library/react-hooks';
import useCounter from './useCounter';

it('should increment counter', () => {
  const { result } = renderHook(() => useCounter());

  act(() => {
    result.current.increment();
  });

  expect(result.current.count).toBe(1);
});
```

#### Aula 8: Testes E2E com Cypress/Playwright (6h)
- Setup de testes E2E
- Cypress vs Playwright
- Escrevendo testes E2E
- Interações de usuário
- Waiters e assertions
- Screenshots e videos
- CI/CD integration

**Projeto Prático:** Suite de testes E2E completa

```javascript
describe('E2E Tests', () => {
  it('should complete user flow', () => {
    cy.visit('http://localhost:3000');
    cy.get('input[type="text"]').type('Hello');
    cy.get('button').click();
    cy.get('.result').should('contain', 'Hello');
  });
});
```

### SEMANA 3: Padrões Avançados e Produção

#### Aula 9: Server Components e Streaming (6h)
- React Server Components (RSC)
- Streaming SSR
- Hydration
- Suspense em produção
- Edge cases
- Performance implications
- Migration strategies

**Projeto Prático:** App com Server Components

#### Aula 10: Internacionalização (i18n) (6h)
- Estratégias de i18n
- i18next library
- Namespacing
- Plural forms
- Date/Number formatting
- Language switching
- RTL support

**Projeto Prático:** App multilíngue com i18n

```javascript
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t, i18n } = useTranslation();

  return (
    <div>
      <p>{t('welcome.message')}</p>
      <button onClick={() => i18n.changeLanguage('pt')}>
        {t('language.pt')}
      </button>
    </div>
  );
}
```

#### Aula 11: Acessibilidade (a11y) (6h)
- WCAG guidelines
- ARIA attributes
- Semantic HTML
- Keyboard navigation
- Screen readers
- Testing accessibility
- Automated accessibility tests

**Projeto Prático:** Auditar e corrigir acessibilidade

```javascript
// Componente acessível
<button
  onClick={handleClick}
  aria-label="Close menu"
  aria-expanded={isOpen}
  aria-controls="menu"
>
  ✕
</button>
```

#### Aula 12: Design Systems e Component Libraries (6h)
- Estruturação de design system
- Component composition
- Storybook setup
- Documentation
- Versionamento semântico
- Publishing to npm
- Maintenance e releases

**Projeto Prático:** Criar e publicar design system

### SEMANA 4: Produção e Projeto Final

#### Aula 13: Segurança em React (4h)
- XSS prevention
- CSRF protection
- Secure cookie handling
- Environment variables
- API key management
- Input validation
- Output encoding

**Projeto Prático:** Implementar segurança em app

```javascript
// Sanitizar HTML user-generated
import DOMPurify from 'dompurify';

function SafeHTML({ html }) {
  return <div dangerouslySetInnerHTML={{ __html: DOMPurify.sanitize(html) }} />;
}
```

#### Aula 14: Monitoramento e Analytics (4h)
- Error tracking (Sentry)
- Performance monitoring
- User analytics
- Session recording
- Log aggregation
- Metrics and KPIs
- Dashboards

**Projeto Prático:** Adicionar monitoramento a app

#### Aula 15: Deployment Pipeline (4h)
- CI/CD com GitHub Actions
- Build optimization
- Environment management
- Blue-green deployment
- Rollback strategies
- Monitoring pós-deploy
- Documentation

**Projeto Prático:** Setup CI/CD completo

#### Aula 16: Projeto Capstone - Aplicação Enterprise (8h)
- TypeScript puro
- Testes E2E e unitários
- Acessibilidade completa
- Performance otimizada
- Segurança implementada
- Monitoramento ativo
- Deploy em produção

## Conteúdo Técnico Detalhado

### Tipagem Avançada

```typescript
// Constrained Generics
interface HasId {
  id: string;
}

function getProperty<T extends HasId, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

// Conditional Types
type IsString<T> = T extends string ? true : false;
type A = IsString<'hello'>; // true
type B = IsString<number>; // false

// Mapped Types
type Readonly<T> = {
  readonly [K in keyof T]: T[K];
};

// Utility Types in React
type ComponentProps<T extends React.ElementType> = React.ComponentProps<T>;
type FC<P = {}> = React.FunctionComponent<P>;
```

### Padrões de Teste

```typescript
// Arrange-Act-Assert Pattern
describe('UserForm', () => {
  it('should submit form with valid data', () => {
    // Arrange
    const handleSubmit = jest.fn();
    render(<UserForm onSubmit={handleSubmit} />);

    // Act
    fireEvent.change(screen.getByLabelText('Name'), { target: { value: 'John' } });
    fireEvent.click(screen.getByText('Submit'));

    // Assert
    expect(handleSubmit).toHaveBeenCalledWith({ name: 'John' });
  });
});

// User-centric Testing
it('should allow user to login', async () => {
  const user = userEvent.setup();
  render(<LoginPage />);

  await user.type(screen.getByLabelText('Email'), 'test@example.com');
  await user.type(screen.getByLabelText('Password'), 'password123');
  await user.click(screen.getByRole('button', { name: /login/i }));

  expect(screen.getByText('Welcome')).toBeInTheDocument();
});
```

## Projetos do Módulo

### Projeto 1: Component Library com TypeScript e Storybook
**Duração:** 24 horas
**Tecnologias:** TypeScript, React, Storybook, Jest
**Funcionalidades:**
- 10+ componentes reutilizáveis
- Documentação completa
- Testes para cada componente
- Storybook interativo
- TypeScript tipagem pura

**Critérios de Avaliação:**
- ✓ Tipos TypeScript robustos
- ✓ 80%+ de cobertura de testes
- ✓ Documentação clara
- ✓ Componentes acessíveis
- ✓ Publicado no npm

### Projeto 2: Aplicação Enterprise com Todas as Práticas
**Duração:** 40 horas
**Tecnologias:** TypeScript, React, Jest, Cypress, CI/CD
**Funcionalidades:**
- TypeScript end-to-end
- Testes unitários e E2E
- Acessibilidade (WCAG AA)
- Internacionalização
- Performance otimizada
- Error tracking
- Deploy com CI/CD

**Critérios de Avaliação:**
- ✓ 80%+ cobertura de testes
- ✓ TypeScript strict mode
- ✓ Acessibilidade validada
- ✓ Performance > 90 Lighthouse
- ✓ Deploy automatizado

### Projeto 3: Revisão e Aprofundamento
**Duração:** 8 horas

## Exercícios Práticos

### Semana 1
1. Converter app para TypeScript
2. Adicionar tipos complexos
3. Generic components
4. Type-safe hooks

### Semana 2
1. Escrever testes unitários (50 testes)
2. Testes de integração
3. Testes E2E (10 casos)
4. Cobertura 80%+

### Semana 3
1. Implementar i18n
2. Audit e fix acessibilidade
3. Setup design system
4. Publicar npm package

### Semana 4
1. Implementar segurança
2. Setup CI/CD
3. Monitoring com Sentry
4. Projeto final

## Stack Tecnológico

- **TypeScript 5+**
- **React 18+**
- **Jest** (testes unitários)
- **React Testing Library**
- **Cypress/Playwright** (E2E)
- **Storybook** (documentação)
- **i18next** (internacionalização)
- **Sentry** (monitoramento)
- **GitHub Actions** (CI/CD)

## Requisitos de Conhecimento Prévio

- Conclusão dos Mês 7-8 e 9
- React intermediário profundo
- JavaScript avançado
- Conceitos de testes
- Git e GitHub

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 13 | 24 | TypeScript | Exercícios |
| 14 | 24 | Testes | Projeto 1 |
| 15 | 24 | Padrões Avançados | Projeto 2 |
| 16 | 24 | Produção | Projeto Final |

## Recursos de Aprendizado

### TypeScript
- [TypeScript Handbook](https://www.typescriptlang.org/docs)
- [TypeScript for React](https://www.typescriptlang.org/docs/handbook/react.html)
- React TypeScript Cheatsheet

### Testes
- [Jest Documentation](https://jestjs.io)
- [React Testing Library Docs](https://testing-library.com/react)
- [Cypress Documentation](https://docs.cypress.io)

### Produção
- [Security in React](https://snyk.io/blog/react-security/)
- [Web Accessibility](https://www.w3.org/WAI)
- [i18next Guide](https://www.i18next.com)

## Avaliação e Aprovação

### Critérios de Aprovação
- Frequência 75%+
- Projetos nota 7.0+
- 80%+ cobertura de testes
- TypeScript strict mode
- Acessibilidade validada

### Cálculo de Notas
- Projeto 1 (Component Library): 30%
- Projeto 2 (Enterprise App): 40%
- Exercícios e Qualidade: 30%

## Próximas Etapas

Após completar este módulo:
- **Mês 11:** Node.js, Express e Backend
- Pronto para trabalhar como React Developer profissional

## Notas Importantes

- TypeScript strict mode é obrigatório
- Testes não são opcional - são essencial
- Acessibilidade não é feature - é requirement
- Performance deve ser medida, não assumida
- Code review é parte do processo

## Dúvidas Frequentes

**P: Quanto tempo leva para aprender TypeScript?**
R: Conceitos básicos em 2 semanas. Domínio total após 2 meses de prática.

**P: Quantos testes preciso?**
R: Mínimo 80% cobertura. Mas qualidade > quantidade.

**P: Vale a pena TypeScript?**
R: Sim. Reduz bugs, melhora documentação, facilita refatoração.

**P: Como conseguir 90+ no Lighthouse?**
R: Otimizar imagens, code splitting, minificação, caching.

## Contato e Suporte

- Chat: Comunidade Discord
- Mentorias: 1-1 semanal
- Office hours: 3x por semana

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Avançado/Enterprise
