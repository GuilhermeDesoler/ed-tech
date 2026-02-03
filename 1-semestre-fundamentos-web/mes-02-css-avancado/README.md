# Mês 2 - CSS Avançado e Responsividade

> **Duração**: 4 semanas | **Carga Horária**: 32h | **Nível**: Intermediário

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:

- ✅ Criar layouts responsivos com Flexbox
- ✅ Dominar Grid CSS para layouts avançados
- ✅ Aplicar animações e transições
- ✅ Trabalhar com variáveis CSS e pré-processadores
- ✅ Otimizar CSS para performance
- ✅ Implementar temas e design systems

## 📅 Cronograma Semanal

### Semana 1: Flexbox e Layout Responsivo
- **Aula 1**: Introdução ao Flexbox - flex container e itens
- **Aula 2**: Propriedades do Flexbox - justify-content, align-items, flex-direction
- **Aula 3**: Cases práticos com Flexbox - menus, cards, galeria
- **Aula 4**: Prática - Recriando layouts com Flexbox

### Semana 2: CSS Grid
- **Aula 5**: Introdução ao CSS Grid - grid container e áreas
- **Aula 6**: Grid Template - linhas, colunas e gaps
- **Aula 7**: Grid avançado - auto-fit, auto-fill, subgrid
- **Aula 8**: Prática - Layouts complexos com Grid

### Semana 3: Animações, Transições e Responsividade
- **Aula 9**: Transições CSS - timing functions e delays
- **Aula 10**: Animações CSS - @keyframes e propriedades
- **Aula 11**: Media Queries - Mobile first approach
- **Aula 12**: Prática - Animações e design responsivo

### Semana 4: Variáveis, Preprocessadores e Projeto
- **Aula 13**: CSS Variables (Custom Properties)
- **Aula 14**: Introdução a SASS/SCSS - variáveis, mixins, nesting
- **Aula 15**: Design Systems - padrões reutilizáveis
- **Aula 16**: Apresentação do projeto final

## 📚 Conteúdo Detalhado

### Bloco 1: Flexbox

#### Fundamentos
- O que é Flexbox e quando usar
- Flex container vs Flex items
- Um eixo vs dois eixos (main axis, cross axis)
- Diferenças entre Flexbox e Grid

#### Propriedades do Container
- `display: flex`
- `flex-direction`: row, column, row-reverse, column-reverse
- `justify-content`: flex-start, center, space-between, space-around, space-evenly
- `align-items`: stretch, flex-start, center, flex-end, baseline
- `align-content`: (similares ao justify-content, para múltiplas linhas)
- `flex-wrap`: nowrap, wrap, wrap-reverse
- `gap`: espaçamento entre itens

#### Propriedades dos Itens
- `flex-grow`: crescimento relativo
- `flex-shrink`: encolhimento relativo
- `flex-basis`: tamanho base
- `flex`: shorthand (grow, shrink, basis)
- `align-self`: override do align-items
- `order`: reordenação visual

#### Cases Práticos
- Navegação horizontal e vertical
- Cards em grid
- Galeria responsiva
- Footers sticky
- Sidebars

### Bloco 2: CSS Grid

#### Conceitos Fundamentais
- O que é CSS Grid e quando usar
- Grid container vs Grid items
- Grid lines, tracks, cells e areas
- Grid template areas

#### Criando Grids
- `display: grid`
- `grid-template-columns`: unidades fr, repeat(), minmax()
- `grid-template-rows`: similares às colunas
- `grid-template`: shorthand
- `grid-auto-rows` e `grid-auto-columns`: implícito
- `grid-auto-flow`: packing algoritmo

#### Posicionamento
- `grid-column`: start / end
- `grid-row`: start / end
- `grid-area`: shorthand
- `place-items` e `place-content`
- Nomeação de linhas e áreas

#### Grid Avançado
- `auto-fit` e `auto-fill`: responsividade automática
- `minmax()`: tamanhos flexíveis
- `subgrid`: nesting de grids (CSS Grid Level 2)

#### Layouts Complexos
- Dashboards
- Portfólios
- Landing pages
- Admin panels

### Bloco 3: Animações e Transições

#### Transições CSS
- `transition-property`: quais propriedades animar
- `transition-duration`: quanto tempo
- `transition-timing-function`: como animar (ease, ease-in, ease-out, ease-in-out, linear, cubic-bezier)
- `transition-delay`: esperar antes de começar
- `transition`: shorthand
- Propriedades animáveis vs não-animáveis

#### Animações CSS
- `@keyframes`: definindo animações
- `animation-name`: qual animação usar
- `animation-duration`: duração
- `animation-timing-function`: timing
- `animation-delay`: delay
- `animation-iteration-count`: quantas vezes (number, infinite)
- `animation-direction`: normal, reverse, alternate
- `animation-fill-mode`: forwards, backwards, both
- `animation`: shorthand
- Múltiplas animações

#### Transforms
- `transform: translate()`: movimento
- `transform: rotate()`: rotação
- `transform: scale()`: escala
- `transform: skew()`: deformação
- `transform: perspective()`: perspectiva 3D
- Combinando transforms
- `transform-origin`: ponto de origem

#### Performance
- Usar `transform` e `opacity` para melhor performance
- Evitar animar propriedades caras (width, height, position)
- Hardware acceleration com `will-change`

### Bloco 4: Responsividade e Design Adaptativo

#### Media Queries
- Sintaxe: `@media (condition) { ... }`
- Condições: min-width, max-width, orientation, etc
- Mobile first approach
- Desktop first approach (legacy)

#### Breakpoints Comuns
- Mobile: até 480px
- Tablet: 481px - 768px
- Desktop: 769px - 1024px
- Large desktop: acima de 1025px

#### Técnicas Responsivas
- Fluid typography com `clamp()`
- Imagens responsivas
- `object-fit` para proporção de imagens
- Viewport meta tag
- CSS containers queries (novo)

#### Testes de Responsividade
- DevTools responsive mode
- Testes em dispositivos reais
- Ferramentas: Responsively App, BrowserStack

### Bloco 5: Variáveis CSS e Preprocessadores

#### CSS Variables (Custom Properties)
- Definindo variáveis: `--cor-primaria: #3498db`
- Usando variáveis: `color: var(--cor-primaria)`
- Fallbacks: `var(--cor-primaria, blue)`
- Escopo: global vs local
- Temas com variáveis

#### SASS/SCSS Introdução
- Variáveis: `$cor-primaria: #3498db`
- Nesting: hierarquia de seletores
- Mixins: reutilização de blocos
- Functions: cálculos
- Operações: matemática em CSS

#### Design Systems
- Cores: paletas e semântica
- Tipografia: escalas, fontes, pesos
- Espaçamento: margin, padding, gaps
- Componentes: buttons, cards, forms
- Documentação: guias de estilo

## 💻 Exercícios Práticos

### Lista de Exercícios
1. [Exercícios de Flexbox](./exercicios/01-flexbox.md)
2. [Exercícios de Grid](./exercicios/02-grid.md)
3. [Exercícios de Animações](./exercicios/03-animacoes.md)
4. [Exercícios de Responsividade](./exercicios/04-responsividade.md)

## 🎯 Projetos do Mês

### Projeto 1: Layout Responsivo com Flexbox (Semana 2)
**Objetivo**: Criar um site completo usando apenas Flexbox

**Requisitos**:
- Header com navegação responsiva
- Hero section
- Seção de serviços em grid flex
- Blog/posts em cards
- Footer multi-coluna
- Totalmente responsivo

**Tecnologias**: HTML + CSS (Flexbox)

[Ver especificação completa](./projetos/projeto-01-layout-flexbox.md)

---

### Projeto 2: Dashboard com Grid CSS (Semana 4)
**Objetivo**: Criar um dashboard interativo com CSS Grid

**Requisitos**:
- Layout principal com sidebar
- Grid de widgets/cards
- Gráficos e estatísticas
- Menu responsivo
- Animações suaves
- Tema claro/escuro com CSS variables

**Tecnologias**: HTML + CSS (Grid, Animações, Variáveis)

[Ver especificação completa](./projetos/projeto-02-dashboard-grid.md)

---

## 📖 Material de Apoio

### Leitura Obrigatória
- [CSS Flexbox - MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/CSS_layout/Flexbox)
- [CSS Grid - MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/CSS_layout/Grids)
- [CSS Animations - MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Animations)

### Vídeos Complementares
- Flexbox em 100 segundos
- CSS Grid - Curso completo
- Animações CSS do básico ao avançado

### Ferramentas Úteis
- [Flexbox Playground](https://flexboxfroggy.com/) - Jogo interativo
- [Grid Garden](https://cssgridgarden.com/) - Jogo interativo
- [Cubic Bezier](https://cubic-bezier.com/) - Visualizador de timing
- [Animista](https://animista.net/) - Biblioteca de animações
- [Responsively App](https://responsively.app/) - Teste responsividade

## ✅ Checklist de Conclusão

Antes de avançar para o Mês 3, certifique-se de que você:

- [ ] Domina Flexbox e consegue criar layouts complexos
- [ ] Entende CSS Grid e Grid template areas
- [ ] Consegue criar animações e transições suaves
- [ ] Implementa Media Queries corretamente
- [ ] Trabalha com CSS Variables para temas
- [ ] Conhece conceitos básicos de SASS/SCSS
- [ ] Completou os 2 projetos do mês
- [ ] Seu código passa em testes de responsividade

## 🎓 Avaliação do Módulo

### Critérios
- **Participação**: Presença e engajamento nas aulas
- **Exercícios**: Resolução das listas propostas
- **Projetos**: Qualidade e completude dos 2 projetos
- **Design Responsivo**: Funcionalidade em múltiplos breakpoints
- **Performance**: Otimização de animações e CSS

### Entregáveis
1. Repositório GitHub com projetos
2. Links para projetos publicados
3. README.md explicando técnicas utilizadas

---

## 📂 Estrutura de Arquivos

```
mes-02-css-avancado/
├── README.md (este arquivo)
├── aulas/
│   ├── aula-01-flexbox-intro.md
│   ├── aula-02-flexbox-propriedades.md
│   ├── aula-03-flexbox-cases.md
│   ├── aula-04-pratica-flexbox.md
│   ├── aula-05-grid-intro.md
│   ├── aula-06-grid-template.md
│   ├── aula-07-grid-avancado.md
│   ├── aula-08-pratica-grid.md
│   ├── aula-09-transicoes.md
│   ├── aula-10-animacoes.md
│   ├── aula-11-responsividade.md
│   ├── aula-12-pratica-animacoes.md
│   ├── aula-13-css-variables.md
│   ├── aula-14-sass-intro.md
│   ├── aula-15-design-systems.md
│   └── aula-16-apresentacoes.md
├── exercicios/
│   ├── 01-flexbox.md
│   ├── 02-grid.md
│   ├── 03-animacoes.md
│   └── 04-responsividade.md
├── projetos/
│   ├── projeto-01-layout-flexbox.md
│   └── projeto-02-dashboard-grid.md
└── recursos/
    ├── cheatsheet-flexbox.md
    ├── cheatsheet-grid.md
    ├── cheatsheet-animacoes.md
    ├── breakpoints-padrao.md
    └── links-uteis.md
```

---

**Pronto para dominar CSS avançado? Vamos para a [Aula 1](./aulas/aula-01-flexbox-intro.md)!** 🚀
